---
title: Setup
---
> ## Data
>
> The data we will be using in the workshop is to practice working with twitter data. Please download the data files `taxday.jsonl` and `Capitol Riot Tweets.txt` and keep it in an accessible place (such as your desktop).
> We used twarc to search for all mentions of the hashtag `#taxday` and created this file (April 15th is the deadline for Americans to file their annual income report).
> The Capitol riot tweets is a dataset from Kaggle. 
> <br/>
> [Taxday data download link](https://github.com/UCSBCarpentry/twitter-with-twarc/blob/gh-pages/data/taxday.jsonl)
> <br/>
> [Capitol Riot Tweets download link](https://github.com/UCSBCarpentry/twitter-with-twarc/blob/gh-pages/data/dehydratedCapitolRiotTweets.txt)
>
> Make sure you save the `taxday.jsonl` as a .jsonl file and not a .txt file. You can do this by right clicking in the browser, choose `save as` then choosing 'all file types'
> and remove the .txt ending and change it to .jsonl.
>
{: .prereq}


> ## Additional Utilities
> 
> We will also be using an extended set of utilities that will help explore the data collected through twarc.
> <br/>
> [twarc utilities download link](https://github.com/UCSBCarpentry/twitter-with-twarc/blob/gh-pages/files/utils.zip)
>
> Make sure you download and unzip this folder onto your desktop. Later in the workshop, we will upload this set of tools to our JupyterHub. 
>
{: .prereq}



### Getting the Necessary Privileges

Generally, we would call this 'getting your API key', but like many API's, the process of getting access to Twitter's has
become a complicated process. These instructions should create a new developer account with *Essential Access* privileges.

To get started, you will need:
* #### [A Twitter Account](https://twitter.com/){:target="_blank" rel="noopener"}:
Valid email account and cell phone number to receive texts are necessary.
* #### [Developer Account](https://developer.twitter.com/en){:target="_blank" rel="noopener"}:
You must create the Twitter account first, in order to link to the Developer account.

Getting developer access requires you to validate yourself as a human, so the
form is particular about having a valid phone number and email address added to your Twitter account. This is so Twitter can authenticate a user.

Once you are logged on to Twitter, go to 
the [Developer Portal sign-up page](https://developer.twitter.com/en/portal/petition/use-case){:target="_blank" rel="noopener"}

Fill out the application questions as listed here:

<img src="fig/setting-up-dev.PNG" width="500">

  
  - What country are you based in?
  - What's your use case? Choose `Doing academic research`
  - Will you make Twitter content or derived information available to a government entity or a government affiliated entity? `No` (recommended)
  - Click through the user agreement and verify your email.

### Making your Project and App

Right after verifying your email, you will be taken to your Developer Portal Dashboard and 
prompted to create a new *Project*. Every instance of Twarc is a *Twitter App* and 
Twitter Apps live inside of *Projects*. After selecting 'Exploring the API' as your use 
case, you will be given "Essential Access". Essential Access allows you to have one 
project with one App inside of it.

<img src="fig/dashboard.PNG" width="500">

<img src="fig/what-you-api.PNG">

<img src="fig/project-description.PNG" width="500">

### Acquiring Keys and Tokens

After you have completed setting up your project, you will see the App details below. You can edit the name and app icon if you'd like to personalize it.

<img src="fig/twarc-app.png" width="500">

Under the project name, you will see *Settings* and *Keys and Tokens* tab. You will need to navigate to *Keys and Tokens* to generate your 5 keys and tokens. 
You will need to click the _generate_ button to get each of your keys and tokens. They are not automatically made for you so you must generate them the first time.

If you forget to save, or lose your tokens, you can click _regenerate_ to regenerate your keys and tokens, and a new set is made for you. 
However, if you do regenerate any keys and tokens, you'll need to reenter them when you try to access the API again.  

<img src="fig/dev-keys-tokens.png" width="500">


> ## Necessary Keys and Tokens
>
> ***SAVE*** these keys in an accessible place like a password manager or in a document. You will not see these 
> keys again, so this is essential. You should have: 
>
> * API Key 
> * API Secret 
> * Authentication Bearer Token 
> * Access Token
> * Access Token Secret
>
> You will have succeeded when you have these 5 keys and tokens
{: .prereq}





<!--

### User Authentication Settings

After generating your tokens and keys, you need to authenticate to use the API. This can be found under Projects & Apps > Project > App.
Navigate to the User Authentication set up in the Settings Page and complete the following:
- Turn on OAuth 2.0
- Type of App: Single Page App
- Callback URL/Redirect URL: https://127.0.01/
- Website URL: https://ucsbcarpentry.github.io/

Save OAuth 2.0 Client ID and Client Secret

<img src="fig/Oauth-2.jpg" width="500">

-->

{% include links.md %}
