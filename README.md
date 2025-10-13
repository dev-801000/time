# PRACTICAL NO 1

## AIM :-
Install Selenium IDE and create a test suite containing a minimum of 4 test cases for different web page formats (e.g., HTML, XML, JSON, etc.).

---

## STEPS:-

1). Open your browser, search for “Selenium IDE” and click on the first link. Add the “Selenium IDE” extension to your browser.

2). For testing, we need a test case suite, so we create a Web-Application in NetBeans IDE.
    Open NetBeans IDE  
    Go to File and click on New Project  
    Select Java Web  
    Select Web Application  
    Add Apache Tomcat server  
    Click on Finish  

3). Write the following code for “ARITHMETIC OPERATIONS” test case suite:  

<index.html>
```html
<!DOCTYPE html> 
<html> 
<head> 
<title>Prac 1</title> 
<script language ="javascript"> 
function addition(){ 
var num1 = parseInt(document.arithmetic.n1.value); 
var num2 = parseInt(document.arithmetic.n2.value); 
var result = num1 + num2; 
document.arithmetic.res.value = result; 
} 
function subtraction(){ 
var num1 = parseInt(document.arithmetic.n1.value); 
var num2 = parseInt(document.arithmetic.n2.value); 
var result = num1 - num2; 
document.arithmetic.res.value = result; 
} 
function multiplication(){ 
var num1 = parseInt(document.arithmetic.n1.value); 
var num2 = parseInt(document.arithmetic.n2.value); 
var result = num1 * num2; 
document.arithmetic.res.value = result; 
} 
function division(){ 
var num1 = parseInt(document.arithmetic.n1.value); 
var num2 = parseInt(document.arithmetic.n2.value); 
var result = num1 / num2; 
document.arithmetic.res.value = result; 
} 
</script> 
</head> 
<body> 
<h1 align ="center">Arithmetic Operations</h1> 
<form name="arithmetic"> 
<table border="1" align="center"> 
<tr> 
<td> Number 1: </td> 
<td> <input type="text" name="n1" size="20"> </td> 
</tr> 
<tr> 
<td> Number 2: </td> 
<td> <input type="text" name="n2" size="20"> </td> 
</tr> 
<tr> 
<td colspan="2"> 
<input type="button" name="Add" value="addition" onclick="javascript:addition();">&nbsp; 
<input type="button" name="Sub" value="subtraction" onclick="javascript:subtraction();">&nbsp; 
<input type="button" name="Mul" value="multiplication" onclick="javascript:multiplication();">&nbsp; 
<input type="button" name="Div" value="division" onclick="javascript:division();">&nbsp; 
</td> 
</tr> 
<tr> 
<td colspan="2"> Result is : <input type="text" name="res" size="20" value=""> </td> 
</tr> 
</table> 
</form> 
</body> 
</html>
```

<newjsp.jsp>

```jsp
<%@page contentType="text/html" pageEncoding="UTF-8"%> 
<!DOCTYPE html> 
<html> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
<title>JSP Page</title> 
</head> 
<body align="center"> 
<h1>Test Cases IDE</h1> 
<a href="index.html">Arithmetic Operations</a> 
</body> 
</html>
```

4). Run this JSP file from NetBeans.

    It will then open up in a browser.
   
    Then from the browser, open the link.
   
    Now you’ll be redirected to ARITHMETIC OPERATIONS page.
   
    Copy the URL of the page and open “Selenium IDE” extension.

5). Record a new test project in Selenium IDE.

 Name your project.

 Paste that URL here and click Start Recording.

 A new tab will be opened, maximize that tab (this tab is your working tab for recording).

 Perform your task, remember each click gets recorded so avoid making unnecessary clicks.

 Click on Stop Recording.
 Just as you stop your recording, you’ll be prompted to Name your new test, provide a name and click on OK.
 Now, to see the recording click on Run Current Test.


---


# PRACTICAL NO 2

## AIM :-
Conduct a test suite for two different websites using Selenium IDE. Perform various actions like clicking links, filling forms, and verifying content.

---

## STEPS:-

1). Open your browser, search for “Selenium IDE” and click on the first link. Add the “Selenium IDE” extension to your browser.

