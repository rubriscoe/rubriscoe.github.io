<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="CS-499 Capstone Final Project by Rulon Briscoe. This project includes a code review of a mobile app developed for warehouse inventory management.">
    <title>CS-499 Capstone Final Project</title>
    <style>
        body {
            background-color: #ADD8E6; /* Light blue background */
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
            margin: 0;
        }
        .content {
            max-width: 800px;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        img {
            max-width: 100%;
            height: auto;
        }
        pre {
            text-align: left;
            background: #f4f4f4;
            padding: 10px;
            border-radius: 5px;
        }
        code {
            font-family: 'Courier New', Courier, monospace;
        }
    </style>
</head>
<body>
    <div class="content">
        <h1>CS-499 Capstone Final Project</h1>
        <h2>Rulon Briscoe</h2>
        <h3>Code Review</h3>
        <p>Code reviews are a critical part of software development that allows the developer to make sure they adhere to best practices. This is an opportunity to collaborate and share knowledge about the project making the code more maintainable. It also fosters better communication between team members. In this code review, I went over the original project completed in a previous class to see which areas could be improved upon. This is a code review of a mobile app that I made to keep track of inventory in a warehouse.</p>
        <p>If you want to see the code review click <a href="https://youtu.be/jfhXHynaGDw">here</a>.</p>

        <h3>Project 1: Software Engineering and Design</h3>
        <p>The artifact that I used for all three projects in this portfolio will display improvements in three different categories: Software engineering and design, algorithms and data structures, and databases. For the first project, I was able to redesign the user interface and add more accessibility and navigational components for an overall better experience for the user. The pictures at the bottom will show that I added features to the secure login screen such as forgot username and password links and a create account button for first-time users.</p>
        <p>If you want to read the narrative for this project, click <a href="https://github.com/rubriscoe/rubriscoe.github.io/blob/main/module%203%20narrative%20(1).docx">here</a>.</p>
        <p>If you want to the full code for the original project before any improvements, click <a href="https://github.com/rubriscoe/rubriscoe.github.io/blob/main/Projectthree_Rulon_Briscoe%20(1).zip">here</a>. You can open the file using Android Studio with a pixel 5 API34 emulator</p>
        <p>If you want to see the full code for this project, click <a href="https://github.com/rubriscoe/rubriscoe.github.io/blob/main/inventory%20(4).zip">here</a>. You can download the zip file and open it using Android Studio. To test this code i used an emulator on a pixel 5 API34 on Android Studio</p>


        <h4>Key Features:</h4>
        <ul>
            <li>Secure login for previous users</li>
            <li>Create account button for new users</li>
            <li>New navigational features</li>
            <li>New print button</li>
            <li>New floating action point button to add inventory</li>
        </ul>

        <h4>Code Snippet:</h4>
        <pre><code>#  code snippet
createAccountButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String username = usernameEditText.getText().toString().trim();
                String password = passwordEditText.getText().toString().trim();

                if (username.isEmpty() || password.isEmpty()) {
                    Toast.makeText(MainActivity.this, "Please enter all the fields", Toast.LENGTH_SHORT).show();
                } else {
                    boolean isInserted = db.registerUser(username, password);
                    if (isInserted) {
                        Toast.makeText(MainActivity.this, "Account Created", Toast.LENGTH_SHORT).show();
                    } else {
                        Toast.makeText(MainActivity.this, "Account Creation Failed", Toast.LENGTH_SHORT).show();
                    }
                }
            }
        });
        </code></pre>

        <h3>Project 2: Algorithms and Data Structures</h3>
        <p>For this app, I added several tables using SQLite, which is a quick and secure way to store and access data on a mobile app. SQLite is lightweight but powerful, making it the ideal software library for this project.</p>
        <p>If you want to read the narrative for this project, click <a href="https://github.com/rubriscoe/rubriscoe.github.io/blob/main/Module%204%20narrative.docx">here</a>.</p>
        

        <h4>Key Features:</h4>
        <ul>
            <li>New SQLite table for a secure login</li>
            <li>New SQLite table to store inventory items</li>
        </ul>

        <h4>Code Snippet:</h4>
        <pre><code>// code snippet
 @Override
    public void onCreate(SQLiteDatabase db) {
        String CREATE_TABLE = "CREATE TABLE " + TABLE_NAME + "("
                + COLUMN_ID + " INTEGER PRIMARY KEY AUTOINCREMENT,"
                + COLUMN_USERNAME + " TEXT,"
                + COLUMN_PASSWORD + " TEXT" + ")";
        db.execSQL(CREATE_TABLE);
    }
        </code></pre>

        <h3>Project 3: Databases</h3>
        <p>For the database section of my project, I was able to implement a fast, self-contained database using SQLite to provide secure logins and an easy-to-use inventory page to keep track of items in a warehouse.</p>
        <p>If you want to read the narrative for this project, click <a href="https://github.com/rubriscoe/rubriscoe.github.io/blob/main/mod%205%20narrative%20(1).docx">here</a>.</p>
        

        <h4>Key Features:</h4>
        <ul>
            <li>New SQLite database that supports ACID transactions</li>
            <li>Lightweight and secure database features</li>
            <li>Serverless operations</li>
        </ul>

        <h4>Code Snippet:</h4>
        <pre><code>-- code snippet
