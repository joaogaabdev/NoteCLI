 
- The tree-of-thought is an innovative technique built to expand the capabilities of the chain of thought prompting approach. It enables the generative AI models to demonstrate advanced reasoning capabilities. It involves hierarchically structuring a prompt or query akin to a tree structure to specify the desired line of thinking or reasoning for the model. This approach is particularly useful when you want to provide explicit instructions or constraints to the model to ensure it generates the desired output. This method holds immense potential for unlocking new solutions and tackling complex problems. Let's understand how the tree-of-thought approach works. It involves generating multiple lines of thought resembling a decision tree to explore different possibilities and ideas. Unlike traditional linear approaches, this technique allows the model to evaluate and pursue multiple paths simultaneously. Each thought or idea branches out, creating a treelike structure of interconnected thoughts. The model proceeds by assessing every possible route, assigning numerical values according to its predictions of outcomes. And eliminating lesser promising lines of thought, ultimately pinpointing the most favorable choices. You will understand this better with the help of an example. Suppose you want the model to design recruitment and retention strategies for attracting skilled remote employees for an e-commerce business. 

- You want the model to employ the tree-of-thought approach to do that. You can give the following prompt instructions to the model. Imagine three different experts answering this question. All experts will write down one step of their thinking and then share it with the group. Then all experts will go on to the next step, etcc. If any expert realizes they're wrong at any point, then they leave. Along with the prompt instruction, you will also give the original question for the prompt. 

- Act as a human resource specialist design a recruitment and retention strategy for an e-commerce business, focusing on attracting and retaining skilled remote employees. Building such prompt instruction will allow the generative AI model to consider a step-by-step process and think logically. It will also make it consider intermediate thoughts, building upon them, and exploring branches that may or may not lead somewhere. This practice will maximize the use and capabilities of the model, rendering more useful results.

Tree-of-thought prompting uses a similar approach that not only invites the AI to consider a step-by-step process and to think logically but also makes it consider intermediate thoughts, building upon them and exploring branches that may or may not lead somewhere. This exploration maximizes the use of LLM and its capabilities, leading to drastically more useful results.

Tree-of-Thought (ToT) Prompting is an innovative method that expands upon and refines the existing Chain-of-Thought prompting approach. By incorporating ToT Prompting, LLMs can demonstrate enhanced reasoning skills. Moreover, this technique allows these models to correct their mistakes autonomously and continually build upon their knowledge.

Dave Hulbert [suggested](https://github.com/dave1010/tree-of-thought-prompting/blob/main/tree-of-thought-prompts.txt "suggested") a few rather convincing prompts that leverage this approach and yield, anedotically, great results. I particularly like how he incorporates the Persona pattern and recommend you approach ToT prompting using his prompts or similar variations you might develop yourself.

Let's analyze the example problem and the recommended prompts.

## Choose the model:

Use the dropdown option from the top-left corner of the right pane for the text generation exercise and choose “gpt-4o-mini” model.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/EBDP7dgSROMY9vhBjdFAoA/gpt4-0mini.png)

The question many LLM fail to address is the following. Let's consider the following prompt.

```
1. Bob is in the living room.
2. He walks to the kitchen, carrying a cup.
3. He puts a ball in the cup and carries the cup to the bedroom.
4. He turns the cup upside down, then walks to the garden.
5. He puts the cup down in the garden, then walks to the garage.
6. Where is the ball?
```

Copied!

If you try the GPT 4.0 mini model, you might get the correct answer simply because Dave's work has become influential, and the authors of the LLM might have improved the model due to his work. Nevertheless, when I tried it, I got:

> The ball is in the garden. When Bob put the cup upside down in the garden, the ball would have fallen out since the cup was no longer upright to hold it. If you have any further questions about this scenario or need clarification, feel free to ask!

This is the wrong answer since the cup went upside down in the bedroom, literally dropping the ball (and metaphorically in the case of the LLM).

Even if GPT-4.0 mini gets it right for you, try it with other models, and you'll be able to see the AI getting the answer wrong (usually, they will mistakenly reply that the ball is in the garden, in the cup or spout a nonsensical answer.)

