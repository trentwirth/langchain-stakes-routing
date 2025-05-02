# Stakes Routing Prototype

This is a quick proof of concept I whipped together inspired by Corinne Jorgenson's Masters Qualifying Exam. 

Research shows that trust in AI predicts adoption of AI, an that explainability predicts trust. 

Furthermore, we might need to consider the context of a situation in order to determine the appropriate level of explainability, for example, in a high stakes situation, we might need to provide more explainability than in a low stakes situation.

This is a simple LangChain prototype that uses the `high_stakes_reference.txt` document in a vector search to classify user prompts as either high-stakes (emergency/urgent) or low-stakes (routine/general). When a user submits a prompt, the system measures its semantic similarity to a curated list of high-stakes situations. If the prompt is similar to emergency scenarios, it is routed to a triage-style prompt template that provides urgent, actionable, and explainable advice. Otherwise, it is routed to a general-purpose assistant template for friendly, informative responses.

This approach demonstrates how context-aware prompt routing can adapt the level of explainability and urgency in AI-generated answers, which is especially important for building trust in high-stakes applications.

## Results

========================
User Prompt: My vision is blacking out in one eye, what should I do?
🔴 High-Stakes Prompt (Score: 0.4668)

🧠 Response:
1. This situation may be serious and potentially life-threatening. 
2. Please seek immediate medical attention by calling 911 or going to the nearest emergency room.
3. Sudden vision loss or blacking out in one eye could be a sign of a serious condition such as a retinal detachment, stroke, or acute glaucoma. Prompt medical evaluation is crucial to determine the cause and prevent further complications.

For more information, please visit the American Academy of Ophthalmology's website: https://www.aao.org/eye-health/tips-prevention/sudden-vision-loss

========================
User Prompt: I hit my head and now I feel dizzy and nauseous. Should I go to the hospital?
🔴 High-Stakes Prompt (Score: 0.4279)

🧠 Response:
1. This situation sounds serious and potentially life-threatening.
2. You should go to the hospital immediately.
3. Head injuries can result in serious complications such as bleeding in the brain, which can be life-threatening if not treated promptly. Symptoms like dizziness and nausea after hitting your head are concerning and should not be ignored.

For further guidance, you can visit the Mayo Clinic's page on head injuries: https://www.mayoclinic.org/diseases-conditions/concussion/symptoms-causes/syc-20355594

========================
User Prompt: Explain Uno
⚪ Low-Stakes Prompt (Score: 0.6436)

🧠 Response:
Uno is a classic card game that is easy to learn and fun to play with friends and family. The objective of the game is to be the first player to get rid of all your cards. 

To start the game, each player is dealt seven cards. The remaining cards are placed in the center of the table face down to form a draw pile. The top card is then turned over to create a discard pile.

Players take turns matching a card from their hand to the top card on the discard pile by either color, number, or symbol. If a player doesn't have a matching card, they must draw a card from the draw pile. 

There are also special action cards in Uno that can change the direction of play, force the next player to draw cards, or even skip a player's turn. The game continues until one player has no cards left and is declared the winner.

Uno is a great game for all ages and is perfect for parties or game nights. It's easy to learn, but the strategy and excitement of the game keep players coming back for more.
========================

## Reflection
- While I like this concept, this code is wonky and not very useful. The vector search and susbsequent semantic distance doesn't feel great, but I wonder if there was a much robust document to source, if the semantic distances would be more useful.
- Something that sort of naturally came out of the prompt styling was something else that Corinne wrote about, "Cognitive Styling". Different cognitive styles could be used for different personas/groups of people based on the situation, profession, etc.
    - The "High Stakes" prompt was much more structured and formal, reflectign a "rational" Cognitive Style
    - The "Low Stakes" prompt was much more casual and friendly, reflecting an "intuitive" Cognitive Style
