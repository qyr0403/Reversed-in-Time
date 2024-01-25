# Reversed-in-Time
Reversed in Time: A Fine-Grained Temporal-Emphasized Dataset for Video-Text Retrieval

The prompts we mentioned in our paper to instruct GPT-4.

## Prompts in Section 3.1.1 to generate seed activity list

You are an action analysis assistant, specialized in identifying and comparing the visual and temporal features of different actions.

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

]"

## Prompts in Section 3.1.2 generating objects to construct verb phrases

You are a professional motion analyst. Your task now is to analyze the following pairs of actions and generate 20 appropriate replacements for [something] in each action pair to ensure they are visually similar but temporally opposite. Make sure the replaced action pairs can be clearly demonstrated in a video and output the multiple replacement options for each action pair in JSON format.

Processing steps:

1.Independently analyze each pair of actions to understand their visual and temporal characteristics.

2.Choose 20 suitable objects or actions for [something].

3.Ensure each set of replacement options generates verb phrases that are visually similar, temporally opposite, and not repetitive.

4.Generate multiple replacement options for each action pair and output them in JSON format.

Example:

Input:

open something, close something

lift something, drop something

push something, pull something

... // more action pairs

Output:

{

"open something": [

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










