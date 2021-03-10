# NeoVim Testing

```
Content-Length: 602^M^@^M^@{"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal[''432'']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal[''432'']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}
```
And yet again...
```py
>>> len(br"""{"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal[''432'']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal[''432'']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}""")
604
```

# Vim Testing

```
Content-Length: 602

{"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal['432']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal['432']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}
```
Checking length (not counting newlines):
```py
>>> len(br"""{"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal['432']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal['432']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}""")
600
```
Checking length: (counting newlines):
```py
len(br"""
... {"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal['432']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal['432']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}
... """)
602
```
# Conclusion
Look at the diff between the two responses: https://www.diffchecker.com/Uc7UxfrF

Something is causing double single quotes to appear...? It also may be an issue with counting/not counting newlines maybe.
