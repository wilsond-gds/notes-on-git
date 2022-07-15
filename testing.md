# Automating visual testing of your work

Software can alert you if you have created a visual bug while working on your CSS code. Options range from the simple to the complex. Here we’ll use a package called [backstop.js](https://github.com/garris/BackstopJS) to create a test that you can run whenever you think you make have broken your design.

Add backstop.js to your project through `npm` – I used `npm install backstop --save-dev` to save it to my `package.json` file. 

We will run backstop as a stand-alone app at this point: in the future we will learn how to make it run automatically when you push your code to GitHub. 

## Initialise backstop

Once the package is installed, your first step is to initialise backstop by running `backstop init`. This will create all the files backstop needs to run, and produce a `backstop.json` that you can modify to control how backstop works.

Once this has completed, you may want to [visit this tutorial](https://www.codurance.com/publications/2020/01/16/backstopjs-tutorial/utm_sourcenewsletterutm_mediumemailutm_campaignfeb2020) which has a useful list of viewports you can cut and paste into `backstop.json`.

**Only initialise backstop once.** If you run `backstop init` again you will loose all your changes in `backstop.json`.

## Create the reference images

Backstop uses a programmable version of Chrome to create screenshots of your website. You will need to tell backstop where your website can be found in the `backstop.json` file. Edit the `"scenarios": [{ "url": }]` value to do this.

When backstop is able to find your website, run `backstop test`. This will create a screenshot of the page you are testing at each of the viewport sizes you’ve specified in `backstop.json`. Backstop will report that all the tests have failed, but this is OK, as you haven’t given backstop a reference image to compare the screenshots against.

To tell backstop that the current state of the website is correct, run `backstop approve`, and backstop will promote the screenshots it’s just taken as the reference images it will compare any future changes to your CSS against.

## Work on your site

As you work on your site, run `backstop test` to check your work. Backstop will report any changes to the visual appearance of your website as a fail. If you are happy that the changes are better, you can re-run `backstop approve` and the snapshots backstop has just taken will now become the reference images it will use ([the developer explains the process on GitHub](https://github.com/garris/BackstopJS/issues/829)).