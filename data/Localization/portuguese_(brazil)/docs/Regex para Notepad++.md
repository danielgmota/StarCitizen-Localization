# Expressões Regulares (Regex) para se usar com VSCode ou outros softwares com Regex padrão na Tradução

## Para selecionar as variáveis de início das linhas.
Selecionar todo o texto após o símbolo `=` até o final da linha.
```
(?<==).+
```
ou
```
(?<=\=)([\s\S]*?)(?=$)
```
Selecionar todo o texto do símbolo `=` até o final da linha.
```
=.*
```
___

## Para selecionar as variáveis dentro do texto.

Para selecionar as variáveis que começam com `~` e terminam com `)` dentro do texto.
```
~(.*?)\)
``` 
Caso precise de selecionar mais de um `)` por conter mais de um dentro da variável, tente este.
```
~(.*?)\)(?![^(]*\))
```
Para selecionar variáveis do tipo `~mission(***)` dentro do texto.
```
~mission\((.*?)\)
```
___

## Isolar Variáveis
Para selecionar todo o texto de uma linha exceto as variáveis que começam com `~` e terminam com `)`.
```
^[^~\n]*|(?<=\))[^~\n]*
```
## Isolar Linhas com Variáveis
Selecionar todas as linhas exceto as que possuem variáveis.
```
^[^~\n]*$
```

Selecionar todas as linhas exceto as que possui a variável `~mission(location)`.
```
^(?!.*~mission\(location\)).*$
```
Para selecionar todo o texto do início da linha até o primeiro símbolo `~`
```
^([^~\n]*)
```
___
# Outros
Selecionar as linhas que tem o símbolo `=` sem nada após.
```
=$
```
___