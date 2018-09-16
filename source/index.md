## Регулярные выражения { data-transition="none" }

### Поиск { data-transition="none" }

<p class="fragment fade-out" data-fragment-index="1">
```dot
digraph workflow {
  bgcolor="transparent"
  node [fontsize="30.0" shape="plain" fontcolor="#383D3D"]
  edge [color="#383D3D"]
  #search [label=" "]
  search -> {
    fuzzy
    exact
  }
}
```
</p>

<p class="fragment" data-fragment-index="1" style="margin-left: -24px;">
```dot
digraph workflow {
  bgcolor="transparent"
  node [fontsize="30.0" shape="plain" fontcolor="#383D3D"]
  edge [color="#383D3D"]
  #search [label=" "]
  search -> {
    fuzzy
    exact
  }
  fuzzy -> {
    google [fontcolor="red"]
  }
  { fuzzy exact } -> {
    postgres [fontcolor="cornflowerblue"]
  }
  exact -> {
    gedit [fontcolor="#e59100"]
  }
}
```
</p>

### Форматная строка / Маска { data-transition="none" }

Похоже, но не эквивалентно

```
DD.MM.YYYY
```

```
#(###) ###-##-##
```

```ruby
Time.now.strftime("%d.%m.%Y") # => "16.09.2018"
```

### Из чего состоят { data-transition="none" }

* Символьные классы
* Квантификаторы
* Альтернативы и группировки
* Модификаторы

### Символьные классы { data-transition="none" }

```regex
[0-9]
[-0-9]
[0-9-]
[^0-9]
[0-9^]
\d
\D
```

### Квантификаторы { data-transition="none" }

* `?` - 0 или 1
* `+` - 1 или много
* `*` - 0 или много
* `{1,2}` - 1 или 2
* `{2,}` - больше 2
* `{,2}` - меньше 2

### Альтернативы { data-transition="none" }

```regex
(one|two)
```

### Жадный или ленивый { data-transition="none" }

```regex
.*?
```

### Группировки { data-transition="none" }

С сохранением в переменные `$1`, `$2`
```regex
(a|b)
```

Без сохранения

```regex
(?:a|b)
```

### Модификаторы { data-transition="none" }

```regex
/[Aa][Bb][Cc]/
/abc/i
```

* **m**ultiline
* **i**gnorcase
* e**x**tended

### Якоря { data-transition="none" }

```regex
^Start of line
End of line$
\AStart of string
End of string\z
```

### Внутреннее устройство { data-transition="none" }

```regex
(t|x|\.)*\.txt
```

Finite automation

```dot
digraph {
  bgcolor="transparent"
  rankdir=LR
  node[shape="circle"]
  0 -> 1 [label="e"]
  1 -> { 2 4 6} [label="e"]
  { 3 5 7 } -> 8 [label="e"]
  2 -> 3 [label="t"]
  4 -> 5 [label="x"]
  6 -> 7 [label="."]
  8 -> 9 [label="e"]
  8 -> 1 [label="e"]
  0 -> 9 [label="e"]
  9 -> 10  [label="."]
  10 -> 11 [label="t"]
  11 -> 12 [label="x"]
  12 -> 13 [label="t"]
  13 [shape="doublecircle"]
}
```

### Сбалансированные скобки { data-transition="none" }

```ruby
re = %r{(?<re>\((?:(?>[^()]+)|\g<re>)*\))}x
"(())()(()())".scan re
 => [["(())"], ["()"], ["(()())"]]
```

### Уровни трансляции { data-transition="none" }

```dot
digraph {
  bgcolor="transparent"
  node [shape="none" fontsize="30.0"]
  edge [fontsize="25.0"]

  ""->lexical [label="  "]
  lexical->syntactic [label="  "]
  syntactic->semantic [label="  "]
  semantic->" " [label="  "]
}
```

### Уровни трансляции { data-transition="none" }

```dot
digraph {
  bgcolor="transparent"
  node [shape="none" fontsize="30.0"]
  edge [fontsize="25.0"]

  ""->lexical [label="  source"]
  lexical->syntactic [label="  tokens"]
  syntactic->semantic [label="  AST"]
  semantic->" " [label="  Attr. AST"]
}
```

### Уровни трансляции { data-transition="none" }

```dot
digraph {
  bgcolor="transparent"
  node [shape="none" fontsize="30.0"]
  edge [fontsize="25.0"]

  ""->lexical [label="  source"]
  lexical->syntactic [label="  tokens"]
  syntactic->semantic [label="  AST"]
  semantic->" " [label="  Attr. AST"]

  lexical [label="regexp" fontcolor="cornflowerblue"]
  syntactic [label="grammar" fontcolor="red"]
}
```

### Кроссворды

> [Несложный](https://regexcrossword.com/challenges/tutorial/puzzles/1)
> [Чуть сложнее](https://regexcrossword.com/challenges/beginner/puzzles/1)
> [Средний](https://regexcrossword.com/playerpuzzles/95899f33-9429-4de2-9949-f6fd2f0f469f)

<script type="text/javascript" src="regex-colorizer.js">
</script>

<script type="text/javascript">
RegexColorizer.colorizeAll();
</script>