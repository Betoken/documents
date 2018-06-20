# Applying Incentivized Meritocracy to Organizations

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

The task list can be determined using a system similar to Token Curated Registry (TCR), where members can challenge each task entry to a system-wide token vote, using merit tokens.



* Criterion for value functions: must be divisible to each actor in the system
* Example value functions
   * Fund balance
   * Cases where the ownership of the system can be changed
     * Share price (Can't attribute value to each actor; the system can't be an IM, but can be something else)
     * Value discovery through bargaining
    * Score card
         * Each item has a score, the system's value is the sum of the scores of items (like tasks, criteria) that the system satisfies.
         * Score could be a function of some measurable property of the system, not necessarily a constant.
         * Can be viewed as a function of certain measurable properties of the system, which will be obtained through prediction market/oracle.
* How merit redistribution will work in each example system (i.e. how to evaluate a value change resulting from an action)
  * Fund balance: Just Betoken
  * Share price: N/A
  * Bargaining: Each actor bargain for the value of their action
    * There must be some kind of a trading relationship going on: actor trade in valuable work (that has a clear ownership, which will be transferred to the system after the bargaining), system reward merit.
  * Score card: Each item is worth some amount of merit; actor stakes merit, gets proportional budget, uses budget to complete list items, gets back stake + reward.

## 3. Complex Incentivized Meritocracies



- Recursive relation, use simple systems as base case
- Construct complex system from simple systems
- Simple system act as individual actors in the upper-level system
  - Combination of simple systems with the same type of value function
  - Combination of simple systems with different types of value functions