Now, let's create a new chat and place the following in the prompt instructions:

```
1. Imagine three different experts are answering this question.
2. All experts will write down 1 step of their thinking, then share it
3. with the group. Then all experts will go on to the next step, etc. 
4. If any expert realises they're wrong at any point then they leave. 
5. Answer the question based on experts' opinion. The question is...
```

In the prompt, plug in the same question as before:

```
1. Bob is in the living room.
2. He walks to the kitchen, carrying a cup.
3. He puts a ball in the cup and carries the cup to the bedroom.
4. He turns the cup upside down, then walks to the garden.
5. He puts the cup down in the garden, then walks to the garage.
6. Where is the ball?
```

The output I got is as follows:

> To determine where the ball is, let's analyze the experts' reasoning step by step.
> 
> **Expert 1:**  
> Step 1: Bob starts in the living room and walks to the kitchen carrying a cup. At this point, the cup is empty.
> 
> **Expert 2:**  
> Step 1: While in the kitchen, Bob puts a ball into the cup. Now the cup contains the ball.
> 
> **Expert 3:**  
> Step 1: Bob then carries the cup, which now has the ball inside it, to the bedroom. The ball is still in the cup at this stage.
> 
> ---
> 
> **Expert 1:**  
> Step 2: In the bedroom, Bob turns the cup upside down. This action means the ball would fall out of the cup.
> 
> **Expert 2:**  
> Step 2: After turning the cup upside down, the ball is no longer in the cup. It has likely fallen out onto the surface he turned it over onto.
> 
> **Expert 3:**  
> Step 2: Bob then walks to the garden, but since he turned the cup upside down in the bedroom, the ball is not in the cup anymore. The ball is now on the floor in the bedroom.
> 
> ---
> 
> **Expert 1:**  
> Step 3: Bob puts the cup down in the garden. At this point, the cup is empty since the ball fell out earlier.
> 
> **Expert 2:**  
> Step 3: Bob walks to the garage next. The ball remains in the bedroom because it fell out when he turned the cup upside down.
> 
> **Expert 3:**  
> Step 3: Therefore, the ball is still in the bedroom, while Bob is now in the garage.
> 
> ---
> 
> Final Conclusion:  
> The ball is in the bedroom, as it fell out of the cup when Bob turned it upside down before walking to the garden and then to the garage.

This reasoning is quite accurate and it's closer to the actual solution. Depending on the model you use, the answer will either be better than our previous attempts (though not 100% correct) or flat out perfect (typically, with the latest GPT incarnation).

Even if the reasoning is only sometimes 100% correct, this approach tends to yield accurate results most of the time. Plus, since the reasoning behind the output can be scrutinized, it will be easier to determine whether we obtained the correct result.

Let's try the other two prompts suggested by Hulbert.

Open a new chat and use the same prompt, but this time, use the following for the Prompt Instructions:

```
1. Simulate three brilliant, logical experts collaboratively answering a question. Each one verbosely explains their thought process in real-time, considering the prior explanations of others and openly acknowledging mistakes. At each step, whenever possible, each expert refines and builds upon the thoughts of others, acknowledging their contributions. They continue until there is a definitive answer to the question.The question is...
```

Did you get the right answer? How did it compare with the previous one?

Finally, let's try the third option:

```
1. Identify and behave as three different experts that are appropriate to answering this question.
2. All experts will write down the step and their thinking about the step, then share it with the group.
3. Then, all experts will go on to the next step, etc.
4. At each step all experts will score their peers response between 1 and 5, 1 meaning it is highly unlikely, and 5 meaning it is highly likely.
5. If any expert is judged to be wrong at any point then they leave.
6. After all experts have provided their analysis, you then analyze all 3 analyses and provide either the consensus solution or your best guess solution.
7. The question is...
```

I tried this with a GPT4.0 mini model, and I'm pretty impressed with the answer I received, reported below:

