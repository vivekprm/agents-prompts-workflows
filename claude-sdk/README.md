https://x.com/i/status/2047875091174981780

Install claude code using below command:

```sh
npm install -g @anthropic-ai/claude-code
```

# Claude code SDK
It's a way to programatically access the power of Claude code agents in headless mode. This is powerful because it's new kind of primitive, new kind of building
block that allows you to build applications that weren't possible before.

Things that you can do with SDK like super simple things. Simple building block for agentic applications:
- Use like a unix tool in scripts, pipelines etc.
    - Unix tool philosophy is what makes Claude code really powerful. You can plug it anywhere you can run bash or terminal.
    - You can use it in your unix pipelines, you can pipe stuff into it and pipe stuff out of it.
- CI and automation tools.
    - You can have Claude review your code.
    - Some people use Claude to write new linters for them.
- Remote environments.
- Web chat bot coding interfaces.

# Example: Basic headless use case
```
>claude -p "Write me a function to calculate the fibonacci series" --allowedTools "Write"
Created 'fibonacci.py' with a function that returns the first `n` numbers in the Fibonacci series.
>cat fibonacci.py
def fibonacci(n):
    if n <= 0:
        return []
    elif n == 1:
        return [0]
    elif n == 2:
        return [0, 1]

    series = [0, 1]
    for i in range(2, n):
        series.append(series[i-1] + series[i-2])

    return series
```

Calling claudesdk is as simple as running ```claude -p``` command followed by the string that you want to ask. Like in above example we are asking claude to write
fibonacci sequence generator.

We can also pipe logs to Claude so you don't have to look at the logs manually.

```
>cat app.log | claude -p "Summarize the most common error logs"
```


