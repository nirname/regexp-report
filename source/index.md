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

<p class="fragment" data-fragment-index="1" style="margin-left: -20px;">
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
    postgres [fontcolor="cornflowerblue"]
  }
  exact -> {
    string [fontcolor="#e59100"]
    regexp [fontcolor="#2aba4c"]
  }
}
```
</p>

### Шаблоны { data-transition="none" }

```1c
DD.MM.YYYY
```

```ruby
Time.now.strftime("%d.%m.%Y") # => "16.09.2018"
```

<script type="text/javascript" src="regex-colorizer.js">
</script>

<script type="text/javascript">
RegexColorizer.colorizeAll();
</script>