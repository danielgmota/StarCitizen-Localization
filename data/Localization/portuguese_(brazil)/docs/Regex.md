# Regex para uso na Tradução

# Regex para Notepad++

Selecionar todo o texto do símbolo `=` até o final da linha.
```
=.*
```
Substitua pelo símbolo de `=` para que apague todo o texto após a variável deixando o sinal de `=` (sem quebrar a variável).
___
Selecionar todo o texto do início da linha até depois do símbolo de `=` 
```
^([\s\S]*?=)
```
ou
```
^[\s\S]*?=
```
___
Selecionar as linhas que tem o símbolo `=` sem nada após
```
=$
```