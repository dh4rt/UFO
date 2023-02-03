# UFO
**Using JavaScript to Track UFO Sightings**

## Resources
### This project was completed with:
- VS Code 1.75
- [Data set provided here] (https://github.com/dh4rt/UFO/blob/main/static/js/data.js) 
- HTML


## Overview of Analysis
### The TRUTH is out there
A former co-worker Dana contacted me out of the blue to ask for some help on a project she has been working on. Having finally gotten to a point in her career as a
data journalist she is now able to make her own pitches, and something that she and I shared was a mutual fascination with UFOs. They are often discussed as the
catnip for conspiracy theorists, and something to not be taken literally. But with recent announcments and acknowledgements from the Department of Homeland Security,
The State Department, and the Joint Chiefs, Dana figured it was time to dig in. Now Dana had the idea and a dataset recently given to her via a FOIA request that 
provided the information she needed to create a searchable database of doucmented sightings (the encounters files she requested were denied becasue they are still
deemed "Classified").

### Getting to work
I know from my own experiences that the best way to build the searchable database that Dana wanted was through JavaScript because of the all-encompassing nature of
the language. It would provide the mutliplatform capabilites for this database to be used across a variety of platforms. The first step was to assess the dataset to
see how it is organized, which would allow to more effectively filter the data. The first input in the data file is as shown:

```
    datetime: "1/1/2010",
    city: "benton",
    state: "ar",
    country: "us",
    shape: "circle",
    durationMinutes: "5 mins.",
    comments: "4 bright green circles high in the sky going in circles then one bright green light at my front door."
    
```
What this shows me is that I've got five meaningful reasonable categories to filter through because those are quanititative measurements. Those categories are 
**"datetime", "city", "state", "country", "shape"**.  These will be important for both the HTML and JavaScript portions of the project.

### The HTML Build
The HTML portion of the project was built using the skeleton of a webpage that Dana had been working on for a while on her own, but had mostly languished over the
last few months. A text blurb was added starting on line 29 to flesh out why this database is important should be taken seriously. The next significant update was
made starting on line 65. Wherein the original HTML had filter that only used **datetime** more where added to include the other categories mentioned earlier. The
filter inputs where added in the order that they appeared on the dataset to allow for an ease in programming, and example of one of the input boxes is below:

```
            <li class="list-group-item bg-dark">
                  <label for="State">Enter State</label>
                  <input type="text" placeholder="State" id="state" />
            </li>
```

The preceding code instructs to script to make a text input box, that will take text input and has the placeholder text **State** inside, this is done for all the 
categories listed earlier. Further down the code starting at line 90 you'll see that the table the end user sees is structed in a manner that matches to dataset.
One of the biggest challenges with this portion of the build was creating an easy to read and accessable site that would be intuitive.

### The JavaScript Build
After having completed the HTML it was on to the backend which would prove to be equally challenging as the HTML build but for different reasons. To start the data
that would be filtered need to be imported which started on line 2, the next step was to build a **function** that would allow the data initally called in line 2 to build a table that would go on to be filtered, but the catch is that the table needed to built blank, shown below:

```
function buildTable(data) {
  // First, clear out any existing data
  tbody.html("");
```

From there a `forEach` loop was built to cycle through every row of data within the table. Which would allow us to make adjustments to the table that was ultimately
displayed to the user. The next step was to create a variable that would keep track of all the inputs put in to each filter, this started on line 26. The variable was
given a simple name to aid in the programming. From there a function that would track the updated filters was created. After that the elements (the text boxes from the
HTML build) are tracked as a variable. After that an `If Else` loop is built to allow multiple filters to used at once. Then on line 53 another function is declared
which ties everything together and give the program a choesive output point. This is among the most important code and placement within the entire build. During
a session with a consultant the `filterTable();` code was placed on line 57 and resulted in a code that produced no output and after more than an hour of fruitless
refreshing resulted in some very angry punctation changes at the suggestion of fourth party. These changes proved successful allowing the code further down to be
come in to play.

Using the `filterTable()` function the code then loops through all the filters and keeps any data that is caught by all of the filters that have inputs, and is then 
built as a new table for the user. That table is then loaded by the last line of code seen on line 84.


## Results
The results are a basic funtional searachable database, this database is filtered by typing input to the text boxes that match those within the data set and pressing
enter on the keyboard. The image below shows the results of searching for results in the state of Texas (https://github.com/dh4rt/UFO/blob/main/TX_search.png)


## Summary
### For those that want to believe
I believe that this project was a tremendous success, the webpage is easy to use and allows for a good deal of specificity from the user. But I think at the biggest
drawback for it is that it is not particularly mobile compatiable, I think that this is critical because the majority of folks interact with disscussions like this
through their phones.

Dana requestd that I provide suggestions for improvements that could be made and I have a couple:
- Time, it would be beneficial to track when throughout the course of the day the sightings happened, this would be done using Zulu to create a standard across the
globe.
- Proximity, I think that it would be helpful to know if sightings took place within contiguous counties/township/parrishes to track if these sightings are hyper-local
or regional
- Weather, it would be good to know if the weather conditions played a part in the visibility of the UFO.
