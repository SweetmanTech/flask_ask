# Flask Ask
Simple memory game using local development for Amazon Alexa
* Configure Local
* Run
* Configure Skill
* Test
* Question and Bugs
## Configure
1. ```git clone url```
2. ```cd flask_ask```
3. ```sudo pip install flask-ask```
## Run Local
1. ```python memory_game.py```
2. Open a second terminal
3. ```./ngrok http 5000``` (windows: ```ngrok.exe http 5000```)
4. Copy the URL in either of the `Forwarding` values
## Configure Skill
1. Make sure you're logged into your Amazon developer account, and go to your list of [Alexa skills](https://developer.amazon.com/edw/home.html#/skills)
2. Click the "Add a New Skill" button.
### Skill Information Settings
1. Leave the "Skill Type" set to "Custom Interaction Model"
2. Enter "Memory Game" (without quotes) for both the "Name" and "Invocation Name" fields.
### Interaction Model Settings
1. Copy the JSON below into the "Intent Schema" field.
```
{
    "intents": [{
        "intent": "YesIntent"
    }, {
        "intent": "AnswerIntent",
        "slots": [{
            "name": "first",
            "type": "AMAZON.NUMBER"
        }, {
            "name": "second",
            "type": "AMAZON.NUMBER"
        }, {
            "name": "third",
            "type": "AMAZON.NUMBER"
        }]
    }]
}
```
2. Copy the utterances below into the "Sample Utterances" field.
```
YesIntent yes
YesIntent sure

AnswerIntent {first} {second} {third}
AnswerIntent {first} {second} and {third}
```
### Configuration Settings
1. Make sure the HTTPS radio button is selected for the "Endpoint" field.
2. Enter the HTTPS endpoint (copied from ngrok terminal) into the textfield.
### SSL Certificate Settings
It's important to choose the second radio button with the label because that's what ngrok uses.

> My development endpoint is a subdomain of a domain that has a wildcard certificate from a certificate authority.

## Test
You: "Alexa, start memory game" or "Alexa, ask memory game"

## Questions and Bugs
Please see [here](https://developer.amazon.com/blogs/post/Tx14R0IYYGH3SKT/Flask-Ask-A-New-Python-Framework-for-Rapid-Alexa-Skills-Kit-Development) for help and bugs
