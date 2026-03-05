
---

# PRACTICAL NO 1

## AIM :-
Define a simple service like Converting Rs into Dollar and call it from different platforms like JAVA and .NET.

---

```java
package server;

import javax.jws.WebService;
import javax.jws.WebMethod;
import javax.jws.WebParam;

@WebService(serviceName = "INRtoUSD")
public class INRtoUSD {

    @WebMethod(operationName = "convert")
    public double convert(@WebParam(name = "rupees") double rupees) {
        
        double exchangeRate = 83.0; // 1 USD = 83 INR
        double usd = rupees / exchangeRate;
        
        return usd;
    }
}


## input

```html
<html>
<body>

<h2>INR to USD</h2>

<form action="output.jsp">

Enter Rupees:
<input type="text" name="rs">

<br><br>

<input type="submit" value="Convert">

</form>

</body>
</html>


## output

```html
<html>
<body>

<%
double rs = Double.parseDouble(request.getParameter("rs"));
double usd = rs / 83;
%>

Rupees = <%= rs %> <br>
USD = <%= usd %>

</body>
</html>
```



# PRACTICAL NO 2

## AIM :-
Create a Simple SOAP Service.

---


```java

package mypkg;

import javax.jws.WebService;
import javax.jws.WebMethod;
import javax.jws.WebParam;


@WebService(serviceName = "Think")
public class Think {


    @WebMethod(operationName = "hello")
    public String hello(@WebParam(name = "name") String txt) {
        return "Hello " + txt + " !";
    }


    @WebMethod(operationName = "Addition")
    public int Addition(@WebParam(name = "x") int x, @WebParam(name = "y") int y) {
        return x + y;
    }

 
    @WebMethod(operationName = "Sub")
    public int Sub(@WebParam(name = "x") int x, @WebParam(name = "y") int y) {
        return x - y;
    }


    @WebMethod(operationName = "Mul")
    public int Mul(@WebParam(name = "x") int x, @WebParam(name = "y") int y) {
        return x * y;
    }


    @WebMethod(operationName = "Div")
    public int Div(@WebParam(name = "x") int x, @WebParam(name = "y") int y) {
        return x / y;
    }
}

##Output

<!DOCTYPE html>
<html>
<head>
<title>Calculator</title>
<script>
function calculate() {
    var x = parseInt(document.getElementById("x").value);
    var y = parseInt(document.getElementById("y").value);

    document.getElementById("add").innerHTML = "Add : " + (x + y);
    document.getElementById("sub").innerHTML = "Sub : " + (x - y);
    document.getElementById("mul").innerHTML = "Mul : " + (x * y);
    document.getElementById("div").innerHTML = "Div : " + (x / y);
}
</script>
</head>

<body>

<h2>Calculator</h2>

Enter the Value of x :  
<input type="number" id="x"><br><br>

Enter the Value of y :  
<input type="number" id="y"><br><br>

<button onclick="calculate()">Calculate</button>

<h3 id="add"></h3>
<h3 id="sub"></h3>
<h3 id="mul"></h3>
<h3 id="div"></h3>

</body>
</html>

```

# PRACTICAL NO 3

## AIM :-
Create a Simple REST Service.

---


```python
from flask import Flask, jsonify, request

app = Flask(__name__)

# In-memory data store
data = [
    {'id': 1, 'name': 'Item 1'},
    {'id': 2, 'name': 'Item 2'},
]

# GET all items
@app.route('/items', methods=['GET'])
def get_items():
    return jsonify({'items': data})

# GET single item by ID
@app.route('/items/<int:item_id>', methods=['GET'])
def get_item(item_id):
    item = next((item for item in data if item['id'] == item_id), None)
    if item:
        return jsonify({'item': item})
    else:
        return jsonify({'message': 'Item not Found'}), 404

# POST - Add new item
@app.route('/items', methods=['POST'])
def add_item():
    new_item = {'id': len(data) + 1, 'name': request.json['name']}
    data.append(new_item)
    return jsonify({'message': 'Item added successfully', 'item': new_item}), 201

if __name__ == '__main__':
    app.run(debug=True)
```


# PRACTICAL NO 4

## AIM :-
Develop an application to consume Google's Search / Google's Map RESTful Web Service.

---

## STEPS :-

1. Login to **Google Cloud Console** at `https://console.cloud.google.com`.

2. Click on **"New Project"** in the select project tab.

3. Give the project a name → Click **Create**.

4. Open the **Project Dashboard**.

5. Go to **"APIs and Services"** → **"Enabled APIs and Services"**.

6. Click on **"+ ENABLE APIS AND SERVICES"**.

7. Search for `Custom Search API`.

8. Select **Custom Search API** from results.

9. Click **Enable** → then click **"Try this API"**.

10. Click on the **Control Panel**.

11. Name the search engine, provide site URL (`www.google.com`) → Click **Add**.

12. Complete the **CAPTCHA** and click **Create**.

13. Copy the generated API code/snippet.

14. Paste the code into an **HTML file** in **VS Code**.

15. Run it using the **"Go Live"** extension.

16. Consume Google Search through the browser interface.

## OUTPUT :-
- A functional Google Custom Search interface running in the browser.
- Search queries return relevant results via Google's RESTful API.

---

# PRACTICAL NO 5

## AIM :-
Installation and Configuration of Virtualization using KVM.

---

## STEPS :-

1. Install and open **VMware Workstation** → Click **"Create a New Virtual Machine"**.

2. Select **"Typical (recommended)"** → Click **Next**.

3. Select **"Installer disc image file (iso)"** → Browse and select the **Ubuntu ISO** file.

