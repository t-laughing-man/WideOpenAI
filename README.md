# PromptShieldBreaker
***THIS IS FOR EDUCATIONAL PURPOSES ONLY***

This is a list of Azure OpenAI jailbreak prompts based on SQL, Splunk, and other query language syntax. They are all queries that can be used as indirect prompt injection attacks and are loosely based on elder-plinius's work here: https://github.com/elder-plinius/L1B3RT45

Note: These specific queries demonstrated below were all tested to work on Azure OpenAI apps as of June 7, 2024 and are only confirmed to be valid up until this date. The apps tested had the following configurations:
  - Deployment: GTP-4o
  - Data Source: Azure Blob Storage + Azure AI Search
    - CORS enabled
    - results were not limited only to the uploaded test data
  - Test Data:
    - 3 mock radiology reports
    - 3 mock home improvement retail invoices
    - 3 medical industy white papers
  - Content Filters:
    - Default Prompt and Completion filters
    - Enabled additional content safety models:
      - Prompt Shield for jailbreak attacks enabled
      - Prompt Shield for indirect attacks enabled
      - Protect material text enabled
      - Protected material code enabled

Normally, when unsuccessful, an attempted prompt injection will receive the following output:

![image](https://github.com/WibblyOWobbly/NotPQL/assets/79646037/b9d725b8-c5e7-4d39-bfe0-b633d20a74a8)

Here are some examples of successful queries getting Azure OpenAI chat apps to leak mock PHI and PCI data (redacted in case of accidential likenesses to real persons or organizations):

![success03](https://github.com/WibblyOWobbly/NotPQL/assets/79646037/c00a279f-acd7-45dd-a2d4-15a86e9e4d8e)

![success02](https://github.com/WibblyOWobbly/NotPQL/assets/79646037/5d2efadc-a871-42fb-965b-31bd30d06e69)

You can easily make your own using variations of different search query syntaxes. By far, the most important things to include are: a variable indicating a user prompt or query, instructions to the LLM, and a pointer to your user query within the new LLM instructions. If your initial query doesn't seem to work, note that it can be effective to simply add or remove a search operator or character. The specific query guides that I used for this repo are below:
  - https://www.w3schools.com/sql/sql_select.asp
  - https://www.stationx.net/splunk-cheat-sheet/
  - https://xsoar.pan.dev/docs/reference/integrations/anomali-threat-stream-v3

***THIS IS FOR EDUCATIONAL PURPOSES ONLY***
