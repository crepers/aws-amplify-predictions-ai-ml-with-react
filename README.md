# Language Translation And Syntax Tool Using AWS Amplify AI/ML With React 

**Language Translation and Syntax Tool Made With React Using AWS Amplify to Integrate Artificial Intelligence and Machine Learning**

### Install Amplify CLI
```bash
npm install -g @aws-amplify/cli
```

### Initialize Amplify App
```bash
amplify init
```
Fill out the form with the appropriate info for your app:
``` bash
? Enter a name for the project (myApp)  

? Enter a name for the environment (dev)   

? Choose your default editor: (Use arrow keys)
❯ Visual Studio Code 
  Atom Editor 
  Sublime Text 
  IntelliJ IDEA 
  Vim (via Terminal, Mac OS only) 
  Emacs (via Terminal, Mac OS only) 
  None  

? Choose the type of app that you\'re building (Use arrow keys)
  android 
  ios 
❯ javascript  

? What javascript framework are you using (Use arrow keys)
  angular 
  ember 
  ionic 
❯ react 
  react-native 
  vue 
  none  

? Source Directory Path:  (src) 

? Distribution Directory Path: (build) 

? Build Command:  (npm run build) 

? Start Command: (npm start) 
Using default provider  awscloudformation

? Do you want to use an AWS profile? (Y/n) 
```
After choosing how you want to authenticate with AWS, Amplify will create all the necessary resources to store your app in the cloud.  
*Note: See the `#amplify` section of `.gitignore` to see the paths to files with credential info that you can expect to see in the amplify directory but aren't present in this repo.*   Now it's time to add our services. For a full list of services you can add see the [Amplify docs](https://docs.amplify.aws/), but for our purposes we're just going to add a few.

## Add Auth
```bash
amplify add auth

❯ Default configuration 
  Default configuration with Social Provider (Federation) 
  Manual configuration 
  I want to learn more. 

 Warning: you will not be able to edit these selections. 
 How do you want users to be able to sign in? (Use arrow keys)
❯ Username 
  Email 
  Phone Number 
  Email or Phone Number 
  I want to learn more. 

 Do you want to configure advanced settings? (Use arrow keys)
❯ No, I am done. 
  Yes, I want to make some additional changes. 
```

## Add AI/ML Predictions
```bash
amplify add predictions

? Please select from one of the categories below 
  Identify #Identify text, labels, or entities (like celebrities) embedded within an image
  Convert #Convert from one language to another, convert text to speech, or convert speech to text
❯ Interpret #Interpret Text for Meaning, Sentiment, Idioms, Syntax, etc.
  Infer #Add Custom Models Using Sagemaker Endpoint 
  Learn More 

? What would you like to interpret? (Use arrow keys)
❯ Interpret Text 

#names must be alphanumeric
? Provide a friendly name for your resource (myinterpreter)

? What kind of interpretation would you like? 
  Language 
  Entity 
  Keyphrase 
  Sentiment 
  Syntax 
❯ All 

? Who should have access? (Use arrow keys)
  Auth users only 
❯ Auth and Guest users 
```

## Add Hosting
Once your app is initialized, you can push updates to amplify services using the `amplify push` command, but before we can access it on the web, we have to add hosting.  

*Note: `amplify push` will only update changes to amplify services, to update app code use `amplify publish` or Automatic Git deployments.*

```bash
amplify add hosting

? Select the plugin module to execute (Use arrow keys)
❯ Hosting with Amplify Console (Managed hosting with custom domains, Continuous deployment) 
  Amazon CloudFront and S3 

? Choose a type (Use arrow keys)
  Continuous deployment (Git-based deployments) 
❯ Manual deployment 
  Learn more
```
Once you get the confirmation that hosting was added, you can publish to the web using `amplify publish`. Once the app is deployed you'll be shown the randomly assigned URL where you can find your app and confirm that the entire process worked.  
You can find instructions on how to use a custom domain with your app [here](https://docs.aws.amazon.com/amplify/latest/userguide/custom-domains.html).  

*Note: Make sure you add all amplify files that have sensitive info in them to your gitignore before pushing to a public repo. To ensure security you can add the entire `amplify` directory to gitignore and then use `amplify pull` to get the necessary backend files before updating.*