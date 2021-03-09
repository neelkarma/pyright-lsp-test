LSP Response:
```
Content-Length: 602^M^@^M^@{"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal[''432'']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal[''432'']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}
```
And yet again...
```py
>>> len(br"""{"jsonrpc":"2.0","method":"textDocument/publishDiagnostics","params":{"uri":"file:///c%3A/Users/nsdjs/Documents/Programming/Python/pyright-lsp-test/main.py","diagnostics":[{"range":{"start":{"line":3,"character":9},"end":{"line":3,"character":14}},"message":"Argument of type \"Literal[''432'']\" cannot be assigned to parameter \"integer\" of type \"int\" in function \"printInt\"\n  \"Literal[''432'']\" is incompatible with \"int\"","severity":1,"code":"reportGeneralTypeIssues","source":"Pyright","codeDescription":{"href":"https://github.com/microsoft/pyright/blob/master/docs/configuration.md"}}]}}""")
602
```