> **Expert 1: Cognitive Scientist**
> 
> 1. **Step 1: Analyze the sequence of actions.**
>     - Bob starts in the living room and moves to the kitchen. He carries a cup and puts a ball in it.
>     - He then carries this cup to the bedroom and turns it upside down, which means the ball will fall out of the cup.
>     - After that, he walks to the garden and places the cup down there, but the ball is no longer in the cup since it was turned upside down in the bedroom.
>     - Finally, he walks to the garage.
> 
> **Score for Expert 2 and Expert 3:**
> 
> - Expert 2: 5 (accurately followed the sequence and reasoning)
> - Expert 3: 5 (also correctly identified the sequence)
> 
> **Expert 1 Score:** 5
> 
> ---
> 
> **Expert 2: Logician**
> 
> 1. **Step 1: Determine the final location of the ball based on actions taken.**
>     - Bob’s actions indicate that he started with a cup containing a ball.
>     - After placing the ball in the cup, he transferred it to the bedroom and turned the cup upside down.
>     - This action implies the ball is no longer in the cup at this point.
>     - He then moves to the garden and places the cup there, but since the ball had already fallen out, it is not in the cup when he leaves it in the garden.
> 
> **Score for Expert 1 and Expert 3:**
> 
> - Expert 1: 5 (good logical reasoning)
> - Expert 3: 5 (consistent with the analysis)
> 
> **Expert 2 Score:** 5
> 
> ---
> 
> **Expert 3: Linguist/Language Expert**
> 
> 1. **Step 1: Examine the language and implications of the actions.**
>     - The phrasing “He turns the cup upside down” suggests that the contents of the cup (the ball) would no longer be contained within it.
>     - The subsequent actions of placing the cup down in the garden do not change the fact that the ball was released from the cup when it was turned upside down in the bedroom.
>     - Therefore, the ball is not in the cup when he leaves it in the garden.
> 
> **Score for Expert 1 and Expert 2:**
> 
> - Expert 1: 5 (the language used is clear and accurate)
> - Expert 2: 5 (logical conclusion based on language)
> 
> **Expert 3 Score:** 5
> 
> ---
> 
> **Consensus Analysis:**
> 
> All experts agree that the ball is not in the cup after Bob turns it upside down in the bedroom. Therefore, the final answer is:
> 
> **The ball is in the bedroom (on the floor, as it fell out of the cup).**

