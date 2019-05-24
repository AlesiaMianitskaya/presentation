Hello, today I want to talk about automation end-to-end tests using Puppeteer.

#### What is End to End Testing & Why is it Important

Before I dive into how to use Puppeteer for end-to-end testing, I think it’s important to briefly explain what it is and why it’s important for web development today.
End-to-end testing is a methodology used to test whether the flow of an application is performing as designed from start to finish. The purpose of carrying out end-to-end tests is to identify system dependencies and to ensure that the right information is passed between various system components.
Essentially, end-to-end testing replicates, in an automated fashion, exactly what a user could do while interacting with the application or browser. And this is done to ensure the application works properly and as expected.
As web applications get more and more complex and full featured, it becomes harder and harder for manual QA teams to keep up with testing every single piece of functionality each time the application is ready to deploy a new feature. End-to-end testing frameworks were created to take repetitive tasks of checking functionality out of the hands of people and have machines (which can move much faster than actual users and exactly replicate a test every time) shoulder more of the load.
Ultimately, it still comes down to us, as developers, to ensure our applications work the way we expect, but testing helps us to better ensure we’re not introducing new bugs into our code.
 
 #### What are Headless Chrome & Puppeteer
The next thing to cover is what exactly are headless Chrome and Puppeteer, and why are they always bundled together?
 
Puppeteer is a Node library which provides a high-level API to control Chrome or Chromium over the DevTools Protocol.
Puppeteer runs headless Chrome or Chromium instances by default, which is why they’re always mentioned in tandem.
Most things that you can do manually in the browser can be done using Puppeteer!
Puppeteer was made for Chrome by the Google Chrome DevTools team to help further automated/headless browser testing and make it less painful for the rest of us.
The biggest drawback is that Puppeteer only works with Chrome.
### Puppeteer Examples

Now it’s time to get down to the business of getting Puppeteer up and running.
Getting started with Puppeteer is actually incredibly easy — just type npm i puppeteer and you’re ready to go. It’s this easy because the Chrome DevTools team conveniently packages each version of Puppeteer with a version of Chromium (the headless Chrome part) that it’s guaranteed to run with.
Let’s take a look at what Puppeteer can automate.
### Take a Screenshot of a Page
As you’ll see, as long as puppeteer is imported at the top of the file, it’s good to go and all the methods packaged along with Puppeteer like newPage() and browser are instantly available to you.
This first sample script goes to the Google home page and takes a photo of the page and saves it to a .png file inside of the repo named ‘google.png’.
The code is pretty self-explanatory. To begin, a headless Chrome browser is launched, a new page is opened, the URL for that page is set to Google, a screenshot is taken and the browser is closed. The whole thing is clean, elegant, asynchronous and wrapped within an IIFE (immediately invoked function expression) so as soon as the script is called, the function runs.
### Create a PDF
The second Puppeteer example goes to a website and makes the site page it visits into a PDF.
Similar to the first script, this one sets up Puppeteer, creates a new browser page, goes to the website and then uses the page.pdf() method to make a PDF of the whole page. That PDF is once again, saved into the project folder. Pretty simple.
#### Google Something
This third example is probably something more like what would be tested in an end-to-end test — it’s automating a Google search (and taking a screenshot to confirm the search worked, in headless mode).
In this script, Puppeteer launches a new browser page, it goes to Google, it waits for the search box and the search button to be visible and types ‘cookies’ into the input, then it waits for the page to navigate to the cookies search results and takes a screenshot before closing the browser at the end.
### Debugging Puppeteer
Now that Puppeteer is running, I want to call out some awesome tools that are built into it to make debugging it much less painful.
### Turn Off Headless Mode
The first (and most obvious one) is how to turn off Chrome’s headless mode; if you want watch the automated browser open and attempt to go through the steps laid out for it. Inside the script where Puppeteer is launched, just add the following line: puppeteer.launch({headless: false});
### Enable SlowMo
SlowMo is just what it sounds like, it slows down Puppeteer’s operations so normal humans can see what’s going on. It can be instantiated in the same command where headless is set to false for Puppeteer; Just add puppeteer.launch({slowMo: 500}) or however many milliseconds you want to slow down the actions by.
###  Auto-Open DevTools Panel
The third debugging trick I have is how to tell Puppeteer whether to auto-open a Chrome DevTools panel with each tab. So if you need to, you can catch things being logged to the console inside the automated test run.
Once again, inside the initial command launching Puppeteer, add in puppeteer.launch({headless: false, devtools: true}); to open a DevTools panel.
Note: If this option is true, the headless option will be set false
### More Cool Features of Puppeteer
In addition to debugging Puppeteer, I wanted to point out a few more cool features that it offers. 
Puppeteer can:
- Run in a Docker container or serverless environment,
- Intercept network requests,
- Capture performance info,
- Test a Chrome extension,
- Run code in a page, and
- Emulate Chrome on a mobile device

That’s a lot of additional useful things it can be used for. The team really wants to make it useful to devs in many ways.
### Bonus: React & Jest & Puppeteer
Also I want briefly mention how to integrate Puppeteer into a React project with Jest tests. 
### Configuration of Jest & Puppeteer
Jest has some very helpful documentation to smoothly work Puppeteer into its own testing framework, and there’s even an entire NPM package named jest-puppeteer to help the process along. Here’s what to install and configure to make Jest and Puppeteer play nice.

- npm install --save-dev jest-puppeteer puppeteer jest

Once everything’s been installed, you can either configure your Jest config file, Webpack file or your package.json file to let Jest know that Puppeteer’s there and ready to be used. Here’s how did it in the package.json.
Right above the scripts in the file, added this snippet, and inside the scripts, included a test command which just runs Jest.
### Jest & Puppeteer Test

If you’ve ever written a Jest test before, the syntax should look familiar. It is simple example test where Jest should go to the Google homepage and find the text ‘Google” on said page after it’s loaded.
If tests failed, you can debug just as you normally would (and even turn on the automated Chrome browser if you need to see what’s messing up), and if not, your computer screen can be test free as your end-to-end tests still run in the background. Awesome. That doesn’t seem so hard, now does it?
 
### Conclusion
Puppeteer is a powerful tool developed by the Google DevTools team to make headless, automated browser testing easier in every way. There’s less configuration to get started, the syntax makes more sense. Likewise, it’s easy to integrate into React applications to automate Jest tests to run headlessly as well.
Thanks for watching, I hope this gives you an idea of how to get started using Puppeteer for your own end-to-end testing and integrating with React and Jest tests. 


