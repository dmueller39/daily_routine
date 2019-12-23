# NBack

**warning** these notes are messy and incomplete

## How it helps me

- Capacity + performance
  - Overall I've found that training with NBack correlates with better performance at work, and better ideas and thinking overall. This is very difficult to quantify for me individually. At a larger level I believe that the [research](https://releases.jhu.edu/2017/10/17/johns-hopkins-finds-training-exercise-that-boosts-brain-power/) points to the likelihood that this is actually a real effect.
- Dealing with context switching
  - There are a few issues with changing or starting a task difficult. I believe that the mental effort of unloading your current active memory set and loading a new active memory set is part of this. Because this is a difficult process people tend to want to avoid it if at all possible. I believe that NBack actually strengthens the part of my brain that does the work of loading and unloading a context. I believe this has resulted in less anxiety and avoidance when I need to switch to some new piece of work.
- Panic Attacks
  - I have found that it may help when dealing with panic attack situations (emphasis on may)
  - There are some requirements for it to work:
    - You need to have enough mental energy to complete multiple rounds of the exercise. If you are mentally exhausted (like after a day of work) this is going to be difficult.
    - You should probably target a level where you know you can probably get a few rounds with perfect scores. I typically get a small nudge of anxiety when I miss more than one answer in a round. It may require some warm up rounds until you get to performing well.
  - Here are some of my hypothesis as to why this works:
    - Because you are exercising your working memory, you need to actively forget the things that might be triggering your anxiety. As a metaphor, if your problems are something you carry in your hands, then its tough to hold on to them if you are lifting weights.
    - [Tim Ferris](https://tim.blog/2015/10/17/5-tools-i-use-for-faster-and-better-sleep/) talks about Visual overwriting, which is why he plays tetris before he goes to bed. This *may* be similar to the process here.
    - A panic attack may be like a cramp, where your muscle is locked in place and causing you a lot of pain. Instead its your brain locked in place and causing you a lot of pain. Working on a memory game like NBack might be similar to "walking it off" (a common remedy for a cramp). If you use your brain in the right way, you loosen it up and allow it to function easily again.

## Building my own app

- I was frustrated with the existing apps on the market.
  - There was a wide selection, and the feature set that I wanted was spread among 3-4.
  - The level progression was discouraging. I found certain difficulty jumps too big and that made me stop training.
- I started with the assumption that I would build something that was super customizable that anyone could tinker with and get any level of customization they needed. I've landed on a version that is much less custom, but is much more fine grained when it comes to difficulty level.

## Release

- At the moment it is in a state that is acceptable to me, but likely unacceptable to others. I don't have a ton of motivation to release it for others (it solves my problems after all) but I am spending some effort polishing it for general release.
- A non release copy is available here if you install the Expo app: https://expo.io/@dmueller39/custom-nback. Quick explanation of what you'll see: The difficulty starts lowest at the top, and gets progressively harder as you go down. Levels are meant to be skipped. The last three games are represented in the circles as green (perfect score) yellow (1 mistake or more). If you get 3 greens you should probably go to a harder level.