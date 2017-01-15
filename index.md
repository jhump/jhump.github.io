---
layout: index
---

This is an overview of the various things in my github account. I've experimented quite a lot with various kinds of libraries for Java. Since this is all done in my spare time, much of it is in an unfinished state. Some of it is more mature, and I hope it can be usable by others (if not now, then in the not-too-distant future).

Below is a tour of my repos.

### [bluegosling](https://jhump.github.io/bluegosling) *alpha*
This is the largest repo here. It is a collection of libraries for Java with a very wide range of topics. Think of it as an extension to Google's [Guava](https://github.com/google/guava). It has undergone a lot of tumultuous changes, all in the name of making the organization sane and easier for usage outside of my "personal playground".

* There are few things here that, for various reasons, are [not being considered for Guava](https://github.com/google/guava/wiki/IdeaGraveyard). These include things like [tuples](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/tuples/Tuple.html), [persistent collections](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/collections/immutable/PersistentCollection.html), and operations like `Lists.filter` and `Sets.transform` (in the form of [filtering](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/collections/FilteringList.html) and [transforming](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/collections/TransformingSet.html) views).
* An [API](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/graph/package-summary.html) for describing complex computations as dependency graphs of steps, which can then be executed in a way that fully exploits possible parallelism.
* There are several concurrency packages here, too. They include new types of locks and synchronizers, a more feature-rich task scheduler than the standard `ScheduledExecutorService`, and an alternate `Future` [API](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/concurrent/fluent/package-summary.html) that tries to bridge the divide and be a best-of-breed between Guava's `ListenableFuture` and the standard Java 8 `CompletionStage`.
* Implementations of thread-safe variables, called [atoms](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/concurrent/atoms/package-summary.html). These are heavily inspired by Clojure's [vars](http://clojure.org/reference/vars) and include implementations that are very similar to Clojure's dynamic vars (`ThreadLocalAtom`), refs (`TransactionalAtom`, *MVCC FTW!*), agents (`AsynchronousAtom`), and atoms (`SimpleAtom`).
* There are numerous packages here for writing annotation processors.
  * [APIs](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/apt/reflect/package-summary.html) for interacting with language models and type mirrors that feel more like core reflection than the `javax.lang.model` APIs.
  * [Tools](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/apt/testing/package-summary.html) for writing unit tests for an annotation processor.
  * An implementation of the `javax.lang.model` interfaces backed by core reflection. This can be used to write reflective code once that can work both in the context of an annotation processor (backed by the compiler's processing environment) and also in a normal runtime context (backed by core reflection).
* A `Result` [API](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/result/Result.html), inspired by Rust's [result](https://doc.rust-lang.org/std/result/) type.
* Numerous other packages and random utilities...

----

### [artificer](https://github.com/jhump/artificer)
A small library that can make annotations more powerful. It consists of an annotation processor that can generate builder classes for your annotations, for using them as value types. It can also generated "bridges", which are a parallel API to your annotations that greatly simplify the implementation of annotation processors for your annotations.

----

### [tru-reflect](https://github.com/jhump/tru-reflect) *unfinished*
After making a [reflection-like API](https://jhump.github.io/bluegosling/javadoc/com/bluegosling/apt/reflect/package-summary.html) for annotation processors, I decided that it would be fun to provide an API that *actually uses core reflection APIs*. It was also a good excuse to play with the ASM library.

This library exposes `javax.lang.model` elements and type mirrors using familiar reflection types: `Class`, `Field`, `Method`, `Constructor`, etc. It does so by translating elements into synthetic classes. (It does not actually compile the source into a class. That would be too slow. The resulting class thus cannot be instantiated or used via reflection APIs like `Constructor.newInstance`, `Method.invoke`, or `Field.get`.)

----

### [hyper-redis](https://github.com/jhump/hyper-redis) *unfinished*
At Square, we wrapped the [Jedis](https://github.com/xetorthio/jedis) library, which is fairly low-level has some API peculiarities (mostly just straying from idiomatic Java), with a more user-friendly a safer API. This project is similar, but it does not wrap Jedis. It instead implements a redis client from scratch, using Netty for the networking components and relying heavily on code generation to provide an idiomatic Java API that provides high performance and type safety.

----

### [arquebus](https://github.com/jhump/arquebus) *unfinished*
When I first tried to get my older son into programming, we talked about building a game. We started this project, but never finished it. I got to play a bit with Google's PlayN library and with JBox2D. It is not in a functioning state at the moment, due to some of the dependencies no longer being available in Maven Central. I'm currently working on fixing it up and changing it to use the latest PlayN (2.0). Slow and steady...

----

### [midi-compozer](https://github.com/jhump/midi-compozer)
This is a music composition program. I've been using it for quite some time to create MIDI files for music that I've written. Warning: it was written for DOS. So you'll have to use [DOSBox](http://www.dosbox.com/) to get it to run. And it's user interface is all keyboard driven, so has a steep learning curve.

Another warning: this is a really hideous bag of C code that I wrote in college, about 20 years ago. (But at least it works!)
