Download Link: https://assignmentchef.com/product/solved-cse1142-assignment-3-simple-cargo-system-simulator
<br>
In this homework you will simulate a simple cargo system for a firm.

<ol>

 <li>In this system, there exists a list of forbidden items that cannot be transported. Create a two dimensional character array <em>forbiddenItems</em> to store the forbidden items.

  <ul>

   <li>Size of the first dimension of the array will be a constant value which is defined as a macro.</li>

  </ul></li>

</ol>

Therefore, if the value of the constant changes, then the size of the first dimension changes. You can write 6 as the initial value of the constant.

<ul>

 <li>You can assume that item names do not exceed 50 characters.</li>

 <li>If an item name consists of more than one word, these words are combined together with underscore “_” sign. For example, if the name of the item is “cutlery pack” it will be stored as “cutlery_pack” in the array.</li>

</ul>




<ol start="2">

 <li>Customers of the firm have unique customer numbers and the firm also keeps how many cargo transactions are done by each customer. To store the customer numbers and their transaction counts, create a two dimensional integer array <em>customers</em>.

  <ul>

   <li>The first dimension of <em>customers</em> array stores the customers. The firm can serve to at most 500 customers.</li>

   <li>The second dimension of the array should store the total number of transaction counts.</li>

   <li>Customer numbers should be greater than zero.</li>

   <li>For each valid transaction, total transaction count of the corresponding customer is incremented.</li>

  </ul></li>

</ol>




<ol start="3">

 <li>If a cargo is damaged, the firm should cover the loss. For this reason, the firm wants the customers to put a price on their goods before delivery. Create a two dimensional double array <em>transactions</em> to store approximate price of each transaction of the customers.

  <ul>

   <li>Each customer can make at most 730 transactions.</li>

   <li>Each row of this array belongs to a unique customer and row number of a customer is the same as the row number that his/her customer number is stored in the <em>customers</em></li>

  </ul></li>

</ol>

<ol start="4">

 <li>When you start the system a welcome message will appear on the screen and the system administrator starts to enter forbidden items.

  <ol>

   <li>Store the items entered by the system administrator into the <em>forbiddenItems</em></li>

   <li>Print “Do you want to start the system? 1 –&gt; Yes, 0 –&gt; No:” message and if the answer is equal to 0 end the program immediately.</li>

   <li>If the answer is equal to 1, then a user starts to write the transactions of the customers.</li>

   <li>The user first writes the customer number. If a customer with the entered number does not exist in the customers array you should add the customer. If there exists a customer with the entered number you will not add again. To understand whether a customer exists or not in the customer array you will write <strong>searchCustomer</strong> function :</li>

  </ol></li>

</ol>

 <strong>int searchCustomer(int customerNumber)</strong> : function searches the customers array and detects whether a customer with the given <em>customerNumber</em> exists or not and returns array index of the customer if finds in the array. Otherwise, the function should return -1.




<ol start="5">

 <li>After the first part, the user starts to enter items contained in the cargo.

  <ul>

   <li>For each item, number of it and its name is written. Items are separated from each other by using at least 1 space between the previous item name and number of the next item. For example, if 2 bags and 5 books are to be sent then the entered string can be written as :</li>

  </ul></li>

</ol>

◦ 2 bag 5 book

<ul>

 <li>You can assume that the list of items to be read does not exceed 500 characters.</li>

 <li>You should read items as a whole line (represented as a single string). In other words, you cannot read items partially, or using formatting.</li>

 <li>There can be many extra spaces in the string and there is no limit for the number of extra spaces.</li>

</ul>

◦ Please Enter the Content of the Cargo :2 bag 5 book 1 cutlery_pack 3 notebook 4 mirror

&#x25aa; For example, the entered string above, does not contain any space in the beginning of the string (before 2). There is just 1 space between the item counts and item names and there is no space at the end of the string (after mirror).

◦ Please Enter the Content of the Cargo :            2            bag

5          book             1 cutlery_pack               3

notebook              4                     mirror

&#x25aa; For example, the entered string above, contains more than one space in the beginning of the string (before 2), between item counts and item names (i.e between 2 and bag), between previous item name and next item count (i.e between bag and 5) and at the end of the string (after mirror).




<ol start="6">

 <li>After reading the content of the cargo, you will call <strong>getContent</strong> recursive function.

  <ul>

   <li><strong>void getContent(char content[], double *money)</strong></li>

   <li><em>char content[]</em> : content of the cargo that you have read.</li>

   <li><em>double *money</em>: calculated approximate value of the cargo. This value will be used in main function to print the price of the cargo content.</li>

   <li>This function stops when the content is empty or contains just spaces.</li>

  </ul></li>

