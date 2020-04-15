a# Project Overview

In this project I are given a web-based application that reads RSS feeds. The original developer of this application clearly saw the value in testing, they've already included [Jasmine](http://jasmine.github.io/) and even started writing their first test suite! Unfortunately, they decided to move on to start their own company and we're now left with an application with an incomplete test suite. That's where you come in.


## Why this Project?

Testing is an important part of the development process and many organizations practice a standard of development known as "test-driven development." This is when developers write tests first, before they ever start developing their application. All the tests initially fail and then they start writing application code to make these tests pass.

Whether you work in an organization that uses test-driven development or in an organization that uses tests to make sure future feature development doesn't break existing features, it's an important skill to have!


## What will I learn?

You will learn how to use Jasmine to write a number of tests against a pre-existing application. These will test the underlying business logic of the application as well as the event handling and DOM manipulation.


## How will this help my career?

Writing effective tests requires analyzing multiple aspects of an application including the HTML, CSS and JavaScript - an extremely important skill when changing teams or joining a new company.

Good tests give you the ability to quickly analyze whether new code breaks an existing feature within your codebase, without having to manually test all of the functionality.


# Development Strategy

For a refresher (or reference) before you begin writing code, we recommend reviewing the content from [JavaScript Testing](https://www.udacity.com/course/javascript-testing--ud549). Your project will be evaluated by a Udacity code reviewer according to the [Feed Reader Testing project rubric](https://review.udacity.com/#!/rubrics/18/view). Please review for detailed project requirements.

1. Familiarize yourself with the starter code
    * Open up `index.html` and review the functionality of the application within your browser /*Done*/
    * What is all the code in `app.js` doing? Be sure to read all code comments/*Done*/
    * Check out `style.css`. How is styling applied to the application?/*Done*/
2. Explore the Jasmine spec file in `feedreader.js`
    * This is the file in which you'll be writing your tests
    * Make sure to read all code comments here as well
    * Review the [Jasmine documentation](http://jasmine.github.io) if needed
3. Edit the `allFeeds` variable in `app.js` to make the provided test fail/*Done*/
    * See how Jasmine visualizes this failure in your application
    * Return the `allFeeds` variable to a passing state after reviewing the failed test
4. Write a test that loops through each feed in the `allFeeds` object and ensures it has a URL defined _and_ that the URL is not empty
    * For example, how would you use a `for...of` loop in this test?
 */ 
specs here defibed by function it  spec contains one or more expectations that test the state of the code make sure every URL defined and not empty
   it('URL is defined ', function() {
        allFeeds.forEach(function(feed) {
        feedLink = feed.url;
        expect(feedLink).toBeDefined();
        expect(feedLink.length).not.toBe(0);
5. Write a test that loops through each feed in the `allFeeds` object and ensures it has a name defined and that the name is not empty
    * Think about how you wrote the previous test. What are you testing for this time?
also using for loop to pass every name in the object tha name defined and not empty 
it('name is defined', function() {
        allFeeds.forEach(function(feed) {
        feedName = feed.name;
        expect(feedName).toBeDefined();
        expect(feedName.length).not.toBe(0); 

6. Write a new test suite named `"The menu"`
    * What are you `describe`-ing in this test suite?
The describe function is for grouping related specs, typically each test file has one at the top level. The string parameter is for naming the collection of specs, and will be concatenated with specs to make a spec's full name
describe('Menu', function () {} 
7. Write a test that ensures the menu element is hidden by default
    * You'll have to analyze the HTML and the CSS to determine how the hiding/showing of the menu element is implemented
    * What code in `app.js` is directly involved with toggling the menu on and off?
it('Menu hidden by default', function () {
         expect($('.menu-hidden').is(':visible')).toBe(true);

8. Write a test that ensures the menu changes visibility when the menu icon is clicked. This test should have two expectations: does the menu display itself when clicked, and does it hide when clicked again?
    * Think about how you wrote the previous test. What is different this time around?
    * Which clickable element are you checking for?
    * How do you "simulate" a mouse click that element without actually clicking it?
 it('changes visibility when is clicked', function () {
          $('.menu-icon-link').trigger('click');
          expect($('.menu-hidden').is(':visible')).toBe(false);
        });
9. Write a test suite named `"Initial Entries"`
    * What are you `describe`-ing in this test suite?
describe('Initial Entries', function() {}
10. Write a test that ensures when the `loadFeed` function is called and completes its work, there is at least a single `.entry` element within the `.feed` container
    * How does Jasmine's `beforeEach()`function work?
    * How does the `loadFeed()` function in `app.js` work? Is it synchronous or asynchronous?
To help a test suite DRY up any duplicated setup and teardown code, Jasmine provides the global beforeEach, afterEach, beforeAll, and afterAll functions
As the name implies, the beforeEach function is called once before each spec in the describe in which it is called

 beforeEach(function (done) {
          loadFeed(0, function() {
            done();
          });

       it('entry element', function () {
         expect($('.feed .entry').length).toBeGreaterThan(0);
       });
11. Write a test suite named `"New Feed Selection"`
    * What are you `describe`-ing in this test suite?
 describe('New Feed Selection', function() {
        var testingFeed;
12. Write a test that ensures when a new feed is loaded by the `loadFeed` function that the content actually changes
    * How is this test different from the previous test?
beforeEach(function(done) {
       loadFeed(0, function() {
         testingFeed = $('.feed').html();
         loadFeed(1, done);
       });
     });

     it('if the feeds are not same', function() {
       expect($('.feed').html()).not.toEqual(testingFeed);
     });
