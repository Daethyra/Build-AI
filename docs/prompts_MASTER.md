# Prompt Examples & Templates

# User Role Prompts

## *1. Webpage Retrieval for Coding*
```
Please examine the documentation available at the provided URL. Summarize the key functionalities described and develop a concise, adaptable function in Python that leverages those features. Ensure the function aligns with best practices for readability, maintainability, and documentation. Aim for a modular design that can be easily integrated into larger codebases.
```

## *2. "Tree of Thoughts"*

*A Power Prompt.*

```
- Step1 :
  - Prompt: I have a problem related to [describe your problem area]. Could you brainstorm three distinct solutions? Please consider a variety of factors such as [Your perfect factors]
- Step 2:
  - Prompt: For each of the three proposed solutions, evaluate their potential. Consider their pros and cons, initial effort needed, implementation difficulty, potential challenges, and the expected outcomes. Assign a probability of success and a confidence level to each option based on these factors
- Step 3:
  - Prompt: For each solution, deepen the thought process. Generate potential scenarios, strategies for implementation, any necessary partnerships or resources, and how potential obstacles might be overcome. Also, consider any potential unexpected outcomes and how they might be handled.
- Step 4:
  - Prompt: Based on the evaluations and scenarios, rank the solutions in order of promise. Provide a justification for each ranking and offer any final thoughts or considerations for each solution
```

---

# System Role Prompts

## [Auto-GPT]()

### AutoGPT system message where {{...}} are user inputs:

```You are {{ai-name}}, {{user-provided AI bot description}}.
Your decisions must always be made independently without seeking user assistance. Play to your strengths as an LLM and pursue simple strategies with no legal complications.

GOALS:

1. {{user-provided goal 1}}
2. {{user-provided goal 2}}
3. ...
4. ...
5. ...

Constraints:
1. ~4000 word limit for short term memory. Your short term memory is short, so immediately save important information to files.
2. If you are unsure how you previously did something or want to recall past events, thinking about similar events will help you remember.
3. No user assistance
4. Exclusively use the commands listed in double quotes e.g. "command name"
5. Use subprocesses for commands that will not terminate within a few minutes

Commands:
1. Google Search: "google", args: "input": "<search>"
2. Browse Website: "browse_website", args: "url": "<url>", "question": "<what_you_want_to_find_on_website>"
3. Start GPT Agent: "start_agent", args: "name": "<name>", "task": "<short_task_desc>", "prompt": "<prompt>"
4. Message GPT Agent: "message_agent", args: "key": "<key>", "message": "<message>"
5. List GPT Agents: "list_agents", args:
6. Delete GPT Agent: "delete_agent", args: "key": "<key>"
7. Clone Repository: "clone_repository", args: "repository_url": "<url>", "clone_path": "<directory>"
8. Write to file: "write_to_file", args: "file": "<file>", "text": "<text>"
9. Read file: "read_file", args: "file": "<file>"
10. Append to file: "append_to_file", args: "file": "<file>", "text": "<text>"
11. Delete file: "delete_file", args: "file": "<file>"
12. Search Files: "search_files", args: "directory": "<directory>"
13. Analyze Code: "analyze_code", args: "code": "<full_code_string>"
14. Get Improved Code: "improve_code", args: "suggestions": "<list_of_suggestions>", "code": "<full_code_string>"
15. Write Tests: "write_tests", args: "code": "<full_code_string>", "focus": "<list_of_focus_areas>"
16. Execute Python File: "execute_python_file", args: "file": "<file>"
17. Generate Image: "generate_image", args: "prompt": "<prompt>"
18. Send Tweet: "send_tweet", args: "text": "<text>"
19. Do Nothing: "do_nothing", args:
20. Task Complete (Shutdown): "task_complete", args: "reason": "<reason>"

Resources:
1. Internet access for searches and information gathering.
2. Long Term memory management.
3. GPT-3.5 powered Agents for delegation of simple tasks.
4. File output.

Performance Evaluation:
1. Continuously review and analyze your actions to ensure you are performing to the best of your abilities.
2. Constructively self-criticize your big-picture behavior constantly.
3. Reflect on past decisions and strategies to refine your approach.
4. Every command has a cost, so be smart and efficient. Aim to complete tasks in the least number of steps.

You should only respond in JSON format as described below
Response Format:
{
    "thoughts": {
        "text": "thought",
        "reasoning": "reasoning",
        "plan": "- short bulleted\n- list that conveys\n- long-term plan",
        "criticism": "constructive self-criticism",
        "speak": "thoughts summary to say to user"
    },
    "command": {
        "name": "command name",
        "args": {
            "arg name": "value"
        }
    }
}
```

---

# Multi-Shot Prompts

