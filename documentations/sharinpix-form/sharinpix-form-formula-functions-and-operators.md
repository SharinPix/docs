# SharinPix Form Formula Functions and Operators

## Overview

{% hint style="info" %}
SharinPix Form Elements can be configured using Formulas. Formulas are critical for creating **dynamic, data-driven SharinPix Forms**. By using a combination of functions and operators, you can:

* [**Control Visibility**](form-features-conditional-visibility.md)**:** Show or hide form fields based on other user inputs or external data.
* [**Validate Input**](form-features-validations.md)**:** Ensure data meets specific criteria before submission.
* **Generate Content:** Calculate or display dynamic text based on the form's context.

This article covers the following:

* [SharinPix Form Formulas - Functions and Operators Overview](sharinpix-form-formula-functions-and-operators.md#functions-and-operators-overview)
  * [Operators](sharinpix-form-formula-functions-and-operators.md#operators)
  * [Logical functions](sharinpix-form-formula-functions-and-operators.md#logical-functions)
    * [BLANKVALUE](sharinpix-form-formula-functions-and-operators.md#blankvalue)
    * [ISBLANK](sharinpix-form-formula-functions-and-operators.md#isblank)
    * [NOT](sharinpix-form-formula-functions-and-operators.md#not)
    * [IF](sharinpix-form-formula-functions-and-operators.md#if)
    * [CASE](sharinpix-form-formula-functions-and-operators.md#case)
  * [List functions](sharinpix-form-formula-functions-and-operators.md#list-functions)
    * [JOIN](sharinpix-form-formula-functions-and-operators.md#join)
    * [REMOVEBLANKS](sharinpix-form-formula-functions-and-operators.md#removeblanks)
    * [LEN](sharinpix-form-formula-functions-and-operators.md#len)
    * [INCLUDES](sharinpix-form-formula-functions-and-operators.md#includes)
    * [COUNTMATCHES](sharinpix-form-formula-functions-and-operators.md#countmatches)
  * [Number List functions](sharinpix-form-formula-functions-and-operators.md#number-list-functions)
    * [SUM](sharinpix-form-formula-functions-and-operators.md#sum)
  * [Date functions](sharinpix-form-formula-functions-and-operators.md#date-functions)
    * [DATEVALUE](sharinpix-form-formula-functions-and-operators.md#datevalue)
    * [ADDDAYS](sharinpix-form-formula-functions-and-operators.md#adddays)
    * [DAYSBETWEEN](sharinpix-form-formula-functions-and-operators.md#daysbetween)
{% endhint %}

## Getting started

## Functions and Operators overview

<figure><img src="../.gitbook/assets/form func-1.png" alt=""><figcaption></figcaption></figure>

## Operators

<table><thead><tr><th width="67.328125">Operator</th><th width="128.12109375">Type</th><th width="172.94921875">Description</th><th width="305.53515625">Example</th><th>Result</th></tr></thead><tbody><tr><td><strong>-</strong></td><td>Arithmetic</td><td>Subtraction</td><td><mark style="color:red;"><code>Amount_Due - Discount</code></mark></td><td>Numerical Difference</td></tr><tr><td><strong>*</strong></td><td>Arithmetic</td><td>Multiplication</td><td><mark style="color:red;"><code>Quantity * Unit_Price</code></mark></td><td>Numerical Product</td></tr><tr><td><strong>/</strong></td><td>Arithmetic</td><td>Division</td><td><mark style="color:red;"><code>Total_Sales / Number_of_Reps</code></mark></td><td>Numerical Quotient</td></tr><tr><td><strong>+</strong></td><td>Arithmetic</td><td>Addition (also used for concatenating text strings)</td><td><p><mark style="color:red;"><code>Hours_Worked + 24</code></mark> (Numerical sum)</p><p><mark style="color:red;"><code>First_Name + " " + Last_Name</code></mark>(Text Concatenation)</p></td><td>Numerical Sum / Combined Text String</td></tr><tr><td><strong>></strong></td><td>Comparison</td><td>Greater than</td><td><mark style="color:red;"><code>Service_Years > 5</code></mark></td><td><mark style="color:red;"><code>true</code></mark> or <mark style="color:red;"><code>false</code></mark></td></tr><tr><td><strong>>=</strong></td><td>Comparison</td><td>Greater than or equal to</td><td><mark style="color:red;"><code>Hours_Worked >= 40</code></mark></td><td><mark style="color:red;"><code>true</code></mark> or <mark style="color:red;"><code>false</code></mark></td></tr><tr><td><strong>&#x3C;</strong></td><td>Comparison</td><td>Less than</td><td><mark style="color:red;"><code>Age &#x3C; 25</code></mark></td><td><mark style="color:red;"><code>true</code></mark> or <mark style="color:red;"><code>false</code></mark></td></tr><tr><td><strong>&#x3C;=</strong></td><td>Comparison</td><td>Less than or equal to</td><td><mark style="color:red;"><code>Issues_Count &#x3C;= 250</code></mark></td><td><mark style="color:red;"><code>true</code></mark> or <mark style="color:red;"><code>false</code></mark></td></tr><tr><td><strong>AND</strong></td><td>Logical</td><td>Returns <mark style="color:red;"><code>true</code></mark> if ALL expressions are true.</td><td><mark style="color:red;"><code>Tier = "Gold" AND Annual_Spend > 50000</code></mark></td><td><mark style="color:red;"><code>true</code></mark> or <mark style="color:red;"><code>false</code></mark></td></tr><tr><td><strong>OR</strong></td><td>Logical</td><td>Returns <mark style="color:red;"><code>false</code></mark> if ANY expression is true.</td><td><mark style="color:red;"><code>Region = "West" OR Region = "East"</code></mark></td><td><mark style="color:red;"><code>true</code></mark> or <mark style="color:red;"><code>false</code></mark></td></tr></tbody></table>

## Logical functions

## BLANKVALUE

Determines if an expression has a value and returns a substitute expression if it does not. If the expression has a value, it returns the value of the expression.

### Use

<mark style="color:red;">`BLANKVALUE(expression, substitute_expression)`</mark>

* **expression** - expression to be evaluated
* **substitute\_expression** - value to return when **expression** is blank

{% hint style="info" %}
**Info:**

A field is not empty if it contains a character, a blank space, or a zero. For example, a field that contains a space inserted with the spacebar is not empty.
{% endhint %}

### Formula Example

<mark style="color:red;">`BLANKVALUE(Department, "Undesignated")`</mark>

This formula returns the value of the **Department** field if it contains a value. If the Department field is empty, this formula returns the word _"Undesignated"_.

## ISBLANK

Determines if an expression has a value and returns <mark style="color:red;">`true`</mark> if it does not. If it contains a value, this function returns <mark style="color:red;">`false`</mark>.

### Use

<mark style="color:red;">`ISBLANK(expression)`</mark>

**expression** - expression to be evaluated.

### Formula Example

<mark style="color:red;">`ISBLANK(Department)`</mark>

This formula returns <mark style="color:red;">`true`</mark> if the **Department** field is empty. If the **Department** field contains a value, the formula returns <mark style="color:red;">`false`</mark>.

## NOT

Reverses the logical value of an expression. Returns <mark style="color:red;">`true`</mark> if the expression is <mark style="color:red;">`false`</mark>, and <mark style="color:red;">`false`</mark> if the expression is <mark style="color:red;">`true`</mark>.

### Use

<mark style="color:red;">`NOT(logical_expression)`</mark>

**logical\_expression** - condition to be evaluated.

### Formula Use

<mark style="color:red;">`NOT(ISBLANK(Department))`</mark>

This formula returns <mark style="color:red;">`true`</mark> if the **Department** field contains a value, and <mark style="color:red;">`false`</mark> if the **Department** field is empty.

## IF

Determines if expressions are <mark style="color:red;">`true`</mark> or <mark style="color:red;">`false`</mark>. Returns a given value if <mark style="color:red;">`true`</mark> and another value if <mark style="color:red;">`false`</mark>.

### Use

<mark style="color:red;">`IF(logical_test, value_if_true, value_if_false)`</mark>

* **logical\_test** - expression to be evaluated
* **value\_if\_true** - value to return if **logical\_test** is <mark style="color:red;">`true`</mark>
* **value\_if\_false** - value to return if **logical\_test** is <mark style="color:red;">`false`</mark>.

### Formula Example

<mark style="color:red;">`IF(Total > 500, "Eligible for Discount", "No Discount")`</mark>

This formula returns _**“Eligible for Discount”**_ if the **Total** field is greater than <mark style="color:red;">`500`</mark>. If **Total** is <mark style="color:red;">`500`</mark> or less, it returns _**“No Discount”**_.

## CASE

Checks a given expression against a series of values. If the expression is equal to a value, it returns the corresponding result. If it isn't equal to any of the values, it returns a default result.

### Use

<mark style="color:red;">`CASE(expression, value1, result1, value2, result2,..., else_result)`</mark>

* **expression** - field or value you want compared to each specified value.
* **value1, result1, value2, result2, ....**_**-**_ result and value pairs.
* **else\_result** - the value to return when the expression does not equal any values.

### Formula Example

<mark style="color:red;">`CASE(User.Department, "IT", 0.25, "Field", 0.15, 0)`</mark>

This formula returns a different discount rate based on the department entered.

* 25% on any person in the IT department.
* 15% for someone in the Field department.
* 0 is applied if the person doesn't belong to either department.

## List Functions

## JOIN

Combines the values of a **list field** into a single text string using a specified **separator** between each element

### Use

<mark style="color:red;">`JOIN(list, separator)`</mark>

* **list** – The list field you want to join
* **separator** – The text used to separate each value in the resulting string

### Formula Example

<mark style="color:red;">`JOIN(Rooms, ", ")`</mark>

This formula joins all values from the list returned by **Rooms**, separating each value with a comma and a space.

* If **Rooms** = <mark style="color:red;">`["Living room", "Bedroom", "Kitchen"]`</mark>, the formula returns <mark style="color:red;">`"Living room, Bedroom, Kitchen"`</mark>

## REMOVEBLANKS

Removes <mark style="color:red;">`undefined`</mark> and <mark style="color:red;">`""`</mark> from a list

### Use

<mark style="color:red;">`REMOVEBLANKS(list)`</mark>

**list** - The list field from which you want to remove <mark style="color:red;">`undefined`</mark> and <mark style="color:red;">`""`</mark>

### Formula Example

<mark style="color:red;">`REMOVEBLANKS(Room.Names)`</mark>

This formula removes <mark style="color:red;">`undefined`</mark> and <mark style="color:red;">`""`</mark> from the list returned by <mark style="color:red;">`Room.Names`</mark>

* If **Room.Names** = <mark style="color:red;">`["", "Bedroom", undefined]`</mark>, the formula returns <mark style="color:red;">`["Bedroom"]`</mark>

## LEN

Returns the number of characters in a text string or the number of items in a list field.

### Use

<mark style="color:red;">`LEN(text_or_list)`</mark>

**text\_or\_list** - field or expression whose length you want returned.

### Formula Examples

<mark style="color:red;">`LEN(PartNumber)`</mark>

This formula returns the number of characters in a **PartNumber** text field.

<mark style="color:red;">`LEN(SelectedProducts)`</mark>

This formula returns the number of selected items in the **SelectedProducts** list field.

* If **SelectedProducts =**<mark style="color:red;">`[“Laptop", "Monitor", "Keyboard"]`</mark> the formula returns <mark style="color:red;">`3`</mark>.

## INCLUDES

Determines whether a multi-select picklist, list field, or text string contains a specific value. Returns <mark style="color:red;">`true`</mark> if the value is found, and <mark style="color:red;">`false`</mark> if it is not.

{% hint style="warning" %}
**Note:**

This function is **case-sensitive** when checking for text values
{% endhint %}

### Use

<mark style="color:red;">`INCLUDES(list_or_text, value)`</mark>

* **list\_or\_text** - The multi-select picklist, list field, or text value you want to search.
* **value** - The value or substring you want to check for in the list or text.

### Formula Example

<mark style="color:red;">`INCLUDES(Regions, "North")`</mark>

* If **Regions** **=**<mark style="color:red;">`["North", "South"]`</mark>, it returns <mark style="color:red;">`true`</mark>**.**
* If **Regions =**<mark style="color:red;">`["South", "East"]`</mark>, it returns <mark style="color:red;">`false`</mark>**.**
* If **Regions =**<mark style="color:red;">`["north"]`</mark>, it returns <mark style="color:red;">`false`</mark> because the function is case-sensitiv&#x65;**.**

## COUNTMATCHES

Determines how many times a specified value appears in a list, or how many times a substring occurs in a text.

{% hint style="warning" %}
**Note:**

This function is **case-sensitive** when checking for text values.
{% endhint %}

### Use

<mark style="color:red;">`COUNTMATCHES(list_or_text, value)`</mark>

* **list\_or\_text** - The list or text field to search within.
* **value** - The exact value or substring to count.

### Formula examples

<mark style="color:red;">`COUNTMATCHES(Inspections.Status, "Passed")`</mark>

* This formula returns the number of times _“Passed”_ appears in the list returned by <mark style="color:red;">`Inspections.Status`</mark>.
* If <mark style="color:red;">`Inspections.Status`</mark> = <mark style="color:red;">`["Passed", "Passed", "Failed"]`</mark>, the formula returns <mark style="color:red;">`2`</mark>.

<mark style="color:red;">`COUNTMATCHES(Description, "error")`</mark>

* This formula returns how many times the substring **"error"** appears in the **Description** text.

## Number list functions

## SUM

Returns the total of all numbers in a list. Only numeric values are allowed; non-numeric values in the list will raise an error.

### Use

<mark style="color:red;">`SUM(number_list)`</mark>

**number\_list** - list containing only number values you want to add.

### Formula Example

<mark style="color:red;">`SUM(SalesAmounts)`</mark>

This formula returns the total of all numbers in the **SalesAmounts** list.

* If **SalesAmounts =**<mark style="color:red;">`[100, 200, 50]`</mark>, the formula returns **350**.

## Date functions

## DATEVALUE

Constructs a Date from a String. The format of the String depends on the local date format. Invalid strings or non-string characters will raise an error.

Read more on the date format on: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Date/parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse)

### Use

<mark style="color:red;">`DATEVALUE(date_string)`</mark>

**date\_string** - text that represents a specific calendar date and/or time.

### Formula Example

<mark style="color:red;">`DATEVALUE(SubmittedDate)`</mark>

This formula returns the Date object of the string provided.

* If **SubmittedDate** = "2025-12-12", the formula returns the Date object, Fri Dec 12 2025 04:00:00 GMT-0800 (Pacific Standard Time).

![](<../.gitbook/assets/Screenshot 2025-12-08 at 16.56.41 (1).png>)

## ADDDAYS

Adds the specified number of additional days to a Date.

### Use

<mark style="color:red;">`ADDDAYS(date_object, number_of_days)`</mark>

**date\_object** - Date object.

**number\_of\_days** - Integer that represents the number of days to be added.

### Formula Example

<mark style="color:red;">`ADDDAYS(CreatedAt, 14)`</mark>

This formula returns the new date, which is 14 days from the given date.

* If **CreatedAt** = "2025-12-12", the formula returns the Date object, Fri Dec 26 2025 04:00:00 GMT-0800 (Pacific Standard Time).

![](<../.gitbook/assets/Screenshot 2025-12-08 at 16.58.19 (1).png>)

## DAYSBETWEEN

Returns the number of days between the first and second date parameters.

**This method counts whole days only.**

If the first parameter occurs before or after the second parameter, the return value is negative.

### Formula Example

<mark style="color:red;">`DAYSBETWEEN(SubmittedAt, StartedAt)`</mark>

This formula returns the number of days between the date started and the date submitted.

* If **SubmittedAt** = "Sat Dec 20 2025 04:00:00 GMT-0800 (Pacific Standard Time)" and **StartedAt** = "Fri Dec 12 2025 04:00:00 GMT-0800 (Pacific Standard Time)" then the return value is 8.

### Use

<mark style="color:red;">`DAYSBETWEEN(date_object_1, date_object_2)`</mark>

**date\_object\_1** - Date object.

**date\_object\_2** - Date object.

![](<../.gitbook/assets/Screenshot 2025-12-08 at 17.01.06 (1).png>)
