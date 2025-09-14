# Moodle XML Quiz Viewer 📝

A secure, serverless web application to view and take Moodle XML quizzes directly in your browser. This tool is perfect for educators and students who need a quick and easy way to interact with Moodle quiz content without needing a full Moodle instance. It runs entirely on GitHub Pages, requiring no backend or installation.



## Features ✨

* **Multiple Loading Options:** Load quizzes by pasting XML content, providing a URL, or using a direct URL parameter.
* **Broad Question Type Support:** Renders a wide range of Moodle question types, including:
    * Description & Category
    * Multiple Choice & True/False
    * Short Answer (with wildcard support)
    * Numerical
    * Matching
    * Essay (for viewing)
    * Cloze (Embedded Answers) with support for various sub-types (dropdowns, radio buttons, checkboxes, etc.)
* **Interactive Experience:** Presents questions sequentially, accepts answers, provides immediate feedback, and calculates a running score.
* **Secure by Design:** All user-provided XML content is sanitized using **DOMPurify** to prevent Cross-Site Scripting (XSS) attacks, ensuring that even untrusted XML files can be rendered safely.
* **Serverless & Portable:** Runs entirely in the user's browser as a single HTML file. Easily hosted for free on GitHub Pages or any static site host.

---

## How to Use 🚀

There are three easy ways to load a quiz.

### 1. Paste XML Content

1.  Open your Moodle XML quiz file in a text editor.
2.  Copy the entire content.
3.  Navigate to the Quiz Viewer page.
4.  Paste the content into the text area under "Or Paste XML Content."
5.  Click **Start Quiz**.

### 2. Load from URL

1.  Make sure your Moodle XML file is hosted at a publicly accessible URL.
    * *Note: Due to browser security (CORS), this may not work for all URLs. Using a service like GitHub Gist is recommended.*
2.  Paste the URL into the "Load from URL" input field.
3.  Click **Start Quiz**.

### 3. Load via URL Parameter

You can create a direct link to a quiz by appending its URL as a query parameter. This is the best way to share a specific quiz with others.

**Format:**
`https://<your-username>.github.io/<repository-name>/?url=<URL_TO_YOUR_XML_FILE>`

**Example:**
`https://your-name.github.io/moodle-quiz-viewer/?url=https://gist.githubusercontent.com/user/quiz.xml`

---

## Deployment 🌐

You can easily host your own instance of this viewer on GitHub Pages.

1.  **Fork** this repository.
2.  Navigate to your new repository's **Settings** > **Pages**.
3.  Under "Build and deployment," select the source as **Deploy from a branch**.
4.  Choose the `main` branch and the `/(root)` folder, then click **Save**.
5.  Your quiz viewer will be live at `https://<your-username>.github.io/<your-repo-name>/` in a few minutes.

---

## Security 🛡️

This application is designed with security as a priority. User-provided content from an XML file can contain malicious scripts (an attack known as Cross-Site Scripting or XSS).

To prevent this, all content drawn from the XML file (`<questiontext>`, `<answer>`, `<feedback>`, etc.) is sanitized using the **DOMPurify** library before it is rendered on the page. This process removes any potentially harmful code, such as `<script>` tags and `onerror` attributes, while preserving safe HTML formatting (like bold, italics, and lists). You can safely load XML files from any source.

---

## Supported Question Types

This viewer has full or partial support for the following Moodle XML question types:

* ✅ `multichoice`
* ✅ `truefalse`
* ✅ `shortanswer`
* ✅ `numerical`
* ✅ `matching`
* ✅ `essay`
* ✅ `cloze` (Embedded Answers)
* ✅ `description`
* ✅ `category`

Any other question types (`ordering`, `gapselect`, etc.) will be gracefully skipped with a message informing the user that the type is not supported, allowing the rest of the quiz to proceed without error.
