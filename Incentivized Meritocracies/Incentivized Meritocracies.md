# Incentivized Meritocracies

### Zebang (Zefram) Liu

## Abstract

We introduce **Incentivized Meritocracy**, a multi-actor decision-making system that always optimizes for its value.

In this paper, we first define the conditions for a system to be categorized as an Incentivized Meritocracy. Next, we introduce the SAR notation used for describing the decision-making process of Incentivized Meritocracies. Then, we describe $\alpha$-Implementation, a category of implementations of Incentivized Meritocracy, and prove that such implementations do satisfy the conditions for being an Incentivized Meritocracy. After that, we describe Betoken's $\alpha$-Implementation using SAR notation. Finally, we prove that Incentivized Meritocracies always optimize for their values.

## 1. Definition

An **Incentivized Meritocracy** is a multi-actor decision making system where:

1. Each actor's control over decisions is proportional to their merit relative to everyone's merit
2. The value of merit to each actor is greater than 0 (they're incentivized to get more merit)

For each actor, 

* their *control* is a percentage whose meaning is entirely dependent on the specific system they're in and exists independent of whether a system is an IM, 
  * ex. percentage of shares in a company one owns
* while their *merit* is an artificial property specific to IMs that's used to represent an actor's ability to increase the value of the system.

Given actor $a$, if we denote their control as $c^a$, their merit as $m^a$, the amount of merit among all actors as $M=\sum_{i \in \mathbb{A}} m^i$ the value of each unit of merit as $v^{merit}$, we can formally write the above conditions as:

1. $c^a \propto \frac{m^a}{M} (1)$
2. $v^{merit} > 0 (2)$

However, they don't mean much if there isn't a clear definition of one's *merit*. If we denote the value of a system as $V$, we can say:

* $m^a \propto V^a(3)$

which means that an actor's merit should be proportional to the part of $V$ that can be attributed to the actor's actions. Of course, you can define merit as something else, but this definition captures well what people mean when they say "merit" in the context of an organization, and it's what we're going with.

Thus, in order to be called an *Incentivized Meritocracy*, a system should satisfy the above three (or just the first two if you're nitpicky) conditions.

(Note: when proportionality is used in this paper, we always assume that the *coefficient of proportionality* is positive.)

## 2. SAR Notation of IMs

SAR means State, Action, and Reward, which are terms often used in describing the Markov Decision Process. Since an Incentive Meritocracy is a decision-making system, it's appropriate to use existing notation.

* State: the value of the system
  * $S_\tau$: the state at the start of time step $\tau$
* Action: an action consumes some amount of the system's value and returns a new value in the next time step
  * $A^a_\tau(v_{in}) = v_{out}$: the value generated from the action that actor $a$ performed during time step $\tau$, given that they used $v_{in}$ on performing the action, is denoted as $A^a_\tau(v_{in})$
  * $A_\tau$: represents the act of all actors performing actions during time step $\tau$
* Reward: the change in merit of each actor
  * $R^a_\tau$: the change in actor $a$'s merit value at the start of time step $\tau$
  * $R_\tau$: represents the act of giving out rewards to all actors at the start of time step $\tau$

Thus, we can represent the progression of an Incentivized Meritocracy like this:

> $S_0 A_0 R_1 S_1 A_1 R_2 ...$

## 3. $\alpha$-Implementation

### 3.1 Definition

**$\alpha$-Implementation** is a category of Incentivized Meritocracies. Betoken's version of Incentivized Meritocracy is a variant of a $\alpha$-Implementation.

A full SARS cycle of a $\alpha$-Implementation will be described below.

1. State $S_\tau = (V_\tau)$ is given by the the previous time step (or the initial conditions when $\tau=0$).
2. $\forall a \in \mathbb{A}, A^a_\tau(s^a_\tau)$ (Actors perform actions)
   * $0 \leq s^a_\tau \leq V_\tau \frac{m^a_\tau}{M_\tau}$ is the amount of value $a$ chooses to invest in performing the action
3. $\forall a \in \mathbb{A}, R^a_{\tau + 1} = \frac{M_\tau}{V_\tau}(A^a_\tau(s^a_\tau) - s^a_\tau)= \frac{M_\tau}{V_\tau}\Delta V^a_\tau$
   * Reward is given at time step $\tau + 1$, since the value of $A^a_\tau(s^a_\tau)$ is unknown until after the current time step is over
4. State $S_{\tau + 1} = (V_{\tau + 1} =\sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) + (V_\tau - \sum_{a \in \mathbb{A}}s^a_\tau))$ 

### 3.2 Proof of IM-ness

* Condition 1 (control $\propto$ relative merit): If we define *control* as the percentage of the system's value that an actor can invest into performing an action during a time step, it's obvious that $c^a_\tau = \frac{m^a_\tau}{M_\tau}$. Thus condition 1 of being an IM is satisfied.

* Condition 2 (merit has value): In the given definition of an $\alpha$-Implementation, merit *does not have any value backing it*, so condition 2 is not satisfied. Thus, an $\alpha$-Implementation is not a complete IM; one must peg merit to *something* of value to ensure that one's $\alpha$-Implementation is a complete IM.

  * The reason merit isn't pegged to anything in the definition is that different systems may have different quirks and needs, so it's best to provide the freedom to choose how actors are incentivized to obtain more merit. Drawing a parallel to OOP, $\alpha$-Implementation is an *abstract class* that implements the *IM interface*, so to instantiate an $\alpha$-Implementation one needs to first implement the *meritValue()* function from the IM interface.
  * As an example, Betoken takes out a certain proportion of the system's value at the beginning of each time step as *commission*, and every actor can get a share of the commission based on their relative merit. Specifics can be found in 3.3.
  * Remark: One could argue that merit has inherent value in that it gives you control over the system's decisions. However, it is not considered in our analysis, since it's difficult to quantify such values for the same reason that moral value or emotional value is difficult to quantify. We assume that the actors are rational.

* Condition 3 (merit $\propto$ contribution to value): 

  $m^a_\tau = \sum_{t=1}^\tau R^a_t = \sum_{t=0}^{\tau - 1} \frac{M_t}{V_t}\Delta V^a_t$

  $\because \forall a \in \mathbb{A}, \frac{\Delta M_\tau^a}{\Delta V_\tau^a} = \frac{R^a_\tau}{\Delta V_\tau^a} = \frac{\frac{M_\tau}{V_\tau}\Delta V_\tau^a}{\Delta V_\tau^a} = \frac{M_\tau}{V_\tau}$

  $\therefore \frac{M_\tau + \Delta M_\tau^a}{V_\tau + \Delta V_\tau^a} = \frac{M_\tau}{V_\tau}$

  $\therefore \frac{M_{\tau+1}}{V_{\tau+1}} =  \frac{M_\tau + \sum_{a \in \mathbb{A}} \Delta M_\tau^a}{V_\tau + \sum_{a \in \mathbb{A}} \Delta V_\tau^a} = \frac{M_{\tau}}{V_{\tau}}$

  $\therefore \forall t, \frac{M_t}{V_t} = constant$ .

  $\therefore m^a_\tau = \sum_{t=0}^{\tau - 1} \frac{M_t}{V_t}\Delta V^a_t = \frac{M_\tau}{V_\tau}V^a_\tau \propto V^a_\tau$

  $\therefore$ condition 3 is met 

Therefore, an $\alpha$-Implementation is necessarily an Incentivized Meritocracy, if additional measure is taken so that merit is being backed by value.

$Q.E.D.$

### 3.3 Betoken's $\alpha$-Implementation

Betoken's Incentivized Meritocracy is a variant of $\alpha$-Implementation. 

In Betoken, the value of the IM is the total funds, and one's merit is represented by one's Kairo balance.

A full SARS cycle of Betoken's IM will be described below.

1. State $S_\tau = (V_\tau)$ is given by the the previous time step (or the initial conditions when $\tau=0$).

2. $\forall a \in \mathbb{A}, A^a_\tau(s^a_\tau)$ (Actors perform actions)

   - $\lambda V_\tau \frac{m^a_\tau}{M_\tau} \leq s^a_\tau \leq V_\tau \frac{m^a_\tau}{M_\tau}$ is the amount of value $a$ chooses to invest in performing the action
     - $\lambda$ is the minimum proportion of the investment limit that must be invested

3. $\forall a \in \mathbb{A}, R^a_{\tau + 1} = \frac{M_\tau}{V_\tau}[(A^a_\tau(s^a_\tau) - s^a_\tau) + \pi s^a_\tau]= \frac{M_\tau}{V_\tau}(\Delta V^a_\tau + \pi s^a_\tau)$

   * $\pi \in \mathbb{R^+}$ is the inflation rate of merit

   - Reward is given at time step $\tau + 1$, since the value of $A^a_\tau(s^a_\tau)$ is unknown until after the current time step is over

4. State $S_{\tau + 1} = (V_{\tau + 1} = \sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) + (V_\tau - \sum_{a \in \mathbb{A}}s^a_\tau) - \beta(\sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) - V_\tau) - \gamma\sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) \\= (1 - \beta - \gamma)\sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) + (1+\beta) V_\tau- \sum_{a \in \mathbb{A}}s^a_\tau)$

   $\forall a \in \mathbb{A}, com^a_{\tau+1} = \beta(\sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) - V_{\tau})\frac{m^a_{\tau+1}}{M_{\tau+1}}$ (Pay out commission to actors)

   * Compared to a vanilla $\alpha$-Implementation, commission and developer fees is deducted from the value generated by actions.
     * $\beta \in [0, 1]$ is the *commission rate*, the percentage of profit to be awarded to actors based on their merit
     * $\gamma \in [0, 1]$ is the *developer fee rate*, the percentage of system value to be paid to Betoken's developers
     * $com^a_{\tau+1}$ is the commission awarded to actor $a$ at the start of time step $\tau+1$

