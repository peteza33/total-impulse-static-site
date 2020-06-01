+++
draft = true

title = "test out katex and figures"
date = 2020-06-03

[taxonomies]
categories = ["Deployment", "Site"]
tags = ["A", "B"]
+++
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore
eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt
in culpa qui officia deserunt mollit anim id est laborum.

<!-- more -->
# More sections
## What shoule we do?
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore
eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt
in culpa qui officia deserunt mollit anim id est laborum.

### Third levels

{% figure(link="https://opspaceservices.com", src="https://www.ecaps.space/assets/img/z1.jpg", title = "Figure 1") %}
<!-- caption here -->
{% end %}

Here is we see in Equation 1:
{% katex(block=true) %} \tag{1} x+\sqrt{1-x^2} {% end %}

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore
eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt
in culpa qui officia deserunt mollit anim id est laborum.

[link to first post](@/1_test.md)

[link to about](@/pages/about.md)

[outside link](https://opspaceservices.com)

Here's a simple footnote,[^1] and here's a longer one.[^2] 
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore
eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt
in culpa qui officia deserunt mollit anim id est laborum.

```rust
let highlight = true;

fn main() {
    println!("This is a print statement!");
}
```

Now we have some Python:

```python
x = 5

for k, v in df.items():
    print k, v

def thrust(m, p, T):
    return m * p
```



________________________

[^1]: Here is my fancy ass is the first footnote.

[^2]: This is a second footnote