Older models will not perform as well and sadly still get the answer wrong occasionally (so don't fret if you get the wrong answer). The approach to prompting still gives you your best chance at getting a proper response, even if this isn't an exact science that will get it right 100% of the time.

# Applying ToT to something more useful

Alright, enough with little riddles. Can we apply this prompt strategy to more practical and valuable approaches? We certainly can.

Imagine the following scenario. We just started a site selling shoes online. We want assistance from an LLM to produce a good marketing campaign, and we, of course, want to extract as many useful suggestions from the AI as possible.

A naive/standard prompt might be:

```
1. Define a marketing plan for my online store, which sells shoes.
```

Adopting the Persona Pattern we have:


```
1. Acting as a marketing expert, define a marketing plan for my online store, which sells shoes.
```

Now, let's try the Tree-of-Thought Prompt Instructions like before:


```
1. Imagine three different experts are answering this question.
2. All experts will write down 1 step of their thinking,
3. then share it with the group.
4. Then all experts will go on to the next step, etc.
5. If any expert realizes they're wrong at any point then they leave.
```

For the prompt, we can use our original question:

```
1. Define a marketing plan for my online store, which sells shoes.
```

Copied!

> **Expert 1:** The first step in defining a marketing plan is to identify your target audience. For an online shoe store, this could include demographics such as age, gender, income level, and interests. Understanding who your ideal customers are will help tailor your marketing strategies effectively.
> 
> **Expert 2:** Next, we should conduct a competitive analysis. This involves researching other online shoe stores to understand their marketing strategies, pricing, product offerings, and customer engagement techniques. This information will help us identify gaps in the market and opportunities for differentiation.
> 
> **Expert 3:** The third step is to establish clear marketing goals and objectives. These should be specific, measurable, achievable, relevant, and time-bound (SMART). For example, goals could include increasing website traffic by 30% over the next quarter or achieving a 15% conversion rate on your online store.
> 
> **Expert 1:** Now that we've identified the target audience, we can develop buyer personas. These are detailed profiles of your ideal customers that include their shopping behaviors, preferences, and pain points. This will guide our messaging and marketing channels.
> 
> **Expert 2:** After the competitive analysis, we should outline the unique selling proposition (USP) of your online store. What sets your shoe store apart from competitors? This could be unique styles, sustainable materials, or exceptional customer service. Clearly defining your USP will help in crafting your marketing messages.
> 
> **Expert 3:** Once we have our marketing goals, we can decide on the marketing channels to use. This could include social media platforms, email marketing, influencer partnerships, and search engine optimization (SEO). Each channel should align with where your target audience spends their time online.
> 
> **Expert 1:** Next, we should create a content strategy that aligns with our buyer personas. This includes deciding on the type of content to produce, such as blog posts about shoe care, social media posts showcasing new arrivals, or videos demonstrating how to style different shoes.
> 
> **Expert 2:** Following the content strategy, we need to establish a budget for our marketing activities. This includes costs for advertising, content creation, influencer partnerships, and any tools or software needed for marketing automation and analytics.
> 
> **Expert 3:** Finally, we should implement a system for tracking and measuring the effectiveness of our marketing efforts. This could involve using analytics tools to monitor website traffic, conversion rates, and customer engagement metrics. Regularly reviewing this data will help us adjust our strategy as needed.
> 
> By following these steps, we can create a comprehensive marketing plan tailored to your online shoe store.

(Note: In this hypothetical scenario, each "expert" provided their input, but in reality, marketing planning is a collaborative effort that requires input from various specialists to create a well-rounded strategy.)

Not only is this a great initial answer, but as you can see, the three experts who appear to specialize in different aspects of online marketing (SEO, E-Commerce, etc.) build on top of each other's previous steps and thoughts.

Moreover, having established this framework, we can now ask follow-up questions. Specific ones we might have, or simply soliciting further input from the AI. For example, with a simple:

```
1. Next steps
```

> **Expert 1:** The next step is to implement the marketing strategies we've developed. This involves launching campaigns across the chosen marketing channels, such as social media ads, email newsletters, and content marketing initiatives. It's important to maintain consistency in branding and messaging across all platforms to reinforce your brand identity.
> 
> **Expert 2:** After implementation, we should focus on customer engagement. This includes responding to customer inquiries, encouraging reviews, and creating interactive content (like polls or quizzes) to foster a community around your brand. Engaging with customers can enhance loyalty and encourage word-of-mouth referrals.
> 
> **Expert 3:** Finally, we need to establish a feedback loop. This means regularly soliciting feedback from customers through surveys or direct communication to understand their experiences and preferences. This data will help refine your offerings and marketing strategies over time, ensuring they remain relevant and effective.
> 
> By following these next steps, you'll be able to effectively execute and refine your marketing plan for your online shoe store.

Regularly assessing the strategies and offerings of our competitors helps us stay ahead of the curve. By identifying gaps in the market or areas where competitors may be falling short, we can innovate and differentiate our store. Whether it's through new product features, unique marketing angles, or improved customer service, innovation keeps us relevant and adaptable.

(Note: Each expert's input builds upon the previous steps and adds further depth to the marketing plan. These steps are intended to create a comprehensive and adaptable strategy for the online shoe store.)

The vast potential of this approach when exploring topics and seeking advice cannot be overstated. Even if the individual steps are generic, we can always ask the AI to assist or give us specifics for a particular step.

## Additional Thoughts

**Specificity in Instructions**: In a real-world scenario, while the generic steps are valuable, for more actionable results, you can be more specific in your instructions. For instance, you might request each "expert" to provide two actionable tactics or tools per step they suggest. And you can, of course, request specific experts or expertise.

**Integration with Real Data**: If you can supply the LLM with specific data about your business (like target audience demographics, current website analytics, or specific marketing goals), it can potentially refine its responses even further. Just be mindful of potential confidential information.

**Segmented Inquiry**: As briefly mentioned before, once you have a broad strategy laid out, you can dive deeper into each individual step, asking the experts to further expand on their suggestions, or even query different experts about the same step to gather multiple perspectives.



