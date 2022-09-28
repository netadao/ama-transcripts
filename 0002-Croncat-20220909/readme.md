# Fireside chat with CronCat founders on September 9, 2022 (3:00PM PST / 10:00PM UTC).
  - Guests of honor: [Croncat (Trevor)](https://twitter.com/croncats), [Mike Purvis](https://twitter.com/mikedotexe)
  - Additional guests: [ekez](https://twitter.com/ekez___), [Tendermint Timmy](https://twitter.com/TendermintTimmy), [Rarma](https://twitter.com/Rarma_)
  - Host: [Neta DAO](https://twitter.com/neta_dao)
  - Date: Friday September 9, 2022 at 3:00PM PT/10:00PM UTC
  - Duration: 53m. 3:00PM PT/10:00PM UTC - 3:53 PM PT/10:53 PM UTC
  - Transcribed by [envy](https://twitter.com/envy_cosmos)
  - Full recording: https://twitter.com/i/spaces/1mnxeRLDqQqKX

## DISCLAIMER

>Light edits have been made for readability.

## Transcript
(Transcription begins at 9:13 in recording; opening banter has been removed.)

[@Neta_DAO](https://twitter.com/neta_dao)  
So, people, this is being recorded, but I know that Twitter sometimes farts out, so whoever's here gets to hear the good stuff. And if you're not... so what, what am I gonna do? But I just wanted to start by thanking everybody who's here. You're here probably because I reached out to you, or you're in the Neta DAO Discord. It's just very exciting to have Croncat here and to talk about some of the stuff that I got a pre-conversation about earlier. So we have Trevor on the line with Croncat, and Trevor, can you just tell everybody what the heck Croncat is and then riff on that?

[@croncats](https://twitter.com/croncats)  
Yeah, so Croncat is the decentralized automation layer for basically the interchain and as far as we can get it to reach. 
We built it to solve a UX pain point for stuff we were building elsewhere, which is basically like: hey, if your user has to come back at all, why can't that just be something that maybe they could pre-sign for? Or you know, do other things and then alleviate the user from having to remember to come back and do something? Because you know, we all are busy, right? So let's let our decentralized Croncat agents do that work for us.

@Neta_DAO  
So what were you building beforehand that you decided, "Oh crap, I need to build this thing so that will work?"

@croncats  
It actually started like... three years ago? I was building a really dumb game for Ethereum, basically a Crypto Kitty Tamagotchi, and I realized that it was a really cool opportunity to play some game - and then a Tamagotchi needs to die at some point, and it's kind of a terrible user experience to have the user come back and trigger the end of their fun game. So I wanted a cool way to be like, "Alright you're going through, your stats are going up or down, and then oh, this isn't gonna work that well after all." And then a couple more apps that I built, one was called Hobby Hodler, which was like an automated portfolio manager - also on Ethereum - and that one was utilizing basically on-chain aggregations of tiny data, maybe price data or maybe balance data or whatever so that your portfolio could rebalance and do other stuff. It also needed a bunch of timing functions that didn't really exist at the time. Now there's been some newer stuff which is great, but at the time it was like, "Alright, this is the second time I've needed this thing, maybe it's worth pursuing." There have been a couple other apps, specifically ones that need subscriptions or just more of the payment flow automation. Think of things that are like, maybe you want to launch an NFT project at a specific time or maybe you want to drip-launch NFTs, or maybe you want to have a DAO and have payroll - that payroll can just send tokens over a period of time. A lot of these use cases started popping up for us, so finally, just about two years ago, Mike and I decided to really sit down and construct this thing, and we built it in Rust on Near Protocol. I think it was last October we did our mainnet launch after a lot of security reviews, so we've been running in mainnet on Near Protocol for almost a year. Since then, we've learned a *lot* of things. We've learned a lot about what people need it for, attack vectors, that kind of good stuff. So I'll pause there.

@Neta_DAO  
That's a lot of juicy stuff! [laughs] What I heard was that you were on Ethereum, then you were on Near, and now you're gonna be on Cosmos. Can you describe why you're here now and what you're most excited about?

@croncats  
Hands down, IBC, and I guess interchain accounts. I've been stoked about Cosmos for a very long time, but it feels like Cosmos has finally arrived this year. It's been a really fun experience to watch everybody accepting how powerful [IBC] is and the ease of the SDK and a bunch of other things, and really seeing Cosmwasm take off. That's another huge thing that I've been waiting for. A big reason why we chose Rust the last couple of years has been that it's really where the most development has been, to kind of move into the contract language, every chain supporting Rust, that kind of thing.

@Neta_DAO  
So basically what you're building with Croncat is something that could cross chains with IBC and touch other chains. Even though you might be, say, on Osmosis doing something, you could touch something on Juno, touch something on Secret, touch something on ATOM or whatever, and then it would all come back to wherever you told it to go.

@croncats  
Yep. Yeah, we kind of have two layers. Since we're on Osmosis and Juno and potentially others, we can control accounts and functionality across other chains via IBC and interchain accounts. But for some of the more native integrations, we're working with chains individually to provide a more native application. That's one of the reasons why we got a grant from Osmosis, we got some really cool thing that we're gonna ship when we launch on Osmosis. And then similar with other networks in the future, we have some really great things planned that would be a lot more special for each of those chains.

@Neta_DAO  
Can you give everybody an example of the power of what Croncat can do, hopping from chain to chain and doing specific things? Can you just sort of paint a picture of that journey?

@croncats  
Yeah. So if you're familiar, there's something called "if this, then that." It's a way that you can try to achieve some goal, and potentially that goal requires multiple steps and even complicated rules. So we learned a lot doing things the past year: basically that automation is great, but we kind of need to have some extra logic. So, "hey, do I have enough balance? If so, do this." So in the Osmosis world, one of the things that kept coming up was, "I want to dollar-cost average. I'm gonna load 1000 units of something, go buy some other token with maybe a hundred of that every week to dollar-cost average into that asset from one into another." In that sense, that's a pretty easy thing, and then maybe you have a simple rule that's like, "Do I have enough to keep averaging? Yes, do this every day/week." We can get pretty complex. We're building this thing that I'm calling Recipes, which are a stack of complicated tasks that our agents perform for you. So that could be stacking things like, "Hey, I received funds. Any time I receive funds, I want to trade those funds on Osmosis into another token, then send them over IBC and go stake them. Or stake 30% of them and just keep the others around." You can imagine now we're talking about very complicated workflows that either developers or semi-technical people can do. Once those recipes are established, they actually get to be cloneable by any other, potentially non-technical, user. They can see, "Someone was able to do a recipe for a dollar-cost average into some asset, send it over to another chain, and stake it. Well, I want to do that too, so I'm gonna copycat that recipe and now I'm doing that automation as well." So if you're technical enough, we're actually making these recipes earn a royalty fee, so we're gonna encourage people to really dive in with us and expand app support for their apps that they're good at, and make some royalties on the side for helping grow these automations.

@Neta_DAO  
So you said something about agents, and I don't know if everybody understands what agents are. Are you able to quickly sum that up for people?

@croncats  
Yeah. So agents work on behalf of you. They're a tiny little CLI[2] runtime that can be deployed as minimally as a Raspberry Pi or as complicated as your you know AWS, Hetzner, VM whatever alongside some RPC. If you want to get crazy, you can; if you want to just earn some some fees with your Raspberry Pi over time, that's great. We really want to encourage this new world of decentralization with the minimal amount of entry possible. So these little agents are going to basically take care of executing tasks at specific times. They're responsible for [going], "Hey, do I have any tasks right now - yes or no? If so, then assign some some tasks and have them execute on chain." And then some of our more complicated agents can also be for continuing with transactions.

@Neta_DAO  
So that brings up another question. This is just one of the questions we have in our Discord and it comes from a lovely pup. He said - and I'm not gonna speak like a pup, I'm just gonna speak like a normal human - but how does Croncat prevent agents from executing malicious tasks?

@croncats  
Yeah, this is something we thought about a ton and we actually went a little bit farther than probably was necessary, but we abstract the execution and the message away from the agent. So one of the things we we decided from a protocol standpoint was that we want being an agent to be fair. You don't ever know what task you're executing, you just know that you have to do something and you need to do it right now. Or you know that it's gonna happen, so get ready to sign it. All of the agents basically just know, "I need to do something" and then our deployed contracts on chain handle all the rest: everything from what parameters need to get sent - maybe there are different complicated messages that need to stack, that kind of stuff. But it's all on-chain, all provable - even to the point where when we have complex queries that need to run before some transaction could get executed, those queries also have to prove out on chain - even if they're as simple as just returning "true" or as complex as, "Is this person the owner of [x] NFT and are they part of this DAO? If so, then sign a transaction" - that kind of stuff.

@Neta_DAO  
Holy moly. So it's kind of like having little nanobots on chain that run and do your bidding and then come back to you for a treat.

[@mikedotexe](https://twitter.com/mikedotexe)  
If I could say something real quick too: I think maybe a good question that may come up is like, "What happens when there's a task and two or three agents see it and they all try to execute at the same time?" You know one person will succeed, the other two will accidentally burn gas. That was something we *really* kept in mind and that is why the contract is called Croncat Manager. We're keeping track of the tasks in there so that we can say, "Hey agents one, two, and three: you have two block-based tasks and five time-based tasks. Agent four, guess what? It is actually your lucky day and you get the same amount but you get one extra block based task." So people are sort of assigned not to tasks, but to the number of different kinds of tasks that they should call into the Croncat Manager with, for instance, full gas. Then the Croncat Manager can know that they have done their job and do the cross-contract calls to make that thing happen so there isn't a sort of collision and the idea of "first come, first serve." Recently we have been leaning into what happens with "if this, then that," which you could say technically is equivalent of creating tasks that have rules - "Did this DAODAO proposal pass? Is the status successful or passed?" That one is really interesting because we're probably going to start having that one be "first come, first serve." We're going to use governance from the DAO to figure out how we want to do this because that may actually be a little bit different. Another thing I'll mention about the agents is that we really want to work as hard as we can to give agents some sense of reliability. If someone has been waiting to be a Croncat agent for a while and they're all stoked because they got let in, we don't want them to just sit there and have nothing to do. It would not be great if 500 people became agents and there are only 20 tasks. So we actually have this idea of two different queues where you can say, "Hey, I want to be an agent" and you get plopped in the pending agent queue. You can only really join the active agent queue, the queue where the folks are responsible for executing tasks, if there are enough tasks - and that's based on a ratio. We're gonna start off having that be 1:2 or 1:3 or 1:5 - whatever makes sense. This is all configurable in our config for the Croncat Manager. As agents work on items, we get feedback, and we get a sense of how this thing ingests and undulates, then we can ask, "Alright, is this working out? Should we increase that? Should be tweak the parameters?" So we're kind of looking after the agents in the beginning, but we will be looking for feedback to see how it goes and tweak the config params accordingly.

@Neta_DAO  
So I guess that brings the next question: can community members run agents? How do they get started? Can anybody be an agent?

@croncats  
Yeah, everybody can be an agent. We want to have so many tasks that everybody can start earning their favorite token for being an agent. Your entry level could be playing around with crypto or earning a substantial income maybe - we'll see how we grow.

@Neta_DAO  
Wait a second, your favorite token? How does that work?

@croncats  
So if [the agent is] deployed on multiple chains, [you could receive a portion] of the fees. You can be an agent on Juno, on Osmosis, or maybe just an agent on all the chains. It's more about: are you running the agent and registered with the manager for that chain? So if you want to earn, say, Juno - just run an agent for Juno and then maybe down the line we'll be able to do some sort of fun things to help you get different tokens. But basically, we will need agents for every chain that we support. That agent list is not blocked by a whitelist or anything like that. It's really open-ended, based off of "first come, first serve," and the more recipes and tasks that come in, the more agents we can support.

@Neta_DAO  
Wow, okay. So let me give you a hypothetical recipe that I want to make just for myself: say there was a DAO and that DAO needed to pay people. Inside of their agreement with the people they need to pay, this person needs to have a specific token for their thing and I said, "Well damn, you're just like one person - how do I set this up and automate it?" So I would go to Croncat, somehow connect it to the DAO that I've been working with, and then tell it the address to pay, the time to pay, and the amount to pay and then just sort of set it and forget it - that would just work as long as the Croncat wallet is filled up?

@croncats  
Ooh, nice, I like this one. So you're actually piggy backing on one of the things we're gonna be watching in a couple weeks, so we can talk about that more. So you have a DAO and it's actually really annoying to have your users come back and distribute payroll weekly, so why not do a recurring payment? In this case, the only thing that you need to do then is add a swap as part of this task - the payment going to a swap before sending to the user. You could actually let the user - as part of the proposal or configuration in this recipe - figure out the token that you want to distribute and then maybe you have sort of the dollar cost average mindset: it's gonna distribute some amount of tokens, so swap them and then send to the recipient.

@Neta_DAO  
After I set it up - oh, go ahead Mike.

@mikedotexe  
I was gonna say, I think Trevror's speaking to the robust way to do it. We actually saw just today the Croncat team fully do this exact scenario you mentioned. We can have bank messages where you can say, "Pay this person or these three people one testnet Juno every five minutes, or every day, or every Sunday at noon - and that totally works. In that case, what you would do - and this is sort of the simplest case - is say "give ten Juno to the Croncat manager." The Croncat manager remembers that you gave that amount and will be slowly ticking down that amount as it gets paid out. At some point since it's presumably recurring - let's say every Sunday at noon - then it will determine whether it is below the threshold of paying out and will basically stop being recurring once it is no longer able to afford that and will reimburse the person who created the task the remainder of the amount.

@Neta_DAO  
Ok, so that has to do with payment because - do you want to speak to that? I mean, are DAOs asking for this type of thing?

[@ekez___](https://twitter.com/ekez___)  
Yeah, I think I think DAOs definitely want payroll. The way you'd normally do this is with some sort of auto compounding payroll or a payroll that would vest every 6 seconds, but there's probably a fair number of people that don't want to visit the website and collect their payroll every once in a while. They want it to magically show up in their wallet. So yeah, Croncat would be good for that.

@mikedotexe  
Yeah, I think DAODAO has a draft pull request that is actually for some sort of payroll smart contract, which kind of works like an escrow. In that case, your smart contract can be the one that is holding the funds that are getting doled out and Croncat gets even simpler. You just say "every Sunday at noon, call this one function on this one smart contract" and then: the end. You don't have to worry about using bank messages. That is if you have a rock solid payroll contract you want to call.

@ekez___  
I think RAW DAO already uses Croncat.

@croncats  
Yep, that's true. If you're getting rewards on RAW, it's from Croncat. We're doing the distribution of rewards today. 

@Neta_DAO  
Are you able to say how that works, like the recipe? 

@croncats  
Yeah, it's a really basic recipe. It's just a Wasm message instead of a recipe, a Wasm message that gets executed every 30 minutes.

@Neta_DAO  
Oh. Well that's... that was easy. [laughs]

@croncats  
Yeah. We can do the super straightforward simple stuff and then beyond that we're really just trying to be an open protocol for anything. Pupmos asked, "Are arbitrary Wasm message types allowed?" - I'm not doing the voice, sorry - "is it limited to transfers initially?" We're gonna launch with two message types: alpha and beta. The first one will be the bank message type, the second one will be Wasm message type. We will fully support everything else: the full breadth of staking, IBC, and other message types, but those two we're gonna start with initially and they're gonna be slightly sandboxed. We're planning to fully support all of those standard message types.

@Neta_DAO  
Yeah, I don't know if Pup's gonna get sneaky or something, trying to do... whatever. Let me put one more example of a more complicated thing that I'd like to do. Say a DAO runs a validator and in that validator they have some reporting mechanism. Could we set up Croncat to look at our validator, see the commission that validator is earning, and when it hits a certain amount, shoot a message over to Howl and post it on Howl? Can Croncat do something like that?

@mikedotexe  
That sounds like off-chain stuff to me. I'm not positive to be honest, but I did write most of Starrybot which is the token gating bot and we did a lot of stuff like that: seeing how many native tokens you have staked versus unbonding versus liquid and stuff. If I recall, that was the REST API where you get the validator information so I think Croncat's mostly for on chain actions. I could be wrong but it feels like like that scenario may involve gathering stuff from from off-chain places.

@Neta_DAO  
Oh, ok, so maybe I screwed up by saying "validator monitor." Maybe it's some sort of on-chain thing and then we tell Croncat to look at that thing. Maybe the validator commission comes in on-chain to the DAO - that would be an on-chain message, so we say "Croncat, look at that thing and when it happens, send a message over to Howl on their chain and post a message for everybody to see that something happened."

@croncats  
Yeah. I'm gonna say this kind of carefully because things may or may not be in the works. For things that are just message over GRPC or indexer style messages where you're just watching for blocks, Croncat doesn't support that out the gate. Instead, the idea is that it could have a contract deployed on chain that checks those variables. Maybe it checks if a custom message was posted or some data or state is available now and it responds with a boolean to Croncat - that's when it can be utilized. The rules are complicated now, but we have a new way to standardize how we can check data on chain. Everything we want to do should be provable on chain; we don't want to arbitrarily call something and the funds drain out of the task immediately. If you wanted to check the value of some state and then post to Howl, you can totally do that. Another really cool thing you can do is based off of things that happen in other contracts: let's say the balance fluctuates or maybe the staked balance fluctuates. You could trigger state changes from those rules.

@ekez___  
So can we do liquidations with Croncat?

@croncats  
As long as you're not expecting much, yeah. [laughs]

@Neta_DAO  
Hey, I think Timmy has a question.

[@TendermintTimmy](https://twitter.com/TendermintTimmy)  
Yeah, unfortunately I have to run in a second here so I just wanted to shout out real quick before I leave that I don't think I've ever wanted a weekend to go quicker. I'm so excited for our chat on Monday, Croncat, because listening to you guys chat here... we are incredibly aligned and I think some of the stuff we're working on and your guys' infrastructure will be a fantastic synergy. I've got to head out but I just wanted to shout out that every word out of your mouth has impressed me today and hopefully (I'd assume) the audience agrees. Really, just awesome stuff, I can't commend you guys enough.

@croncats  
Sweet, thanks a lot.

@Neta_DAO  
Thank you for joining.

@TendermintTimmy  
Have a good evening everyone and enjoy your weekend.

@ekez___  
Thanks Timmy!

@Neta_DAO  
Get outta here. [laughs] Okay, so when can we use this? When is this going to be available? When can I touch it?

@croncats  
I mean, if you can time travel! We're going to be launching and having our alpha version ready for Cosmoverse, so those of you that will be at Cosmoverse: we'll be there as well. We're hoping to ship four really cool use cases. The first one's going to be dollar cost averaging on Osmosis, which I'm really excited about. I've wanted to do this for years. Second one is going to be that payroll idea - we're gonna help out some DAODAO folks and ship the payroll setup. The other two are kind of interesting: one of them's token swaps and then the last one is a custom message. If you're pretty technical and know what you want to do, you can get your hands dirty and do custom Wasm calls however you want - that one's going to be a little bit tough on the user experience in the short term. Beyond that, we have some epic plans. If you want to be part of our awesome user experience UI review board, we've been doing three different reviews and we're working on the fourth one now. Doing this "if this, then that" future of Cosmos messages is really complicated, so feedback is really welcome from the community.

@Neta_DAO  
Awesome. We've got a couple people requesting to speak. Kobos, let's bring you up here real quick. And then Rarma wanted to ask a question, but Kobos you go first. [no answer] Or, Rarma, if you've got your question ready to go.

[@Rarma_](https://twitter.com/Rarma_)  
Alright, I'm in. If you give me the opportunity, I'm going to jump in. Firstly: crazy cats, I'm so excited for this. I've been waiting for so long, I'm so pumped. I think when I spoke to you a few months ago I think originally it was just gonna be the payroll idea and I was like, "That's sick, but let me get my hands on it" and now you guys are giving us some DCA, I love that. The custom message has got me absolutely pumped - I don't know if you can tell from my voice, it's like 8:30 in the morning here but you just elevated me to another level. I'm pumped.

@croncats  
Is it pre-coffee?

@Rarma_  
I had one, I'm working on the second. The kid's just having a bath at the moment so I'm just listening in, but yeah, I'm super excited for this. The custom message part just got me absolutely amped. From a use case perspective, I'm assuming that people can just write the the contract initiation and then Tweet it like, "Hey, if you want to do X, here is a command you could do." Are you looking to have a repository of commands that people can leverage off?

@croncats  
We don't have a lot that we can share yet, but the idea is to have a public registry, almost like a TCR that holds recipes. The way that the royalties are gonna work is that these recipes are going to be a collection of tasks with query rules in them. Basically it's a self-defining set of tasks that can be packaged in a unique way - "unique" being the key part here for distributing royalties to the original owner. Those will be in a registry format that can be indexed by anybody, that can be easily displayed by our website or really anywhere, and then those can be spun up in whatever wallet you're used to. We're really aiming towards a "mobile first" experience. That kind of encapsulates the vision, I guess.

@ekez___  
So can we... this is making me think, I'm scheming a little bit here. You know, DAODAO's got actions, we've got little things that you can put on proposals.
Can we use your things and use our things and maybe when this repo's open, we share?

@croncats  
We talked about doing two PRs for DAODAO today.

@ekez___  
Yes!

@croncats  
The first one is going to be a payroll action type for DAODAO and then we want to set up a check box that says something like, "automatically execute when proposal passes." And then I would like to do something with DAODAO following our new recipes spec. Imagine we ship an NFT that holds the definitions of the task messages, the rule messages, and also has the types that are needed for those. So we can basically generate any kind of UI we need for these automations and then yeah, off to the races.

@Neta_DAO  
Holy shit. Zeke, can you package Croncat with pre-vetted recipes so when anybody spins up a DAO, they get this package of commands with Croncat that allows them to basically supercharge their DAO?

@croncats  
Yeah, we're hoping that. We're gonna ship the alpha version here in a couple weeks that will be the "pre-vetted recipes," let's call them. Then we're gonna have the open spec available that DAODAO can say, "OK, we support Croncat actions or Croncat recipes," and maybe it's a category of actions that DAOs can use. The only difference is that they start from a proposal and then submit a new recipe to the Croncat management.

@Rarma_  
That's so sick. Just very quickly if I can, @ekez___, I know DAODAO is your topic - I'm going to jump in and be like I know CryptoTank has his Maneki Cosmos thing. The idea of their DAO is to be an investment DAO type thing. That's a perfect example of where the DAO can just initiate a proposal to spend X amount of dollars on X token and then have Croncat do that. That's going to revolutionize that entire philosophy of what that DAO is for. It's perfect.

@croncats  
If I could push you further, this is one thing I've wanted for a long time especially from portfolio automation: think of it more like how an index 
runs, think of your values, and maybe portfolio ratios can be curated 
by your DAO and then run with Croncat.

@Rarma_  
Ooh. Okay, that's really sick.

@ekez___  
I'm kind of thinking that there's no reason- right now we've done a lot of work in DAODAO to make our actions really generic and easy to add, they're really like this separate package. I'm thinking that there are probably some technical differences, but I don't really see much of a reason to want our DAODAO actions 
to be separate from the Croncat ones. If you guys have a repo where you're putting together a bunch of actions for things to do on Cosmos chains, in my opinion we should be sharing [our actions] with you guys and maintaining it with you.

@croncats  
The way that DAODAO was thinking about handling code ID and code registries, that's how I'm thinking about registries. I think there's a lot to align there.

@ekez___  
Yeah, this is sick. Right now we're really really busy - we've got really cool things coming, I'm not sleeping that much, we're really working hard right now - but once we're done I think this would be a cool thing to look at.

@Neta_DAO  
This feels like spontaneous alpha, is that right? Am I using it right?

@ekez___  
[laughs] Yeah, no promises. DAODAO has, at all times, approximately 20 million things to do and there's not 20 million of us

@Neta_DAO  
Well there could be if you had little bots!

@ekez___  
If we had infinite money.

@Rarma_  
I just have one more example I wanted to talk about and this would probably fall to the custom contract execution. JunoSwap's got a bunch of contracts at the moment, an example is like the Racoon gambling stuff. I'm full degen, so my pitch to initiate that contract would be like, "buy a lottery ticket every day after I claim my rewards" or "roll the dice once a day with X percentage" as an example. But then other contracts, I know that there's like an arb contract currently on JunoSwap that not many people know about. Like b-

@ekez___  
There's an arbitrage contract? What?!

@Rarma_  
...People know about it now! [laughs] Someone developed it and they very infrequently run it but it sits there and it's pretty successful. It just 
runs and then it must meet certain parameters or a threshold and it just executes the swap they've turned it from a couple of Juno into a couple hundred Juno. So just being able to initiate his contract and be like... you know.

@ekez___  
Rarma, you're an on-chain god, dude. Wait, you just found this on chain and just reinstantiated it yourself? Dude, this is so sick.

@Rarma_  
Well I haven't really instantiated it myself but I found it. I'm not smart enough to do that part. I talk to @Reecepbcups_ quite a lot and he's like a dev god in my eyes, so I'm thinking I'll just go, "Hey Reese, I know that you're full degen, you know how to do shit, can you write me a Croncat instantiate contract" and he'll be like, "Sure!" So my plan is to be full degen with this, try and get some help because I'm not a dev, to be like, "here is a template you can use, change these parameters." I'll be trying to tweet about it, I'll get you guys to put in the repository. But super sick man, I love the idea. 

@ekez___  
I cannot believe there's an arbitrage contract.

@croncats  
I want to caution you slightly just because when you do that kind of thing, the tasks are pretty transparent - people can see the configuration of every message. We've actually gotten a lot of feedback, but maybe we need to consider shielded tasks because if you're gonna do arb or something like that, people are gonna probably try to race ahead of you or MEV, you know?

@Neta_DAO  
Yeah, that was my next question: recipes or gated recipes. My first thought is what if you're part of the DAO and you create these recipes that use code 
that you've written or things that you've written that only people in your 
DAO could use it. But if you run the recipe, then everybody could see what you're doing, right?

@croncats  
Yep. So there's been a lot of good feedback on that and I will just stub it here that we're not gonna talk about it anymore but that is definitely something that we're gonna have in the future. [laughs]

@Neta_DAO  
Okay. Anybody else have any questions? Raise your hand to come up and talk or write them in the Discord for us to see. So we got the degen idea going with Rarma - Mike, were you gonna say something?

@mikedotexe  
I was gonna say that the Croncat DMs are open too in case someone thinks of something afterwards.

@Neta_DAO  
Yeah. We got the degen, we got the DAO side of it. Pupmos is asking questions in the Discord - I don't know if I wanna publicly talk about those questions, but I do think we probably should just ask this one: how do you respond to the recent allegations that cats are actually pointy dogs?

@croncats  
I think we actually need to talk to Mike about his local representative.  

@mikedotexe  
Yeah, my dog has a pointy mohawk and that's the only pointy thing that matters on animals.

@Neta_DAO  
[laughs] That's great. Ok, so you said you're gonna be announcing basically your alpha at Cosmoverse which is September 24?

@croncats  
We're announcing it now!

@Neta_DAO  
Oh, you're announcing it now, right here! Oh, sweet! But people will be able to use it at Cosmoverse?

@croncats  
Yeah, that was the alpha. We're gonna launch a day or two before. We're 
gonna have alpha ready, the four features of DCA, payroll, token swaps, and custom messages. If you're around in Cosmoverse, come hit us up and we'll show you how to do it. If you're not, if you're somewhere else in the globe, all good. We're gonna take feedback after that so would love to have people start using it.

@mikedotexe  
In the beginning we're gonna have two testnet and two mainnet nodes that are running on our infrastructure just so people don't have to worry about that, but of course we want to progressively decentralize. Hopefully that'll be easy to get people started on it.

@Neta_DAO  
Will they just go to Croncat's website to try it?

@croncats  
Yeah. It's not live yet but it's going to be alpha.cron.cat and when it's ready, we'll share it.

@Neta_DAO  
Oh this is lovely, I'm very excited.

@Rarma_  
I'm just gonna step down. Thank you so much guys, I'm super pumped. Keep up the good work, you guys are revolutionizing the way in which I operate within the space and and certainly more people. So I just wanted to jump up, ask a couple of questions, and sayyou'd say thanks heaps and keep it up.

@Neta_DAO  
Awesome. Thank you for joining, Rarma, we appreciate you.

@croncats  
Yeah, thanks.

@Neta_DAO  
Okay so we've got a bunch of juicy thing that have happened. It got DAODAO even thinking about stuff that they weren't thinking about before, Pupmos asked some very juicy questions. Is there anything else that anybody else wants to ask? If so, raise your hand or shout it in the Discord. If not, I think we're gonna call it. Guys, thank you for taking the time to meet with us. Such a small but impactful group. We really appreciate you as Neta DAO and everybody here for joining us. And you can always reach out to them in their Discord the Croncat Discord or ping them in the Neta DAO Discord or Twitter DM's if you has questions. But thank you for joining.

@croncats  
Yeah, thank you. Appreciate setting it up and hopefully see you guys all soon. 

@Neta_DAO  
Awesome, have a great day. 

@ekez___  
Cheers.

@mikedotexe  
Thank y'all.
