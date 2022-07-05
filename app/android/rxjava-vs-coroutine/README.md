# RxJava vs Kotlin Flow

## Key Concepts
### Why comparing RxJava and Kotlin Flow?
Both main purpose of RxJava and Kotlin Flow are reactive programming.
### How about Kotlin Coroutine?
Kotlin Coroutine provides a suspendable block. The main purpose is not reactive programming, so it will not be discussed in this article
### Still wants RxJava vs Kotlin Coroutine?
The only common concept between RxJava and Kotlin Coroutine maybe background threading. However, if we discuss "thread handling" in Android, just choose Coroutine.

In fact, most of the Jetpack Components support Coroutine Scope and bring us a lots of benefits. For example, Coroutine Scope of ViewModel will be auto cancelled and it avoid memory leaks.

## When to use
| Case | Choice | Reason |
| ---- |--------| ------ |
| Java App project | RxJava | Java cannot use Flow |
| Java supported library / SDK | RxJava | Java cannot use Flow |
| The rest of cases | Kotlin Flow | Light weight and native supported by many Jetpack Components |