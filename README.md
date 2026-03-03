# ☁️ Cloud Computing Practical Manual

> **Subject:** Cloud Computing  
> **Total Practicals:** 6  
> **Tools Used:** Java, Python (Flask), NetBeans IDE, GlassFish Server, VMware, Google Cloud

---

# PRACTICAL NO 1

## AIM :-
Define a simple service like Converting Rs into Dollar and call it from different platforms like JAVA and .NET.

---

## STEPS :-

1. From **File Menu** → Select **New Project** → Categories: `Java Web` → Projects: `Web Application` → Click **Next**.

2. Give the project a name and click **Next**.

3. Select **GlassFish Server** and click **Finish** to create the Web Application.

4. Right-click on your project → Click **New** → Select **Web Service**.

5. Give the **Web Service name** and **Package name** → Click **Finish**.

6. Right-click on your code → Select **Insert Code**.

7. From the Insert Code tab → Select **Add Web Service Operation**.

8. In the Add Operation tab → Give **Operation name**, **Return type**, **Parameters** → Click **OK**.

9. Operation will be added in your code — change the return value to implement the conversion logic (Rs → Dollar).

10. Right-click on the project → Click **Deploy**.

11. View the output screen after successful deployment.

12. Right-click on your Web Service → Click **Test Web Service** to verify.

13. To create the **Client Application**: File Menu → New Project → Categories: `Java` → Projects: `Java Application` → Click **Next**.

14. Give the project a name → Click **Finish**.

15. Right-click on your project → New → **Web Service Client**.

16. Click **Browse** → Select your Web Service → Give Package name → Click **OK** and **Finish**.

17. Right-click on your code → **Insert Code**.

18. From the Insert Code tab → Select **Call Web Service Operation**.

19. Select your operation → Click **OK**.

20. Add the code to run your application.

21. Run your App.

## OUTPUT :-
- Successful deployment screen on GlassFish Server.
- Java application runs and shows the converted Dollar value from Rs input.

---

# PRACTICAL NO 2

## AIM :-
Create a Simple SOAP Service.

---

## STEPS :-

1. Create a **Web Application**: New Project → Java Web → Web Application.

2. Name the project and click **Next**.

3. Select **GlassFish Server** → Click **Finish**.

4. Right-click project → **New** → **Web Service**.

5. Provide Web Service name and Package name → Click **Finish**.

6. Right-click code → **Insert Code** → Select **Add Web Service Operation**.

7. Define **Operation name**, **Return type**, and **Parameters** → Click **OK**.

8. Modify the return value in the generated code. Add more operations as needed.

9. Right-click project → **Deploy**.

10. View output screen after successful deployment.

11. Right-click Web Service → **Test Web Service** to verify SOAP operations.

12. Create a **Java Application**: New Project → Java → Java Application.

13. Name the project → Click **Finish**.

14. Right-click project → New → **Web Service Client** → Browse to select the Web Service → Provide Package name → Click **Finish**.

15. Right-click code → **Insert Code** → **Call Web Service Operation**.

16. Select all required operations one by one.

17. Add the code to run the application.

18. Run your App.

## OUTPUT :-
- Successful SOAP service deployed on GlassFish.
- Java client application successfully calls SOAP operations and displays results.

---

# PRACTICAL NO 3

## AIM :-
Create a Simple REST Service.

---

## STEPS :-

1. Write the Python/Flask code given below.

2. Run the python script in **CMD** using:
   ```
   python app.py
   ```

3. Open a browser and type `http://127.0.0.1:5000/items` → displays all records.

4. Type `http://127.0.0.1:5000/items/1` → displays item with ID 1.

5. Open a new CMD terminal and run the following POST command to add a new record:
   ```powershell
   Invoke-WebRequest -Uri http://127.0.0.1:5000/items -Method Post -Headers @{"Content-Type" = "application/json"} -Body '{"name" : "New Item"}'
   ```

6. Refresh the items URL → displays the updated records.

---

## CODE :-

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

## OUTPUT :-
- JSON response showing list of all items at `/items`.
- Single item JSON response at `/items/1`.
- New item added successfully via POST request.
- Updated item list visible after refresh.

---

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

## 🛠️ Prerequisites

| Tool | Purpose |
|------|---------|
| Java JDK | Java development |
| NetBeans IDE | Project creation & deployment |
| GlassFish Server | Hosting web services |
| Python 3.x + Flask | REST service (Practical 3) |
| VMware Workstation | Virtualization (Practical 5) |
| Google Cloud Account | API integration (Practical 4) |
| JAX-WS 2.2.6 JAR | MTOM web service (Practical 6) |

---

## 🚀 Quick Start

```bash
# Practical 3 - REST Service
pip install flask
python app.py
# Visit: http://127.0.0.1:5000/items
```

---

*📘 Cloud Computing Lab Manual — For Educational Use Only*
