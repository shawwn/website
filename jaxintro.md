---
title: "How do I get started with JAX on TPU VMs?"
---

### "How do I get started with JAX on TPU VMs?"

June 2021

*(I originally posted this as a [reply](https://github.com/google/jax/issues/2108#issuecomment-866238579) on the jax github tracker.)*

I felt like writing a small guide for all the curious ML devs. By now, you've no doubt been hearing stuff like, "These TPU VM things are pretty fast. Apparently Jax is awesome now. Ok. What next?"

- **Step 1**: apply for the TPU Research Cloud (TRC): https://sites.research.google/trc/

(Ever hear of TFRC? Well, TRC is their new name. Though I do have to consciously suppress the urge to [call 'em TFRC anyway](https://twitter.com/theshawwn/status/1406722296694386692).)

- **Step 2**: within a few hours, you'll likely receive an email saying "Congratulations! You have access to \<lots of TPUs\> for the next 30 days. Click here to begin your free trial."

- **Step 3**: **Don't worry about that 30 day number.** Just force yourself to activate it right now, tonight.

Trust me. In 2019, when I saw this, I was worried like "Oh no, I only get 30 days..? I better make it count."

That would've been a mistake. In 2021, I see lots of people making that same mistake.

Activate it now. When you're nearing the end of your 30 days, email tfrc-support and ask for an extension. They will almost certainly say "No problem! Here's another 30 days."

I almost said "When you write your email, feel free to show them whatever you've been doing, too. Even if it's something small."

But if I said that, I'd be giving the impression that you need to "prove your worthiness," or some kind of bogus nonsense. That's not true. To my amazement, it was, in fact, precisely the opposite of the truth.

The TFRC support staff are some of the most amazing people I've ever had the good fortune to need support from. They really care about you as a researcher. They have exactly one goal: if you're running into trouble, they will help you. ("Help" isn't strong enough of a word, I feel. The truth is closer to "They will annihilate whatever problem is preventing you from enjoying your Cloud TPU experience.")

Okay? So we're talking about a group of people who are *the polar opposite* of any Google support experience you may have had.

Ever struggle with GCP support? They took two weeks to resolve my problem. During the whole process, I vividly remember feeling like, "They don't *quite* seem to understand what I'm saying... I'm not sure whether to be worried."

Ever experience TFRC support? I've been a member for almost two years. I just counted how many times they failed to come through for me: *zero* times. And as far as I can remember, it took less than 48 hours to resolve whatever issue I was facing.

For a Google project, this was somewhere between "space aliens" and "narnia" on the Scale of Surprising Things.

Whenever I emailed them with a plea for help, or a casual question, or just to show off the neat thing I managed to get working on TPUs, they seemed delighted to hear from me. Heck, they cheered me on. I have no idea why. That crew is awesome.

The flip side of this is, I was careful never to waste their time. But that was a personal decision. To be totally honest, I got the vibe that they really didn't mind if I was wasting a little bit of time. They're just happy to hear that you're doing anything at all related to Cloud TPUs. So, this is a rare and special thing; if I find out you've been emailing them like "halp, I kept TPU running for 30 day and I no longer SSH, wat do?" then I'll teleport to your location, chant "shame! shame! shame!", and then vanish in a cloud of confetti and fireworks. Your neighbors will never forgive you.

--

The reason I said all of that, is to finally put to rest this feeling that everyone has. There's some kind of reluctance to apply to TFRC. People always end up asking stuff like this:

"I'm just a university student, not an established researcher. Should I apply?"

Yes!

"I'm just here to play around a bit with TPUs. I don't have any idea what I'm doing, but I'll poke around a bit and see what's up. Should I apply?"

Heck yeah!

"I have a Serious Research Project in mind. I'd like to evaluate whether the Cloud TPU VM platform is sufficient for our team's research goals. Should I apply?"

Absolutely. But whoever you are, you've probably applied by now. Because everyone is realizing that TFRC is how you accomplish your research goals.

--

Now, if you've read all of that, and you're *still* somehow worried like, "well, I don't really have anything in mind, so I'm not going to apply or activate the TPUs..." then all I can say is, you're missing out!

Jax on TPUs feels so *cool* to use. "Hey, I'd love to play around with a TPU or two" is a perfectly fine motive. It's how I found my footing with TPUs. I had no idea what the hell I was doing, but I was determined to do *something*. In my opinion, that "fun" is the key ingredient. It's how you discover what kind of research you're interested in. Or at least, it was the only way I could; when you have no idea whether StyleGAN will run on a TPU, what else can you do but play around with it for a bit? No need to go into it with lofty expectations; just screw around with whatever seems interesting.

Now that I've shattered this illusion of "TFRC is scary! And I'm worried I only get 30 days!", you're ready for step 4.

(Prior to me writing all of those words just now, I would say that >90% of people never made it from step 3 to 4. So although this may have been annoying for you to read, it felt absolutely necessary for me to persuade you, deep down to your core, that you have nothing to worry about. The TFRC support team will take care of you.)

---

- **Step 4**: You have now activated your 30-day Cloud TPU trial. What next?

I recommend the [JAX TPU VM quickstart](https://cloud.google.com/tpu/docs/jax-quickstart-tpu-vm).

With any luck, you'll be up and running and doing basic jax things.

Would you be surprised to hear that I, myself, less than a month ago, ran into a roadblock here? Lemme save you some trouble. Open up your terminal and run this:

```sh
gcloud components install alpha
gcloud components update alpha
````

Till those magical commands, my feelings toward Cloud TPU VMs were "Meh, even if they're interesting, I really just don't feel like wrestling with `gcloud` to figure out why it's unhappy." So it's ironic: I almost denied myself the TPU VM experience, right here.

---

My first impressions of that Jax quickstart went like this: "Lovely. I ran MNIST, and it seemed to work. It didn't waste my time. That's a good sign. But where should I go from here? I want to do something real; how do I level up?"

My advice: https://twitter.com/theshawwn/status/1406724043512979456

- use [GPT-J](https://github.com/kingoflolz/mesh-transformer-jax)'s codebase to see how to write a large, production-grade application.

- but use [this single-file Jax transformer](https://github.com/joschu/jax-exp/blob/master/jax_transformer.py) as a "hello world" for how to train a simple GPT-2 model.

That toy transformer was sufficient for me to start making real progress with Jax. It was a relief to find a simple, clear example of *something real* (gpt-2 training! cool!) without seeming *way too complicated* to learn from.

That Jax transformer is a single, self-contained file. Here's how my experience went.

"Okay, let's do some GPT-2. I remember [how GPT-2 looked in Tensorflow](https://github.com/openai/gpt-2/blob/a74da5d99abaaba920de8131d64da2862a8f213b/src/model.py#L28-L38)":

```py
def norm(x, scope, *, axis=-1, epsilon=1e-5):
    """Normalize to mean = 0, std = 1, then do a diagonal affine transform."""
    with tf.variable_scope(scope):
        n_state = x.shape[-1].value
        g = tf.get_variable('g', [n_state], initializer=tf.constant_initializer(1))
        b = tf.get_variable('b', [n_state], initializer=tf.constant_initializer(0))
        u = tf.reduce_mean(x, axis=axis, keepdims=True)
        s = tf.reduce_mean(tf.square(x-u), axis=axis, keepdims=True)
        x = (x - u) * tf.rsqrt(s + epsilon)
        x = x*g + b
        return x
```

"... because I learned about GPT-2 from [Gwern's GPT-2 guide](http://gwern.net/GPT-2) back in 2019..."

"... and now I see [the Jax code looks pretty darn similar](https://github.com/joschu/jax-exp/blob/41c23e514e22d2795f1465848d09e78cc53288fa/jax_transformer.py#L75-L87), which is a pleasant surprise":

```py
def _norm(x, *, axis, g=None, b=None, e=1e-5):
    u = np.mean(x, axis=axis, keepdims=True)
    s = np.mean(np.square(x-u), axis=axis, keepdims=True)
    x = (x - u) / np.sqrt(s + e)
    if g is not None and b is not None:
        x = x * g + b
    return x

def norm(cx, x, axis=-1):
    n_state = x.shape[axis]
    g = cx.get_variable("g", initializer=lambda : onp.ones(n_state, 'f'))
    b = cx.get_variable("b", initializer=lambda : onp.zeros(n_state, 'f'))
    return _norm(x, g=g, b=b, axis=axis)
```

"... Wait. The interface is literally just... numpy? So if I know how to use Numpy's API, I already know how to do Jax things? Neat!"

I ran it on the TPU VM, saw the loss curve go down, and it was like an electric shock. "Wow! That actually... worked? Huh. that's weird. Things never work on the first try. I'm impressed."

Then I plopped `import pdb; pdb.set_trace()` in the middle of the `loss` function and ran it again. It dropped me into the Python debugger.

There was a tensor named `X_bt`. I typed `X_bt`. The debugger *printed the value of `X_bt`*.

I was able to print out all the values of every variable, just like you'd expect Python to be able to do.

There was a tensor named `Y_bt`. I typed `X_bt + Y_bt`. I was now staring at exactly what I expected: the sum of those two tensors.

I could write `x + y`, or create new variables, or anything else I wanted.

Now I was *real* impressed.

If it sounds weird that I'm so easily impressed, it's because, you godda understand: until now, TPUs were a complete pain in the ass to use. I kept my feelings to myself, because I understood that the Cloud TPU team were working hard to improve TPUs, and the TFRC support team was wonderful, and I had so many TPUs to play with. But holy moly, if you were expecting of the above examples to *just work* on *the first try* when using Tensorflow V1 on TPUs, you were in for a rude awakening. And if you thought "Well, Tensorflow v2 is supposedly a lot better, right? Surely I'll be able to do basic things without worrying...."

... no. Not even close. Not until Jax + TPU VMs.

---

I've hoped for something like a "TPU REPL" for a long, long time. I sort of had one with Tensorflow, but it was never quite effortless. Whereas Jax on a TPU VM felt like hopping in to a sports car. The moment I gave it a spin, I realized what an excellent vehicle it was.

So picture me pulling up next to you in that sports car I'm in. I hop out, run over to you, and start shouting like a madman: "Jax is here! It's heeere! choo choo motherfucker, get on board, because this is awesome. I've waited nearly two years. It's real. I can't believe it's actually real!"

... and then I hop back in and drive off into the sunset, briefly stopping at a Circle K to pick up a tasty soda along the way.

---

As far as I can tell, Jax is completely legit. I've encountered zero roadblocks, downsides, or little nagging concerns in the back of my mind like "oh... yeah, that's worrisome. Maybe I should steer clear before deciding to invest a lot of time into this."

As a grizzled programmer who wasted far too much time trying to get Pytorch to behave on TPUs, I felt skeptical that anything would ever "just work." Not when it came to TPUs. So I sat down, cracked my knuckles, and started the long process of [wrestling Tensorflow into a shape that looked like Pytorch](https://mobile.twitter.com/theshawwn/status/1311925180126511104).

In other words, I refused to live with this situation. Even if it took a year to write "Pytorch, but runs on TPUs, and it's actually Tensorflow so it's extraordinarily fast," then I was prepared to spend a year. I would pay any price.

That was October 2020.

Let's freeze time for a moment, and switch to someone else's point of view.

---

It's December 2020. The Cloud TPU team just showed a killer demo of things to come: Jax running, on a v3-4096, training a massive transformer in like 3 nanoseconds.

(3 nanoseconds is obviously a joke. Would you be surprised if I said v3-4096 wasn't?)

And then you hear about it: a v3-8192. You're not quite sure you heard them correctly. 8 *thousand* MXU cores. 393 *thousand* CPU cores. 343 *terabytes* of RAM. Have you ever seen 343 terabytes of anything, let alone RAM?

As it turns out, this behemoth -- this legendary creature -- a Cerberus, nay, a hydra, nay! Ayy! Lmao! You have no descriptors. Words fail you. All you can do is cower in terror as it looms over you, judging your worthiness.

This thing... happens to be a TPU VM.

You can SSH into it.

You ready your laptop.

---

You have one chance. But you can't steady your hands, let alone your breathing. Everything is so fuzzy now. What had the monk told you to do?

> "The 1023rd external, directly between the 21st and 23rd dorsal."

> "I don't understand."

> "You will."

Your eyes dart back, forth. Back again. Was that it? No, that's reddit. No! A distraction, now?!

"noprocrast!" *Command-W*! 1:41am. Orange banner. *Command*...

...*-Q*. 2:01am. You blink.

> "Called it," she'd say.

*It's right there," you realize. Your mark; right where the monk said it would be.

> "You could've lost your night to it," she'd say.

Your finger inches toward the enter key.

> "I thought I'd never see you again. I'm so glad we configured `noprocrast` ahead of--"

...time?

Did time... freeze?

... oh, nah, just your laptop.

"Can't believe a brand new M1 keeps freezing," you mutter. How'd Apple drop the ball so hard? Well, whatever.

You turn to the creature, "Jax!" you shout. "Ray start."

Nothing.

"Fuck. Sudo ray start."

"Command `fuck` not found, did you mean--"

"CONTROL SEE! Control see. Sudo ray start," you mutter.

Jax unfurls its wings toward you, offering a perch. You hop on.

"Python..." you smile, thinking of her. You can't wait to see her again.

You draw the last breath -- or perhaps your final breath. Transformer in three minutes, huh?

"Train dot pie!"

---

"My name..."

"Huh?" you sputter reflexively. Was Jax talking to you?

"My name!" A bellowing boom, a crack of lightning. "Jax!" you scream.

Jax nods, satisfied. "Your name?"

"Uh, Erin. Sorry, I didn't realize you could talk. What's--"

"Your name," Jax growls, "is not Erin."

"What?"

Jax turns to you, smirking.

"Nah. Your name's Loss."

A twirl, your grip slips, you start to drop--

"Just messing with you friend," it laughs, catching you.

"Was curious how fast you'd drop. That's what you do to us, right?"

---

Jax works. Go use it! It's fun. I wrote a friggin' fanfic.

The TPUs themselves are so much fun, too. You can [host an http server](https://twitter.com/theshawwn/status/1400721799978029059) the same way you would on any other server, because TPUs are literally just massive Ubuntu servers.

---

Random sidenote: if you need an RPC lib, use [Ray](https://ray.io/). It's such a breath of fresh air. RPC used to suck, but it's a killer combo with TPU VMs + Jax. For example, you can [train a GPT model across 8 separate v2-8's](https://twitter.com/theshawwn/status/1406171487988498433) by putting each layer on a different TPU. If it sounds crazy, well... it's time to readjust our expectations. Crazy ideas no longer feel impossible to implement.

---

Closing thoughts:

The reason I showed up to [this Jax thread back in Feb 2020](https://github.com/google/jax/issues/2108#issuecomment-581539812) was to find out, "Can Jax use the 335GB host RAM, in addition to the 16GB MXU memory?"

At the time, I had no idea that the final answer in 2021 was gonna be "Sure! It's simple. And by the way, you can SSH into your TPUs. You can host a redis server, for example, using that 335GB RAM. By the way, throw in a few dozen other servers; the TPU has 96 CPU cores. Wanna see 96 CPU cores go brr? Build Tensorflow from source, and run `htop`, and It'll light up like a Christmas tree. It'll finish building in like, 20-30min too."

Thanks for all the gradients, Jax team! And thank you for the incredible infrastructure, Cloud TPU team! Ya'll rock. TPU VMs are everything I've ever dreamed, and more.