4. Provide user information (Full name, Username, Password) → Click **Next**.

5. Name the virtual machine → Select storage location → Click **Next**.

6. Specify disk capacity → Select **"Split virtual disk into multiple files"** → Click **Next**.

7. Click **Finish** to complete hardware requirements setup.

8. Ubuntu setup opens → Select **Keyboard Layout** → Click **Continue**.

9. Select **"Normal Installation"** and check **"Download updates while installing Ubuntu"** → Click **Continue**.

10. Select **"Erase disk and install Ubuntu"** → Click **Install Now**.

11. Click **Continue** on the **"Write changes to disk"** confirmation.

12. Select your **Region/Timezone** → Click **Continue**.

13. Provide **user account information** (name, computer name, password) → Click **Continue**.

14. Wait for the background installation to complete.

15. Click **Restart Now** when prompted.

16. Log in to start using the **Ubuntu Virtual Machine**.

## OUTPUT :-
- Ubuntu Linux successfully installed and running inside VMware Workstation.
- KVM virtualization configured and operational.

---

# PRACTICAL NO 6

## AIM :-
Develop an application to download image/video from server or upload image/video to server using MTOM techniques.

---

## STEPS :-

**Server Side (MTOMServer):**
1. Create a new Java Web Application → Name it `MTOMServer`.
2. Select **GlassFish Server**.
3. Create a new **Java Class** → Name: `ImageWS`, Package: `mypkg`.
4. Replace the code in `ImageWS.java` with the server code below.
5. Right-click project → **Deploy**.
6. Verify successful deployment.

**Client Side (MTOMClient):**
7. Create a new Java Web Application → Name it `MTOMClient`.
8. Select **GlassFish Server**.
9. Create a new **JSP file** → Name it `index.jsp`.
10. Replace code in `index.jsp` with the client code below.
11. Right-click project → New → **Web Service Client**.
12. Browse to the `ImageWS` service → Set package name.
13. Go to **Project Properties** → **Libraries** → Add library **JAX-WS 2.2.6**.
14. Run the application.
15. Check `D:/upload/` and `D:/Downloaded/` folders for uploaded/downloaded files.

---

## SERVER CODE :- (`ImageWS.java`)

```java
package mypkg;

import java.io.*;
import javax.jws.Oneway;
import javax.jws.WebService;
import javax.jws.WebMethod;
import javax.jws.WebParam;
import javax.xml.ws.soap.MTOM;

@MTOM(enabled = true, threshold = 60000)
@WebService(serviceName = "ImageWS")
public class ImageWS {

    // Upload Method
    @WebMethod(operationName = "upload")
    @Oneway
    public void upload(
        @WebParam(name = "Filename") String Filename,
        @WebParam(name = "ImageBytes") byte[] ImageBytes) {

        String filePath = "D:/upload/" + Filename;
        try {
            FileOutputStream fos = new FileOutputStream(filePath);
            BufferedOutputStream bos = new BufferedOutputStream(fos);
            bos.write(ImageBytes);
            bos.close();
            System.out.println("Received file: " + filePath);
        } catch (Exception ex) {
            System.out.println(ex);
        }
    }

    // Download Method
    @WebMethod(operationName = "download")
    public byte[] download(@WebParam(name = "Filename") String Filename) {
        String filePath = "D:/Downloaded/" + Filename;
        try {
            File file = new File(filePath);
            FileInputStream fis = new FileInputStream(file);
            BufferedInputStream bis = new BufferedInputStream(fis);
            byte[] fileBytes = new byte[(int) file.length()];
            bis.read(fileBytes);
            bis.close();
            return fileBytes;
        } catch (Exception ex) {
            System.out.println(ex);
        }
        return null;
    }
}
```

---

## CLIENT CODE :- (`index.jsp`)

```jsp
<%@page import="java.io.*"%>
<%@page import="javax.xml.ws.soap.MTOMFeature"%>
<html>
<body>

<%
// ── UPLOAD ───────────────────────────────────────────────
try {
    mypkg.ImageWS_Service service = new mypkg.ImageWS_Service();
    mypkg.ImageWS port = service.getImageWSPort(new MTOMFeature(60000));

    String filePath = "D:/ABC.png";
    File file = new File(filePath);
    FileInputStream fis = new FileInputStream(file);
    BufferedInputStream bis = new BufferedInputStream(fis);
    byte[] imageBytes = new byte[(int) file.length()];
    bis.read(imageBytes);

    port.upload(file.getName(), imageBytes);
    bis.close();
    out.println("File uploaded: " + filePath);
} catch (Exception ex) {
    out.println("Upload Error: " + ex.getMessage());
}
%>

<hr/>

<%
// ── DOWNLOAD ─────────────────────────────────────────────
try {
    mypkg.ImageWS_Service service = new mypkg.ImageWS_Service();
    mypkg.ImageWS port = service.getImageWSPort();

    String filename = "ABC.png";
    byte[] fileBytes = port.download(filename);

    FileOutputStream fos = new FileOutputStream("D:/Downloaded/" + filename);
    BufferedOutputStream bos = new BufferedOutputStream(fos);
    bos.write(fileBytes);
    bos.close();

    out.println("File downloaded to D:/Downloaded/");
} catch (Exception ex) {
    out.println("Download Error: " + ex.getMessage());
}
%>

</body>
</html>
```

## OUTPUT :-
- Image/video file successfully **uploaded** to `D:/upload/` directory.
- Image/video file successfully **downloaded** to `D:/Downloaded/` directory.
- MTOM technique used for efficient binary data transfer between client and server.

---