private void addItem(String itemName, int quantity, double price) {
        Log.d(TAG, "addItem() called with: itemName = " + itemName + ", quantity = " + quantity + ", price = " + price);
        SQLiteDatabase db = dbHelper.getWritableDatabase();
        ContentValues values = new ContentValues();
        values.put(InventoryDatabase.COLUMN_ITEM_NAME, itemName);
        values.put(InventoryDatabase.COLUMN_QUANTITY, quantity);
        values.put(InventoryDatabase.COLUMN_PRICE, price);
        long newRowId = db.insert(InventoryDatabase.TABLE_NAME, null, values);
        </code></pre>

        <img src="https://github.com/rubriscoe/rubriscoe.github.io/assets/131625839/76f5be0c-8f5e-4da1-9a11-e2934fc9189b" alt="Code Review Image 1">
        <img src="https://github.com/rubriscoe/rubriscoe.github.io/assets/131625839/1eec076e-4255-4c7f-8ac0-bf2700ec208b" alt="Code Review Image 2">

        <h3>Professional Self-Assessment</h3>
        <p>My journey at SNHU has helped me come closer to reaching my professional goals. Using XML, I was able to illustrats a few my skills in UI/UX design and my knowledge of creating databases and data structures using SQLite for a mobile app. This project outlines my comprehension in three different categories, data structures and algorithms, Software Design and Engineering, and Databases.</p> 
        <p>I was able to show skills in all three areas with one app that was created to allow a user to keep track of inventory in a warehouse. Following best design practices, I created a login page with navigational features to make an easy to use app. I was able to create a secure login system using a serverless database system. This lightweight database made it easy to create read update and delete inventory items as well.</p> 
        <p>I have done several projects throughout my time in SNHU. Some of them include a full-stack website using the MEAN stack method. I also was able to use openGL to create a 3D world that mimicked my personal house. These projects all help me to learn how to work as part of a team during the software development life cycle. The expereinces in this course have helped me achieve five course outcomes.</p>
        <p>I employed strategies for building collaborative environments that enable diverse audiences to support organizational decision making in the field of computer science by interacting in class discussions to network, completing a code review of my projects, and creating an app that members of a warehouse team can collaborate on to make their work life more organized.</p>
        <p>I was able to design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, techniccaly sound, and appropriately adapted to specific audiences and contexts by uploading a code review to youtube. The code review allowed me to share my knowledge of software devlopment in an organized manner.</p>
        <p>I was able to design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices with the second section project of this course, Algorithms and Data structures. I was able to make enhancements to the artifact by adding tables for secure login and create ACID transactions for a table of inventory items. These SQLite tables are a quick, efficient way to organize and perform tasks with the given data.</p>
        <p>I was able to demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals with the software engineering and design portion of this project. I was able to create a user interface using XML to provide simple buttons, search bar, and floating action point buttons. I also created the backend database and tables with SQLite for a self-contained database.</p>
        <p>I was able to develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources with the database section of this project. The data needed to be secure, especially for the login page. The SQLite database created a secure place to store inventory data stored on a plain file. </p>
        </p>
    </div>
</body>
</html>