</ol>

◦ The function should invoke <strong>checkFinish </strong>function firstly to check whether the content is empty or contains just spaces and call this function inside <strong>getContent</strong> function.

<ul>

 <li><strong>int checkFinish(char stringToCheck[])</strong></li>

 <li><em>char stringToCheck[]</em> : character array to be evaluated for being empty or containing just spaces.</li>

</ul>

<ul>

 <li>Then, you should remove forbidden items if there exists any in the content of the cargo.</li>

</ul>

◦ To remove forbidden items, write<strong> removeForbiddens </strong>recursive function and call it inside <strong>getContent</strong> function.

&#x25aa;<strong> void removeForbiddens(char content[], int itemIndex)</strong>

&#x25aa; <em>char content[]</em> : content of the cargo

<strong>functions and formatters to separate a string into words.</strong>

<table width="723">

 <tbody>

  <tr>

   <td width="96">&#x25aa;</td>

   <td colspan="3" width="627"><em>int itemIndex</em> : index of  last element of the <em>forbiddenItems</em> array. You should change the <em>itemIndex</em> for each recursive call.</td>

  </tr>

  <tr>

   <td width="96">&#x25aa;</td>

   <td colspan="3" width="627">This function checks whether any of the forbidden items is contained in the content of the cargo or not. It starts checking from the last element of the <em>forbiddenItems</em> array and stops when the first element is checked. If it finds any forbidden item, that item and its count is removed from the content string. <strong>Since this function is a recursive function and calls for itself you cannot write for/while loop(s) to iterate through all elements of the <em>forbiddenItems</em> array.</strong></td>

  </tr>

  <tr>

   <td width="96">&#x25aa;</td>

   <td colspan="3" width="627">A specific forbidden item can exist in the content more than one time and repetitive occurrences should also be removed from the content. <strong>Since this function is a recursive function and calls for itself you cannot write for/while loop(s) to check repetitive occurrences of forbidden items.</strong></td>

  </tr>

  <tr>

   <td rowspan="3" width="96">&#x25aa;</td>

   <td colspan="3" width="627">To check the occurrences of each forbidden item in an order, you should call the <strong>searchWord</strong> function. <strong>searchWord</strong> function searches for occurrence of a string in another string.</td>

  </tr>

  <tr>

   <td rowspan="2" width="24"></td>

   <td colspan="2" width="603"><strong>int searchWord(char str1[], char str2[])</strong></td>

  </tr>

  <tr>

   <td width="24">◦</td>

   <td width="579">occurrence of string <em>str2</em> in string <em>str1</em> is checked.</td>

  </tr>

  <tr>

   <td width="96"> </td>

   <td width="24"> </td>

   <td width="24">◦</td>

   <td width="579">this function determines the start and end index of <em>str2</em> in <em>str1</em> if it exists in <em>str1</em>. If <em>str2</em> = mirror, start and end indexes are shown below for <em>str1</em> (given below)&#x25aa; 2            bag         5          book             1 cutlery_pack               3 notebook              14</td>

  </tr>

  <tr>

   <td width="96">   </td>

   <td width="24">  </td>

   <td width="24">◦◦◦</td>

   <td width="579">      mirror      5   knifeend = index of r                                                                 start = index of 1 <strong>searchWord</strong> function returns 1 if <em>str2</em> occurs in <em>str1</em>, returns 0 otherwise.<strong>You should write your own function and you cannot use built-in functions to compare strings.</strong><strong>You should deal with extra spaces; therefore, you cannot use built-in </strong></td>

  </tr>

 </tbody>

</table>







◦ If <strong>searchWord</strong> function finds a forbidden item, calls <strong>reconstruct </strong>function to remove this item from the string. Start and end parameters of the <strong>reconstruct</strong> function will be the start and end indices that you have found in <strong>searchWord</strong> function.

&#x25aa;<strong> void reconstruct(char stringToConstruct[], int start,int end)</strong>

&#x25aa;<strong> reconstruct</strong> function updates the <em>stringToConstruct</em> char array by extracting the substring between <em>start</em> and <em>end</em> indices. You should keep the extracted substring in <em>stringToSeach</em> char array.

 For example, if string below (a) is entered as the content of the cargo, first forbidden items are removed from the string. 12 knife is removed from the string firstly, since the search is done starting from last element of the <em>forbiddenItems</em> array (b). Secondly, 5 knife is removed because knife occurs for the second time (c). Thirdly, 1 cutlery_pack is removed from the string (d). Finally, 14 mirror is deleted from the string (e). The text is painted with blue color and spaces are printed as dots to make spaces visible to you. a)

