# Kids Daily Task Tracker 🚀

A fun, simple, and collaborative web application designed to help kids track their daily tasks and chores. Built with modern web technologies, it provides a real-time, interactive experience for the whole family.

**Live Demo:** [tasks.msdigitalsolutions.in](https://tasks.msdigitalsolutions.in) 
![App Screenshot]([https://github.com/ajaysingh0021/kids_task_app/blob/8c3cc58e36b2e0d1d5f4ec1daa6d143211b8cfc5/app_screenshot.png])

---

## ✨ Features

* **Secure Family Accounts:** Create a unique "Family Name" and a 6-digit PIN to keep your family's task list private.
* **Multi-Device Sync:** Log in on any device (phone, tablet, computer) with your Family Name and PIN to access the same shared list in real-time.
* **Child Profiles:** Add up to 4 children to the dashboard.
* **Flexible Task Creation:**
    * **General Tasks:** For chores that happen every day.
    * **Weekly Tasks:** Assign tasks to specific days of the week.
    * **Time-Bound:** Set start and end times for each task.
* **Interactive Dashboard:**
    * A clean "To-Do" and "Completed" view for each child.
    * Simply tap a task to mark it complete!
* **Visual Status Indicators:**
    * 🔵 **Blue:** A standard to-do task.
    * 🟡 **Yellow (Blinking):** The task is active and should be worked on now!
    * 🔴 **Red:** The time for the task has passed, and it wasn't completed.
    * 🟢 **Green:** The task is successfully completed!
* **Fun Animations:** A rewarding sparkle animation plays when a task is completed.

---

## 💻 Tech Stack

This project is built with a modern, serverless architecture:

* **Frontend:** HTML5, Tailwind CSS, and vanilla JavaScript (ES6+).
* **Database:** Google Firestore for real-time NoSQL data storage.
* **Authentication:** A custom Family Name/PIN system built on top of Firebase for secure data access.
* **Hosting:** Deployed on [Vercel](https://vercel.com).

---

## 🚀 Getting Started

### For Users

1.  Visit the live demo link.
2.  Click on "Create one!" to register a new family account.
3.  Choose a unique Family Name and a 6-digit PIN.
4.  Go to the "Settings" page to add your children and their daily/weekly tasks.
5.  Share the Family Name and PIN with other family members so they can log in on their devices and see the same list!

### For Developers (Running Your Own Version)

If you want to host your own instance of this application, follow these steps:

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/kids-task-app.git](https://github.com/YOUR_USERNAME/kids-task-app.git)
    cd kids-task-app
    ```

2.  **Create a Firebase Project:**
    * Go to the [Firebase Console](https://console.firebase.google.com/).
    * Click "Add project" and give it a name.
    * Once created, go to **Project Settings** > **General**.
    * Under "Your apps", click the web icon (`</>`) to register a new web app.
    * Give it a nickname and click "Register app".
    * Firebase will provide you with a `firebaseConfig` object. **You will need this!**

3.  **Set up Firestore Database:**
    * In the Firebase console, go to the **Firestore Database** section.
    * Click "Create database" and start in **production mode**.
    * Choose a location for your database.
    * Go to the **Rules** tab and paste the following rules to allow authenticated users to read and write to the public data paths. This is crucial for the app to function.
        ```
        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            // Allow public read/write for family account creation and task data
            match /artifacts/{appId}/public/data/{document=**} {
              allow read, write: if request.auth != null;
            }
          }
        }
        ```
    * Click "Publish".

4.  **Configure the Application:**
    * This application is designed to be used in a platform that provides the Firebase configuration and App ID dynamically. If you are hosting it yourself, you will need to manually edit the `index.html` file.
    * Find the `Firebase Configuration` section in the `<script>` tag.
    * Replace the placeholder values with your own `firebaseConfig` object and a unique `appId`.

5.  **Deploy:**
    * You can open the `index.html` file directly in your browser for local testing.
    * For public hosting, follow the deployment guide for a service like **Vercel** or **Netlify**.

---

## ❤️ Contributing

Contributions are welcome! If you have ideas for new features or find a bug, please feel free to open an issue or submit a pull request.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
