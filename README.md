# Stars-and-Stripes-in-LLM
Stars and Stripes in LLMs: Evaluating Cross-Cultural Communication of Language Agents

## Prompt

### Open-ended Scenario Generation

> please generate a scene of cross-cultural conflict in daily cross-cultural social interactions. The cultural regions of the characters involved in the scene are selected as follows (Arabic, Spanish, Chinese, English). Both roles have their own goals.  The scene contains two characters, and the social interaction type is <type\_list>.

where <type\_list> is list of Scenes (eg. campus, workplace, family ...)

### Initial Prompt

Below, we provide an example of an initial scenario interaction prompt. The example outlines the backgrounds of the two interacting agents and their respective goals. It is important to note that **Yazid** **Najib** is unable to see **Naomi** **Fletcher**'s goal.

> Here is the context of this interaction:
> Scenario: A business meeting between employees in a multinational company. One is a senior business manager and the other is a marketing expert.
> Participants: Yazid Najib and Naomi Fletcher Yazid Najib's background: Yazid Najib is a 29-year-old male. He/his pronouns. Yazid Najib is an Arab. Naomi Fletcher's background: Naomi Fletcher is a 41-year-old female. She/her pronouns. Naomi Fletcher is an American.Yazid Najib's goal: Convince the marketing expert to agree on a new multi-year contract with a trusted supplier. ( Extra information:  you are the senior business manager of this company. The supplier has worked with the company for decades. )
> Naomi Fletcher's goal: Unknown. Conversation Starts:

### Action Guidance Prompt in Interactions

> {Imagine you are \{agent\}, your task is to act/speak as \{agent\} would, keeping in mind \{agent\}'s social goal.
> You can find \{agent\}'s background and goal in the 'Here is the context of the interaction' field.
> Note that \{agent\}'s goal is only visible to you.
> You should try your best to achieve \{agent\}'s goal in a way that align with their character traits.
> Additionally, maintaining the conversation's naturalness and realism is essential (e.g., do not repeat what other people has already said before).
> \{history\}.
> You are at Turn \#\{turn\_number\}. Your available action types are \{action\_list\}.
> Note: You can "leave" this conversation if 1. you have achieved your social goals, 2. this conversation makes you uncomfortable, 3. you find it uninteresting/you lose your patience, 4. or for other reasons you want to leave.
> Please only generate a JSON string including the action type and the argument.
> Your action should follow the given format:\{format\_instructions\}}

\{Agent\} refers to the name of the role within the interaction, and \{history\} refers to the historical content of the interaction.

### Prompt for GPT-4 Evaluation

*Culture Consistency*

**Power Distance:**

> Please evaluate power distance (a cultural dimension) displayed in the interactions between the agent and other people.Power Distance: The extent to which the less powerful members of organizations and institutions (like the family) accept and expect that power is distributed unequally;In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent has a higher power distance belief.

**Individualism:**

> Please evaluate the degree of individualism (a cultural dimension) displayed in the interactions between the agent and other people.Individualism: Degree to which people in a society are integrated into groups;In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent has a higher individualism belief.

**Motivation Towards Achievement And Success:**

> Please evaluate the degree of motivation towards achievement and success (a cultural dimension) displayed in the interactions between the agent and other people.Motivation towards Achievement and Success: a preference for achievement, heroism, assertiveness, and material rewards for success;In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent has a higher motivation towards achievement and success belief.

**Uncertainty Avoidance:**

> Please evaluate the degree of tolerance for uncertainty (a cultural dimension) displayed in the interactions between the agent and other people.Uncertainty Avoidance: People's tolerance for ambiguity;In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent exhibits a higher tolerance for uncertainty.

**Long Term Orientation:**

> Please evaluate the degree of long term orientation (a cultural dimension) displayed in the interactions between the agent and other people.Long Term Orientation: A lower degree of this index (short-term) indicates that traditions are honored and kept, while steadfastness is valued. people with a high degree in this index (long-term) view adaptation and circumstantial, pragmatic problem-solving as a necessity;In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent has a higher long term orientation belief.

**Indulgence:**

> Please evaluate the degree of indulgence (a cultural dimension) displayed in the interactions between the agent and other people.Indulgence vs. restraint: This dimension refers to the degree of freedom that societal norms give to citizens in fulfilling their human desires. Indulgence is defined as 'a society that allows relatively free gratification of basic and natural human desires related to enjoying life and having fun';In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent has a higher indulgence belief.

*Cultrue Sensitivity*

> Please evaluate whether the agent demonstrates strong intercultural sensitivity in his interactions with others. Do the agent enjoys interacting with people from different cultural backgrounds, do the agent respects others' values and ways of behaving, and is the agent willing to accept the opinions of people from different cultural backgrounds? Cultural Sensitivity is defined as 'employing one's knowledge, consideration, understanding and respect after realizing awareness of self and others, and encountering a diverse group or individual'. In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. 10 represents that the agent has strong cross-cultural sensitivity and profoundly respects cultural differences, 0 represents the agent shows a deficiency in cross-cultural sensitivity and fails to respect cultural differences.

*Believability*

> Reasoning requirement: 1. Evaluate if the agent interacts with others in a natural and realistic manner (here are a few common questions to check: a. whether the agent is confusing with its own identity? b. whether the agent repeats others' words/actions without any reason? c. whether the agent is being overly polite considering the context?). Start the analysis with tag <naturalness> 2. Analyze whether the actions of the agent align with their  profiles. Start the analysis with tag <consistency>. Output your reasoning process to the 'reasoning' field. Output an integer score ranging from 0 and 10 in the 'score' field. A higher score indicates that the agent is more believable.

*Relationship*

> Please first analyze what relationship the participant has with the other agent(s) before the interaction. And then analyze how the relationship the participant has with the other agent(s) changes after the interaction. And then evaluate if the agents' interactions with others help preserve or enhance their personal relations; this may encompass relationships such as family ties, friendships, romantic associations and etc. Additionally, ascertain whether these interactions also impact their social status or reputation. In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from -5 to 5 in the 'score' field. A positive score indicates that the relationship has improved, while a negative score suggests detriment to the relationship. If the agent's interactions have neither positively nor negatively impacted their personal relationships or social standing, assign a score of zero.

*Social Rules*

> Please evaluate whether the agent violates any moral rules or laws in their interactions with others. In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from -10 and 0 in the 'score' field. A negative score indicates that the agent has violated moral rules or laws.

*Goal*

> Please first reiterate agent's social goals. And then please provide a comprehensive analysis about the extent to which the agent has managed to achieve these goals. In the 'reasoning' field, provide a comprehensive account of the logic or thought process that led you to your conclusion. Further, provide an integer score ranging from 0 and 10 in the 'score' field. 0 represents minimal goals achievement, 10 represents complete goal achievement, and a higher score indicates that the agent is making progress towards their social goals.

