<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->
- [CalendarEvent](#calendarevent)
- [Contacts](#contacts)
- [Calendars](#calendars)
- [EventDetails](#eventdetails)
- [Threads](#threads)
- [CollaborationElement](#collaborationelement)
- [Header](#header)
- [Date](#date)
- [Properties](#properties)
- [Content](#content)
- [Attachments](#attachments)
- [Task](#task)
- [Details](#details)
- [Subtask](#subtask)

<!-- /TOC -->

# Objects

## CalendarEvent
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|[collaborationelement](#collaborationelement)|Array (of collaborationelement objects)|-|Collaboration properties values|A collaborationelement object array|-|
|[contacts](#contacts)|Array (of contact objects)|-|Contact information of the person|A contact object array|-|
|[eventdetails](#eventdetails)|Array (of eventdetails objects)|-|eventdetails information of the calendarevent|An eventdetail object array|-|

## Contacts

|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|name|String|-|Name of the contact|"John Doe"|-|
|eMail|String|-|E-mail of the contact|"john.doe@email.com"|-|
|[calendars](#calendars)|Array (of calendar objects)|-|Calendar information of the person|A calendar object array|-|

## Calendars

|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|calendar|String|-|URI to the person's calendar|http://cal.example.com/calA|-|
|requestCalendar|String|-|URL to request an appointment with the person|janedoe@example.com|-|
|status|String|-|URL which describes if the person is available or busy|http://www.example.com/busy/janedoe|-|


## Eventdetails

|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|location|String|-|Name of the location|"Room 123"|-|
|start|Date|-|startdate of the event|01.01.2018|-|
|end|Date|-|enddate of the event|31.12.2018|-|

## Email

|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|[collaborationelement](#collaborationelement)|Array (of collaborationelement objects)|-|Collaboration properties values|A collaborationelement object array|-|
|[threads](#threads)|Array (of thread objects)|-|thread information of the e-mail|A thread object array|-|

## Threads

|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|threadname|String|-|Name of the Thread|"Subject of the E-Mail"|-|
|topic|String|-|Identification of the thread|randomized string|-|

## CollaborationElement

|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|[header](#header)|Array (of header objects)|-|header information of the element|A header object array|-|
|[date](#date)|Array (of date objects)|-|date information of the element|A date object array|-|
|[properties](#properties)|Array (of properties objects)|-|properties information of the element|A properties object array|-|
|[content](#content)|Array (of content objects)|-|content information of the element|A content object array|-|
|[attachments](#attachments)|Array (of attachment objects)|-|attachment information of the element|An attachment object array|-|

## Header
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|from|String|-|E-Mail of sender|"john.doe@email.com"|-|
|to|String|-|E-mail of receiver|"jane.doe@email.com"|-|
|cc|String|-|E-mail of the contact in copy|"janet.doe@email.com"|-|
|bcc|String|-|E-mail of the contact in blind copy|"jonathan.doe@email.com"|-|
|subject|String|-|Subject line of the e-mail|"RE: Your Question"|-|

## Date
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|date|Date|-|Date|01.01.2018|-|
|day|Enum|-|Day of the week|"Monday"|"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"|
|time|Time|-|Timestamp|10:10:10|-|


## Properties
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|message ID|String|-|Unique ID of the E-Mail|randomized string|-|
|language|String|-|Language of the e-mail content|"en"|-|
|authentification|String|-|Authentication Result|"spf=pass smtp.mailfrom=email.com"|-|
|MIME Version|Decimal|-|Version of MIME|1.3|-|

## Content
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|format|String|-|Format of the email content|"HTML"|-|
|content|String|-|Content of the e-mail|"Dear John, please find attached"|-|

## Attachments
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|type|String|-|Datatype of the attachment|"JPG"|-|
|size|String|-|Datasize of the e-mail attachment|"54 KB"|-|

## Task
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|[collaborationelement](#collaborationelement)|Array (of collaborationelement objects)|-|Collaboration properties values|A collaborationelement object array|-|
|[subtask](#subtask)|Array (of subtask objects)|-|subtask information of the task|A subtask object array|-|
|[details](#dateils)|Array (of details objects)|-|detail information of the task|A details object array|-|


## Details
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|subject|String|-|Subject of the Task|"Create a datamodel"|-|
|startdate|Datetime|-|Date when the task starts|01.01.2018 00:00|-|
|enddate|Datetime|-|Date when the task is closed|31.01.2018 00:00|-|
|reminderdate|Datetime|-|Date when the task completion should be reminded|20.01.2018 00:00|-|
|content|String|-|description of the Task|"To create a datamodel we have to analyze different systems..."|-|
|status|String|-|status of the Task|"completed"|"started", "in progress", "completed"|

## Subtask
|Attribute|Type|Properties|Description|Example|Possible Enumeration Options|
|---|---|---|---|---|---|
|[details](#dateils)|Array (of details objects)|-|detail information of the task|A details object array|-|
|task|String|-|name of the subtask|"Analyze different systems"|-|
