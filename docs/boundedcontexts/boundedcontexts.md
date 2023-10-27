The Wildlife.AI comes across as a small solution, with just four bullet points of requirements. However, when breaking this down, we found several 
"units" of tightly cohesive services, which form our bounded contexts. 

In this analysis, we follow the rule that a bounded context should be a business capability and not a single entity. For example, a single entity in this 
domain would be:

- Camera
- Frame
- Video
- Animal
- Etc...

This is incorrect, and instead we are looking groupings by business capability.

- Camera management - the ability to connect to and retrieve/delete a camera and view its footage
- Camera Bootstrap
- Frames Analysis
- Video Analysis