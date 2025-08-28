> To circumvent the non-deterministic nature of AI, is writing elaborated scripts a viable solution?

✦ That's a very insightful question. It gets to the core of the difference between traditional programming and working with AI.


  The short answer is that elaborated scripts are a critical part of the solution, but they don't eliminate non-determinism—they manage it.

  Here’s a breakdown of why that is and how it works in practice:


  Traditional Scripts vs. LLMs


   * A Traditional Script is Deterministic: If you write a script that says "if X, then do Y," it will do Y every single time it sees X. The output is 100% predictable.
   * An LLM is Probabilistic: When you give an LLM a prompt, it calculates the most probable
      sequence of words to come next. There isn't one single "correct" answer, but a
     spectrum of likely good answers. This is what allows it to be creative and flexible.


  How Elaborated Scripts Help (The Viable Solution)


  You can't force an LLM to be deterministic, but you can use scripts and specific
  techniques to heavily guide it toward a desired output structure and style. This is the
  essence of "prompt engineering" and building reliable AI applications.

  Here are the viable solutions:


   1. Controlling Randomness with Parameters: When calling an AI model via an API, you can
      set a parameter called temperature.
       * `temperature = 0.0`: This makes the model almost deterministic. It will always try
         to pick the single most likely word, leading to very consistent, predictable
         outputs. This is ideal for tasks like classification or data extraction.
       * `temperature > 0.7`: This makes the model more "creative" and random, leading to
         more varied and interesting outputs. This is better for brainstorming or content
         creation.
       * For your dashboard, the script calling the AI would set a low temperature (e.g., 
         0.1) to ensure the insights are consistent.


   2. Structuring the Prompt (The "Elaborated Script"): This is the most powerful tool.
      Instead of a simple prompt, you write a detailed one that tells the AI exactly what
      format to use.


       * Weak Prompt: "Find anomalies in this data." (This could return anything).
       * Elaborated Prompt (Scripted): "You are a procurement analyst. Analyze the following
          JSON data. Identify the top 3 anomalies. For each anomaly, provide a 'type', a
         'description', and a 'risk_score' from 1 to 10. Return your response ONLY as a
         valid JSON array."


   3. Post-Processing and Validation: After the AI responds, a traditional script can take
      over.
       * The script would parse the AI's JSON output.
       * It would validate that the output matches the required format (e.g., does it have
         the risk_score field?).
       * If the output is valid, it's displayed in the dashboard. If not, the script can
         retry the AI call or flag an error.

  Conclusion:


  So, yes, writing "elaborated scripts" is absolutely a viable and necessary solution. The
   script doesn't change the AI's fundamental nature, but it creates a robust framework
  around it. It constrains the AI's output through detailed instructions and
  low-temperature settings, and then validates the result to ensure it's reliable enough
  for a professional application.