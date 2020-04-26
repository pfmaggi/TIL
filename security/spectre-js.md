# Meltdown, Spectre Can Be Exploited Through Your Browser

[Tom's Hardware has an article that explain the high level exploit](http://www.tomshardware.com/news/meltdown-spectre-exploit-browser-javascript,36221.html), and there's the [official vulnerabilities' website](https://meltdownattack.com/) with links to the papers.
  * [Meltdown](https://meltdownattack.com/meltdown.pdf)
  * [SPECTRE](https://spectreattack.com/spectre.pdf)

**..looks so strange to have vulnerabilities with an "official website" and logo..**

At the end, these exploits are using a couple of features that all modern browsers provide:

  * [Shared Buffers](https://tc39.github.io/ecma262/#sec-sharedarraybuffer-objects)
    * [Mozilla: Mitigations landing for new class of timing attack](https://blog.mozilla.org/security/2018/01/03/mitigations-landing-new-class-timing-attack/)
    * [Chromium: Actions required to mitigate Speculative Side-Channel Attack techniques](https://sites.google.com/a/chromium.org/dev/Home/chromium-security/ssca)
  * [High Precision Timers](https://caniuse.com/#feat=high-resolution-time)
    * [The Spy in the Sandbox -- Practical Cache Attacks in Javascript](https://arxiv.org/abs/1502.07373)

## How does it work?
Shared buffers are used to poison the CPU branch prediction logic, and then retrieve the content of the cache.
To be able to identify if the data are from the cache or not, a sub-millisecond timer is required.

## What are the mitigation steps?
The first line of action it has been to disable, by default, the shared buffers functionality and then to reduce the precision of the High Precision Timers (adding some Jittering).