2). For testing, we’ll choose “redbus.in” as our first website. We’ll be checking some Selenium IDE Commands like assertText, verifyTitle, storeText, echo.  
    Now Google, “Redbus.in”.  
    Copy the URL of the page and open “Selenium IDE” Extension.  
    Now, Click on Record a new test project in a project  
    Provide a name for your project.  
    Paste that URL here and click on Start Recording.  
    A new tab will be opened, maximize that tab (this tab is your working tab for recording).  
    Now we’ll make use of command verifyTitle. (This command verifies title of the webpage and keeps on continuing the execution.) So anywhere on the window, do Right Click > select Selenium IDE > click Verify Title.  
    Now after filling the FROM, TO, ONWARD DATE, we proceed further by clicking on Search Buses.  
    Now we’ll make use of command assertText. (This command verifies particular text of the webpage and stops the execution of testcase if the match isn’t found.) So, we want to make sure that our automated testcase chooses our specified Bus Provider. To ensure that, here we do Right Click over the name of the bus provider > then select Selenium IDE > and click Assert Text.  
    Now we’ll make use of command storeText. (This command stores the text value of page element into variable for future use.) Here we’ll store the price of the ticket. So, we select the price > right click over it > select Selenium IDE > click Store Text.  
    Now Selenium IDE will prompt us to enter the name of the variable in which that price will be stored.  
    After clicking OK, we can see how the target is automatically mapped to the css attribute of the page, and our price is stored.  
    Now we’ll make use of command echo. (This command is used to display text (comments, notes) and/or the stored value of variables in the log area of Selenium IDE.) Here we’ll display the price of the ticket from the variable “price” that we stored during the use of storeText command. To create a new command, we just click onto the next line and enter our command.  
    We’ll enter the Command name echo, & Value ${price} because we are calling the created variable “price” from this command.  
    Click on Stop recording and provide a name for test.  
    Now we’ll Run current test.  
    After the test gets completed, we can see the echo: 3000 in the log area of Selenium IDE showing the output of the echo command. Here we can see how 3000 is stored in variable “price” by storeText command, and that variable is then called by the echo command, which is then returning the value fetched from the page.

---

## OUTPUT :-

- Successfully recorded test cases in Selenium IDE for Redbus.in.  
- Commands used include **verifyTitle**, **assertText**, **storeText**, and **echo**.  
- The price of the ticket is stored in a variable using storeText and displayed using echo command.  
- Selenium IDE executes all recorded actions to validate content and functionality of the website.



---


# PRACTICAL NO 3

## AIM :-
Write a program using Selenium WebDriver to automate the login process on a specific web page. Verify successful login with appropriate assertions.

---

## CODE :-
```java
package hello;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.remote.DesiredCapabilities;

public class hello {
    static String drivePath ="D:\\STQA\\Selenium\\geckodriver.exe";
    public static WebDriver driver;

    public static void main(String[] args) {
        System.out.println("Hi.. We are Testing the RC server");
        System.out.println("Selenium Demo");

        System.setProperty("webdriver.gecko.driver", drivePath);
        DesiredCapabilities capabilities = DesiredCapabilities.firefox();
        capabilities.setCapability("marionette", true);

        driver = new FirefoxDriver();
        driver.get("http://www.google.com");
        driver.manage().window().maximize();

        driver.quit();
    }
}

```


---


# PRACTICAL NO 4

## AIM :-
Write a program using Selenium WebDriver to update 10 student records in an Excel file. Perform data manipulation and verification.

---

## STEPS:-

1). Download & Install Selenium IDE.

2). For testing WebDriver for verifying Excel sheet, we have to provide script.  
    Open Eclipse IDE  
    Select a Workspace for your project  
    In Eclipse IDE, click on create a new java project  
    In New Java Project window, provide a Project Name, leave the settings default and click on finish  
    From left panel, Left click on project name, go to Build Path and select Configure Build Path  
    In Properties window, select Java Build Path from left panel, then select Libraries Tab  
    In Libraries Tab, select Classpath and click on Add External JARs  
    After Adding JAR files, click on Apply and Close  
    From menu bar, click on Help and open Eclipse Marketplace  
    In Eclipse Marketplace window, search for TestNG for Eclipse and click on install  
    Click on Confirm for proceeding with the download  
    Accept the Terms and click on Finish  
    From left panel, Left click on project name, go to Build Path and select Add Libraries  
    In Add Library window, select TestNG and click on Next  
    From left panel, Left click on project name, go to New and click on Class  
    In New Java Class window, provide a name and click on Finish  

3). Create 2 Excel sheets for this project:  
    `Students.xls` – Input Excel file with student records  
    `results.xls` – Output Excel file (must be empty, will be used for results)  

4). Write the following code for checking WebDriver:

