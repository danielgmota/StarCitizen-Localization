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

## Para selecionar as variáveis e/ou textos que começam com `[` e terminal com `]`
Para selecinar as variáveis e/ou textos que começam com `[` e terminal com `]` como `[item]`
```bash
\[.*?\]
```


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

# Procurar e Substituir Textos
>Para procurar por determinados textos e substituí-los

## Procurar por texto com apenas números se usa `(\d+)`. Exemplo: `00/00ºC` e trocar por `00 / 00 ºC`
Pesquisa por
```bash
(\d+)/(\d+)(ºC)
```
Substitua por
```bash
$1 / $2 ºC
```

## Procurar por textos com apenas letras se usa `(\w+)`. Exemplo: `(\w+) 1.0b`

## Procurar por textos com letras e números se usa o coringa `(.+)`. Exemplo: `(?<==)(.+) Targeting Computer`
>Para procurar por todo texto depois so sinal `=` até Targeting Computer
```bash
(?<==)(.+) Targeting Computer
```
E podemos substituir este texto utilizando a captura de variável `$`. Exemplo: `$1` `$2` `$3`.
> Para substituir utilizando texto anterior à `Targeting Computer` em variável

```bash
Computador de Mira $1
```

## Procurar por textos e trocar a posição de palavras substituindo ou não alguma palavra.
Exemplo: Procurar por palavras após o símbolo de `=` que contenham letras, números ou símbolos seguidos da palavra `Cannon`, e alterar a ordem delas substituindo `Cannon` por `Canhão`. Como: `C-912 Cannon` ficando: `Canhão C-912`

Caso tenha apenas uma palavra antes de `Cannon` pesquisa por:
```bash
(?<==)(\S+) Cannon
```
Caso possa ter várias palavras antes de `Cannon` pesquise por:
```bash
(?<==)(.*?) Cannon
```

Substitua por:
```bash
Canhão $1
```


