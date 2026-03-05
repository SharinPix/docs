---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: false
  tags:
    visible: true
---

# SharinPix Aggregate Search (Developer-Oriented)

This article, we will see how to personalize the SharinPix search when querying images from a large number of records.

The following sections demonstrate how to use the SharinPix Album to perform a personalized aggregate search to display all the images present on the **Contact** records related to a particular **Account** record. This can be done by embedding the SharinPix component inside an **Iframe**.

Therefore, you will need:

* An [Apex Class Controller](sharinpix-aggregate-search-developer-oriented.md#apex-controller) that will build the query and generate the token. In the Apex controller you will need to:
  * [build a token to initiate the SharinPix search](sharinpix-aggregate-search-developer-oriented.md#build-a-token-to-initiate-the-sharinpix-search)
  * [split in group of 20 album IDs](sharinpix-aggregate-search-developer-oriented.md#split-records-in-groups-of-20-album-ids)
  * [build the query string for each groups and generate the token for each](sharinpix-aggregate-search-developer-oriented.md#build-query-strings-and-generate-tokens-for-each-groups)
* A [Visualforce Page](sharinpix-aggregate-search-developer-oriented.md#visualforce-page) that will embed the Iframe

## Apex Controller

The Apex Class controller implementation can be found in the following sections.

### Build a token to initiate the SharinPix search

```apex
public String getSearchUrl() {
  loadParams = new Map<String, Object> {
    'path' => '/search?search_bar=false',
    'q' => '',
    'download' => true,
    'download_filename' => acc.Name,
    'download_filenames' => acc.Name
  };
  return clientInstance.token(loadParams);
}
```

### Split records in groups of 20 album IDs

```apex
public List<String> slice(List<String> original, Integer startIndex, Integer endIndex) {
  if (startIndex == 0 && endIndex == original.size()) {
  	return original;
  }
  List<String> sliced = new List<String>();
  for (Integer i = startIndex; i < endIndex && i < original.size(); i++) {
  	sliced.add(original[i]);
  }
  return sliced;
}
```

### Build query Strings and generate tokens for each groups

```apex
public List<Contact> cnt;
public Account acc;

public SharinPixAggregateSearch(ApexPages.StandardController stdCtrl) {
  Id accId = stdCtrl.getId();
  cnt = [SELECT Id FROM Contact WHERE AccountId = :accId];

  acc = [SELECT Name FROM Account WHERE Id = :accId];
  setParameters();
}

public void setParameters() {
	Map<String, Object> query = new Map<String, Object>();
	list<string> ids = new list<string>();
    for (Contact contact : cnt) {
      ids.add('"'+contact.Id+'"');
    }

    tokens = new List<String>();
    for (Integer i = 0; i < ids.size(); i += 20) {
      List<String> slicedIds = slice(ids, i, i + 20);
      if (slicedIds.size() == 0 || String.isBlank(slicedIds[0])) return '';
      String queryStr = '"' + String.join(albumIds, '" "') + '"';

      params = new Map<String, Object> {
        'path' => '/search?search_bar=false',
        'q' => queryStr,
        'download' => true,
        'download_filename' => acc.Name,
        'download_filenames' => acc.Name
      };

      tokens.add(clientInstance.token(params));
    }
}
```

## Visualforce Page

The code snippet below shows the implementation of the Visualforce Page used to display the search results on a SharinPix Album:

```html
<script>
  const eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
  const eventer = window[eventMethod];
  const messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";
  var tokens = JSON.parse("{! JSENCODE(parameters) }");

  document.getElementById("sharinpixIframe").onload = function() {
  	this.contentWindow.postMessage({ token: "{! generateBaseToken }" }, 'https://app.sharinpix.com');
  }

  window.addEventListener('message', event => {
  	const { origin, data: { name, componentId } } = event
  
  	if (origin !== 'https://app.sharinpix.com') { return }
    if (name === 'search-ready') {
      for(i = 0; i < tokens.length; i++) {
        document.getElementById("sharinpixIframe").contentWindow.postMessage({ payload: tokens[i], name: 'search-aggregate' }, 'https://app.sharinpix.com');
      }
    }
  });
</script>
```

{% hint style="danger" %}
**Note:**

The SharinPix Aggregate Search is limited to 500 results.

If your search includes more than 500 images, it stops once the limit is reached and the extra results are not displayed.
{% endhint %}
