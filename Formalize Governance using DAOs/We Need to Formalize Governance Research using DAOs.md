# We Need to Formalize Governance Research using DAOs

### Zefram Lou

**Disclaimer: Anything mentioned in this post could be horribly wrong or inaccurate. But hey, there's a non-negligible chance that a deadly Gamma ray burst hits Earth right now and kills everyone before you can feel anything, so does it *really* matter?**

> Man is a political animal. --Aristotle

From the city-states of Mesopotamia to the polis of Greece, from the Roman republic to the United States, governance systems have always been at the center of human civilizations. Before the introduction of free-market capitalism, it has been the governments who organized our economic activities, who dictated our beliefs, traditions, and ideologies, who decided how we lived our lives. Even now, it's safe to say that governments are pretty darn important to our everyday lives. 

Before I go any further, let me define what a governance system is. A governance system consists of two major components:

* A decision-making system: The mechanism that participants use to arrive at a decision when faced with a problem
  * ex1. How you pick the designated driver: coin flips, rock-paper-scissors, etc.
  * ex2. Using a first-past-the-post voting system to determine the President of your country.
* An incentive system: A system that rewards good behavior and punishes bad behavior
  * ex1. If you forget to take out the trash, you have to do it for a week.
  * ex2. If you murder someone, you get thrown in prison.

Since governance systems are so important, you can almost bet that they're held together by duct tapes and zip ties. Seriously, until very recently, the only reason that rulers had sway over their subjects is that people literally believed some invisible sky-being pointed at the kings and queens and said "Yeah I want those guys to boss over you and you should also give all your money to them". Yes, human society only existed because everyone in the past fell for a scam that your old granny wouldn't fall for. (Greece was the exception, not the rule.)

The Renaissance and the Enlightenment made that situation a lot better. We started to use our rationality to analyze our political systems, and finally called bullshit. We developed a theoretical framework to think about governance systems, namely modern political science. We also came up with the modern notion of a democratic republic, which derived power from the consent of its own people. Turns out it's pretty useful.

Victory? Not yet.

>  Democracy is the worst form of government, except for all the others. --Winston Churchill

Ever since WW2, democracy--rule of the people--has always been perceived as the natural, and the best, solution to governance, but reality is rarely so black-and-white. America has flouted its democratic system as the source of its ideological and moral superiority, despite the fact that political "donation" is considered free speech, the failed attempts to "establish democracy" in the Middle East, not to mention the election of Donald Trump. The democratic governments in western Europe have established welfare states where citizens enjoy free health care, free education, and the highest quality of life, but the sloth-like due process has not been able to properly handle the influx of refugees and the subsequent rise of terrorism and religious fundamentalism. And, as we've found out recently, Russia has been successfully meddling in foreign elections, in countries we have often viewed as the most successfully run democracies. 

If democracy--with all its vulnerabilities and disadvantages--is indeed the best governance system we as a species can come up with, then we're truly doomed.

But why are we facing such a crisis in our governance systems? Didn't we use political science to sort out all the problems we had with our governments? Why are our governments still so incompetent, inefficient, and vulnerable to attacks?

> ...I call these things cargo cult science, because they follow all the apparent precepts and forms of scientific investigation, but they're missing something essential...
>
> --Richard Feynman

Well, you see, this is kind of awkward. Political Science is **NOT** a science. (Sorry, PoliSci majors) In order for something to be called a science, it must employ the **scientific method**, which means that to arrive at any conclusion about reality you need to:

1. Propose a hypothesis that explains a phenomenon.
   * ex. That girl has been checking you out several times, so you hypothesize that she likes you.
2. Perform experiments that **challenge** your hypothesis, meaning you have to say "If X happens, I will concede that my hypothesis is wrong", where X is an event that has a reasonable chance of happening before the universe dies.
   * ex. You bribe her friend so that her friend asks her opinion about you. You say, "If she says I'm dumb/ugly/awkward/unattractive/etc., I will concede that she doesn't like me".
