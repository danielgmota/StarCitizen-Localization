# Expressões Regulares (Regex) para se usar com VSCode ou outros softwares com Regex padrão na Tradução

## Para selecionar as variáveis de início das linhas.
Selecionar todo o texto após o símbolo `=` até o final da linha.
```
(?<==).+
```
Selecionar todo o texto do símbolo `=` até o final da linha.
```
=.*
```

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
Para selecionar todas as linhas que NÂO possuem variáveis
```
^[^~\n]*$
```
Para selecionar todo o texto do início da linha até o primeiro símbolo `~`
```
^([^~\n]*)
```