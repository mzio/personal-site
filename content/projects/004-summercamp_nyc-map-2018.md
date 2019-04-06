---
title: "Mapping out SummerCamp NYC 2018"
date: 2018-05-31T22:43:46-05:00 
publishdate: 2018-12-25  
draft: false
summary: "An interactive map of Harvard interns working in NYC during Summer 2018" 
preview_image: "004-sc_nyc-preview.png"   
project: true  
project_date: May 31, 2018
project_link: "https://michaelzhang.xyz/SummerCamp-NYC-2018-Map/#"
post: true    
post_link: "https://michaelzhang.xyz/posts/004-summercamp_nyc-map-2018/"
---

_Second part of a two-part series introducing SummerCamp NYC 2018. Also published on Medium [here](https://medium.com/@michael.zhang/an-intro-to-summercamp-nyc-2018-e9a08f65628a)._

## Part 2: Location, Location, ... Intern Preferences!

If the students make up the heart of SummerCamp, the events bring them together and keep the community running. While ranging in size and nature, none of them would be possible without the fantastic hosts and partner companies we’ve been able to work with over the years, and a big part of organizing SummerCamp involves coordinating and planning for a series of meet-ups over the summer.

From more intimate meet-ups such as five to 10 person dinners organized off-site, to larger get-togethers involving office tours, speaking panels, and networking sessions, we aim to make events both fun and informative for both our student attendees and hosting companies. Actual event structure is left to the company’s discretion, but giving students a chance to learn about the company, hear about employees’ backgrounds and day-to-day activities, and get exposure to cool technology and relevant projects are all good jumping points. As most recruiters are probably well aware, two standbys for the fastest way to a college student’s heart — free food and branded swag — are also bonuses that are always appreciated.

### Following the Real Estate Agent’s Mantra  
This year, I wanted to focus on generating a greater student turnout, courtesy of a bigger SummerCamp group and more careful planning. For example, SummerCamp events are usually scheduled on workday evenings (starting around 6 or 7 pm) so that students can come after work and employees don’t have to come in on the weekends. But even then, New York City is a big place, and from firsthand experience I know how discouraging it can be to travel somewhere too far or too inconvenient to get to from work or home.

What’s even worse to me however is a party that no one shows up to, and so while still a work in progress and amenable to updates, to combat this I mapped out all interns’ rough locations based on employer and rough NYC 2010 census tract data.

{{< figure src="/images/004-sc_nyc-01.png"  >}} 

The choropleth-based app gives a wide overview on where interns are congregated up to census tract specificity, and also specifies the top neighborhoods related to a query. Besides identifying where interns are, we can also apply filters to specifically account for certain categories, say if you wanted to look for where software engineers or Statistics majors were congregated (Hudson Yards seems popular among that crowd). Another handy feature is separating out interns by event preference, such as if they prefer large, medium, or small events, and identifying the parts of Manhattan where students are down to go to museums (fun trips with alumni!) versus just grabbing a meal.

{{< figure src="/images/004-sc_nyc-app-01.gif"  >}} 

_Work in progress indeed. Notice that through filtering and data processing, only 76 interns made it to the map, and so while it's hopefully still representative it's also flagged for further development :)_  

The above information becomes possible through the sign-up process for SummerCamp. Students were asked how frequently they would be down to attend a SummerCamp event, if they'd be interested in small, medium, or large meet-ups, and also if there were any specific activities outside of the standard office tour / networking session that appealed to them. Using this data (take this as proof that we actually use your answers in the submission form for something), we can further break down preferences and provide some insight into popular things to do.  

For example, we can see that interns are more commonly looking to go to smaller or medium-sized events more frequently, with those preferring to go to something weekly or every other week both being twice as numerous as those that would only be interested in doing something monthly.

{{< figure src="/images/004-sc_nyc-app-02.png"  >}} 
_Interns were asked to pick which of the three frequencies they preferred the most, but were free to choose any and up to all event sizes that they'd be interested in attending._

In addition, while the most popular response overall involved biweekly medium-sized events (like a company mixer targeted at hosting 30–50 people), smaller events (such as private dinners capped at 10 to 15 people) were equally as popular as medium-sized events when considering both weekly and biweekly intended attendance. Meeting demand in our group, these are most likely easier to put together (reservation for twelve at a nearby restaurant) more frequently. So while SummerCamp might always like being able to attend a big company-dedicated night full of featured speakers, panel discussions, and networking + food, perfectly viable alternatives exist at lower organizational budgets.

{{< figure src="/images/004-sc_nyc-app-03.png"  >}} 
_The same data as before, just swapping variables to display. If weekly and biweekly groups settle their differences (two events every three weeks?), small and medium events are equally preferred._

Exploring that idea of alternate events further, we can also look at what social events with other members of SummerCamp students would be interested in.

{{< figure src="/images/004-sc_nyc-app-04.png"  >}} 

Top choices involve restaurants (good thing that NYC has a lot of those), going to music venues (concerts and festivals, which are also pretty numerous over the summer), and house parties (perhaps limited by company housing). Another positive note for companies is that among weekly preferences, there were above 10 positive responses for each event type. For the companies that might want to interact with students, but for which hosting networking mixers might sound too much like a career fair redux, there's ample opportunity to get your employees to spend some time with Harvard kids doing something new :)

{{< figure src="/images/004-sc_nyc-app-05.png"  >}} 
_Again same data as above, but this time the heat map really brings out the stronger representation in weekly and biweekly event attenders. Also restaurants and music venues are good too._  

So there you have it; a further look into what SummerCamp members are into regarding events, and the introduction of using location to help guide the right events. Play around with the map, notice where all the SWE / ML / finance interns or CS / Stats / Applied Math majors are, and hopefully the choropleth can provide some insight for better event planning and answering questions such as whether hosting Sunday brunch in Tribeca is a good idea.

{{< figure src="/images/004-sc_nyc-app-06.gif"  >}} 
_More gratuitous zooming and flying available at [http://michaelzhang.xyz/SummerCamp-NYC-2018-Map/#](http://michaelzhang.xyz/SummerCamp-NYC-2018-Map/#)_