<ol>

 <li>b)</li>

</ol>

c)

<ol>

 <li>d)</li>

 <li>e)</li>

</ol>

Figure 1




<ol start="7">

 <li>After removing forbidden items, remaining items are separated from the string. For this purpose, <strong>seperateItem</strong> function is called in <strong>getContent</strong> function to detect and separate each item from the string.

  <ul>

   <li><strong>void seperateItem(char wholeString[], int *itemCount, char item[])</strong>  <em>char wholeString[]</em> : is the string that contains items.</li>

   <li><em>int *itemCount</em>: number of the separated item will be stored in this address.</li>

   <li><em>char item[]:</em> is the item to be detected and separated from the string.</li>

   <li>For example, if the string in Fig. 1e is the first argument of the <strong>separateItem</strong> function, “2 bag” is stored in <em>item[]</em> array and 2 is stored in address pointed by <em>itemCount</em></li>

   <li>This function calls <strong>reconstruct</strong> function to separate “2 bag” from the <em>wholeString</em>.</li>

   <li>Since <strong>getContent</strong> function is a recursive function you will not call <strong>separateItem</strong> function in while/for loop(s).</li>

  </ul></li>

</ol>




<ol start="8">

 <li>For each separated item you will request approximate price for it in <strong>getContent</strong> function and calculate the cumulative sum of them</li>

</ol>

<ul>

 <li>For example, after obtaining string in Fig.1e, the program wants approximate value for notebook, book and bag items :</li>

</ul>







<ul>

 <li>Here price is calculated as (1.2 * 3) + (10 * 5)  + (2 * 2.2 )  = 58.0 in the <strong>getContent</strong> function and printed to the screen in <strong>main</strong></li>

 <li>If the user enters an empty string or a string that contains just spaces than the price should be calculated as 0.</li>

 <li>If the item count of an item is less than or equal to zero price will not be calculated for that item and a warning message should be printed on the screen.</li>

</ul>




<ol start="9">

 <li>In <strong>main</strong> function, you will read customer numbers and content of the cargo until a negative value is entered for a customer number.

  <ul>

   <li>If a customer number is entered for the first time, you will add this customer as a row of the 2 dimensional <em>customers</em> The column of the <em>customers</em> array should keep the total number of transactions belonging to customers. If there exists a valid transaction for a customer, you will increment the number of valid transactions stored in the column of corresponding customer row.</li>

   <li>Calculated price of valid transactions will be stored in the <em>transactions</em> array in the same row as the <em>customers</em> array starting from the first empty column.</li>

   <li>If a customer number is entered before, you will not add this customer again to the <em>customers</em> If the new transaction is a valid one, then increment the transaction count of the customer. Additionally, you should add the calculated price for the second transaction to the corresponding row of the <em>transactions</em> array.</li>

  </ul></li>

 <li>Invalid transactions:

  <ul>

   <li>If an empty string or a string which contains just spaces is entered for the content of the cargo, then the transaction count of the customer should not be incremented. However, if this customer number is entered for the first time you will add this customer number to customers array.</li>

   <li>If content of a cargo consists of just forbidden items; then, this is an invalid transaction and will not be added to the <em>transactions</em> However, if this customer number is entered for the first time you will add this customer number to customers array.</li>

   <li>If the user enters 0 as the price of the all items in the cargo, then this transaction will not be added to the <em>transactions</em> array because the price is equal to 0. However, if this customer number is entered for the first time you will add this customer number to <em>customers</em></li>

   <li>If all item counts are less than or equal to 0, then this transaction will not be added to the <em>transactions</em> array because the price is equal to 0. However, if this customer number is entered for the first time you will add this customer number to <em>customers</em></li>

   <li>If not all but some of the item counts are less than or equal to 0 and user enters 0 as the price of all remaining items, then this transaction will not be added to the <em>transactions</em> array because the price is equal to 0. However, if this customer number is entered for the first time you will add this customer number to <em>customers</em></li>

  </ul></li>

 <li>When a negative number is entered for the customer number, call <strong>printCustomers </strong>functionto print all customer numbers and their total transaction count and price of each transaction.

  <ul>

   <li><strong>void printCustomers()</strong></li>

  </ul></li>

 <li>Sample output:</li>

</ol>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>This is a simple scenario to test your implementation. There might be other test cases too. Therefore, please pay attention to use the function and variable names in your implementations. You cannot decrease the number of functions. </strong>

<strong> </strong>