---

Due to the abovementioned modifications, Betoken's implementation is in fact only approximately an Incentivized Meritocracy.

* Since a new term, $\frac{M_\tau}{V_\tau}\pi s^a_\tau$, is added in $R^a_{\tau + 1}$'s expression, condition 3 is only approximately met if $\pi \ll 1, |\Delta V_\tau^a| \gg 0$

  > $\because \frac{\Delta M_\tau^a}{\Delta V_\tau^a} = \frac{R^a_\tau}{\Delta V_\tau^a} = \frac{\frac{M_\tau}{V_\tau}[\Delta V_\tau^a + \pi s^a_\tau] }{\Delta V_\tau^a} = \frac{M_\tau}{V_\tau}(1 + \frac{\pi s^a_\tau}{\Delta V_\tau^a})$ 
  >
  > $\therefore\pi \ll 1, |\Delta V_\tau^a| \gg 0 \implies \frac{\Delta M_\tau^a}{\Delta V_\tau^a} \approx \frac{M_\tau}{V_\tau}$  
  >
  > $\therefore \frac{M_\tau + \Delta M_\tau^a}{V_\tau + \Delta V_\tau^a} \approx \frac{M_\tau}{V_\tau}$
  >
  > $\therefore \frac{M_{\tau+1}}{V_{\tau+1}} =  \frac{M_\tau + \sum_{a \in \mathbb{A}} \Delta M_\tau^a}{V_\tau + \sum_{a \in \mathbb{A}} \Delta V_\tau^a} = \frac{M_{\tau}}{V_{\tau}}$
  >
  > $\therefore \forall t, \frac{M_t}{V_t} = constant$
  >
  > $\therefore m^a_\tau = \sum_{t=0}^{\tau - 1} \frac{M_t}{V_t}[\Delta V^a_t + \pi s^a_t] = \frac{M_\tau}{V_\tau}(V^a_\tau + \pi \sum_{t=0}^{\tau - 1} s^a_t) \propto V^a_\tau$, and therefore condition 3 is approximately met.

