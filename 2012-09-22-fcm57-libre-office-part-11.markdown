---
layout: post
title: "57期 - Libre Office - 第11部分"
date: 2012-09-22 13:35
comments: true
categories: issue57 HOW-TO Libre-Office
---

Written by Elmer Perry

In the last part of this series, we added the data and formulas for our budget worksheet. The end result, while functional, is not very pretty or easy to read. Now, we will add some styles to our spreadsheet to help make the worksheet not only more pleasant to look at, but easier to read and find specific data. We will accomplish this using cell styles.
 
Back in part 3 of this series, we used paragraph styles to format the paragraphs in our documents. Cell styles are Calc's equivalent to paragraph styles. Cell styles allow us to specify the border, font, background color, font effects, number format, alignment and cell protection. Styles help to create consistency throughout the spreadsheet. 

## Section and Column Title Styles

We'll start by creating styles for our section titles and column titles. Click on the styles icon (above).
Now, we will create a style for our column titles based on the Section style. Basing one style on another style makes it quick and easy to just add and change the differences between the styles. In the Styles and Formatting windows, right-click on the Section style and select New. Give the style the name “Column Title.” You will notice that the style is linked to the Section style. If you browse through the tabs, you will see all the settings we made for the Section style are already set. To distinguish column titles from sections, we will give them a different background color. On the Background tab, select a suitable light color for the background, such as Blue 8. 

## Applying the Section and Column Title Styles

Now, we can apply our two new styles to cells in our spreadsheet. The sections are “Income This Period”, “Assets”, and “Expenses”. Select the cells for these items and double-click on the Section style in the Styles and Formatting window. You can select more than one cell and apply the style all at once. For example, highlight all the column titles under Income (Source and Amount) and double-click on the Column Title style. Do the same for the column titles under the other two sections. 

## Editable, Total, and Date Styles

Editable items are the items in our budget spreadsheet that we will need to change from use to use. These are most of the cells under the column titles, except those that contain formulas - which are our total cells. We will first create the Editable style and use it as the link for our Total and Date styles. 

In the Styles and Formatting window, right-click on the default style and select New. Give the new style the name “Editable”. On the Number tab, select currency and your currency type. Set your font and font size on the font tab. I suggest a font size of at least 12 points. Make sure the font style is regular (not bold or italic). On the border tab, create light gray borders on the left and right. You can accomplish this by clicking on the third box under defaults. Make sure that the Protected box is unchecked on the Cell Protection tab. 

Now, we will create the Total styles by linking it with the Editable style. Right-click on the Editable style in the Style and Formatting window, and select New. Once again, we are starting with an exact copy of the style we right-clicked. Name the style “Total”. We will make changes to distinguish our totals from ordinary items. On the Font tab, change the style to bold. On the background tab, select a darker gray color than the light gray we used for the borders - like gray or gray 40%. Finally, check Protected on the Cell Protection tab. 

Apply the styles much in the same manner as we did previously. You will notice that if you apply the Editable style to the date column under expenses, you get a strange result for your dates (probably ####). That's because it was converted into currency. Right-click the Editable style and create a new style named “Dates”. All we need to do here is change the number type to Date and select a simple numeric date style on the Numbers tab.

## Conditional Formatting

We need a way to break up the big block of data under the Expenses section. We could just put borders around them, but large groups of bordered boxes look dull. Instead, we will highlight all the even rows with light gray. We also want to do this quickly. For this we will use conditional formatting. 

    ISEVEN(ROW())

With this formula, whatever style we choose will only apply to the even rows. For the cell style, click on the New Style button. Give the style the name “Editable Highlight” and link it to the Editable style. On the Borders tab, change the border color from light gray to gray. Move to the Background tab and change the background color to light gray. Click OK to save the changes. You will notice the Cell style is now Editable Highlight. Click OK and you will see the even number rows are highlighted in light gray. 

Unfortunately, this has the side effect of changing our dates again, but that is easily fixed by doing the same thing with the Date style. Select all the dates in the Expenses section. Format > Conditional Formatting. Once again use the formula ISEVEN(ROW()). Click on the New Style button and name the new style “Dates Highlight”. Link the style with Dates style. Change the border color to gray and the background to light gray. OK to save the style, and OK to apply the conditional formatting. 

## Finishing Touches

Just a few simple things to make all things even. If you have more than two items in the Income section, you can add the highlights to it as well using conditional formatting and the Highlight Editable style. Also, you can right justify the “Total Expenses” and “Total Payments” labels at the bottom.

Now, to test run your spreadsheet. Remember, we protected the cells we didn't want to change. Tools > Protect Document > Sheet. You can enter a password to password-protect the document, or just click OK to protect it without a password. If you try to edit one of the protected cells you will get a message window saying the cell is protected. However, the unprotected cells are easily edited as before. Using cell protection is a good way to keep your formulas from getting changed once you have the spreadsheet set up and working the way you want it. 

In the next part of this series, we will prepare our spreadsheet for printing by adding a header and footer to the page, and looking into our printing options. 


Elmer Perry's history of working, and programming, computers involves an Apple IIE, adding some Amiga, a generous helping of DOS and Windows, a dash of Unix, and blend well with Linux and Ubuntu.
