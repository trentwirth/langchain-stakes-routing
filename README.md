# Stakes Routing Prototype

This is a quick proof of concept I whipped together inspired by Corinne Jorgenson's Masters Qualifying Exam. 

Research shows that trust in AI predicts adoption of AI, an that explainability predicts trust. 

Furthermore, we might need to consider the context of a situation in order to determine the appropriate level of explainability, for example, in a high stakes situation, we might need to provide more explainability than in a low stakes situation.

This is a simple LangChain prototype that uses the `high_stakes_reference.txt` document in a vector search to classify user prompts as either high-stakes (emergency/urgent) or low-stakes (routine/general). When a user submits a prompt, the system measures its semantic similarity to a curated list of high-stakes situations. If the prompt is similar to emergency scenarios, it is routed to a triage-style prompt template that provides urgent, actionable, and explainable advice. Otherwise, it is routed to a general-purpose assistant template for friendly, informative responses.

This approach demonstrates how context-aware prompt routing can adapt the level of explainability and urgency in AI-generated answers, which is especially important for building trust in high-stakes applications.

## Reflection
- While I like this concept, this code is wonky and not very useful. The vector search and susbsequent semantic distance doesn't feel great, but I wonder if there was a much robust document to source, if the semantic distances would be more useful.
- Something that sort of naturally came out of the prompt styling was something else that Corinne wrote about, "Cognitive Styling". Different cognitive styles could be used for different personas/groups of people based on the situation, profession, etc.
    - The "High Stakes" prompt was much more structured and formal, reflectign a "rational" Cognitive Style
    - The "Low Stakes" prompt was much more casual and friendly, reflecting an "intuitive" Cognitive Style
