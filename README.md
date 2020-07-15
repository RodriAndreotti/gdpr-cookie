
# gpdr-cookie

A GPDR cookie consent plugin

This is a fork of https://www.jqueryscript.net/other/GDPR-Cookie-Compliance-Plugin.html with some improvements

### Requirements

 - Jquery 1.11+
 

### Installing

 - Donwload or clone this repository;
 - Import basic CSS template (*gdpr-cookie.css*) on header;
 - Import basic JS just before closing body tag;
 - Instanciate plugin;

 ### How to use
After install and instanciate plugin we have 3 events to manage cookies:

 - **gdpr:show:** triggered when popup appear
 - **gdpr:accept :** triggered when user accept the cookies
 - **gdpr:advanced:** triggered when user click on Advanced Button

The most important event here is **gdpr:accept**, which is what we will actually use to create or not the website's cookies.

Here a example of initialization of plugin:

    // Plugin Initialization
    $.gdprcookie.init({   
	    title:  "Cookies & privacy",    
	    subtitle:  "Select cookies to accept",    
	    message:  "Cookies enable you to use shopping carts and to personalize your experience on our sites, tell us which parts of our websites people have visited, help us measure the effectiveness of ads and web searches, and give us insights into user behaviour so we can improve our communications and products.",    
	    expires:  30, // expiration <a href="https://www.jqueryscript.net/time-clock/">date</a>
	    cookieName:  "cookieControlPrefs",
	    acceptBeforeAdvanced: ["essential", "analytics", "marketing"],
	    acceptAfterAdvanced: ["essential"],
	    acceptBtnLabel:  "Accept cookies",
	    advancedBtnLabel:  "Select cookies",
	    submessage:  "",
	    delay:  2000,
	    acceptReload:  false,
	    allowUnadvanced:  false,
	    switchAdvanced:  false,
	    unadvancedBtnLabel:  "Back",
	    customShowMessage:  undefined,
	    customHideMessage:  undefined,
	    customShowChecks:  undefined,
	    customHideChecks:  undefined,
	    renderDescriptionAsDiv:  true,
	    viewDescriptionLabel:  'View details',
	    hideDescriptionLabel:  'Hide details',
	    viewDescriptionChar:  '?',
	    cookieTypes: [
		    {
			    type:  "Essential",
			    value:  "essential",
			    description:  "These cookies are essential for enabling user movement around our website and providing access to features such as your profile and purchases, member-only resources, and other secure areas of the website. These cookies do not gather information about you that could be used for marketing purposes and do not remember where you have been on the internet. This category of cookies cannot be disabled. ",
			    checked:  true
		    },
		    {
			    type:  "Analytics",
			    value:  "analytics",
			    description:  "We use Google Analytics cookies to collect information about how visitors use our website. These cookies collect information in the aggregate to give us insight into how our website is being used. We anonymize IP addresses in Google Analytics, and the anonymized data is transmitted to and stored by Google on servers in the United States. Google may also transfer this information to third parties where required to do so by law, or where such third parties process the information on Google's behalf. Google will not associate your IP address with any other data held by Google."
		    },
		    {
			    type:  "Marketing",
			    value:  "marketing",
			    description:  "We also use a marketing database management program that deploys a cookie when a user interacts with a marketing communication, such as a marketing email or a marketing-based landing page on our website. This cookie collects personal information such as your name, which pages you visit on our website, your history arriving at our website, your purchases from the IAPP, and the like. Collected information is used to evaluate the effectiveness of our marketing campaigns or to provide better targeting for marketing."
		    }
	    ]
    });

**Important:** It is very important that non-essential cookies are loaded only after the user's consent.

### Loading previous consent
To obtain consents already given use the following method:

    const preferences = $.gdprcookie.preference();
    
You now have an array with all the permissions provided, just treat them on init of script.


### Fork Improvements
This version implements some improvements to allow to add the description text below of types list, making the plugin compatible with touch devices.

Now we have four new properties that allow you to view and customize the description controls.

    renderDescriptionAsDiv:  true,
    viewDescriptionLabel:  'View details',
    hideDescriptionLabel:  'Hide details',
    viewDescriptionChar:  '?',

| Property | Behavior |
|--|--|
| renderDescriptionAsDiv | Enable description rendering on div |
| viewDescriptionLabel | Label for view description link |
| hideDescriptionLabel | Label for hide description link |
| viewDescriptionChar | Icon to view description link |

