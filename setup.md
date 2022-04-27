---
title: Setup
---
> ## Data
> Coming soon...
{: .prereq}

### Getting the Necessary Credentials

Generally, we would call this 'getting your API key', but like many API's, the process of getting access to the guts of Twitter has 
become a complicated process. For this workshop, these instructions should get a brand new account what Twitter calls *Essential Access*
credentials.

To get started, you will need: 
* #### [A Twitter Account](twitter.com):
Valid email account and cell phone number necessary. 
* #### [Developer Account](developer.twitter.com/en): 
You must create the twitter account to link to the Developer account first. 
Getting developer access really does require to validate yourself as a human, so the
form is particular about having a valid phone number and email address added to your Twitter account.

Fill out the Application questions as listed: 
  - someone insert figure here
  - What Country are you based in? 
  - What's your use case? Choose `Doing academic research` (recommended)
  - Will you make Twitter content or derived information available to a government entity or a government affiliated entity? `No` (recommended)
  - Click through the user agreement and verify your email. 

### Making your Project and App

Right after verifying your email, you wil be taken to your Developer Portal Dashboard and prompted to create a new *Project*.
Every instance of Twarc is a *Twitter App* and *Twitter Apps* live inside of *Projects*. After selecting 'Exploring the API' as your use case, 
you will be given "Essential Access". Essential Access allows you to have one project with one App inside of it. 

<img src="fig/what-you-api.PNG" width="400">
<img src="fig/project-description.PNG" width="400">

*SAVE* these keys in an accessible place like a password manager. You will not see these keys again, so this is essential. You should have:
* Consumer Key: API Key and Secret 
* Authentication Bearer Token
* Access Token and Secret 

> ## Obtain Access Token and Secret 
> On the App Page (twarc-app in the example) go to 'Keys and Tokens'. Generate 'Access Token and Secret Token'. Note down both Access Token
> and Access Token Secret. If you want to use twarc on another computer, generate new keys and tokens

There are a total of 5 of these super-long numbers to keep track of. 


{: .prereq}


### User Authentication Settings 

After generating your tokens and keys, you need to authenticate to use the API. This can be found under Projects & Apps > Project > App.
Navigate to the User Authentication set up in the Settings Page and complete the following: 
- Turn on OAuth 2.0
- Type of App: Single Page App
- Callback URL/Redirect URL: https://127.0.01/
- Website URL: https://ucsbcarpentry.github.io/

- someone insert figure here 

Save OAuth 2.0 Client ID and Client Secret 

> ## You will know you have succeeded when you have 
> the following set of Keys and Tokens: 
> - Bearer Token
> - API Key
> - API Key Secret 
> - Access Token
> - Access Token Secret 
> - OAuth 2.0 turned on
{: .prereq}

{% include links.md %}
