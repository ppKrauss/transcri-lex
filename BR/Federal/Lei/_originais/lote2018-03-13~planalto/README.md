## Procedimentos

Conversão do HTML oficial disponivel para o formato `HTML5-lex2`, especializado de  [HTML5-onlyContent](https://github.com/okfn-brasil/HTML5-onlyContent).

## 2002-01-10;10406

[Lei nº 10.406, de 10 de Janeiro de 2002](http://lexml.gov.br/urn/urn:lex:br:federal:lei:2002-01-10;10406) (**Código Civil**).

Download dos orgiginais no `http://planalto.gov.br` requer uso do *User-Agent*, 

```sh
curl -H "User-Agent: Mozilla/5.0 (Linux)" \
   http://www.planalto.gov.br/CCivil_03/leis/2002/L10406compilada.htm \
   | iconv -c  -t UTF-8  -f ISO-8859-1 > 2002-01-10-10406-compilada~p01-utf8.htm
```

Conversões iniciais:

```sh
pandoc -f html-native_divs-native_spans -t gfm \
   2002-01-10-10406-compilada~p01-utf8.htm > 2002-01-10-10406-compilada~p02-pandoc0.md
```


Em seguida o `pandoc0` tem seus elementos básicos corrigidos (poderiam já ser convertidos em pipe), para se tornar o markdown de referência inicial para os diffs e versionamento no git.