* Since state transitions are modified to include commission and developer fees, condition 3 is only approximately met if $\beta , \gamma \ll 1$

  > $V_{\tau + 1} = (1 - \beta - \gamma)\sum_{a \in \mathbb{A}} A^a_\tau (s^a_\tau) + (1+\beta) V_\tau- \sum_{a \in \mathbb{A}}s^a_\tau \\= (1 - \beta - \gamma)[V_\tau + \sum_{a \in \mathbb{A}} (A^a_\tau (s^a_\tau) - s^a_\tau)] + (2\beta + \gamma)V_\tau - (\beta + \gamma)\sum_{a \in \mathbb{A}}s^a_\tau \\=  (1 - \beta - \gamma)(V_\tau + \sum_{a \in \mathbb{A}}\Delta V^a_\tau) + (2\beta + \gamma)V_\tau - (\beta + \gamma)\sum_{a \in \mathbb{A}}s^a_\tau$
  >
  > $\therefore \beta , \gamma \ll 1 \implies \frac{M_{\tau+1}}{V_{\tau+1}} \approx  \frac{M_\tau + \sum_{a \in \mathbb{A}} \Delta M_\tau^a}{V_\tau + \sum_{a \in \mathbb{A}} \Delta V_\tau^a} = \frac{M_{\tau}}{V_{\tau}}$

