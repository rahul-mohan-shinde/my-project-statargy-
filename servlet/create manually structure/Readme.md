
# **Manual Servlet Hello World Project – README**

## **Project Overview**

This project demonstrates how to manually create a simple Java Servlet (`HelloServlet`) that prints **“Hello World”** in a browser using Apache Tomcat. All steps are done manually without using IDE automation.

---

## **Folder Structure**

```
ServletLMS/
├── index.html                     # Optional homepage
├── WEB-INF/
│   ├── web.xml                    # Deployment descriptor
│   └── classes/
│       └── com/example/
│           └── HelloServlet.class  # Compiled servlet class
└── src/
    └── com/example/
        └── HelloServlet.java      # Source code
```

**Notes:**

* `src/` contains your Java source code.
* `WEB-INF/classes/` contains compiled `.class` files.
* `web.xml` is required for servlet configuration.

---

## **Step-by-Step Instructions**

### **1. Create Project Structure**

1. Inside `webapps` of Tomcat, create folder `ServletLMS`.
2. Create subfolders:

```
ServletLMS/src/com/example
ServletLMS/WEB-INF/classes
```

3. Place `HelloServlet.java` in `src/com/example`.

---

### **2. Write Servlet Code**

```java
package com.example;

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class HelloServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Hello World</h1>");
        out.println("</body></html>");
    }
}
```

---

### **3. Configure `web.xml`**

```xml
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                             http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>HelloServlet</servlet-name>
        <servlet-class>com.example.HelloServlet</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>HelloServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
</web-app>
```

**Notes / Common Mistakes:**

* Do **not forget the full package name** in `<servlet-class>`.
* Correct spelling: `<url-pattern>`, not `<url-patter>`.
* `web.xml` must be inside `WEB-INF`.

---

### **4. Compile Servlet**

**From project root (`ServletLMS`)**:

```powershell
javac -cp "C:\Program Files\Apache Software Foundation\Tomcat 9.0\lib\servlet-api.jar" -d WEB-INF/classes src/com/example/HelloServlet.java
```

**Notes / Common Mistakes:**

* `.class` not generated if the `-d` path is wrong.
* Source and class folders must not overlap (keep `src` separate from `WEB-INF/classes`).
* Package declaration in `.java` must match folder structure (`com/example`).

---

### **5. Verify Compiled Class**

Check:

```
WEB-INF/classes/com/example/HelloServlet.class
```

---

### **6. Start Tomcat**

* Start Tomcat normally.
* Note the HTTP port in logs (usually `8080` or `9494` in your case).
* Example URL:

```
http://localhost:9494/ServletLMS/hello
```

* If it works → Hello World is printed in the browser.

---

### **7. Optional: index.html**

```html
<!DOCTYPE html>
<html>
<head>
    <title>ServletLMS Home</title>
</head>
<body>
    <h1>Welcome to ServletLMS</h1>
    <a href="hello">Run HelloServlet</a>
</body>
</html>
```

* Place this in `ServletLMS/` for quick access to the servlet.

---

## **Common Errors & Fixes**

| Error / Issue                                                | Cause                                                      | Fix                                                           |
| ------------------------------------------------------------ | ---------------------------------------------------------- | ------------------------------------------------------------- |
| `404 Not Found`                                              | Servlet class not found / wrong package / web.xml typo     | Check package, .class path, `<servlet-class>`, restart Tomcat |
| `cannot find symbol` for `ServletException` or `HttpServlet` | Using wrong imports (`jakarta.servlet` vs `javax.servlet`) | Use `javax.servlet.*` for Tomcat 9 and servlet-api.jar        |
| `.class` not generated                                       | Wrong `-d` path or source inside classes folder            | Keep source in `src/`, use correct `-d WEB-INF/classes` path  |
| `web.xml` parsing error                                      | Typos in tags                                              | Check spelling, e.g., `<url-pattern>`                         |

---

## **Tips for Manual Servlet Projects**

1. Always **separate source (`src`) and compiled classes (`WEB-INF/classes`)**.
2. Always include **full package name in web.xml**.
3. Restart Tomcat after every compilation.
4. Use correct **port number** in browser URL.
5. Keep a **consistent folder structure** for all future manual servlet projects.

---

This README should allow you to **recreate the Hello World Servlet manually anytime in the future**, including all common pitfalls and fixes.

