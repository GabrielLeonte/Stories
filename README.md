[Instructions]: # (To submit to the Grant For The Web x DEV Hackathon, please fill out all sections.)


## What I built
Stories is a web application that allows users to sent anonymous letters to a loved person. The best part of using our platform is the fact that everybody can earn moneys using Web Monetization API. The Platform Provides free content and premium content based on a COIL Subscription (5$ per month). 


### Submission Category: 

[Note]: # (Foundational Technology, Creative Catalyst, or Exciting Experiments)
Exciting Experiments and Creative Catalyst

## Demo
[Go to Stories](https://stories-aca62.web.app/)
 

## Link to Code

[Client](https://github.com/GabrielLeonte/Stories)
[Firebase Functions](https://github.com/GabrielLeonte/Stories-Functions)


## How I built it 

The slack is a composite between Firebase and NuxtJS and Send Grid API
We're using Firebase Hosting (for demo), Firebase Real Time Database to store every public post, and Firebase Functions for Send Grid API to deliver each amazing love letter.

Day 1 started with another kind of idea, first project was a way that photographers can monetize their own photos, but after around 2 weeks while scrolling through Coil web page i just realized that this kind of project already exists and its Imgur Emerald.


Day 20: After i found out that Imgur Emerald already exists, I've decided to build this love story project, because we're living a pandemic time, and the love expression has gone low because of the social distancing, so its the perfect time to write a love letter to the one we love. Why anonymous ? Well, you still have the opportunity to tell who you are, but let's get our loved ones more active and challenge them to find out who is behind that magic letter.

Submission Day: Here we are with a working application that is ready to deliver awesome letters to our loved ones. This platform still has a lot of potential, i would like to make in production, but first of all, i need some teammates to do it, add email scheduling function, filtering functions, improve the UI and UX, and many more awesome things.


## Additional Resources/Info 
- [Illustrations from Undraw.co](https://undraw.co/illustrations)
- [Bulma Framework](https://bulma.io/)

## Screen Shots
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/a2rkbp4gcmh931urvkba.png)

### Setup

```bash
# install dependencies
$ npm install

# rename .env.example to .env
# complete env file with firebase auth details

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

Also make sure to setup firebase function from the other repository!
