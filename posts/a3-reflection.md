---
title: A3 - Evaluating the Exchange Student Community Hub

date: 2026-06-07
author: Molly Branigan
summary: 
tags:
  - reflection
  - future planning
  - accessibility
---
# Note
Looking back at this project, one of the biggest differences between where our group started and where we finished is how much my understanding of feasibility changed. In earlier development blog posts, I focused more on planning, user needs, and the features we wanted to build. At that stage, many ideas felt reasonably straightforward because they existed mainly as design intentions. Once development began, however, it became clear that even simple-looking features can become technically complex very quickly.
Our project aimed to create a community hub for exchange students at the University of Sydney. The final prototype allows users to create discussion posts, comment and reply, view user profiles, and navigate between specific discussion areas such as travel, surfing, hiking, museums, and events in Sydney. The main goal was to support exchange students in finding information and connecting with others who might be going through similar experiences.
The final prototype does not include every feature we originally discussed. Private messaging, for example, was removed from the final product. However, I think this was an important part of the development process because it forced us to reassess what was realistic within the timeframe.
Performance and Technical Behaviour
One of the biggest technical lessons from this project was that interactive functionality takes much longer than expected. At the start, I assumed the homepage discussion feed would be one of the simpler parts of the application because it mainly involved displaying posts and allowing users to respond. In practice, it became one of the most time-consuming parts of the project.
The discussion feed required more than just displaying text. It needed to store posts in the database, associate posts with users, support comments and replies, allow deletion, and update the page without making the interaction feel confusing. This meant that the database structure, server-side routes, templates, and HTMX interactions all had to work together. If one part was slightly wrong, the feature either did not appear correctly or did not behave as expected.
A strength of the final prototype is that the core discussion functionality works through the database rather than relying on placeholder data. Posts and comments are stored and retrieved using SQLite, which means user-generated content remains available after refreshing the page. This was important because the brief warned against relying too heavily on placeholder content. The application also supports multiple logged-in users on the same local device, such as through a normal browser and an incognito window, which allowed us to test different user sessions.
However, the technical process also revealed limitations. The project uses a local SQLite database, so it is not designed for multiple computers each running their own separate server and expecting shared data. This was something I had to understand more clearly during development. The discussion page can show posts from all users in the same database, but separate local databases cannot automatically share content.
The application was responsive enough for the scope of the prototype, but the technical complexity of the discussion system showed that future performance testing should be more systematic. With more time, I would have liked to record clearer load time evidence and compare performance before and after adding more posts or comments. This would have made the evaluation more measurable rather than relying mainly on observed responsiveness.
![homepage](Wireframe.png)

User Experience and Accessibility
The user experience of the final prototype was strongest on desktop. The main discussion page gives users a clear place to create a post, view existing posts, respond to comments, and navigate to more specific discussion categories using the side panel. This matched the core aim of the project because exchange students need a space where information is easy to find and contribute to.
One design decision that worked well was making the homepage the discussion page. Earlier, the discussion area was separate from the home page, which made the site feel less direct. Since discussion was the main purpose of the community hub, placing it immediately on the home page made the application clearer.
Accessibility testing became one of the most important parts of our evaluation. My partner tested the site using Firefox accessibility checks, the WAVE browser extension, and AXE DevTools. These tools identified an issue with the cookie policy link because the only link styling was a colour change. However, this still met WCAG 2 Technique G183 under criterion 1.4.1 because the contrast ratio was higher than 3:1 and the link changed colour on hover and focus.
Manual keyboard testing was also completed. Every post, the post form, comment form, discussion links, and related interactive elements could be reached using tab navigation after reviewing and adjusting the interface during testing. This means the application can be navigated without a mouse. However, the tab order was not perfect. The right panel comes after the discussion feed in the tab order, which means a keyboard user may have to tab through many discussion items before reaching the side navigation. Given more time, this would be worth improving or testing further.
VoiceOver testing was completed using native screen reader tools on Mac and Windows. Overall, the application was usable, but there were some issues. The navigation was sometimes read twice because of the way the navigation code was structured, and automatic reading occasionally announced “banner” for the left side of the navigation bar. There were also inconsistent issues where automatic reading skipped some text inside cards or grouped elements, such as post content or reply author names. However, when elements were moved through manually, the screen reader generally read the content correctly.
This testing was useful because it showed that accessibility is not just about passing automated checks. Automated tools helped identify some issues, but manual testing revealed problems with reading order, tab order, and how assistive technologies interpret page structure.
User testing also showed that navigation was generally accessible, but the experience could have been more engaging. The interface was functional and understandable, but I think the user experience could have felt more visually exciting. This matters because a social community platform should not only work correctly but also feel inviting.
The largest usability weakness was mobile filtering. On mobile, moving between different discussion categories was less effective than on desktop. The side-panel filtering approach worked better on larger screens, while on smaller screens it felt less immediate and less easy to scan. If I continued the project, I would redesign mobile filtering so categories are easier to access without requiring awkward scrolling or searching.
Functional Requirements Reflection
Our original functional requirements focused on supporting community interaction between exchange students. In that sense, the final prototype met the most important parts of the brief. Users can create posts, comment and reply, view profiles, and navigate between specific discussion spaces.
The discussion system became the centre of the final prototype, which I think was the right choice. Exchange students are likely to need practical advice, social recommendations, and peer support, so the ability to post and respond directly supports the purpose of the community hub.
Some requirements changed during development. Private messaging was originally discussed because it seemed useful for students who wanted more personal communication. However, it did not make the final product. Looking back, I think this was the correct decision because messaging would have added a large amount of complexity. It would require private conversation storage, message routing, notifications or inbox behaviour, and more privacy considerations. Trying to add it within the same timeframe may have weakened the core discussion features.
Another idea that was reduced in scope was supporting more universities. In future, it would be valuable to expand the platform beyond the University of Sydney so exchange students from different institutions could have their own communities. However, for this prototype, focusing on one university made the project more manageable.
This experience changed how I think about functional requirements. At the beginning, I saw requirements mainly as a list of desired features. By the end, I understood them more as priorities that need to be constantly reassessed. A smaller set of working features is more valuable than a larger set of incomplete ones.
Requirement
Planned
Final Outcome
Create discussion posts
Yes
Completed
Comment and reply
Yes
Completed
User profiles
Yes
Completed
Specific discussion pages
Yes
Completed
Private messaging
Yes
Removed due to scope
Multiple universities
Considered
Future improvement
Mobile filtering
Yes
Functional but needs improvement

Lessons Learned and Future Improvements
The biggest lesson I learned was that web development requires much more scoping than I expected. Features that sound simple in planning can become complicated once they involve databases, user sessions, routing, templates, and interaction states. The homepage discussion feed was the clearest example of this. It sounded like one feature, but it actually involved many connected parts.
Group work was also valuable because different team members brought different experiences. Sophia’s background and the technical concepts she had learned in Sydney gave us a wider range of approaches to problem solving. This helped me see that collaboration is not only about dividing tasks but also about learning from different ways of thinking.
If I continued the project, I would prioritise three improvements. First, I would improve mobile filtering so discussion categories are easier to browse on small screens. Second, I would explore private messaging, but only after the core discussion system was stable. Third, I would consider expanding the platform to support more universities, as long as the information architecture was carefully planned.
Overall, the final prototype is not identical to our original vision, but I think that is part of what made the project valuable. Building and testing the application forced us to reassess our assumptions about feasibility, accessibility, and user experience. The project helped me understand that a successful web system is not just one that contains features, but one where technical behaviour, usability, accessibility, and scope all work together.

