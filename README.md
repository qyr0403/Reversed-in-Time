# Reversed-in-Time
Reversed in Time: A Fine-Grained Temporal-Emphasized Dataset for Video-Text Retrieval

The prompts we mentioned in our paper to instruct GPT-4.

## Prompts in Section 3.1.1 to generate seed activity list

    messages = [{"role" : "user", "content": f"""You are an action analysis assistant, specialized in identifying and comparing the visual and temporal features of different actions.
    Task Objective: Generate a series of action pairs that are visually similar but semantically opposite in timing, considering only the actions and not the objects involved (use [something] as a placeholder). Ensure that these action pairs can be clearly demonstrated through video.
    Specific Steps:
    1.Choose a common action, such as 'open [something]'.
    2.Determine the direct antonym action, such as 'close [something]'.
    3.Ensure that these action pairs are common across various environments and can be clearly demonstrated through video.
    4.Repeat the above steps to generate more action pairs.
    Output Format:
    Use JSON format for output. Each action pair should be an object containing two fields: action1 and action2.
    Example Output:
    [
        {"action1": "open [something]", "action2": "close [something]"},
        {"action1": "pick up [something]", "action2": "put down [something]"},          
        ... // more action pairs        
    ]"""}]

## Prompts in Section 3.1.2 generating objects to construct verb phrases

    messages = [{"role" : "user", "content": f"""You are a professional motion analyst. Your task now is to analyze the following pairs of actions and generate 20 appropriate replacements for [something] in each action pair to ensure they are visually similar but temporally opposite. Make sure the replaced action pairs can be clearly demonstrated in a video and output the multiple replacement options for each action pair in JSON format.
    Processing steps:
    1.Independently analyze each pair of actions to understand their visual and temporal characteristics.
    2.Choose 20 suitable objects or actions for [something].
    3.Ensure each set of replacement options generates verb phrases that are visually similar, temporally opposite, and not repetitive.
    4.Generate multiple replacement options for each action pair and output them in JSON format.
    Example:
    Input:
          [      
            {"action1": "open [something]", "action2": "close [something]"},        
            {"action1": "lift [something]", "action2": "drop [something]"},        
            {"action1": "push [something]", "action2": "pull [something]"},        
            ... // more action pairs      
          ]
    Output:
          {      
            "action pair 1": [        
              ["open the door", "close the door"],          
              ["open the window", "close the window"],          
              ["open the book", "close the book"],          
              ... // The remaining 17 verb phrases      
            ],      
            "action pair 2": [        
              ["lift the box", "drop the box"],          
              ["lift the bag", "drop the bag"],          
              ["lift the chair", "drop the chair"],          
              ... // The remaining 17 verb phrases        
            ],        
            "action pair 3": [        
              ["push the cart", "pull the cart"],          
              ["push the button", "pull the lever"],          
              ["push the broom", "pull the rope"],          
              ... // The remaining 17 verb phrases        
            ],      
          }
    For this message, you just need to understand. I will input the action pairs I have provided in the next message. Please generate multiple replacement options for each action pair following these guidelines.
    """}]
## Prompts in Section 3.1.3 for rewriting annotations
    messages = [{"role" : "user", "content": f"""You are an assistant who specializes in language conversion and rewriting. Next you are going to carry out a task where the goal of the task is to rewrite a given number of sentences of text, generating 9 different versions, each of which should keep the meaning of the original text intact.
    In the rewriting process, you can selectively use the following devices:
    1. synonym replacement: use synonyms that have similar meanings to the words in the original text.
    2. Sentence restructuring: change the structure of the sentence, such as changing the active voice to passive voice, or adjusting the order of subordinate and main clauses.
    3. Adding or deleting modifiers: Adding or deleting adjectives, adverbs and other modifiers as appropriate to change the way a sentence is expressed but not its basic meaning.
    4. use different grammatical structures: e.g., use different grammatical devices such as participle structures, infinitive structures, etc. to express the same meaning.
    Both my input and the format you should output are in JSON format and should not contain redundancy for the program to parse.
          {      
            "text1": "It's a very nice day for a walk.",        
            "text2": "The sky is blue.",        
             // Other more input sentence cases         
          }
    Sample output is as follows:
          {      
            "text1":{        
            "original": "It's a very nice day for a walk.",        
            "rewrites": [        
              "Today's weather is pleasant and perfect for a walk outside.",          
              "It's a beautiful sunny day, perfect for a walk.",          
              "It's a sunny and pleasant day, just right for a walk outside.",          
              "... (the remaining 6 rewritten versions)"          
            ]}        
            "text2":{        
            "original": "The sky is blue.",        
            "rewrites": [        
              "The color blue covers the sky.",          
              "The sky shows its blue color.",          
              "We see the sky with a blue color.",          
              "... (the remaining 6 rewritten versions)"          
            ]}        
            // Other more output        
          }
    For this message you just need to understand it, I will give you the correctly formatted input next.
    """}]










