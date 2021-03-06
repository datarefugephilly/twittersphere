# Twittersphere

This is a small script that can harvest tweets from a public user account into a spreadsheet through a single command run at a terminal/command prompt.

It can harvest up to approximately the first 3,200 tweets from public user accounts in accordance with the Twitter API's limitations. 

Spreadsheets generated by this script contain tweets and all relevant information about them on the first tab, one tweet per row, and all relevant information about the Twitter user's public account information on the second tab.

## Requirements
To use this script, you will need:
* A Twitter account
* Twitter API credentials associated with your Twitter account.  To set these up, log into Twitter, visit the [Applications Management](https://apps.twitter.com/) section, click the "Create New App" button, and follow the onscreen instructions.
* The ability to access a terminal/command prompt and run commands

## Getting started

* First, install Ruby, version 2.2.1 or higher.  For information on installing ruby on Windows, Mac, and Linux, visit [Installing Ruby (source:ruby-lang.org)](https://www.ruby-lang.org/en/documentation/installation/)
* Next, the `twitter` and `rubyXL` gems are required for interacting with the Twitter API and for creating spreadsheets, respectively.   To install these, open up a terminal/command prompt and issue the following commands:

```
gem install twitter
gem install rubyXL
```

* Finally, make sure that you have Twitter API credentials set up.  For the application to use your API access credentials, they must be defined as environment variables with the following names: 

```
TWITTER_CONSUMER_KEY
TWITTER_CONSUMER_SECRET
TWITTER_ACCESS_TOKEN
TWITTER_ACCESS_TOKEN_SECRET
```

For more information on setting environment variables, visit the following suggested resources:
* Linux - [Environment Variables (source: help.ubuntu.com)](https://help.ubuntu.com/community/EnvironmentVariables)
* Mac OSX - [Where to Set Environment Variables in Mac OSX (source:osxdaily.com)](http://osxdaily.com/2015/07/28/set-enviornment-variables-mac-os-x/)
* Windows 10 - [How to Set Environment Variables in Windows 10 (source: techjunkie.com)](https://www.techjunkie.com/environment-variables-windows-10/)


## How to Use

To use this script, open a terminal/command prompt and navigate to the directory containing the script using the [cd command](https://en.wikipedia.org/wiki/Cd_(command)) and issue the following command:
```bash
ruby harvest.rb username X
```
Replace `username` with the Twitter handle (minus the "@" symbol) of the public user whose tweets you'd like to harvest.

Replace `X` with the number of tweets you'd like to harvest, starting with the latest.  The Twitter API allows for roughly the latest 3,200 tweets maximum to be harvested from a user timeline.

## Protected Accounts
This script will not harvest tweets from protected users.  It can only harvest tweets from public users.

## Rate Limiting
Harvesting a large volume of tweets at a rapid rate may result in rate limiting from Twitter.  This means that Twitter will begin requiring you to wait for certain periods of time (up to 15 minutes) between harvesting requests.  This script handles this case, and will report to the terminal if its rate limit has been hit.  It will retry at the recommended interval on its own and should not need to be restarted.
