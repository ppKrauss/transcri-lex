## Preparo do lote de documentos
...

## Passo-a-passo da conversão de um documento

Conversão, partindo de um documento HTML fiel ao original,  para se chegar ao formato `HTML5-lex2` de  [HTML5-onlyContent](https://github.com/okfn-brasil/HTML5-onlyContent).

0. [`curl`](https://en.wikipedia.org/wiki/CURL) para *download* do HTML origonal oferecido pelo site do Planalto.
1. conversão para UTF-8 (não foi respeitado o padrão ePING);
2. conversão, via [`pandoc`](https://en.wikipedia.org/wiki/Pandoc), do HTML para [formato Markdown GFM](https://en.wikipedia.org/wiki/Markdown#GFM);
3. Correção problemas de formatação menores, principalmente na represetação dos caracteres (entidades HTML por exemplo), 
4. Cópia inicial do  `p03-ref` para se completar a transcrição com assistência humana.  Todas as alterações (software ou humanas)  serão daí em diante mantidas no git, sob o arquivo `~p04-format`. 
5. Volta do documento revisado para HTML, `~p05-pandoc`. Neste momento já temos uma DTD *lex1*.
6. Transformação do *HTML-lex1* em *HTML5-lex2* (estruturado com seções e listas devidamente hierarquizadas), `~p06-format`.

Cada um desses passos ficam registrados nos respectivos arquivos, ou seja, de final `~p01-utf8.htm`, `~p02-pandoc0`, `~p03-ref.md`, etc.

### Preparo inicial

Importante que download dos orgiginais seja automatizável e fiel aos nomes e identificadores previstos. Ferramentas simples como o `curl` ou `wget` são flexíveis e confiáveis para este fim.
Exemplo:

```sh
curl -H "User-Agent: Mozilla/5.0 (Linux)" \
   http://www.planalto.gov.br/CCivil_03/leis/2002/L10406compilada.htm \
   | iconv -c  -t UTF-8  -f ISO-8859-1 > 2002-01-10-10406-compilada~p01-utf8.htm
```

Conversões iniciais, conforme passo-2. Exemplo:

```sh
pandoc -f html-native_divs-native_spans -t gfm \
   2002-01-10-10406-compilada~p01-utf8.htm > 2002-01-10-10406-compilada~p02-pandoc0.md
```

Em seguida o `pandoc0` tem seus elementos básicos corrigidos (poderiam já ser convertidos em pipe), para se tornar o markdown de referência inicial para os diffs e versionamento no *git*.


### Preparo no p04-format 

Primeira etapa.. por exemplo  **marcação das seções**. 

Como ainda não conhecemos o código do planalto, nem acompanhamos a confiabilidade das ferramentas, foram realizadas manualmente as conversões por regular expression no Atom:


Terceira etapa.... por exemplo **Eliminação dos links explicativos** (ficam apenas os indicativos de revogação), resumo:


... Quarta etapa... por exemplo **Normalização e marcação dos itens**.

### Preparos finais
Conversão de volta para HTML. Exemplo:

```sh
pandoc -s -t HTML5 --template _src/html5.pandoc.tpl  2002-01-10-10406-compilada~p04-format.md \
  > 2002-01-10-10406-compilada~p05-pandoc.htm
```
Software de estruturação ...

