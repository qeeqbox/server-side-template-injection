<p align="center"> <img src="https://raw.githubusercontent.com/qeeqbox/server-side-template-injection/main/server-side-template-injection.png"></p>

A threat actor may use a native template syntax on the vulnerable target to execute commands

## Example #1
1. Threat actor sends a native template syntax to a vulnerable target that uses a template engine
2. The target process the syntax and executes the result

## Code
#### Target-Logic 
```py
@app.route('/welcome', methods=['GET'])
def welcome():
  user = request.args.get('user')
  template = f"<h1>Welcome, {user}!</h1>"
  return render_template_string(template)
```

#### Target-In
```
{{1+1}}
```

#### Target-Out
```
Welcome, 4
```

## Impact
High

## Names
- Server Side Template Injection
- SST injection

## Risk
- Command execution

## Redemption
- Input validation
- Logic-less

## ID
E0679353-0BB6-404B-A6CC-6F6305FF118C

## References
- [owasp](https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/07-Input_Validation_Testing/18-Testing_for_Server_Side_Template_Injection)
