# Lifetime rules
![[Lifetime diagram rust]]
- A function's signature indicates everything regarding the lifetime of its variables.
ex: `g<'a>(p: &'a i32)'` indicates that it does not "stash" `p` anywhere that will outlive the call

[Lifetime Kata](https://tfpk.github.io/lifetimekata/index.html)