```java
package StudentResult;

import jxl.Sheet;
import jxl.Workbook;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;
import jxl.write.*;
import java.io.*;

public class StudentResult {
    @BeforeClass
    public void f1() {}

    @Test
    public void testImportExport1() throws Exception {
        FileInputStream f1 = new FileInputStream("D:\\STQA\\Selenium\\Student.xls");
        Workbook w = Workbook.getWorkbook(f1);
        Sheet s = w.getSheet(0);
        String a[][] = new String[s.getRows()][s.getColumns()];
        FileOutputStream f0 = new FileOutputStream("D:\\STQA\\Selenium\\results.xls");
        WritableWorkbook wwb = Workbook.createWorkbook(f0);
        WritableSheet ws = wwb.createSheet("result1", 0);

        for(int i=0; i<s.getRows(); i++) {
            for(int j=0; j<s.getColumns(); j++) {
                a[i][j] = s.getCell(j,i).getContents();
                Label l2 = new Label(j,i,a[i][j]);
                ws.addCell(l2);
                Label l1 = new Label(6,0,"Result");
                ws.addCell(l1);
            }
        }

        for(int i=1; i<s.getRows(); i++) {
            for(int j=2; j<s.getColumns(); j++) {
                a[i][j] = s.getCell(j,i).getContents();
                int x = Integer.parseInt(a[i][j]);
                if(x>35) {
                    Label l1 = new Label(6,i,"Pass");
                    ws.addCell(l1);
                } else {
                    Label l1 = new Label(6,i,"Fail");
                    ws.addCell(l1);
                    break;
                }
            }
        }

        wwb.write();
        wwb.close();
    }
}
```


---


# PRACTICAL NO 5

## AIM :-
Write a program using Selenium WebDriver to select the number of students who have scored more than 60 in any one subject (or all subjects). Perform data extraction and analysis.

---

## STEPS:-

1). Download & Install Selenium IDE.

2). For testing WebDriver for verifying Excel sheet, we have to provide script.  
    Open Eclipse IDE  
    Select a Workspace for your project  
    In Eclipse IDE, click on create a new java project  
    In New Java Project window, provide a Project Name, leave the settings default and click on finish  
    In Properties window, select Java Build Path from left panel, then select Libraries Tab  
    In Libraries Tab, select Classpath and click on Add External JARs  
    After Adding JAR files, click on Apply and Close  
    From menu bar, click on Help and open Eclipse Marketplace  
    In Eclipse Marketplace window, search for TestNG for Eclipse and click on install  
    Click on Confirm for proceeding with the download  
    From left panel, Left click on project name, go to Build Path and select Add Libraries  
    In Add Library window, select TestNG and click on Next and Finish  
    From left panel, Left click on project name, go to New and click on Class  
    In New Java Class window, provide a name and click on Finish  

3). Create 2 Excel sheets for this project:  
    `Students.xls` – Input Excel file with student records  
    `results1.xls` – Output Excel file (must be empty, will be used for results)  

4). Write the following code for checking WebDriver:

```java
package CountStud;

import jxl.*;
import jxl.write.*;
import java.io.*;
import org.testng.annotations.Test;

public class CountStud {
    @Test
    public void testImportExport1() throws Exception {
        FileInputStream f1 = new FileInputStream("D:\\STQA\\Selenium\\Student.xls");
        Workbook w = Workbook.getWorkbook(f1);
        Sheet s = w.getSheet(0);
        String a[][] = new String[s.getRows()][s.getColumns()];
        FileOutputStream f0 = new FileOutputStream("D:\\STQA\\Selenium\\result1.xls");
        WritableWorkbook wwb = Workbook.createWorkbook(f0);
        WritableSheet ws = wwb.createSheet("Result", 0);
        int c = 0;

        for(int i=0; i<s.getRows(); i++) {
            for(int j=0; j<s.getColumns(); j++) {
                if(i>=1) {
                    String b = s.getCell(3, i).getContents();
                    int x = Integer.parseInt(b);
                    if(x < 60) {
                        c++;
                        break;
                    }
                }
                a[i][j] = s.getCell(j, i).getContents();
                Label l2 = new Label(j, i-c, a[i][j]);
                ws.addCell(l2);
            }
        }

        wwb.write();
        wwb.close();
    }
}
```


---


# PRACTICAL NO 6

## AIM :-
Write a program using Selenium WebDriver to provide the total number of objects present or available on a web page. Perform object identification and counting.

---

