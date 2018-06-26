# Applying Incentivized Meritocracy to Complex Organizations

Zefram Lou

## 1. Previous Work and Problems Faced

In [Incentivized Meritocracies](https://github.com/Betoken/documents/blob/master/Incentivized%20Meritocracies/Incentivized%20Meritocracies.pdf), I formally defined the criteria for a governance system to be classified as an Incentivized Meritocracy (IM), provided proof that an IM optimizes its system value function, and gave the notations for talking about Incentivized Meritocracies accurately. From the document, I think many people can observe that IM is radically different from most existing governance systems: it completely avoids the usage of voting, and purely employs economic incentives and algorithmic redistribution of power to ensure that good decisions are made, rather than relying on subjective rules and assumptions. It also broadens the definition of governance systems into any multi-actor system that optimizes for its value function, and turns governance design into an optimization problem.

However, it's obvious to see the problems that it faces: defining the value function of a complex organization is quite difficult, and the Betoken hedge fund is one of the rare instances where the system value function can be clearly defined. In this document, I will discuss the various ways that we can construct a clear value function for complex organizations.

## 2. Simple Incentivized Meritocracies

In order to construct complex Incentivized Meritocracies, it's necessary to first discuss the most simple Incentivized Meritocracies. Simple IMs can be divided into two types: for-profits and non-profits. 

For-profit IMs are the most basic IMs, where each actor simply strives to maximize a single numerical value--the amount of funds the IM owns; the Betoken hedge fund belongs to this group. For-profit IMs have the least subjectivity involved in their decision-making process, since the system value function is purely objective.

Non-profit IMs are considerably more complex, since the lack of an obvious objective--profit--necessitates the existence of a subjective goal that the IM should be working towards, and subjective things are often difficult to quantify.

### 2.1 For-profits

The workflow of a for-profit IM looks like the following:

1. Each actor stakes some merit tokens
2. The IM gives each actor funding proportional to their stake
3. Each actor uses the funding to somehow gain profits
4. Each actor returns the original funding +/- profits/losses to the IM
5. Each actor gets $(1 + ROI) \times stake$ merit tokens back

//TODO: Consider changing this into a task-based system as well

This looks rather simple, but when applied to generalized organizations, there are additional risks involved. In the Betoken hedge fund, the action space is relatively small, since all the actors do is trade tokens, which allowed us to handle all actions using smart contracts. However, in generalized organizations the action space is quite a bit larger, which includes literally any action that takes funding as input and produces funds as output, meaning that unless you restrict the action space for your specific application it's impossible to use smart contracts to define all actions. 

This introduces the possibility of a hit-and-run attack, where an actor simply exits the IM after they receive funding. The hit-and-run attack applies to non-profits as well as for-profits. We can quantify the vulnerability of an IM to such attacks with *hit-and-run safety*: $h=\frac{stake}{funding(stake)}$ . Since in IMs $funding(stake) \propto stake$, $h$ is a constant. We can say that an IM is *hit-and-run safe* if $h \ge 1$. Depending on the amount of trust in an IM, $h$ can be set to different values: in an anonymous DAO, it's best to set $h \ge 1$, while in a normal company with employees bound by legal contracts one can set $h < 1$.

### 2.2 Non-profits

There are many potential ways to incorporate subjective values into an IM, and thus many potential models for non-profit IMs. I will only go over a task-based model in this document.

The workflow of a task-based non-profit IM looks like the following:

1. The IM decides on a list of tasks to be completed in the current cycle, where each task specifies the amount of merit tokens that need to be staked for an actor to work on this task
2. Each actor picks some tasks from the list of tasks, and stakes merit tokens in each task
3. The IM gives each actor funding proportional to their stake
4. Each actor uses the funding to complete the tasks
5. For each task, the actor who worked on the task gets $(1 + rewardRate) \times stake$ merit tokens back if the task was completed, and $(1 - penaltyRate) \times stake$ if it was not

The task list can be determined using a system similar to Token Curated Registry (TCR), where members can challenge each task entry to a system-wide token vote, using merit tokens. This is of course one of many potential solutions, and it's almost certainly not the best possible option, but TCR can do the job while introducing minimal subjective rules.

The value function is the historical completion rate of tasks weighted by the stake of each task, i.e.
$$
V = \frac{\sum_{t \in \mathbb{T^{completed}}} s^t}{\sum_{t \in \mathbb{T}} s^t}
$$
where $s^t$ is the amount of merit token staked into task $t$.

//TODO: Find more appropriate value function

//TODO: Prove that non-profits are IMs using the value function expression

## 3. Complex Incentivized Meritocracies

Using the simple Incentivized Meritocracies, it is possible to construct complex IMs via synthesis. We can build IMs of different levels of complexity: level-1 IMs are the simple IMs where each actor is a single human/bot, level-2 IMs are made up of level-1 IMs, level-3 IMs are made up of level-2 IMs, and so on. IMs on a lower level act as actors in the higher level. There are 3 types of complex IMs: for-profits, non-profits, and hybrids. For-profits contain only for-profit IMs, non-profits contain only non-profit IMs, and hybrids contain both. I think hybrid IMs are the most interesting of the bunch, and likely will also be the most successful, so I will only discuss hybrids in this document. For the sake of simplicity, I will also only talk about level-1 & 2 IMs.

Hybrid IMs most resemble traditional (tech) companies: they contain departments that focus on ensuring the short-term incoming cash-flow (for-profits), as well as departments that focus on R&D, who don't bring in immediate profits but ensure the company's income in the relatively distant future (non-profits). This means that hybrid IMs not only can be financially self-sustainable, but also can be forward-looking and make decisions based on long-term benefits. 

A level-1 hybrid IM is simply a combination of a level-1 for-profit IM and a level-1 non-profit IM. Each member can work on for-profit actions, non-profit actions, or both at the same time. The IM's value function is the sum of the for-profit's value function and the non-profit's value function. This setup leverages the advantages of hybrid IMs while maintaining simplicity, but its simplicity is precisely its biggest disadvantage: when each actor is an individual, each action must be easy enough so that one person can complete it within a reasonable amount of time, like a week or a month, which severely restricts the IM's ability to work on complex projects. It would only be appropriate for small organizations of 1-50 people. Sure, it is possible to build informal structures to divide a complex task into smaller subtasks, but that defeats the purpose of having a formal governance system--IM--in the first place.

Level-2 hybrid IMs are much more capable at working on complex tasks. In level-2 hybrids, each actor is either a level-1 IM or an individual, though ideally they should all be level-1 IMs. A level-2 hybrid's value function is the sum of the value functions of its subsidiary IMs; since we have already proven that level-1 IMs maximize their value functions, it's obvious that the level-2 value function also gets optimized. Level-2 hybrids are similar to companies with many subsidiary departments each focusing on different jobs, which is why it can better handle complex tasks: for instance, the level-2 IM can have complex tasks like "develop the new front end", and the level-1 IM that takes on this task can divide it into simpler subtasks like "create GitHub repo" and "make mockups" that are reasonable to be handled by an individual.

As the number of levels increase, the complexity of tasks that the IM can handle greatly increases. Since the number of individuals the IM can handle increases exponentially w.r.t. the number of levels, a level-2/3 IM would be sufficient for most organizations.

## 4. Comparison Between Complex IM And Other Governance Models

* Non-hierarchical vs. hierarchical

## 5. Potential Pitfalls

*  Lack of cooperation between level-1 IMs?
* Need for collateral may be prohibitive
* Legal issues: should the IM be responsible for an individual's action?
  * e.g. hacking an exchange as a for-profit action