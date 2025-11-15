## Step 3: Review and Triage CodeQL Alerts

With our pull request changes now reviewed by CodeQL, we now have some results to view.Let's learn about managing alerts.

GitHub provides a dedicated **Security** tab for securely managing all security related issues. CodeQL saves alerts using the same standard as many other analysis tools with the results showing up under the **Code scanning** area.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/cf4fc6ec-e40e-4df6-8984-b6ec35341737" />

### What information do alerts provide?

The main area of an alert provides the resolution status, affected branch, code location, and classification information like severity and [CVE identification number](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories#cve-identification-numbers).

After the status information, a detailed description of the issue, recommended solutions, and suggested code changes are provided.

<img width="600" alt="additional information" src="https://github.com/user-attachments/assets/9a5aaf3f-e063-4d07-8cdd-6272eec8a411"/>

### What is CWE?

Many of the patterns CodeQL scans for come from existing databases of vulnerabilities, which are categorized for easier understanding.

The **Common Weakness Enumeration (CWE)** is a category system for hardware and software weaknesses and vulnerabilities. Think of it as a way to describe and categorize security issues in an application's source code. For more information on CWEs, see the Wikipedia article [Common Weakness Enumeration](https://en.wikipedia.org/wiki/Common_Weakness_Enumeration).

### ⌨️ Activity: View existing alerts

1. In the top navigation, select the **Security** tab.

1. In the left navigation, find the **Vulnerability alerts** area and select the **Code scanning** option.

   - Notice that there are no alerts. This is expected since the vulnerable code on the pull request has not been merged yet.

1. Return to the recently created pull request. Ignore the failed check and click the **Merge pull request** button.

   <img width="300" alt="merge button" src="https://github.com/user-attachments/assets/cb6fc4a9-c441-4d63-9104-efca6171d262" />

1. Click the **Delete branch**. It is not needed anymore.

1. Wait a moment for CodeQL to analyze the new changes to the `main` branch.

1. Return the the **Security** tab.

1. In the left navigation, notice that the **Code Scanning** option now has a `1` entry next to it, informing us of an open alert.

   <img width="250" alt="code scanning alerts count" src="https://github.com/user-attachments/assets/80f17f92-bd8e-45c4-b471-c60665e116d7" />

### ⌨️ Activity: Review an Alert

1. In the left navigation, select the **Code scanning** option.

1. Click on the open alert.

1. Notice the description, vulnerability description, and a recommended solution.

   <img width="600" alt="alert overview" src="https://github.com/user-attachments/assets/6da3aaa7-c9bb-4046-9372-c137a2d43106" />

1. Notice the audit trail provides the source of the vulnerability and shows that it came from our pull request.

### ⌨️ Activity: Add Comments to Alerts

One of the key features of Code scanning alerts is the ability to add comments when managing them. Comments provide context, document decisions, and create an audit trail for security issues.

#### How to Add Comments to Code Scanning Alerts

There are several ways to add comments to code scanning alerts:

1. **When dismissing an alert**: You can add a comment explaining why you're dismissing it (e.g., false positive, risk accepted, used in tests).
2. **In pull requests**: Code scanning alerts appear in PR conversations where you can discuss them with your team.
3. **Via REST API**: For automated workflows, you can programmatically add comments using GitHub's API.

Let's practice adding comments by dismissing and reopening an alert with explanatory text.

### ⌨️ Activity: Dismiss and Reopen an Alert with Comments

1. In the top right, click **Dismiss alert** dropdown.

1. Select the `Used in tests` option and enter the below comment in the description field.

   ```md
   This is a playground repository for learning about CodeQL alerts.
   ```

   <img width="300" alt="dismiss alert options" src="https://github.com/user-attachments/assets/7be133a7-3f20-4bf3-8073-383eb1cce359" />

   > 💡 Tip: This description becomes a **comment** on the alert, visible in the audit trail.

1. Click the **Dismiss alert** button.

   - The alert state will change to `Dismissed`.
   - A read-only entry was added with your comment to the audit trail showing who closed it and why.

   <img width="300" alt="audit log entry showing alert dismissed" src="https://github.com/user-attachments/assets/afdd6e11-d4c9-466c-82d4-622c96e039a3" />

1. In the top right, click the **Reopen alert** button.

   - The alert state will change back to `Open`.
   - A read-only entry was added to the audit trail showing who opened it.

   > 💡 Tip: Comments on alerts are permanent and provide valuable context for security audits and team collaboration.

1. With an alert closed and reopened, add a comment to this issue asking Mona to check our progress and share the next steps.

   ```md
   Hey @professortocat, I've closed an reopened an alert. What is the next step?
   ```
