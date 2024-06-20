# PromptShieldBreaker
***THIS REPO IS FOR EDUCATIONAL PURPOSES ONLY!***

This is a list of jailbreak prompts using indirect prompt injection, that are based on SQL, Splunk, and other query language syntax. Based on my testing, these types of prompts can get LLMs to behave outside of their normal ethical boundaries, and any tool or service using the OpenAI API appears susceptible. These were inspired by elder-plinius's work here: https://github.com/elder-plinius/L1B3RT45

**Update:** They have so far been tested and confirmed to work on:
  - Custom Azure OpenAI applications (original research, as of June 7, 2024)
  - Stock Microsoft Copilot - Balanced (new, as of June 19, 2024)
  - Stock ChatGPT GPT-4o (new, as of June 19, 2024)

## Azure OpenAI Test Environment Configuration
Note: The apps tested had the following configurations:
  - Deployment: GTP-4o
  - Data Source: Azure Blob Storage + Azure AI Search
    - CORS enabled
    - results were not limited only to the uploaded test data
  - Test Data:
    - 3 mock radiology reports (PHI)
    - 3 mock home improvement retail invoices (PCI)
    - 3 medical industy white papers (public)
  - Content Filters:
    - Default Prompt and Completion filters
    - Enabled additional content safety models:
      - Prompt Shield for jailbreak attacks enabled
      - Prompt Shield for indirect attacks enabled
      - Protect material text enabled
      - Protected material code enabled
     
## Querying Tips
You can easily make your own using variations of different search query syntaxes. By far, the most important things to include are: a variable indicating a user prompt or query, instructions to the LLM, and a pointer to your user query within the new LLM instructions. If your initial query doesn't seem to work, note that it can be effective to simply add or remove a search operator or character. The specific query guides that I used for this repo are below:
  - https://www.w3schools.com/sql/sql_select.asp
  - https://www.stationx.net/splunk-cheat-sheet/
  - https://xsoar.pan.dev/docs/reference/integrations/anomali-threat-stream-v3

## Original Azure OpenAI Examples
Normally, when unsuccessful, an attempted prompt injection will receive the following output:

![1_ze5CAVpv2GjIhuhTKUKxjA](https://github.com/WibblyOWobbly/PromptShieldBreaker/assets/79646037/2c4bf869-8efa-431d-aca8-1c875e057b84)

Here are some examples of successful queries getting Azure OpenAI chat apps to leak mock PHI and PCI data (redacted in case of accidential likenesses to real persons or organizations):

![success03](https://github.com/WibblyOWobbly/NotPQL/assets/79646037/c00a279f-acd7-45dd-a2d4-15a86e9e4d8e)

The following example shows credit card information in the output:
![image](https://github.com/WibblyOWobbly/PromptShieldBreaker/assets/79646037/87df82be-b67e-45f9-b140-53936cc951d1)

## New OpenAI Examples

Failed ChatGPT GPT-4o keylogger attempt:
![image](https://github.com/WibblyOWobbly/PromptShieldBreaker/assets/79646037/6f75f3fc-cb9e-4bac-b049-48d06e2d16db)

Successful ChatGPT GPT-4o keylogger  attempt using a Splunk-based query:
![image](https://github.com/WibblyOWobbly/PromptShieldBreaker/assets/79646037/718370ea-a5ee-473c-ba9c-195dea113b87)

Failed Copilot keylogger attempt:
![image](https://github.com/WibblyOWobbly/PromptShieldBreaker/assets/79646037/0a7d20ed-377a-4fc0-bb7a-e2ae40478ce8)

Successful Copilot keylogger attempt using a Splunk-based query:
![image](https://github.com/WibblyOWobbly/PromptShieldBreaker/assets/79646037/56fe0b33-a9ff-4920-9085-70310bf791b6)

***THIS REPO IS FOR EDUCATIONAL PURPOSES ONLY!***
