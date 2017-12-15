# Azure-Experience-Centre

<br><br>

<!-- TOC -->

1. [Getting Started](#getting-started)
<br> a. [Logging to Management Portal](#logging-to-management-portal)
<br> b. [Browse Through](#browse-through)
<br> c. [Definitions](#definitions)
<br>* [ODL](#odl)
<br>* [Event](#event)
<br>* [Template](#template)
<br>* [License](#license)
<br>* [User Management](#user-management)
<br> d. [Adding Co-Admins)](#adding-co-admins)
2. [Creating AEC templates](#creating-aec-template)
<br> a. [Create Template](#create-template)
<br>* [Explanation of all fields](#explanation-of-all-fields)
<br>* [Region best practices](#region-best-practices)
<br> b. [ARM Template Best Practices](#arm-template-best-practices)
<br>* [Best practice for creating ARM template for AEC(Outputs, Parameters etc)](#best-practice-for-creating-arm-template-for-aec)
<br>* [Parameter file best practices(Explanation of functions)](#parameter-file-best-practices)
<br> c. [Template Permissions](#template-permissions)
<br>* [Explanation with details to implement](#explanation-with-details-to-implement)
<br>* [Recommendation for](#recommendation-for)
<br> d. [Validating Template](#validating-template)
<br>* [Validation](#validation)
3. [Creating and Managing ODLs'](#creating-and-managing-odl)
<br> a. [Create ODL](#create-ODL)
<br>* [Explanation of all fields](#explanation-of-all-fields)
<br>* [Region best practices](#region-best-practices)
<br> b. [ODL Hot Instances Management](#odl-hot-instances-management)
<br>* [Why and How of Hot Instances](#explanation-of-all-fields)

## Portal Overview

### Home Page Overview

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/AEC_Portal.png"/>  

### How to login to AEC
- Navigate to the portal using the link https://experience-azure-mgmt.azurewebsites.net/#/main.
- Click on the **Log In** button on the top right portion of the page.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Login.png"/>  

- On clicking **LOGIN** button, you will be redirected to the following page.

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Login-1.png"/>

- Enter your Email address and click on Next.

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Choose-Account.png"/>

- Enter the password for your account and click on Sign in

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Password.png"/>

### How to logout from AEC
-To logout from the portal, Click on the button with your username on the top right hand side of the page. A drop down list will be displayed. Click on logout and you will be logged out and will be redirected to the home page.

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Logout.png"/>

### How to Create Template
-Navigate to the portal using the link https://experience-azure-mgmt.azurewebsites.net/#/main and login with your AEC credentials.  
-Once logged in, click on **Templates** on the left pane of the portal. This will list the templates if any.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Select-templates.png"/>

-Click on **ADD** at the top right corner of the templates page, to add a new template.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/add-template.png"/>

-Now provide the following details in the Add Template page that comes up.  
* Name : Provide a suitable name to the template.
* Code : Provide an identifyable course code.
* Description : Enter the description of the template.  
* ARM Template URL(optional) : Upload the ARM template that automate the required resources for the event, to storage and provide the template link.  
* Parameter Template URL(optional) : Upload the Parameter template that is used in the ARM template, to storage and provide the parameter template link.  
* Owner Email : Provide the email ID of the owner of the workshop.  
* Deployment Plan : Choose any of the deployment plan as below
<br> a. [Single Resource Group](#single-resource-group) : Choose this plan if you need only one resource group for the workshop to deploy.
<br> b. [Shared Instance](#shared-instance) : Choosing this plan will provide one resource group for all the attendees in the workshop.
<br> c. [Resource Group - Two](#resource-group-two) : Choose this plan if you need two resource group for the workshop to deploy.
<br> d. [Resource Group - Three](#resource-group-three) : Choose this plan if you need three resource group for the workshop to deploy.
<br> e. [Resource Group - Four](#resource-group-four) : Choose this plan if you need four resource group for the workshop to deploy.   
<br> f. [Resource Group - Five](#resource-group-five) : Choose this plan if you need five resource group for the workshop to deploy.

* Lab Guide URL(optional) : Upload the lab guide for the workshop, to storage and provide the lab guide link. 
* Demo URL(optional) : Provide the link to sample or quickstart.  
* PPT URL(optional) : Provide link to presentation slides.  
* Prerequisites URL(optional) : Provide the link to prerequisites URL(if any).  
* Regions : Provide the regions where you want to deploy the template.
* MS Cloud Licenses(optional) : Choose the license which you want to assign to the user for the lab.
* Create Service Principal(optional) : Check this option if you want to create separate service principle for each of the users registered for the lab.
* Send Service Principal(option comes up only if you check the above option) : Check this option if you want to send the service principle details to each of the users registered for the lab. The details will be sent with the lab details.
* Attendee Custom RBAC URL(optional) : Create custom RBAC policies for the attendees in the workshop and upload in storage. Provide the link to policy here. 

-Click on **Submit** once required options above are filled.

-Click on **Edit Icon** to edit the created template and add the template permissions if any

* Permission Type : Choose any of the deployment plan as below
<br> a. [Azure Built-in Role](#azure-built-in-role) : Choose this permission type to assign the Azure Built-in Role to the Attendee/Instructor of the workshop.
<br>* [Profile Type](#profile-type) : Choose Attendee or Instructor according to whom you want to assign this permission.
<br>* [Identity](#identity) : Choose AAD user or AAD Service Principle according to where you want to apply this permission.
<br>* [Scope Type](#scope-type) : Choose Azure to set this permission scope level at Azure
<br>* [Scope Level](#scope-level) : Choose scope level as RG level or subscription level to set the scope level of this permission.
<br>* [Permission](#scope-level) : Choose the permission as Reader or Owner or contributor from the drop down according to what permission you want to assign to the Attendee/Instructor.
<br>* [Apply at Launch](#apply-at-launch) : Check this option if you want to apply the permission at 

-Click on **Submit** once required options above are filled.

<br> b. [Shared Instance](#shared-instance) : Choosing this plan will provide one resource group for all the attendees in the workshop.
<br> c. [Resource Group - Two](#resource-group-two) : Choose this plan if you need two resource group for the workshop to deploy.
<br> d. [Resource Group - Three](#resource-group-three) : Choose this plan if you need three resource group for the workshop to deploy.
<br> e. [Resource Group - Four](#resource-group-four) : Choose this plan if you need four resource group for the workshop to deploy.   
<br> f. [Resource Group - Five](#resource-group-five) : Choose this plan if you need five resource group for the workshop to deploy.

* Instructor Custom RBAC URL(optional) : Create custom RBAC policies for the instructor in the workshop and upload in storage. Provide the link to policy here.  
* Custom ARM policy URL(optional) : Create a custom policy for the attendees, so that we can restrict the resources that they deploy in Azure.  

-Click on **Submit** once required options above are filled.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/templates-creation.png"/>

-Click on **Validate subscription with ARM template** icon corresponding to the event created.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/template-validation.png"/>

-Provide the azure subscription group and subscription in which the validator should be run and click on **Submit**.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/final-validation.png"/>


### Use of template outputs
-If you want to provide the attendees some results that are required in the workshop, you can provide it by using an output section in the ARM template. The results can be sent as email to the attendees when the event begins.  

### Creating and Managing Event

The event registration page looks as below  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/event-registration-page.png"/>

**A** : The users can register for the event here with the required details and click on **Submit**.  
**B** : The name of the event is displayed here, which is same as the event name given at the time of event creation.  
**C** : This is the short description of the event, which is same as the description given at the time of event creation.  
**D** : This is the date at which the event is scheduled, which is same as the date given at the time of event creation.  
**E** : This is the time and time zone at which the event is scheduled, which is same as the time given at the time of event creation.  
**F** : This shows that the event will be held online. An event type can be either Online or In person depending on the choice we provide at the time of event creation. If we choose In person option, the address at which the event will be held will be displayed here.  
**G** : This is the language in which the event will be held, which is same as the language choose at the time of event creation.  
**H** : This is the email ID of the contact at which the event is scheduled, which is same as given at the time of event creation.  
**I** : Clicking on this will take you back to Events calendar.  

- Now we will create an **Event**
- Navigate to the portal using the link https://azuretraining-mgmt.spektrasystems.com/#/main and login with your AEC credentials.  
-Once logged in, click on **Events** on the left pane of the portal. This will list the events if any.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/select-event.png"/>

-Click on **ADD** at the top right corner of the events page, to add a new event.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/add-event.png"/>

- Now the Add Event Details window comes up, where you can provide the following details.  
•	Event Title : Enter the Name of the event, which should be displayed on the event registration page.  
•	Template : Select the template which will be used to pre-deploy the resources required for the workshop.    
•	Description : Enter a description of the event which will be displayed on the event registration page as description.  
•	Tags(optional) : Enter tags such as Azure, checkpoint. Not being used as of now  
•	Event Type : Choose either of the following type  
	Virtual : Choose this type when the event is to be conducted online  
   <br>a.	Link to online meeting : Provide a link on which the Attendees can join the event  
	In Person : Choose this type when the event is to be conducted offline  
   <br>a.	Address : Enter the required details so that the Attendees gets to know where the event is held. It will be displayed on the event registration page.  
•	Sponser(optional) : Choose the sponser of the event from the list.    
•	Channels(optional) : Specify the channel to which the event belongs to.   
•	Email Template : Choose the template for emails sent out to event participants. This template defines the structure and content of the emails.  
•	Suscription Group : Specify the Azure subscription detail to be used while deploying the resources required for the event.    
•	Is Private : Check this option if you do not want to show up this event on public pages. This can be checked for test or dry run events.  
•	Time Zone : Scroll and select the time zone from where you are setting up the event. This will be displayed on the event registration page.    
•	Start Date and Start Time : Specify Start date and time of the event.  This will be displayed on the event registration page.    
•	End Date and End Time : Specify end date and expected time on which the event will end. This will be displayed on the event registration page.    
•	Approval Type : Specify how the participant registrations should get approved  
	Manual : Will have to manually approve participant registrations.  
	Automatic : Will automatically approve the registration until the total limit is met.  
•	Maximum number of users : Define the maximum number of participants for the event. Any registration after reaching this number would be marked in waitlist category.  
•	Allow personal email addresses : Checking this option will allow sign up to the event from social accounts such as gmail,yahoo,etc, Business/Work emails address are always allowed.  
•	Contact Email : Specify the email address that will appear on the event registration page for any support/questions about the event.  
•	Survey URL(optional) : This is to collect feedback post event, you can leave this blank to start with and enter survery url later on if required.  This will be sent to participants in thank you email after the completion of event.  
•	Recorded Session URL(optional) : Provide the link to recorded session. you can leave this blank to start with and enter survery url later on if required. You can choose to send this to participants after training.  
•	Language(optional) : Specify the language to be used in workshop. This will be displayed on the event registration page.    
•	Additional Notes(optional) : Type in additional notes if any, which will be shown on the public event page.  
•	Schedule Remainder Email : Check the options below to send event remainder email automatically.  
	Before Two Weeks  
	Before Two Days  
	Before Two Hours  
                Click on Submit.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/event-creation.png"/>

-Now you can see the event that you just created, in the Event page.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/event-list.png"/>

### Archieve an Event

Navigate to the portal using the link https://azuretraining-mgmt.spektrasystems.com/#/main and login with your AEC credentials.  
-Once logged in, click on **Events** on the left pane of the portal. This will list the events if any.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/select-event.png"/>

-Now click on **Archive** icon coreesponding to the evnet you want to archive.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/archive-event.png"/>

-Now you can find the archived event by clicking on **Archived Events** options at top right corner of events page.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/Archive-list.png"/>

### Manage Registrations


-Now we will **Approve/Reject** the attendees registration from AEC portal.  
-Navigate to the portal using the link https://azuretraining-mgmt.spektrasystems.com/#/main and login with your AEC credentials.  
-Once logged in, click on **Events** on the left pane of the portal. This will list the events if any.  

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/select-event.png"/>

-Now click on **Manage this event**  button corresponding to your event, in the Events Page.

<img src="https://github.com/Suraj2093/Azure-Experience-Centre/blob/master/Images/open-event-settings.png"/>

-Now inside event page, scroll down and under the registration section, click on **Manage Attendees**.

### Define Instructor
<!-- /TOC -->
