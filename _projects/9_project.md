---
layout: page
title: Voice-based Grievance System
description: NLP based citizen issues redressal system
img: assets/img/grievance.jpg
importance: 9
category: work
related_publications: false
---

[[Project Presentation]]({{ '/assets/pdf/Voice_Grievance_Project_Presentation.pdf' | relative_url }})


### Problem Statement
* The citizens and members of local communities encounter frequent domestic problems that can range from the petty to the most serious and time-critical. A few examples of the problems are as follows:
- The street lights on the road may not be working
- The water supply might be irregular
- The robberies in the neighbourhood might have increased
A short circuit might have occured resulting in a dangerous fire, etc
* It is imperative that the concerned authorities are intimated immediately and the problem be rectified to ensure the smooth functioning of the society
* But the citizens often find it confusing and troublesome to address these issues to the right department
* They are often unaware of who, where and how a particular problem should be reported
* There are often endless delegations wherein a department transfers the complainant to another and so on. This coupled with the inconveniences involved makes the entire process lengthy, cumbersome and ineffective and can result in dangerous consequences due to the delay in addressing the problems.


### Our Solution
The project addressed and solved the above problems by implementing a solution in the following manner:

* A mobile application that can accept the grievances and complaints of the citizens in voice and text format.
* The voice based complaints are converted to text.
* The recorded complaints and grievances are classified and redirected to the appropriate departments.
* Further, the complaints reaching a department are ranked on the basis of severity. This is decided based on the type of complaint and the time-critical nature of the matter under consideration.
* In this way, the citizens will have a single interface to address all their concerns. On the other hand, the departments will only receive the complaints that concern them in a prioritized order.
* This makes the entire process seamless and very convenient for all the parties involved. It should help both the citizens to address their problems effortlessly and should aid the departments to solve the problems aptly with a much shorter turnaround time.
* Further, a mobile application with regular updates and statistics about the problems and solutions encourages a constructive dialogue between the citizens and civic authorities and enables a united approach to improve the city.


### Implementation Details
* The project involved the implementation of an Android mobile application that can accept the user grievances and complaints in voice and text format.
* In the case of voice complaints, the project involved the implementation and use of a voice to text conversion algorithm.
* The complaints in text format are then tokenized and mapped to the respective departments using the concepts of Natural Language Processing (NLP).
* Further, the complaints reaching a particular department are ranked based on severity and the time-critical nature which is again deduced from the complaint using the concepts of NLP.
* The project also involved the implementation of a front-end website for the departments to ensure that these complaints are ranked and displayed to the respective departments. The App on the user side and the Website on the department side were completely integrated into an end-to-end pipeline to ensure that the complaints voiced on the app undergo the processing using NLP to finally rank and display the complaints to the respective department on their website.