# Task-2 : Analyzing a phishing email sample

### Objective: Identify phishing characteristics in a suspicious email sample.
### Tools:  Email client or saved email file (text)

### What are phishing emails?
It is a type of online scam where criminals try to trick people into giving away sensitive information, like passwords, credit card numbers, and personal details. To accomplish this, a criminal pretends to be a trusted person or company, like a bank, government agency, or popular website.
A phishing email is a fraudulent message designed to look authentic. It usually asks you to click a link, download an attachment, or provide personal details in an effort to steal valuable information.

### Top 10 most common phishing are:
1. Social media phishing emails
2. PayPal phishing emails
3. Amazon phishing emails
4. Google Docs scams
5. IRS phishing emails
6. Suspended account phishing emails
7. Unusual activity phishing attempts
8. CEO phishing emails
9. Fake job scams
10. Apple phishing attacks

### Step 1 : Obtraining a phishing email:
We can obtain a sample phishing emain from the internet.
This is the reference I am using https://security.berkeley.edu/news/phishing-example-paypal-we-need-your-help
Please look for the the image of the email will be attached in a different file labelled as "phishing email sample exapmle".

### Step 2 : Examining sender’s email address for spoofing:
1. As visible in the screenshort, From: Customer service <Acces@up.com> (notice the misspelling Acces and the domain up.com which is not paypal.com).
2. It is suspicious because, display name uses “Customer service” (generic), and the actual email domain is unrelated to PayPal — a common spoof tactic (change one character or use unrelated domain).
Solution: We can flag the sender, block domain if repeated, and preserve the raw message for header analysis.

### Step 3 : Checking email headers for discrepancies (steps to follow if you had a raw file):
Since the sample phishing used in this example is just an image, headers are not available here.
But if we have the .eml file you should paste the full headers into MXToolbox or Microsoft Message Header Analyzer and check:
1.Received: chain (first hop IP)
2.Return-Path / envelope-from
3.Authentication-Results (SPF / DKIM / DMARC)
If it fails or is missing SPF/DKIM/DMARC is strong evidence of spoofing.
#### Tools: tools: MXToolbox, Microsoft header analyzer, PhishTank (for URLs/attachments).

### Step 4 : Identifing suspicious links or attachments:
From the screenshot the “Update your information” button’s destination is not PayPal — Berkeley(the page that is analysing the email) reports it points to treebeard.mschosting.com. That mismatch (button text claims PayPal but link goes to a third-party hosting domain) is a red flag.

What to do: Right-click , Copy link address (do not click). Submit the URL to PhishTank to inspect domain structure (subdomains, IP in URL).
Few of the most common things in a phishing URL are lexical features like : spelling mistakes, hypen count, dot count, URL length, and subdomain.

### Step 5 : Looking for urgent or threatening language in the email body.
The text “Your account has been limited until we hear from you” and a BIG button, creates an urgency and panic among the readers, and Urgent deadlines (“your account will be closed”, “act within 24 hours”) are classic phishing tactics.

### Step 6 : Mismatched URL:
The button text claims a PayPal action but resolves to an unrelated host (treebeard.mschosting.com) per the example notes — this is a direct mismatch.

### Step 7 : Presence of spelling errors and grammar mistakes:
The sample contains misspellings like “Your account has been Iimited untiI we hear from you” (capital I used instead of lowercase L in “Limited / until”) and the sender address itself Acces@up.com (missing one ‘s’). Spelling/grammar errors are common phishing signals.

### Step 8 : Summary
Display name “Customer service” but actual From address is Acces@up.com (domain unrelated to PayPal) — suspicious.
Button claims PayPal action but links to a third-party host (treebeard.mschosting.com) — mismatched URL/redirect.
Urgent language pushing immediate action — classic social engineering.
Spelling/typos visible in subject and sender — another marker.
High—likely credential-harvesting or invoice scam. (Krebs and Fortinet detail similar PayPal scams where phishing pages or invoices are used to capture credentials or link malicious accounts.)

#### Recommended  actions:
Quarantine the message and preserve the raw .eml. (If only screenshot exists, preserve that.)
Extract and document link(s) — do not click. Submit to PhishTank and check whether the link is legitimate or not.
If any user clicked, advise password reset + enable MFA and monitor account activity.
Report to APWG / org security team and forward the raw headers to your security team for further triage.
