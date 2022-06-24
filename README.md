# Module-15-Challenge - Roboadvisor
Design and develop a robo advisor based upon Machine Learning (ML) and Natual Language Processing (NLP) to advise retirement plan options.

The Starter Code was provided along with the relevant data.

---

## User Story
As a digital transformation consultant you are hired by a prominent retirement plan provider in the country to develop a robo advisor to recommend investment portfolio for retirement plans leveraging advances in ML and NLP, which are disrupting the industry to improve the customer experience.

---

## Acceptance Criteria  

Create a Robo Advisor bot using AWS Lex and Lambda that must meet the following criteria:

* initial robo advisor muse be configured with a single intent that establishes a conversation about requirements to suggest an investment portfolio for retirement.
* test to ensure the bot responds accurately to the conversation with the user
* test the validation and fulfilment functions which are designed using AWS Lambda
* record short videos for the last two items establishing proper functioning of the bot and its validation/fulfilment functions

---

## The Application  

The application uses the following steps to build the robo advisor:

### Configure the initial Robo Advisor
* Using Amazon Lex create a new custom Amazon Lex bot, with the following parameters:
> Bot name: RoboAdvisor  
Language: English (US)
Output voice: Salli  
Session timeout: 5 minutes
Sentiment analysis: No
COPPA: No
Advanced options: No
All other options: The default value

* Add a new intent, `recommendPortfolio`
* Configiure sample utterances as follows: 
>I want to save money for my retirement  
I'm {age} and I would like to invest for my retirement  
I'm {age} and I want to invest for my retirement  
I want the best option to invest for my retirement  
I'm worried about my retirement  
I want to invest for my retirement  
I would like to invest for my retirement  

* Create four slots as follows; these slots are the variables used to store the results of the conversation and are passed to the Lambda functions during validation and fulfilment. Make sure you use the same slot names in the Lambda function.   
|SLOT NAME| SLOT TYPE |PROMPT|  
|-|-|-|  
|firstName|  AMAZON.US_FIRST_NAME| Thank you for trusting me to help, could you please give me your name|  
|age | AMAZON.NUMBER| HOW OLD ARE YOU?|  
|investmentAmount| AMAZON.NUMBER | How much do you want to invest?|    
|riskLevel | AMAZON.Alphanumeric| What level of risk are you willing to take? (None, Low, Medium or High)|  
* Mark all the slots as `required`  
* On the `Confirmation prompt` set the following messages:  
>Confirm; Thanks, now I will look for the best investment portfolio for you. Okay?  
Cancel; No Problem. I will be pleased to assist you in the future.

### Build and Test the Robo Advisor

* click on the `Build` button to build
* click on `Test` button to test the conversation
* record the conversation using `CMD-SHIFT-5` on your mac. [Click here](https://drive.google.com/file/d/1BOgV0yS6litvsQS_oDt_10i_CWMXIrMf/view?usp=sharing) to view the recorded coversation.

### Enhance the Robo Advisor with Amazon Lambda Function
The Lambda function is created to validate the inputs and also to accomplish fulfilment of the user requests. Create the Lambda function as follows:
* Create a new Lambda function from scratch,  name it `recommendPortfolio`
* Choose `Python 3.7` as the runtime programming language 
* In the online code editor, delete the AWS-generated default lines of code, and then paste in the provided `lambda_function.py` from the Starter code.
* modify the `lambda_function.py` to do validation of user inputs:
    - age must be between 0-65
    - investmentAmount has to >=5000
* once the itent is fulfilled, the bot reponds with the recommendation based upon risk levels as follows:
    - None: “100% bonds (AGG), 0% equities (SPY)”
    - Low: “60% bonds (AGG), 40% equities (SPY)”
    - Medium: “40% bonds (AGG), 60% equities (SPY)”
    - High: “20% bonds (AGG), 80% equities (SPY)”  
    
* test the bot using test events that are provided.  Attached are the screenshots of the results of these tests:
    - [age error test](ageError.png)
    - [Correct Dialog](correctDialog.png)
    - [Incorrect Amount test](incorrectAmt.png)
    - [Negative Age test](negativeAgeError.png)
* integrate the Lambda function into the bot by
    - unchecking the `Confirmation` prompt
    - checking  `Lambda initialization and validation` and `Fulfillment` sections and selecting the lambda function `recommendPortfolio`
* build the bot  
* test the bot  
* record the bot conversation using `CMD-SHIFT-5` on your mac. [Click here](https://drive.google.com/file/d/1NsHZ3qyrE-7JBLSY-ESgsIy4P_RsivWF/view?usp=sharing) to view the recorded conversation.

---

## Technologies
The application is developed using:  
* Language: Python 3.7,   
* Packages/Libraries: Pandas; AWS Lex, AWS Lambda  
* Development Environment: VS Code and Terminal, Anaconda 2.1.1 with conda 4.11.0, Jupyterlab 3.2.9
* OS: Mac OS 12.1

---
## Installation Guide
Following are the instructions to install the application from its Github respository.  

### Clone the application code from Github as follows:
copy the URL link of the application from its Github repository      
open the Terminal window and clone as follows:  

   1. %cd to_your_preferred_directory_where_you want_to_store_this_application  
    
   2. %git clone URL_link_that_was_copied_in_step_1_above   
    
   3. %ls     
        Module-15-Challenge    
        
   4. %cd Module-15-Challenge     

At this point you will have the the entire application files in the current directory as follows:

    * ageError                        (Test Result screenshot)  
    * bot w lambda                    (bot video)  
    * bot_without_lambda              (bot video)   
    * correctDialog                   (test result screenshot)  
    * incorrectAmt                    (test result screenshot)  
    * negativeAgeError                (test result screenshot)  
    * README.md                       (this file you are reading)  
    * Starter_Code  
        - Lambda  
            - lambda_function.py      (start code that was modified)
        - Test_Events                 (used for testing the Lambda function)
            - ageError.json  
            - correctDialog.json  
            - incorrectAmountError.json  
            - negativeAgeError.json  
       
---

## Usage
The following details the instructions on how to run the application.  

### Setup the environment and Run the application 

In order to run the Robo Advisor youwill have to log on to the Amazon AWS Console and go through the process of creating the bot and then running the bot with lambda function as detailed above.

---

## Contributors
Ashok Pandey - ashok.pragati@gmail.com   
www.linkedin.com/in/ashok-pandey-a7201237

---

## License
The source code is the property of the developer. The users can copy and use the code freely but the developer is not responsible for any liability arising out of the code and its derivatives.

---