## CODE :-
```java
package CountLink;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.remote.DesiredCapabilities;

public class CountLink {
    static String driverPath = "D:\\STQA\\Selenium\\geckodriver.exe";
    public static FirefoxDriver driver;

    public static void main(String[] args) {
        System.setProperty("webdriver.gecko.driver", driverPath);
        DesiredCapabilities capabilities = DesiredCapabilities.firefox();
        capabilities.setCapability("marionette", true);

        driver = new FirefoxDriver();
        driver.get("http://www.wikipedia.com");

        java.util.List<WebElement> Links = driver.findElements(By.tagName("a"));
        System.out.println("Total links are " + Links.size());

        for(int i=0; i<Links.size(); i++) {
            System.out.println("Links " + i + " Link name " + Links.get(i).getText());
        }
    }
}
```





# PRACTICAL NO 7 
AIM: Write a program using Selenium WebDriver to get the number of items in a list or combo box on a web 
page. Perform element identification and counting 
Code:- 
Create a web page consisting of a combo box with multiple values.
 
  ComboBox.html 
 ```<html> 
<body> 
<select id='combo'> 
<option>Volvo</option> 
<option>Express</option> 
<option>Mercedes</option> 
<option>RajaHamsa</option> 
</select> 
</body> 
</html> 
1). Write the following code for checking Webdriver. 
package ComboBox; 
import java.util.List; 
import org.openqa.selenium.By; 
import org.openqa.selenium.WebDriver; 
import org.openqa.selenium.WebElement; 
import org.openqa.selenium.firefox.FirefoxDriver; 
import org.openqa.selenium.remote.DesiredCapabilities; 
import org.openqa.selenium.support.ui.Select; 
public class ComboBox { 
static String driverpath = "D:\\STQA\\Selenium\\geckodriver.exe"; 
public static WebDriver driver; 
public static void main(String[] args) { 
System.setProperty("webdriver.gecko.driver", driverpath); 
DesiredCapabilities capabilities = DesiredCapabilities.firefox(); 
capabilities.setCapability("marionette", true); 
driver = new FirefoxDriver(capabilities); 
driver.get("D:\\STQA\\Selenium\\ComboDemo.html"); 
Select oSelect = new Select(driver.findElement(By.id("combo"))); 
List<WebElement> oSize = oSelect.getOptions(); 
int iListSize = oSize.size(); 
for(int i=0; i<iListSize; i++) { 
String sValue = oSelect.getOptions().get(i).getText(); 
} 
System.out.println("Total No. of Items in Dropdown : "+iListSize); 
}```
  
 
OUTPUT:-




---

PRACTICAL NO 8 
AIM: Write a program using Selenium WebDriver to count the number of checkboxes on a web page, 
including checked and unchecked counts. Perform checkbox identification and counting. 
code:- 
 CheckBox.html 
 <html> 
<body> 
<form name="testform" action="" method="POST"> 
<div align="center"> 
<br> 
<input id='c1' type="checkbox" name="option-1" value="Java">Java 
<input id='c1' type="checkbox" name="option-2" value="C++">C++ 
<input id='c1' type="checkbox" name="option-3" value="Python">Python 
<input id='c1' type="checkbox" name="option-4" value="PHP">PHP 
<input id='c1' type="checkbox" name="option-5" value="CSharp">CSharp 
<input id='c1' type="checkbox" name="option-6" value="Ruby">Ruby 
<input id='c1' type="checkbox" name="option-7" value="Perl">Perl 
</form> 
</body> 
</html> 
1). Write the following code for checking Webdriver. 
package CheckBox; 
import java.util.*; 
import org.openqa.selenium.By; 
import org.openqa.selenium.WebDriver; 
import org.openqa.selenium.WebElement; 
import org.openqa.selenium.firefox.FirefoxDriver; 
class CheckBox { 
public static void main(String[] args) { 
System.setProperty("webdriver.gecko.driver", "D:\\STQA\\Selenium\\geckodriver.exe");  
WebDriver driver = new FirefoxDriver(); 
driver.get("D:\\STQA\\Selenium\\CheckBox.html"); 
int chk=0; 
int unchk=0; 
List<WebElement> els = driver.findElements(By.id("c1")); 
for(WebElement el:els) { 
if(el.isSelected()) { 
chk++; 
} 
else { 
} 
unchk++; 
} 
System.out.println("Total Checked : "+chk); 
System.out.println("Total Unchecked : "+unchk); 
} 
}
OUTPUT:-