3. If X happened, you reject your hypothesis. If X didn't happen after repeating the experiment multiple times, you tentatively agree that your hypothesis might not be wrong. 
   * ex. If she called you Mr. Poopy McPoopface, you reject your hypothesis. Sorry.
   * ex. If she told her friends that "oh yeah he's pretty good looking" after you bribed multiple friends of hers, you tentatively agree that she might like you.

Political Science has **none** of that. Political Science researchers usually don't make hypotheses or perform experiments, they mostly concern themselves with how things are and how things should be in political systems. Fun rule of thumb, if some field of study has the word "science" as its suffix, you can almost be sure that it's not really science. (Good thing I work in Computer Science...oh wait)

To be fair, it's not their fault. For the vast majority of human history, experimenting with a new form of governance required either violent revolutions or gradual political reforms that took lifetimes to complete, and there's no guarantee that the new leaders won't disrupt or change your experiment for personal gains. Prominent examples are the French Revolution, the Communist Revolution in Russia, and the American Revolution, none of which were anywhere near "peaceful" (the American one, as you may know, was literally a war), and Robespierre and Stalin certainly believed in very different ideals compared to Rousseau and Marx.

It got better after WW2, where corporations started to experiment with new organizational structures, such as [Holocracy](https://en.wikipedia.org/wiki/Holacracy). However, it was still difficult and expensive to do so, and corporations haven't been all that enthusiastic to try out newfangled governance models on a large scale (it doesn't bring in them sweet sweet greens). For the majority of corporations today, traditional share-based systems are still the way to go.

If only, if only there was some way for us to create an organization at almost no cost, incorporate any kind of decision-making system we want, set up a system of incentives, and guarantee that the rules and mechanisms cannot be changed at the whim of a vicious dictator. I mean, it would be so friggin' awesome, right? We would be able to cheaply and consistently perform experiments with governance systems, and make Political Science a real ~~boy~~ science.

Surprise! We already do!

The wondrous invention that I just described is called [Decentralized Autonomous Organization (DAO)](https://en.wikipedia.org/wiki/Decentralized_autonomous_organization). DAOs are virtual organizations where "code is law": their rules and mechanisms are defined by immutable pieces of code ([smart contracts](https://en.wikipedia.org/wiki/Smart_contract)) running on blockchains such as [Ethereum](https://en.wikipedia.org/wiki/Ethereum). How do DAOs satisfy the properties I listed?

1. You can build a DAO with any kind of decision-making system you want: 
   1. traditional ones like democracy, dictatorship, oligarchy
   2. or newfangled ones like liquid democracy and futarchy that haven't been implemented in real governments
   3. or stuff that hasn't been invented yet; the limit is literally your imagination
2. You can build monetary incentive systems into the DAO with a high level of freedom, using scarce crypto-tokens.
   * For example, you can give out token rewards when someone votes in order to incentivize voter turnout
   * You can modify any aspect of the incentive system you want, in any way you want
3. All it takes is writing a couple lines of code.
4. No one can change the code after you've published it onto the blockchain.

Now, with DAOs, you can build six shiny new governance systems before breakfast. 

I hope Political Scientists are thrilled.

## Current Efforts

Now that I've hopefully hyped you up about DAOs, you are probably excited to hear about what amazing progress we have achieved. Well...let me just lay out the good stuff first.

### The Good

* [Aragon](https://aragon.one/), an Ethereum-based platform for building DAOs, has [recently released version 0.5](https://blog.aragon.one/aragon-core-v0-5-the-architect-release-327c7163b89c), which you can start using right now.
* [Augur](https://www.augur.net/), an Ethereum-based decentralized prediction market, is now in beta. [Gnosis](https://gnosis.pm/), another Ethereum-based prediction market, recently launched Gnosis Olympia, an alpha release. Prediction markets are essential to [Futarchy](https://en.wikipedia.org/wiki/Futarchy), a form of governance system where decisions are made based on predictions of how much value an action would bring.
* [Colony](https://colony.io/) is an Ethereum-based platform for building reputation-based DAOs where users collaborate on projects and get paid for it. 
* [DAOStack](https://daostack.io/) is an Ethereum-based platform for building DAOs that employ a new type of governance system--Holographic Consensus--which has two orthogonal types of value: reputation being one and predictive merit being another.

And now, as you might've guessed, the bad stuff.

### The Bad

The majority of existing efforts are focused on turning existing organizations into DAOs, rather than experimenting with radically new governance ideas. And guess what system everyone picked.

That's right, our dear ol' democracy.

Whenever the word "governance" is mentioned in blockchain projects, you can bet that they're using some variation of token-based democracies--systems where you vote to make decisions, and your vote is weighted by how much tokens you own, just like how shareholders of a company use shares to vote and make decisions.

Such systems are bound to be riddled with problems, the most prominent of which is the bribing attack. For example, you promise voters that everyone who votes No on an issue will get X dollars, if at the end of the vote the majority of votes go to Yes. This way, you can influence voters to vote No on an issue, likely without paying a dime, since voters rushing to vote No to get the reward means that the majority of votes is likely to go to No. 

Traditional corporations are somewhat resilient to bribing attacks, due to existing laws and regulations that punish such attacks, but token-based democracies are not regulated in the same way.

You can read more about it in the blog post [Plutocracy Is Still Bad](https://vitalik.ca/general/2018/03/28/plutocracy.html), written by Mr. Vitalik Wonderpants.

---

Of course, I know what many of you nerds are gonna say: But what about the token democracy used in [insert project here], which deals with bribing attacks and [insert attacks here]? What about quadratic voting? Everything you've said is wrong, [insert 5th-gen blockchain here] is going to change the world and kill Ethereum (why not), and I'm gonna close this browser tab without finishing the entire post.

Well, hear me out.

I do not intend to bash the idea of democracy and using democracy to govern DAOs. In fact, I think token-based democracies can be quite useful in certain situations. I'm also not saying that all those variants of token-democracy can't possibly work.

No, what I wish to convey to you all is that we need to start taking things seriously.

If you didn't be a jerk and just skip over everything before "Current Efforts", you'd know that I view DAOs as the key tool to turn Political Science into a real science. Indeed, we are in the process of establishing a new field of research, which demands a paradigm shift in our mindset and our methodology. As all research go, we need to do everything formally, with grown-up math and fancy symbols. We need less whitepapers, and more academic papers; less out-of-thin-air Rube Goldberg systems with only hand-wavy justifications as to why they would work as intended, and more simple systems backed by mathematical proofs and analyses that can be the building blocks of complex systems. We need to stop treating discussions as political debates, and start using formal logic and scientific evidence to convince others of our points. 

This is why I don't think your 5th-gen quantum-resistant blockchain governance system is the way to go: whether it works or not doesn't matter, what does matter is how you got to where you are and how your work fits into the bigger picture. A skyscraper is worthless if it's made of matches, no matter how high it gets. We don't need or want isolated islands of brilliance, we want an interconnected universe of research, where others can extend or adopt your work with minimal effort, thanks to a shared language and a shared philosophy.

---

In the rest of this post, I would like to introduce a new governance system that we at Betoken are currently working on, as well as the relevant formal mathematical analysis we've done, as an example of the kind of governance research we really hope to see more of. While it may not be all that ground-breaking, I hope it can at least inspire some of you to start your own research.

(Yes, this is a shameless plug. You are free to leave now, but y'know, we just spent months working on something that's extremely relevant to the topic at hand for free, which can likely give you some pretty cool and useful insight, so 5 minutes of your time doesn't seem like too much to ask. Plus, you've gone this far, so why not finish it?)

Here goes.

## What Betoken Is

Betoken is a decentralized crypto hedge fund that uses a new governance system we've created called **Incentivized Meritocracy** to make all of the investment decisions.

## Our New Governance System

The basic idea behind our Incentivized Meritocracy is that one's control over decisions is proportional to one's ability to make profitable decisions--one's merit. I'm going to break it down into two parts: its decision-making system, and its incentive system.

### Decision-making

When a manager wants to, say, buy some X tokens for the fund, they would simply stake some Kairo--Betoken's internal token that denotes control/merit--that's proportional to the amount of X tokens to be purchased, after which the fund immediately executes this investment. They can then sell those tokens for the fund at (almost) any time they want, and the amount of Kairo tokens they get back depends on how profitable this investment was, so if the ROI of this investment was +20%, they get 20% more Kairo back; if the ROI was negative, they lose the same proportion of their stake.

It's easy to see how Kairo tokens denote control, since the amount of funds that you can use for investing is directly determined by how much Kairo you own. It's also easy to see how Kairo can denote merit, since you can earn Kairo by making profitable decisions and lose Kairo for losing money.

### Incentives

Every month, a certain proportion (ex. 20%) of profits made in the previous month is distributed to Kairo holders, based on how much Kairo you own. The more good decisions you make, the more Kairo you have, the more income you get.

## Our Research Efforts

We have summarized our research work in [a formal analysis of Incentivized Meritocracy](https://github.com/Betoken/documents/blob/master/Incentivized%20Meritocracies/Incentivized%20Meritocracies.pdf). I know you don't have time to read it, so I'll break it down for you.

* Firstly, we formally defined what an Incentive Meritocracy is, in terms of the conditions it satisfies. 
* Next, we proved that an Incentivized Meritocracy optimizes for its value function, by proving that the partial derivative of the system value function with regard to the individual value functions of all the actors is always positive.
* Then, we appropriated the nomenclature used for describing Reinforcement Learning agents to describe general multi-actor systems.
* After that, we used our new notation to define a particular family of implementations of Incentivized Meritocracy. We then proved that this implementation is indeed an Incentivized Meritocracy by showing that it satisfies all the conditions to be one.
* Finally, we formally described Betoken's governance system, and showed that it belongs to the family of Incentivized Meritocracy implementations we just mentioned.

Seems complicated, I know, but basically we did two things:

1. Defined and used a set of formal nomenclature to precisely describe our governance system.
2. Used formal logic and mathematics to prove that our system will work how we claimed it would.

We believe that doing these two things is essential to establishing a serious field of research into governance systems. We need to use precise language in order to start communicating our ideas properly with each other, and we need to back up our ideas with convincing evidence, whether by using mathematical analyses or by conducting experiments.

We hope that our attempt to formalize our governance system can give you a reference of how it can be done.

## Post Script: Where We're Headed--Inflection Point

Where exactly will governance research lead us?

Before the Internet, most organizations experienced significant decreases in efficiency as they accepted more members. This is caused by the increase in communication degradation and structural complexity. For example, the Athenian direct democracy was only viable due to the small population of citizens with voting rights; as you increase the number of voters, the time it takes to reach a decision inevitably increases, and the effort to educate all voters on the decisions at hand also increases, thus the efficiency of the system suffers a decrease. This is why most modern democracies are delegated democracies, where a small number of delegates make all the decisions.

The introduction of the Internet changed this situation, but not completely. People can now communicate and collaborate much more efficiently, thanks to new tools empowered by the Internet: Slack, Google Docs, GitHub, etc.. However, the value of an organization still increases concavely with regard to the number of members, since the Internet did not fundamentally solve the issue of decreasing efficiency.

What if an organization's value increased convexly, where the additional value of a new member actually increases as the organization has more people?

This will become a reality once we reach the **inflection point** of governance systems. Instead of increasing sub-linearly, an organization's value will increase linearly, quadratically, or even exponentially as the organization gets bigger. Such organizations will be unstoppable once they're created, and I don't think we can predict what kind of ramifications they will have.

That said, we do have a rough idea of how powerful they will be, based on what we have observed in online communities on platforms such as Reddit and Facebook. In such communities, the value of the system increases quadratically due to network effect ([Metcalfe's Law](https://en.wikipedia.org/wiki/Metcalfe's_law)), which is evident in the constant deluge of high quality user-generated content. (visit [r/WritingPrompts](https://reddit.com/r/WritingPrompts) and [r/nosleep](https://reddit.com/r/nosleep) to get a feel of it). After we reach the inflection point, all organizations will be able to employ the power of network effect in a similar fashion, and generate value explosively.

We believe that our research into new governance systems using DAOs and smart contracts will one day bring us past the inflection point, and revolutionize how we as a species organize ourselves.