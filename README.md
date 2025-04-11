## AI in Your Kitchen: Generating Recipes from Ingredient Photos with Gen AI

We've all been there: staring into the refrigerator or pantry, surrounded by a random assortment of ingredients, yet completely stumped on what to actually *make*. This daily "what can I cook?" dilemma often leads to decision fatigue or, worse, food waste. As part of the recent "5-day Gen AI Intensive Course" hosted by Google experts, I tackled this very problem for my Capstone project by exploring how Generative AI could help.

The result? An **AI Recipe Generator** – a concept designed to act like a helpful sous-chef. The idea is simple: show the AI what ingredients you have via a photo, and it suggests a recipe you can cook using primarily those items.

### The Challenge: Beyond Just Listing Ingredients

While knowing you have tomatoes, onions, and pasta is one thing, figuring out a coherent and appealing dish requires more creativity and knowledge. How could AI bridge this gap? This project leveraged a pipeline combining several powerful Generative AI techniques available through Google's AI tools (specifically, the Gemini models accessed via their Python SDK).

### How Gen AI Powers the Recipe Generator

Building this tool involved orchestrating three key AI capabilities:

1.  **Seeing the Ingredients (Image Understanding):** The first step is understanding the input photo. We used the multimodal capabilities of **Gemini Vision** to analyze the image and identify the primary food ingredients pictured. This transforms the visual information into a usable list of text items.

2.  **Finding Inspiration (Retrieval Augmented Generation - RAG):** Simply knowing the ingredients isn't enough for a *good* recipe. To give the AI relevant culinary context, we implemented RAG. This involved:

    * **Embeddings:** Creating numerical representations (vectors) of both the identified ingredients (our query) and a collection of existing recipes (our knowledge base). These embeddings capture the semantic meaning of the text.

    * **Vector Search:** Comparing the query embedding (from the photo's ingredients) against the recipe embeddings using cosine similarity. This allowed us to retrieve the top few recipes from our dataset that were semantically most similar to the available ingredients – essentially, finding relevant "inspiration" recipes.

3.  **Writing the Recipe (Structured Output):** With the identified ingredients and relevant context recipes retrieved via RAG, the final step was generation. We prompted the **Gemini Pro** model, providing it with the ingredients list and the inspirational context. Crucially, we instructed the model to generate a *new* recipe and output it in a specific **JSON format**. This structured output ensures the recipe details (title, description, ingredients list, instructions, prep/cook times) are cleanly organized and easy for another application (or the user) to parse and display.

### The Building Process & Learnings

This pipeline was implemented within a Kaggle Notebook using Python. Connecting these different AI steps, handling the data flow (images, text, embeddings, JSON), and debugging the interactions was where the real learning happened! Prompt engineering, especially for reliable JSON output, required careful iteration. It was fascinating to see how combining these distinct AI capabilities could create a solution more powerful than any single component alone.

### Try It Out & Future Ideas

This project served as a practical application of the techniques learned during the Google Gen AI course. While the current version uses a limited dataset, it demonstrates the potential of this approach.

You can explore the complete implementation, including the code and detailed explanations, in the Kaggle Notebook here:
<https://www.kaggle.com/code/alexoliveira0103/genai-capstone-project-the-ai-recipe-generator>

Future enhancements could include using much larger recipe datasets, incorporating user dietary preferences, allowing users to edit the identified ingredient list, or even building a simple web interface.

Building this AI Recipe Generator was a rewarding experience, showcasing how modern AI tools can be applied creatively to everyday problems. What other daily tasks do you think Gen AI could help streamline? Let me know your thoughts!