### 3.4 Remarks

#### 3.4.1 Handling New Actors

In the previous analysis, it is assumed that the set of all actors, $\mathbb{A}$, is immutable. However, in real-life systems, it is usually the case that new actors would join the system long after the system's creation. This can be dealt with by making $\mathbb{A}$ an infinite set with only finitely many non-empty actors. To "add" a new actor, we can simply select one of the empty actors and initialize it with the desired parameters. Thus, the previous analysis is applicable to systems where $\mathbb{A}$ is mutable as well.

#### 3.4.2 Handling Merit Transfers

It is sometimes the case that an actor's merit is transferrable, such as in Betoken. To handle this in our analysis, we simply transfer part of $V^a$ together with the merit, such that $\Delta V^a = \frac{\Delta m^a}{m^a}V^a$. Thus, condition 3 of IM-ness is still met.

#### 3.4.3 Handling Deposits & Withdrawals

It is sometimes the case that the value of the system can be changed by things other than actions made by actors. For example, users can deposit or withdraw funds in Betoken, which is separate from the actions made by managers. To handle this in our analysis, we set aside a "dummy actor" that simulates deposits and withdrawals of value using actions with special values. Specifically:

* Depositing $d$ units of value is equivalent to performing an action in the form of $A(0)=d$
* Withdrawing $w$ units of value is equivalent to performing an action in the form of $A(w) = 0$

Since the actor is a dummy, we ignore the merit that it gets from these special actions. This doesn't affect our analysis.

## 4. Proof that IMs Optimize Their Values

Even though it is intuitively clear that Incentivized Meritocracies would optimize their values, it is still necessary to provide a formal proof of this property. 

---

Define the value function of actor $a$ as $v^a$. It is obvious that each actor would attempt to optimize their individual value functions. In the context of an Incentivized Meritocracy, it is reasonable to let $v^a = v^{merit}m^a$.

**To Prove:** $\forall a \in \mathbb{A}, \frac{\partial V}{\partial v^a} > 0$

**Proof:**

$V = \sum_{a \in \mathbb{A}}V^a$

$\because \forall i,a \in \mathbb{A}, i \not = a \implies \frac{\partial V^i}{\partial v^a} = 0$

$\therefore \forall a \in \mathbb{A}, \frac{\partial V}{\partial v^a} = \frac{\partial (\sum_{i \in \mathbb{A}}V^i)}{\partial v^a}=\sum_{i \in \mathbb{A}} \frac{\partial V^i}{\partial v^a}= \frac{\partial V^a}{\partial v^a}$

$\therefore \forall a \in \mathbb{A}, \frac{\partial V}{\partial v^a} = \frac{\partial V^a}{\partial v^a} = \frac{\partial V^a}{\partial v^{merit}}\frac{\partial v^{merit}}{\partial v^a}+\frac{\partial V^a}{\partial m^a}\frac{\partial m^a}{\partial v^a}=\frac{\partial V^a}{\partial v^{merit}}\frac{1}{m^a} + k\frac{1}{v^{merit}} (k=\frac{V^a}{m^a}>0)$

If we make the reasonable assumption that $\frac{\partial v^{merit}}{\partial V^a}>0$, meaning that the more value an actor contributes to the system, the more valuable merit becomes, then:

$\forall a \in \mathbb{A}, \frac{\partial V}{\partial v^a}=\frac{1}{\frac{\partial v^{merit}}{\partial V^a}}\frac{1}{m^a} + k\frac{1}{v^{merit}}>0$

$Q.E.D.$

