# whatsapp-Chatgpt-bot


# whatsapp-Chatgpt-bot


In this note, we'll build a bot that gives you the ability to chat with ChatGPT directly from Whatsapp!

We'll be using the ChatSonic API to build this. If you're not familiar with ChatSonic, it's like ChatGPT, but with superpowers! It's powerful and incredibly conversational for text and image creation, and it's definitely worth checking out if you want to level up your content creation game

One of the key benefits of using ChatSonic is that it can connect to the internet, allowing it to access a wealth of information and resources. This makes it even more powerful than ChatGPT, as it can provide more accurate and up-to-date responses to user queries.

Let's get started!

<h2>Step 1: Setting up Twilio account</h2>
If you have ever built WhatsApp bots before, you must have heard of Twilio. Twilio is a cloud communications platform that allows you to build WhatsApp bots easily. With Twilio, you can create automated chatbots that can send and receive messages from your customers on WhatsApp.

You can use Twilio to build a wide range of WhatsApp bots, such as customer service chatbots, e-commerce chatbots, and more.

Setting up a WhatsApp bot with Twilio is super simple and straightforward.

![image](https://user-images.githubusercontent.com/89147384/214356187-4fc3615f-0808-4c53-8489-f029f1c160dc.png)


The first step is to sign up for a Twilio account. You can sign up for a free trial account to get started.

After creating and verifying your account, log into your account and click on "Console" tab on the navbar. Here, take note of your ACCOUNT SID and AUTH TOKEN.

![image](https://user-images.githubusercontent.com/89147384/214356374-fe53616f-ea77-49b9-b0e3-007a1bc9329e.png)


Finally, to set up your WhatsApp sandbox environment, <a href="https://console.twilio.com/us1/develop/sms/settings/whatsapp-sandbox?frameUrl=%2Fconsole%2Fsms%2Fwhatsapp%2Fsandbox%3Fx-target-region%3Dus1">Click Here</a>. This will take you to the appropriate page where you can complete the setup process.

![image](https://user-images.githubusercontent.com/89147384/214356672-d49721e6-06e7-45d7-8187-83b3d2bb804d.png)


Connect to your sandbox by sending a WhatsApp message to the Twilio number on the page.
PS. Your join code will be different than mine.

![image](https://user-images.githubusercontent.com/89147384/214356747-4fc779fc-48e5-464a-a655-e8ff51907ae3.png)

Great! We’ve set up Twilio for our chatbot. Believe it or not, this was the most difficult part of this entire note. 😆

Moving on…

<h2>Step 2: Setting up ChatSonic account </h2>
Visit <a href="http://app.writesonic.com/">app.writesonic.com</a> and create an account/log in. Once you're in, hover your cursor over the display picture in the top-right corner to open the profile menu.

![image](https://user-images.githubusercontent.com/89147384/214356837-956b2a59-bb29-43de-b34a-9bd8977313db.png)

To access your API dashboard, click on the "API Dashboard" button. This will navigate you to the page containing your API dashboard. In this dashboard, click on the switch to activate the API.

![image](https://user-images.githubusercontent.com/89147384/214356886-136cd145-c3cd-47bf-afa4-6c72789dda9d.png)

Once the API has been activated, click on the “Reveal API Key” button and note down your API key.

This API key will be used to interact with the ChatSonic API. To explore how the API works, head over to the documentation of the API via <a href="https://docs.writesonic.com/reference/chatsonic_v2businesscontentchatsonic_post-1">This Link</a>.

![image](https://user-images.githubusercontent.com/89147384/214356973-2d560e2f-d2a2-46c4-bba2-d14b6c3cf4fd.png)

You can also test the API by pasting your API key in the Header and clicking on the “Try it!” button.

![image](https://user-images.githubusercontent.com/89147384/214357705-6c139e72-3373-4481-a520-5b191541160a.png)

Now we’re all set to write the code for our chatbot.

So without wasting any more time, let’s get down to business.

<h2>Step 3: Building the webhook</h2>
We'll be using Replit to deploy our webhook. Replit is a really cool platform that allows you to build, run, and share code in a variety of programming languages. It's super easy to use and you can get started with just a few clicks.

If you don't already have a Replit account, I'd recommend creating one. It's free and only takes a few minutes to set up. Go here to create an account/login.
I've set up an environment for us to use on Replit to skip the setup process.

Just head on over <a href="https://replit.com/@sahildotexe/chat-bot-template?v=1">Here</a> and give it a couple of seconds to fork. Easy peasy!
The server.js file contains all the code for our chatbot.

![image](https://user-images.githubusercontent.com/89147384/214357813-1096c253-e898-464f-8c6f-12bc29e25347.png)

Let me break this code down and explain the important parts in a way that's a bit easier to understand.

![image](https://user-images.githubusercontent.com/89147384/214357872-f31fc8a6-04b1-4012-94bc-36e6cc339e1e.png)

So first off, we're pulling in some libraries at the top of the code that we'll be using later on. These libraries give us some tools to build out our webhook and do stuff like send and receive text messages, make API requests, and more.

![image](https://user-images.githubusercontent.com/89147384/214357920-1cf7787b-42f9-4df5-b094-c98e2895b98a.png)

Next, we see some variables being defined with const. These are just strings or objects that we'll be using later on in the code.
Copy and paste the accountSid and authToken from your <a href="http://console.twilio.com/">Twilio console</a>.
Similarly, enter your ChatSonic API key on line number 11.

![image](https://user-images.githubusercontent.com/89147384/214357999-34679ec9-eacf-46e2-b560-9153bfc176db.png)

Next, we see an app.post() route being defined. This route will be run whenever we get a POST request at the /incoming endpoint.

Inside the route handler, we see a bunch of stuff happening.

First, we create a new MessagingResponse object, which is just an object that we can use to build a response to send back to the client. Then, we see an async function being defined, which makes a request to the ChatSonic API using the sdk object that we defined earlier. The function is passed some options and some additional options specifying the "engine" to use.

You can set the enable_google_results option as true if you want your chatbot to include google results in its answers.

The enable_memory option can be set to true or false depending on whether you want the chatbot to remember the conversations or not.

Finally, we see the twiml.message() function being called with the response from the ChatSonic API, and the response being sent back to the client.

<h2>Step 4: Deploying the webhook</h2>
Click on the run button or type node server.js in your console to run the webhook.

![image](https://user-images.githubusercontent.com/89147384/214358286-925dd96e-b9b2-4d1a-981c-bc0712a81c30.png)

LFG! If you’re getting the same message as mine, it means you’ve successfully deployed the webhook.

<h2>Step 5: Configuring the webhook on Twilio</h2>
Copy the URL of your of your webhook from Replit.

![image](https://user-images.githubusercontent.com/89147384/214358345-14fc252a-bfe4-48ca-ac57-7026b93c1855.png)


Let's return to the <a href="https://console.twilio.com/us1/develop/sms/settings/whatsapp-sandbox?frameUrl=%2Fconsole%2Fsms%2Fwhatsapp%2Fsandbox%3Fx-target-region%3Dus1">WhatsApp Sandbox</a> and input a webhook URL for receiving messages.

![image](https://user-images.githubusercontent.com/89147384/214358404-cd756517-7819-4e7d-8d97-e5802fe47e69.png)

Don’t forget to add /incoming at the end of the URL which is the route of our webhook that we had defined earlier.
Finally, click on the “Save” button at the bottom of the page to save our config.

Our chatbot is finally ready to use. Let’s test it out! 🥳

![image](https://user-images.githubusercontent.com/89147384/214358576-2e782373-6df2-4455-bbe2-2427b23218c3.png)

You've made it!
And just like that, you've just built your own personal ChatGPT with the ChatSonic API in less than 10 minutes! The best part is you can now access it directly through WhatsApp without opening a browser and visiting a website. Just send it a WhatsApp message, and it will use its natural language processing abilities to generate a response. You can even train it on specific topics or conversational styles to make it more tailored to your preferences.

Personally, I had a lot of fun building this chatbot. It is indeed a rewarding build that is sure to teach you a lot, whether you're a seasoned developer or a complete beginner.

Till next ship,
Akhil

Thank You!

