# **PerfectPayMAUI**

Another great project led by Hector Perez on his Udemy course: *.NET MAUI course with Visual Studio 2022 creating PROJECTS*

This android app takes in a bill total, the amount of desired tip, and the number of people splitting the check. The program then calculates the amount of the bill that will be paid by each person.
The XAML is comprised of a Grid container that is broken down into 2 sections, also Grid layouts. The top Grid holds the labels that display the pertinent bill information: the bill total (bill with tip), then a BoxView separating it from the information on the right half of the Grid, the subtotal (bill without tip), and the tip amount. 

The bottom Grid container houses the functionality of the application:
- An entry form that locks the Keyboard to Numeric, where the user can input their bill total
- 3 buttons that allow the user to quickly select from 10%, 15%, and 20% tip amounts
- A slider, which allows the users to select a tip amount all the way up to 50%
- 2 buttons at the bottom which enable the user to increase/decrease the number of people splitting the check

The codebehind implements a method and the EventHandlers that make the application function:
- *CalculateTotal()* calculates the tip, tip per person, subtotal, and total by person
  - It then updates these values for each of the x:Name components in the XAML so that the numbers are displayed correctly on the Page
  - This method is called in each subsequent EventHandler so that the values are constantly reflecting the changes made by the user
- *txtBill_Completed()* parses the string from the entry form and converts it to a double, then assigns the value to the Property *bill*
- *sldTip_ValueChanged()* casts the slider value to an int, and then updates *lblTip*'s text with string interpolation
- *Button_Clicked()* casts the Event's sender as a Button so that its properties can be accessed, replaces the % with an empty string so that the value can be parsed as an int, and subsequently updates the slider value with the value from the tip button that was clicked
- *btnMinus_Clicked()* first checks that the value of Property *noPersons* is at least 1 (**somebody's gotta pay the bill**), and then allows the user to reduce the amount of people splitting the check down to no fewer than one person and updates *lblNoPersons*'s text
- *btnPlus_Clicked()* allows the users to add people splitting the check one at a time per click, and then updates *lblNoPersons*'s text
