# Regex para uso na Tradução

# Regex para Notepad++

Selecionar todo o texto do símbolo `=` até o final da linha
```
=.*
```

Selecionar todo o texto do início da linha até depois do símbolo de `=` 
```
^([\s\S]*?=)
```
ou
```
^[\s\S]*?=
```

Selecionar as linhas que tem o símbolo `=` sem nada após
```
=$
```