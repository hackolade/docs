# Getting help

The different options currently available are:

* [eLearning platform](<https://community.hackolade.com/slides/all>) with self-paced tutorials
* Read the online [manual](<http://hackolade.com/help> "target=\"\_blank\"")&nbsp;
* Watch these short [videos](<http://hackolade.com/videos.html> "target=\"\_blank\"")&nbsp;
* Send an [email](<mailto:support@hackolade.com>) to open a support ticket to [support@hackolade.com](<mailto:support@hackolade.com?subject=Hackolade%20Studio%20question>)

&nbsp;

&nbsp;

## AI Browsers

Both our [online documentation](<https://hackolade.com/help> "target=\"\_blank\"") and our [eLearning platform](<https://community.hackolade.com/slides/all>) have powerful search boxes.&nbsp; Recently, new AI browsers such as [Perplexity Comet](<https://www.perplexity.ai/comet> "target=\"\_blank\""), [OpenAI Atlas](<https://openai.com/index/introducing-chatgpt-atlas/> "target=\"\_blank\""), [Brave Leo AI](<https://brave.com/leo/> "target=\"\_blank\""), or the [Gemini in Chrome](<https://www.google.com/chrome/ai-innovations/> "target=\"\_blank\"") introduced Natural Language processing of your questions.&nbsp; Right now, it seems that only Perplexity Comet fully leverages our knowledge resources for an even richer experience.&nbsp; For other destinations than the Hackolade online documentation, you may want to be careful with AI browsers and some [security concerns](<https://martinfowler.com/articles/2025-11-03-frags.html> "target=\"\_blank\"") around them.

&nbsp;

Here is an example, asking a question from the Comet assistant from any page of our [online documentation](<https://hackolade.com/help>), and getting the correct response plus related link to the relevant page:

&nbsp;

![Perplexity Comet Assistant example 1](<lib/Perplexity Comet Assistant example 1.png>)

&nbsp;

&nbsp;

Alternatively, you can create a notebook in Google's [NotebookLM](<https://notebooklm.google.com/> "target=\"\_blank\""), and include these 3 sources:

[https://hackolade.com](<https://hackolade.com>)

[https://hackolade.com/help](<https://hackolade.com/help>)

[https://community.hackolade.com/slides/all](<https://community.hackolade.com/slides/all>)

then you may ask any Hackolade-related questions.

&nbsp;

In our experience as of the time of writing -- and recognizing tools evolve at lightning speed -- we have found that, while NotebookLM is impressive at first, and super fast, in fact the Assistant of Perplexity Comet provides the best and most thorough results, including accurate step-by-step instructions:

&nbsp;

![Perplexity Comet Assistant example 2](<lib/Perplexity Comet Assistant example 2.png>)

&nbsp;

&nbsp;

## When opening a ticket

When contacting the helpdesk, please include as much relevant context as possible in your initial message rather than holding back information until later. Providing details about your goal, environment, recent changes, error messages, and what you have already tried allows us to understand your situation quickly and accurately.&nbsp;

&nbsp;

When key context is missing, we often need to ask several follow-up questions, which slows down the process and can lead to misunderstandings or incomplete solutions. Sharing the full picture upfront helps us diagnose the issue faster, avoid unnecessary back-and-forth, and get you to a solution more efficiently.

&nbsp;

At Hackolade, we release a new version of the software every single week with new enhancements.&nbsp; Prior to opening a ticket, it is best to be running a recent, if not current version of the software.

&nbsp;

Please share precise and complete information in order to speed up troubleshooting and resolution:

* context: briefly describe what you’re trying to do, your environment (OS, software version), and whether the issue affects all users or specific ones.
* steps to reproduce: list the different steps leading to the error message, and ideally provide the data model file.  If necessary, you may mask information in the model file with File \> Save Obfuscated As…
* current behavior: describe what happened.  In most case, it is useful to provide screenshots or a short movie capture.&nbsp;
* expected behavior: explain what result or output you would expect for the operation.  In some cases, it may help to illustrate with a mockup.
* additional information : provide other details that might help with troubleshooting and a speedy response to your request.
* log files: information from the application logs can be immensely helpful for our development team to diagnose and resolve the issue, ideally captured immediately after the issue occurred. Log files can be found in Help \> Access Application Logs, or at:

  * Windows: in the C:\\Users\\%username%\\AppData\\Roaming\\HackoladeLogs directory
  * Mac/Linux: in the Users/$USER/Documents/HackoladeLogs folder.

&nbsp;

## When responding to a helpdesk email

In the email sent by our Zendesk helpdesk solution, the communication starts with the line "##- Please type your reply above this line -##".  &nbsp;

It is important to avoid replying with inline comments below that line\!&nbsp; If you type anything below that line, our helpdesk operator will not see your inline comments.

This line serves as a separator so that only your new comments are captured in the Zendesk operator screen.&nbsp; To ensure we get your feedback, please type your comments above that line.

&nbsp;

## The XY problem

When creating a ticket for support, it may also be helpful to take into consideration the following...

&nbsp;

The [XY problem](<https://en.wikipedia.org/wiki/XY\_problem> "target=\"\_blank\"") arises when someone attempts to solve problem X, and uses solution Y in an attempt to solve problem X, then also faces challenges with solution Y. Instead of seeking help for problem X, they request support for solution Y, obscuring the root cause and leading to miscommunication, wasted time, and suboptimal solutions.

&nbsp;

The XY problem is further described [here](<https://xyproblem.info/> "target=\"\_blank\""):&nbsp; In particular, it describes what to do about it:

* Always include information about a broader picture along with any attempted solution.
* If someone asks for more information, do provide details.
* If there are other solutions you've already ruled out, share why you've ruled them out. This gives more information about your requirements.

&nbsp;

The kind of answers you will get to your technical questions depends as much on the way you ask the questions as on the difficulty of developing the answer.

&nbsp;

## Support response times and Service Level Agreement&nbsp;

Hackolade provides maintenance and support for its products according to the following Maximum Response Times and Maximum Resolution Times.&nbsp; The Maximum Response Time and Maximum Resolution Times identified below are calculated using standard business hours and days:

&nbsp;

| **Ticket Priority** | **Maximum Response Time** | **Maximum Resolution Time** | **Definition** |
| --- | --- | --- | --- |
| &#49; – Urgent | &#49;5 minutes | &#52; Hours | Critical Business Impact, production line down |
| &#50; – High | &#49; Hour | &#56; Hours | Major Business Impact, multiple users affected, no workaround available |
| &#51; – Medium | &#50; Days | &#50; Weeks | Moderate Business Impact, single user affected, workaround available |
| &#52; – Low | &#56; Days | &#52; Weeks | Low Business Impact |
| &#53; – Project |  |  | Timeframe to be decided through coordination between the Project Manager and development, based on resources available, requirements and time estimates. |


&nbsp;

## Tracking your organization's support requests

For large customers of Hackolade, it might be useful for a person to be able to have a consolidated view of all the tickets of their organization.&nbsp; Hackolade uses the helpdesk solution by [Zendesk.](<https://www.zendesk.com/> "target=\"\_blank\"")&nbsp; You would be tracking your org tickets following these [instructions](<https://urldefense.com/v3/\_\_https:/support.zendesk.com/hc/en-us/articles/4408846805530-Submitting-and-tracking-requests-in-the-help-center-Customer-Portal\*topic\_vgd\_mqd\_yy\_\_;Iw\!\!MjXRb4uW6x5k\!Go5HRJbg8MJP-igoFe9N2EEP040b9SP7Iz-nVw3hH-GF1l8sptTcmzZlP5JDbq4Jhj8JEMTX9Ejh9b7DZ5Gp5JtAeYrW0Ue2$> "target=\"\_blank\"").&nbsp; Please follow the steps below:

&nbsp;

\- request from our support to create an organization in our Zendesk platform and provide the domain name or names that should be included.&nbsp; Also include the email addresses of each user who should have the rights to view all their org's tickets (as opposed to the default which is that a viewer can only see their own tickets.)

\- each user who needs to view this portal will need to sign up on [https://hackolade.zendesk.com/hc/en-us/signin](<https://hackolade.zendesk.com/hc/en-us/signin> "target=\"\_blank\"") then click on the Signup link

&nbsp;

![Zendesk signin](<lib/Zendesk signin.png>)

&nbsp;

then fill out the form:

![Zendesk signup form](<lib/Zendesk signup form.png>)

&nbsp;

Once signed up, go to [https://hackolade.zendesk.com/hc/en-us/requests](<https://hackolade.zendesk.com/hc/en-us/requests> "target=\"\_blank\"") (you may want to bookmark this link...) and identify yourself if necessary.&nbsp; Then click in the box with your name, and choose My activities:

![Image](<lib/Zendesk Choose My activities.png>)

&nbsp;

Depending on the rights you have been given, you should see just your requests and those for which you were Cc'd, or also your organization requests:

&nbsp;

![Zendesk My activities](<lib/Zendesk My activities.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