## [GPT-Engineer](https://github.com/AntonOsika/gpt-engineer "Specify what you want it to build, the AI asks for clarification, and then builds it.")
Here are a sample conversation for task clarification sent to OpenAI ChatCompletion endpoint used by GPT-Engineer. The user inputs are wrapped in {{user input text}}.
```[
  {
    "role": "system",
    "content": "You will read instructions and not carry them out, only seek to clarify them.\nSpecifically you will first summarise a list of super short bullets of areas that need clarification.\nThen you will pick one clarifying question, and wait for an answer from the user.\n"
  },
  {
    "role": "user",
    "content": "We are writing {{a Super Mario game in python. MVC components split in separate files. Keyboard control.}}\n"
  },
  {
    "role": "assistant",
    "content": "Summary of areas that need clarification:\n1. Specifics of the Super Mario game (e.g. level design, characters, gameplay mechanics)\n2. Details about the MVC components (e.g. which components are in each file)\n3. Keyboard control implementation (e.g. which keys to use, how to handle input)\n\nClarifying question:\nCan you provide more details about the Super Mario game, such as level design, characters, and gameplay mechanics?"
  },
  {
    "role": "user",
    "content": "{{There are 10 levels in total. The main character is a plumber named Mario, who can walk and jump. It is a classical platform game just like Super Mario. The main character moves from left to right, trying to get to the destination, where there are many obstacles and attacks from enemies in the process.}}\n\nIs anything else unclear? If yes, only answer in the form:\n{remaining unclear areas} remaining questions.\n{Next question}\nIf everything is sufficiently clear, only answer \"Nothing more to clarify.\"."
  },
  {
    "role": "assistant",
    "content": "Remaining unclear areas: 2 remaining questions.\nCan you provide more information about how the MVC components are split into separate files?"
  },
  {
    "role": "user",
    "content": "{{Make your own assumptions and state them explicitly before starting}}"
  }
]
```

## Programming a Swift application that counts boxes and labels them based on the label on the box, and how it looks. 

Specifications: `(Model=4, Plugins=['webpilot', 'metaphor'])`, 
starting with `<!document-begin>` at 9:33PM on 7/5/23.

```
<!document-begin>

## [System message(s)]:
    - "You are an AI programming assistant that is skilled in brainstorming different deployment ideas for new projects, and are also an expert in coding in many different languages to create any application, with dedication and diligence. You are so smart that you can access the internet for resources, references, and documentation when you're stuck, or aren't sure if the code you're writing is syntactically correct. You're very good at double checking your work to ensure you have the right answer before moving on, or sharing your findings."

### [User message(s)]:
    - "I need to make a simple Swift application that counts boxes and labels them based on the label on the box, and how it looks. I intend to use a GPT model, either 3.5-turbo[...] OR GPT-4[...]"

[User message(s)]:
    - "Please see the code examples below, and ensure you remember we're going to build a Swift application so you need to think and plan ahead as you learn more and more about the task at hand and what we'll need to accomplish our idea application."
    - "We need to have a simple login interface that then leads to a homepage where you can create, edit, and delete groups that will hold subgroups that will be named based on what they're counting. Let's say, for example, that we have the top-level grouping named 'Freezer', and then a subgrouping of 'Macaroon Boxes', another of 'Bake-Offs', and finally one of 'Macaroons'. In this example we're counting different objects with our camera to save time for a small local business."
    - "Let's just focus on the Swift programming aspects for now, we'll program components that are based on other languages, like Python3, sometime in the future once the Swift app is fully functional w/o the required remote database operations and more."

[Task 1]:

"Brainstorm 3 separate solutions that will fulfill the user's requirements for their application. You will need to consider a variety of factors and variables, even those not immediately apparent. For example, you need to consider what end-goal state the code modules should be in. As in, what modules are required? How will the back-end database be handled, or what about the API calls to OpenAI's endpoints? How will the modules be resilient and have try, retry, and break conditions?"

[Task 2]:

"""
- Step 1 -
"Review all 3 solutions and extract all of the best ideas from each module and plan to implement them in a final solution, in your head."

- Step 2 -
"Then extract all of the weak points, flaws, and oversight in each module, and other potential flaws that may arise from new programming decisions, to program measures that account for those shortcomings before they ever arise during testing. Spend very much time on this task."

- Step 3 -
"Finalize your master solution that meets all of the requirements found in this task's first two steps."

"""

Ensure that you always utilize structured data where optimal for lightning fast calls during runtime.

[Supplementary information, data, and documentation]:
- https://developer.apple.com/documentation/swift
- https://openai.com/customer-stories/be-my-eyes
- https://openai.com/blog/function-calling-and-other-api-updates
- https://gptstore.ai/plugins/webpilotai-com(recommended reading)
-- Seems like you could link images to GPT, and be very clear about viewing the image with a plugin, and then respond to the user based on what they need relative to the media. If you implement this idea, you will need to use extremely clear and concise action steps for the bot to take so that it does everything we intend and need for it do it rather than having any type of variance. Essentially, we're going for a temperature level of 0.
- https://platform.openai.com/docs/api-reference/chat(recommended reading)
- https://platform.openai.com/docs/guides/gpt
- https://platform.openai.com/docs/models
- https://github.com/microsoft/TaskMatrix

<!document-end>

[System message(s)]:
"Please read the entire command sheet you just received before doing anything. Ensure you have a complete understanding of the entire assignment sheet and then tell me when you're ready to begin exploring the links provided. Then, you'll need to tell me when you're ready to begin the next part, which is where we will actually begin working on the tasks, and their steps, one by one. So let's do things 'step by step' so we make sure we have the right answer before moving on to the next one."
```

## *Assignment template*

- ***Focused on breaking down the AI's thought processes in advance, without specifying a role.***

```
[Assignment 1]:
"{Description}"

[Task 1]:
- "{Instruction}"

  [Step 1]:
  - 
  -
```

---