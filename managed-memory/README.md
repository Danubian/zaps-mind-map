# Managed Memory Experiments
Playing around with bounds of memory managed programming languages

## Abstract
Memory management always comes up in programming whether you are using a programming language that has a garbage collector or not.

Recently, I was refreshing my understanding of how modern garbage collectors work and that got me into thinking about just memory for programs.
Additionally, I realized that there are some small, fun little experiments that you can run to learn a bit more about program memory.

I'm going to be using C# for the following experiments, but this should work similarly for Java

# Quick Terminology
* *Stack Frame* - Within a given scope, the set of that variables are accesible
* *Stack* - 
* *Heap* - 

# Stack Experiment #1 - Stack Overflow
So the infamous stack overflow exception is suppose to happen when the stack has grown too high and has exceeded the maximum expected capacity

**Question:** What is that capacity?

One way to determine the stack capacity would be to write a program, as seen below, and to see what value is written to the console

## C#
```csharp
public static void Main(string[] args)
{
    StackOverflow(1);
}

public static void StackOverflow(long i)
{
    Console.WriteLine($"Iteration: {i}");
    StackOverflow(i + 1);
}
```

Can you guess what the console will say?





## Console

```
Iteration: 173960
Iteration: 173961
Iteration: 173962
Iteration: 173963
Iteration: 173964
Process is terminating due to StackOverflowException.
```

So it looks like the last value printed out is `173964`. Alright, cool. So what does this number mean? Is it the stack capacity or *almost* the stack capacity?
How is this value set?

Interesting, running this code in Debug Mode and Release Mode gives different outcomes
- **Debug + Run**: 173964
- **Debug + Debug**: 173917
- **Release + Run**: 65237
- **Release + Debug**: 173917

Not that the stack size should ever really get that high, but this does indicate that a stack overflow exception would occur sooner in the Release configuration that in the Debug configuration

The `65237` value from the Release configuration run is really grabbing my attention. It seems oddly close to `65536` or 2^16. 

Doing some googling around, I find that I can figure out the [stack size of my operating system](https://stackoverflow.com/questions/42315207/extend-the-stack-size-on-macos-sierra). Lo and behold, it's `65532`

That's great and all but that raises two more questions:
- There's a `299` difference between the operating stack size and the reported stack overflow size for the Release configuration, `65237`. **What is that difference?**
- If the operating system's hard limit is `65536`, how can the value `173917` be reported, when it exceeds the hard limit by over 250%?

Well, for the first question, `65237` is already under-reporting the number of stack methods we know about since it only counts the number of times the `StackOverflow` method is called
and does not include the `Main` method, so the real known stack number is `65238`. There's still `298` values not accounted for, but the best guess would be that the particulars of .NET 
