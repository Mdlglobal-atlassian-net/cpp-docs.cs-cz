---
title: Regulární výrazy (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, regular expressions
- regular expressions, Visual C++
- regular expressions
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 143ffe47181d438d278de7fa9027f4016dfa74cd
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="regular-expressions-c"></a>Regulární výrazy (C++)

Standardní knihovna C++ podporuje více gramatika regulární výraz. Toto téma popisuje dostupné gramatika rozdíly při použití regulárních výrazů.

## <a name="regexgrammar"></a> Gramatika regulární výraz

Regulární výraz gramatika používat je ve zadán pomocí jednoho z `std::regex_constants::syntax_option_type` hodnot výčtu. Tyto regulární výraz gramatika jsou definovány v std::regex_constants:

- `ECMAScript`: Toto je nejblíže k gramatika, používané jazyky rozhraní .NET a používání jazyka JavaScript.
- `basic`: POSIX základní regulární výrazy nebo BRE.
- `extended`: POSIX rozšířené regulární výrazy nebo ERE.
- `awk`: Toto je `extended`, ale má další řídicí sekvence pro netisknutelné znaky.
- `grep`: Toto je `basic`, ale také umožňuje nový řádek (\n) znaků jednotlivé změny.
- `egrep`: Toto je `extended`, ale také to umožňuje znaky nového řádku jednotlivé změny.

Ve výchozím nastavení, pokud není zadaný žádný gramatika `ECMAScript` se předpokládá. Je možné zadat pouze jeden gramatika.

Kromě gramatika můžete použít několik příznaky:
- `icase`: Ignorovat velká / při kontrole shody.
- `nosubs`: Ignorujte označený odpovídá (tj. výrazy v závorkách); jsou uloženy žádné nahrazení.
- `optimize`: Zkontrolujte odpovídající rychlejší, na úkor větší konstrukce času.
- `collate`: Pomocí pořadí kolace národní prostředí – velká a malá písmena (například rozsahy ve formátu "[a-z]").

Příznaky nula nebo více může nelze kombinovat s gramatika určit způsob chování modul regulární výraz. Pokud jenom příznaky jsou nastaveny, `ECMAScript` se předpokládá, že jako gramatiky.

### <a name="element"></a>Prvek

Prvek může být jeden z následujících:

- *Obyčejnou znak* odpovídající ve stejném v pořadí cíl.

- A *zástupný znak* ,., který odpovídá jakémukoliv znaku v pořadí cíl kromě nového řádku.

- A *závorka výraz* ve tvaru "[`expr`]", který odpovídá znak nebo element kolace v pořadí cíl, která je také v sadě definované výraz `expr`, nebo ve tvaru "[^`expr`]", který odpovídá znak nebo element kolace v pořadí cíl, který není v sadě definované výraz `expr`.

     Výraz `expr` může obsahovat libovolnou kombinaci z následujících akcí:

    -   Jednotlivý znak. Přidá tento znak do sady definované `expr`.

    -   A *znak rozsah* ve tvaru "`ch1`-`ch2`". Přidá znaky, které jsou reprezentované pomocí hodnoty v rozsahu uzavřené [`ch1`, `ch2`] do sady definované `expr`.

    -   A *znak třída* ve tvaru "[:`name`:]". Přidá do sady definované znaky ve třídě s názvem `expr`.

    -   *Ekvivalenční třída* ve tvaru "[=`elt`=]". Přidá kompletování prvky, které odpovídají `elt` do sady definované `expr`.

    -   A *kompletování symbol* ve tvaru "[.`elt`.]". Přidá element kolace `elt` do sady definované `expr`.

- *Ukotvení*. Ukotvení „^“ odpovídá začátku cílové sekvence; ukotvení „$“ odpovídá konci cílové sekvence.

A *zachycení skupiny* ve tvaru "( *dílčím výrazu* )", nebo "\\( *dílčím výrazu* \\)" v `basic` a `grep`, které odpovídá pořadí znaků v pořadí cíl, který má odpovídající vzoru mezi oddělovače.

- *Identity řídicí* ve tvaru "\\`k`", který odpovídá znak `k` v pořadí cíl.

Příklady:

- „a“ odpovídá cílové sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

- „.“ odpovídá všem cílovým sekvencím „a“, „B“, „b“ a „c“.

- „[b-z]“ odpovídá cílovým sekvencím „b“ a „c“, ale neodpovídá cílovým sekvencím „a“ nebo „B“.

- „[:lower:]“ odpovídá cílovým sekvencím „a“, „b“ a „c“, ale neodpovídá cílové sekvenci „B“.

- „(a)“ odpovídá cílové sekvenci „a“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

V `ECMAScript`, `basic`, a `grep`, může být také element *zpět odkaz* ve tvaru "\\`dd`", kde `dd` představuje desetinnou hodnotu N, která odpovídá posloupnost znaky v cílové pořadí který je stejný jako posloupnosti znaků, který má odpovídající n. *skupiny zachycení*. Například „(a)\1“ odpovídá cílové sekvenci „aa“, protože první (a jediná) skupina zachycení odpovídá počáteční sekvenci „a“ a \1 odpovídá závěrečné sekvenci „a“.

V `ECMAScript`, element může být také jeden z následujících akcí:

- A *skupiny bez zachycení* ve tvaru "(?: *dílčím výrazu* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači.

- Omezené *souboru formátu řídicí* formuláře "\f", "\n", "\r", "\t" nebo "\v". Tyto odpovídají znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- A *kladnou assert* ve tvaru "(= *dílčím výrazu* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači, ale nemění pozici shody v cílové sekvenci.

- A *záporné assert* ve tvaru "(! *dílčím výrazu* ) ". Odpovídá jakékoli sekvenci znaků v cílové sekvenci, která neodpovídá vzorci mezi oddělovači a nemění pozici shody v cílové sekvenci.

- A *šestnáctková řídicí sekvence* ve tvaru "\x`hh`". Odpovídá znaku v pořadí cíl, která je reprezentována dvě hexadecimální číslice `hh`.

- A *unicode řídicí sekvence* ve tvaru "\u`hhhh`". Odpovídá znaku v pořadí target, která je reprezentována čtyři hexadecimální číslice `hhhh`.

- A *řídit – řídicí sekvence* ve tvaru "\c`k`". Řídicí znak, který se nazývá ve znak, který odpovídá `k`.

- A *hranice slova assert* ve tvaru "\b". Odpovídá po aktuální pozici v pořadí cíl ihned po *hranice slova*.

- A *hranice záporné slova assert* ve tvaru "\B". Odpovídá, pokud aktuální pozici v pořadí cíl není ihned po *hranice slova*.

- A *řídicí znak dsw* ve tvaru "\d", "\D", "\s", "\S", "\w", "\W". Poskytuje krátký název pro třídu znaků.

Příklady:

- „(?:a)“ odpovídá cílové sekvenci „a“, ale „(?:a) \1“ je neplatné, protože není k dispozici žádná skupina zachycení 1.

- "(=a)" odpovídá pořadí cíl "a". Kladný kontrolní výraz odpovídá počáteční sekvenci „a“ v cílové sekvenci a závěrečné „a“ v regulárním výrazu odpovídá počáteční sekvenci „a“ v cílové sekvenci.

- "(!a)" neodpovídá cílové sekvence "a".

- "a\b." odpovídá pořadí cíl "~", ale neodpovídá cílové sekvence "ab".

- "a\B." odpovídá pořadí cíl "ab", ale neodpovídá cílové sekvence "~".

V `awk`, element může být také jeden z následujících akcí:

- A *souboru formátu řídicí* ve tvaru "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" nebo "\v". Tyto odpovídají zpětnému lomítku, upozornění, klávese Backspace, znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- *Osmičková řídicí sekvence* ve tvaru "\\`ooo`". Odpovídá znaku v pořadí cíl, jejichž reprezentace je hodnota reprezentována jednu, dvě nebo tři osmičková číslice `ooo`.

### <a name="repetition"></a>Opakování

Libovolný element, jinak než *kladnou assert*, *záporné assert*, nebo *ukotvení* může následovat počet opakování. Nejobecnější typ počtu opakování má podobu "{`min`,`max`}", nebo "\\{`min`,`max`\\}" v `basic` a `grep`. Element, který následuje tento formulář počtu opakování odpovídá alespoň `min` následných výskytů a ne víc než `max` následných výskyty sekvenci, která odpovídá elementu. Například "{2,3}" odpovídá pořadí cíl "aa" a cíl pořadí "aaa", ale není pořadí cíl cíl pořadí "a" nebo "aaaa".

Počet opakování může mít také jednu z následujících forem:

- "{`min`}", nebo "\\{`min`\\}" v `basic` a `grep`. Ekvivalentní "{`min`,`min`}".

- "{`min`,}", nebo "\\{`min`,\\}" v `basic` a `grep`. Ekvivalentní "{`min`, bez vazby}".

- "*". Ekvivalentní „{0,unbounded}“.

Příklady:

- "{2}" odpovídá pořadí cíl "aa", ale není pořadí cíl cíl pořadí "a" nebo "aaa".

- "{2,}" odpovídá pořadí cíl "aa", cílový pořadí "aaa" a podobně, ale neodpovídá cílové sekvence "a".

- „a*“ odpovídá cílové sekvenci „“, cílové sekvenci „a“, cílové sekvenci „aa“ atd.

Pro všechny gramatika s výjimkou `basic` a `grep`, počet opakování můžete také provést jednu z následujících podob:

- "?". Ekvivalentní "{0,1}".

- "+". Ekvivalent "{1, bez vazby}".

Příklady:

- "a"? odpovídá pořadí cíl "" a pořadí cíl "a", ale není pořadí cíl "aa".

- „a+“ odpovídá cílové sekvenci „a“, cílové sekvenci „aa“ atd., ale nikoli cílové sekvenci „“.

V `ECMAScript`, všech formulářů počtu opakování může následovat znak '?', který označuje *typu non-greedy opakování*.

### <a name="concatenation"></a>Zřetězení

Regulární výraz elementů s nebo bez *počtu opakování*, může být zřetězen do formuláře delší regulární výrazy. Výsledný výraz odpovídá cílové sekvenci, která je zřetězením sekvencí odpovídajících jednotlivým prvkům. Například "{2,3}b" odpovídá pořadí cíl "aab" a cíl pořadí "aaab", ale neodpovídá pořadí cíl "ab" nebo cílové sekvence "aaaab".

### <a name="alternation"></a>Alternace

Ve všech gramatika regulární výraz s výjimkou `basic` a `grep`, zřetězených regulárního výrazu může následovat znak '&#124;' a jiné zřetězených regulární výraz. Tímto způsobem lze spojit libovolný počet zřetězených regulárních výrazů. Výsledný výraz odpovídá jakékoli cílové sekvenci, která odpovídá jednomu nebo více zřetězeným regulárním výrazům.

Když více než jeden z zřetězených regulární výrazy odpovídá cílové sekvence `ECMAScript` vybere první zřetězených regulární výrazy, který odpovídá pořadí jako shody (*nejprve odpovídat*); dalších regulární výraz gramatika vybrat tu, která dosáhne *nejdelší shody*. Například "ab&#124;cd" odpovídá pořadí cíl "ab" a cíl pořadí "cd", ale neodpovídá pořadí cíl "abd" nebo cílové sekvence "acd".

V `grep` a `egrep`, znak nového řádku (\n) lze použít k oddělení změny.

### <a name="subexpression"></a>Dílčí výraz

V `basic` a `grep`, je sloučen dílčím výrazu. V ostatních gramatikách regulárního výrazu je dílčí výraz změnou.

## <a name="grammarsummary"></a> Souhrn gramatiky

Následující tabulka shrnuje funkce, které jsou k dispozici v různých gramatikách regulárního výrazu:

|Prvek|Základní|rozšířené|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternace pomocí '&#124;.||+|+||+|+|
|alternace pomocí „\n“||||+|+||
|ukotvení|+|+|+|+|+|+|
|zpětný odkaz|+||+|+|||
|výraz závorky|+|+|+|+|+|+|
|skupina zachycení používající „()“||+|+||+|+|
|zaznamenání pomocí skupiny "\\(\\)"|+|||+|||
|řídicí sekvence|||+||||
|řídicí znak dsw|||+||||
|řídicí znak formátu souboru|||+|||+|
|šestnáctková řídicí sekvence|||+||||
|řídicí znak identity|+|+|+|+|+|+|
|záporný kontrolní výraz|||+||||
|záporný kontrolní výraz hranice slova|||+||||
|skupina bez zachycení|||+||||
|opakování bez metody Greedy|||+||||
|osmičková řídicí sekvence||||||+|
|běžný znak|+|+|+|+|+|+|
|Kladný kontrolní výraz|||+||||
|opakování pomocí "{}"||+|+||+|+|
|opakování pomocí "\\{\\}"|+|||+|||
|opakování pomocí „*“|+|+|+|+|+|+|
|opakování pomocí „?“ a „+“||+|+||+|+|
|řídicí sekvence Unicode|||+||||
|zástupný znak|+|+|+|+|+|+|
|kontrolní výraz hranice slova|||+||||

## <a name="semanticdetails"></a> Sémantické podrobnosti

### <a name="anchor"></a>Ukotvení

Ukotvení odpovídá pozici v cílovém řetězci, nikoli znaku. „^“ odpovídá začátku cílového řetězce; „$“ odpovídá konci cílového řetězce.

### <a name="back-reference"></a>Zpětný odkaz

Zpětný odkaz je zpětné lomítko, za kterým následuje desítkovou hodnotu N. Odpovídá obsahu n. *skupiny zachycení*. Hodnota N nesmí být větší než počet skupin zachycení, které zpětnému odkazu předcházejí. V `basic` a `grep`, hodnota N je dáno desítková číslice, který následuje zpětné lomítko. V `ECMAScript`, hodnota N je dáno desetinných míst, které okamžitě postupujte podle zpětné lomítko. Proto v `basic` a `grep`, hodnota N se nikdy více než 9, i když regulární výraz má více než devět zachycení skupin. V `ECMAScript`, N hodnotu bez vazby.

Příklady:

- „((a+)(b+))(c+)\3“ odpovídá cílové sekvenci „aabbbcbbb“. Zpětný odkaz „\3“ odpovídá textu ve třetí skupině zachycení, tedy „(b+)“. Neodpovídá cílové sekvenci „aabbbcbb“.

- „(a)\2“ není platné.

- "((((a))) \10 b" má odlišný význam `basic` a v `ECMAScript`. V `basic` "\1" je zpětný odkaz. Zpětný odkaz odpovídá obsahu první skupiny zachycení (to znamená skupiny, která začíná na „(b“ a končí posledním znakem „)“ a předchází zpětnému odkazu) a závěrečný znak 0 odpovídá běžnému znaku 0. V `ECMAScript`, je zpětný odkaz "\10". Odpovídá desáté skupině zachycení, tedy té nejvíce uvnitř.

### <a name="bracket-expression"></a>Výraz závorky

Výraz závorky definuje sadu znaků a *kompletování elementy*. Když výraz závorky začíná znakem ,^ʻ, porovnávání je úspěšné, pokud žádné prvky v množině neodpovídají aktuálnímu znaku v cílové sekvenci. Porovnání je jinak úspěšné, pokud jakýkoli z prvků v množině odpovídá aktuálnímu prvku v cílové sekvenci.

Sadu znaků může být definovaná výpis libovolnou kombinaci *jednotlivé znaky*, *znak rozsahy*, *znak třídy*, *ekvivalenční třídy*, a *kompletování symboly*.

### <a name="capture-group"></a>Skupina zachycení

Skupina zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu a označuje popiskem cílový text, který odpovídá jejímu obsahu. Popisek, který je spojen s každou skupinou zachycení, je číslo, které je určeno výpočtem úvodních závorek, jež označují skupiny zachycení až do úvodní závorky včetně, která označuje aktuální skupinu zachycení. V této implementaci je maximální počet skupin zachycení 31.

Příklady:

- „ab+“ odpovídá cílové sekvenci „abb“, ale neodpovídá cílové sekvenci „abab“.

- „(ab)+“ neodpovídá cílové sekvenci „abb“, ale odpovídá cílové sekvenci „abab“.

- „((a+)(b+))(c+)“ odpovídá cílové sekvenci „aabbbc“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „aabbb“, skupinu zachycení 2 k dílčí sekvenci „aa“, skupinu zachycení 3 k dílčí sekvenci „bbb“ a skupinu zachycení 4 k dílčí sekvenci „c“.

### <a name="character-class"></a>Třída znaků

Třída znaků ve výrazu závorky přidá všechny znaky v pojmenované třídě do množiny znaků, která je definována výrazem závorky. Chcete-li vytvořit třídu znaků, použijte „[:“, dále název třídy a nakonec „:]“. Interně jsou názvy tříd znaků rozpoznány voláním `id = traits.lookup_classname`. Znak `ch` patří takové na třídu, pokud `traits.isctype(ch, id)` vrací hodnotu true. Výchozí hodnota `regex_traits` šablona podporuje názvy tříd v následující tabulce.

|Název třídy|Popis|
|----------------|-----------------|
|„alnum“|malá písmena, velká písmena a číslice|
|„alpha“|malá písmena a velká písmena|
|„blank“|mezera nebo tabulátor|
|„cntrl“|*souboru formátu řídicí* znaků|
|„digit“|číslice|
|„graph“|malá písmena, velká písmena, číslice a interpunkce|
|„lower“|malá písmena|
|„print“|malá písmena, velká písmena, číslice, interpunkce a mezera|
|„punct“|interpunkce|
|„space“|mezera|
|„upper“|velká písmena|
|„xdigit“|číslice, „a“, „b“, „c“, „d“, „e“, „f“, „A“, „B“, „C“, „D“, „E“, „F“|
|"d"|stejné jako digit|
|"s"|stejné jako space|
|„w“|stejné jako alnum|

### <a name="character-range"></a>Rozsah znaků

Rozsah znaků ve výrazu závorky přidá všechny znaky v rozsahu do množiny znaků, která je definována výrazem závorky. Chcete-li vytvořit rozsah znaků, umístěte znak „-“ mezi první a poslední znak v rozsahu. Umístíte tak do množiny všechny znaky, které mají číselnou hodnotu větší nebo rovnu číselné hodnotě prvního znaku a menší nebo rovnu číselné hodnotě posledního znaku. Všimněte si, že tato množina přidaných znaků závisí na reprezentaci znaků konkrétní platformy. Pokud se znak ,-ʻ vyskytuje na začátku nebo na konci výrazu závorky nebo jako první nebo poslední znak rozsahu znaků, představuje sám sebe.

Příklady:

- „[0-7]“ představuje množinu znaků {'0', '1', '2', '3', '4', '5', ' 6', ' 7'}. Odpovídá cílovým sekvencím „0“, „1“ atd., ale nikoli „a“.

- V systémech, které používají kódování ASCII, představuje „[h-k]“ množinu znaků { 'h', 'i', 'j', 'k' }. Odpovídá cílovým sekvencím „h“, „i“ atd., ale nikoli „\x8A“ nebo „0“.

- V systémech, které používají kódování EBCDIC, představuje „[h-k]“ množinu znaků { 'h', 'i', '\x8A', '\x8B', '\x8C', '\x8D', '\x8E', '\x8F', '\x90', 'j', 'k' } ('h' je kódováno jako 0x88 a 'k' je kódováno jako 0x92). Odpovídá cílovým sekvencím „h“, „i“, „\x8A“ atd., ale nikoli „0“.

- „[-0-24]“ představuje množinu znaků { '-', '0', '1', '2', '4' }.

- „[0-2-]“ představuje množinu znaků { '0', '1', '2', '-' }.

- V systémech, které používají kódování ASCII, představuje „[+--]“ množinu znaků { '+', ',', '-' }.

Pokud používáte rozsahy citlivé na národní prostředí, jsou znaky v rozsahu určeny kolačními pravidly pro dané národní prostředí. V šabloně jsou znaky, které se kompletují za prvním znakem v definici rozsahu a před posledním znakem v definici rozsahu. V množině jsou také dva koncové znaky.

### <a name="collating-element"></a>Kolační prvek

Kolační prvek je sekvence více znaků, která je zpracovávána jako jeden znak.

### <a name="collating-symbol"></a>Kolační symbol

Přidá symbol kompletování ve výrazu závorky *kompletování element* do sady, který je definován výrazem závorky. Chcete-li vytvořit kompletování symbol, použijte "[." následovaný kompletování element následuje ".]".

### <a name="control-escape-sequence"></a>Řídicí sekvence

Řídicí sekvence je zpětné lomítko následované písmenem „c“ a poté jedním z písmen od „a“ do „z“ nebo od „A“ do „Z“. Odpovídá řídicímu znaku ASCII, který je pojmenován podle daného písmena. Příklad: "\ci" odpovídá pořadí cíl "\x09", protože \<ctrl-i > má hodnotu 0x09.

### <a name="dsw-character-escape"></a>Řídicí znak DSW

Řídicí znak dsw je krátký název pro třídu znaků, jak je znázorněno v následující tabulce.

|Řídicí sekvence|Třída s ekvivalentním názvem|Třída s výchozím názvem|
|---------------------|----------------------------|-------------------------|
|„\d“|„[[:d:]]“|„[[:digit:]]“|
|„\D“|„[^[:d:]]“|„[^[:digit:]]“|
|„\s“|„[[:s:]]“|„[[:space:]]“|
|„\S“|„[^[:s:]]“|„[^[:space:]]“|
|„\w“|„[[:w:]]“|„[a-zA-Z0-9_]“*|
|„\W“|„[^[:w:]]“|„[^a-zA-Z0-9_]“*|

*znaková sada ASCII

### <a name="equivalence-class"></a>Třída ekvivalence

Přidá třídu ekvivalenční ve výrazu závorky všechny znaky a *kompletování elementy* , které jsou ekvivalentem kompletování elementu v definici třídy ekvivalenční do sady, který je definován výrazem závorky. Chcete-li vytvořit třídu ekvivalence, použijte „[=“, dále kolační prvek a nakonec „=]“. Interně dva elementy kompletování `elt1` a `elt2` odpovídají Pokud `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Řídicí znak formátu souboru

Řídicí formát souboru se skládá z obvykle C jazyk znak – řídicí sekvence, "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Tyto mají obvykle významy, to znamená, zpětné lomítko, výstrahy, backspace, informační kanál formuláře, nového řádku, znaky CR, vodorovné kartě a vertikální tabulátor, v uvedeném pořadí. V `ECMAScript`, "\a" a "\b" nejsou povoleny. ("\\\\" je povolena, ale je identity řídicí, není řídicí formátu souboru).

### <a name="hexadecimal-escape-sequence"></a>Šestnáctková řídicí sekvence

Šestnáctková řídicí sekvence je zpětné lomítko následované písmenem „x“ a dvěma šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí dvou číslic. Například „\x41“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="identity-escape"></a>Řídicí znak identity

Řídicí znak identity je zpětné lomítko následované jedním znakem. Odpovídá danému znaku. Je vyžadován, když má znak zvláštní význam; pomocí řídicího znaku identity je zvláštní výraz odebrán. Příklad:

- "\*" odpovídá pořadí cíl "aaa", ale neodpovídá cílové sekvence "\*".

- "\\\*" neodpovídá cílové sekvence "aaa", ale odpovídá pořadí cíl "\*".

Množina znaků, které jsou v řídicím znaku identity povoleny, závisí na gramatice regulárního výrazu, viz následující tabulka.

|Gramatika|Povolené řídicí znaky identity|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended` Plus {' "', '/'}|
|`ECMAScript`|Všechny znaky kromě těch, které mohou být součástí identifikátoru. Obvykle obsahuje písmena, číslice, '$', '\_' a unicode řídicí sekvence. Další informace naleznete ve specifikacích jazyka ECMAScript.|

### <a name="individual-character"></a>Jednotlivý znak

Jednotlivý znak ve výrazu závorky přidá daný znak do množiny znaků, která je definována výrazem závorky. Kdekoli ve výrazu závorky s výjimkou na začátku představuje znak '^' sám sebe.

Příklady:

- „[abc]“ odpovídá cílové sekvenci „a“, „b“ a „c“, ale nikoli sekvenci „d“.

- „[^abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“ nebo „c“.

- „[a^bc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „^“, ale nikoli cílové sekvenci „d“.

Ve všech gramatika regulární výraz s výjimkou `ECMAScript`, pokud ']' je první znak, který následuje otevření ' [' nebo je první znak, který následuje počátečního ' ^', představuje sám sebe.

Příklady:

- „[]a“ je neplatné, protože není k dispozici žádný znak ']' pro ukončení výrazu závorky.

- „[]abc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „]“, ale nikoli cílové sekvenci „d“.

- „[^]abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“, „c“ nebo „]“.

V `ECMAScript`, použijte '\\]' představující znak ']' ve výrazu závorky.

Příklady:

- „[]a“ odpovídá cílové sekvenci „a“, protože výraz závorky je prázdný.

- "[\\] abc]" odpovídá pořadí cíl "a", "b", "c" a "]", ale není pořadí cíl "d".

### <a name="negative-assert"></a>Záporný kontrolní výraz

Záporný kontrolní výraz odpovídá všemu kromě svého obsahu. Nespotřebovává žádné znaky v cílové sekvenci. Například "(! aa)(a*)" odpovídá pořadí cíl "a" a partnerů zachycení skupina 1 se dalším "a". Neodpovídá cílové sekvenci „aa“, ale cílové sekvenci „aaa“.

### <a name="negative-word-boundary-assert"></a>Záporný kontrolní výraz hranice slova

Assert hranic záporná word odpovídá, pokud aktuální pozici v cílový řetězec není ihned po *hranice slova*.

### <a name="non-capture-group"></a>Skupina bez zachycení

Skupina bez zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu, ale neoznačuje popiskem cílový text. Například "(a)(?:b)\*(c)" odpovídá cílové textu "abbc" a přidruží zachycení skupina 1 dalším ""a zachycení skupiny 2 s dalším "c".

### <a name="non-greedy-repetition"></a>Opakování bez metody Greedy

Opakování bez metody Greedy spotřebovává nejkratší dílčí sekvenci cílové sekvence, která odpovídá vzoru. Opakování s metodou Greedy spotřebovává nejdelší sekvenci. Například "(a+) (\*b)" odpovídá pořadí cíl "aaab". Je-li použito opakování bez metody Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „a“ na začátku cílové sekvence a skupinu zachycení 2 k dílčí sekvenci „aab“ na konci cílové sekvence. Je-li použita shoda s metodou Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „aaa“ a skupinu zachycení 2 k dílčí sekvenci „b“.

### <a name="octal-escape-sequence"></a>Osmičková řídicí sekvence

Osmičková řídicí sekvence je zpětné lomítko následované jednou, dvěma nebo třemi osmičkovými číslicemi (0-7). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí těchto číslic. Jsou-li všechny číslice „0“, sekvence je neplatná. Například „\101“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="ordinary-character"></a>Běžný znak

Běžný znak je jakýkoli platný znak, který nemá v aktuální gramatice zvláštní význam.

V `ECMAScript`, mají zvláštní význam následující znaky:

- ^  $  \  .  *  +  ?  (  )  [  ]  {  }  &#124;

V `basic` a `grep`, mají zvláštní význam následující znaky:

- .   [   \

Také v `basic` a `grep`, následující znaky mají zvláštní význam, když jsou použity v určitém kontextu:

- '\*"mají zvláštní význam ve všech případech kromě případů, kdy je první znak v regulárním výrazu nebo prvního znaku, který následuje počátečního ' ^' v regulárním výrazu, nebo pokud je první znak digitalizace skupiny nebo první znak, Následuje počátečního ' ^ "ve skupině pro zachycení.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

V `extended`, `egrep`, a `awk`, mají zvláštní význam následující znaky:

- .   [   \   (   *   +   ?   {   &#124;

Také v `extended`, `egrep`, a `awk`, následující znaky mají zvláštní význam, když jsou použity v určitém kontextu.

- ') má zvláštní význam v případě, že odpovídá předchozímu znaku '('.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

Běžný znak odpovídá stejnému znaku v cílové sekvenci. Ve výchozím nastavení to znamená, že porovnání se zdaří, pokud jsou dva znaky zastoupeny stejnou hodnotou. V rozlišování velikosti písmen shodu, dva znaky `ch0` a `ch1` splněno, pokud `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. V porovnání závislé na národním prostředí se dva znaky `ch0` a `ch1` splněno, pokud `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Kladný kontrolní výraz

Kladný kontrolní výraz odpovídá svému obsahu, ale nespotřebovává žádné znaky v cílové sekvenci.

Příklady:

- "(=AA) (\*)" odpovídá pořadí cíl "aaaa" a přidruží k dalším "aaaa" zachycení skupina 1.

- "(aa) (\*)" odpovídá pořadí cíl "aaaa" a přidruží zachycení skupina 1 s dalším "aa" na začátku cílové pořadí a zachycení skupiny 2 s dalším "aa" na konci pořadí cíl.

- "(=aa)(a)&#124;(a)" odpovídá pořadí cíl "a" a partnerů zachycení skupina 1 prázdnou sekvencí (protože se nezdařilo kladné assert) a zachycení skupiny 2 se dalším "a". Také odpovídá cílové sekvenci „aa“ a přiřadí skupinu zachycení 1 k dílčí sekvenci „aa“ a skupinu zachycení 2 k prázdné sekvenci.

### <a name="unicode-escape-sequence"></a>Řídicí sekvence Unicode

Řídicí sekvence Unicode je zpětné lomítko následované písmenem „u“ a čtyřmi šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí čtyř číslic. Například „\u0041“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="wildcard-character"></a>Zástupný znak

Zástupný znak odpovídá libovolnému znaku v cílovém výrazu, s výjimkou nového řádku.

### <a name="word-boundary"></a>Hranice slova

Hranice slova se vyskytuje v následujících situacích:

- Aktuální znak na začátek pořadí cíl a je mezi znaky aplikace word `A-Za-z0-9_.`

- Aktuální poloha znaku je za koncem cílové sekvence a poslední znak v cílové sekvenci je jedním ze znaků slova.

- Aktuální znak je jedním ze znaků slova a předchozí znak není.

- Aktuální znak není jedním ze znaků slova a předchozí znak je.

### <a name="word-boundary-assert"></a>Kontrolní výraz hranice slova

Odpovídá assert hranic word při aktuální pozici v cílový řetězec ihned po *hranice slova*.

## <a name="matchingandsearching"></a> Porovnávání a vyhledávání

Aby regulární výraz odpovídal cílové sekvenci, musí celý regulární výraz odpovídat celé cílové sekvenci. Například regulární výraz „bcd“ odpovídá cílové sekvenci „bcd“, ale nikoli cílové sekvenci „abcd“ ani cílové sekvenci „bcde“.

Aby hledání regulárního výrazu bylo úspěšné, někde v cílové sekvenci se musí nacházet dílčí sekvence, která odpovídá regulárnímu výrazu. Hledání obvykle najde odpovídající dílčí sekvenci nejvíce vlevo.

Příklady:

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcd" je úspěšné a odpovídá celé sekvenci. Stejné vyhledávání v cílové sekvenci "abcd" je také úspěšné a odpovídá posledním třem znakům. Stejné vyhledávání v cílové sekvenci "bcde" je také úspěšné a odpovídá prvním třem znakům.

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcdbcd" je úspěšné a odpovídá prvním třem znakům.

Pokud existuje více než jedna dílčí sekvence, která odpovídá v určitém umístění cílové sekvence, můžete odpovídající vzor vybrat dvěma způsoby. *Nejprve odpovídat* zvolí dalším, která byla nalezena první, pokud je nalezena shoda s regulárním výrazem. *Nejdéle odpovídat* zvolí nejdelší dalším od těch, které odpovídají v tomto umístění. Pokud existuje více než jedna dílčí sekvence, která má maximální délku, nejdelší shoda zvolí tu, která byla nalezena jako první. Například když se použije první shodu, vyhledejte regulární výraz "b&#124;bc" v cílové pořadí "abcd" odpovídá dalším "b", protože levé období alternace odpovídá této dalším; první shodu proto, zkuste není pravé období alternace. Při použití nejdelší shody stejné vyhledávání odpovídá „bc“, protože „bc“ je delší než „b“.

Částečná shoda bude úspěšná, pokud shoda dosáhne konce cílové sekvence bez selhání, i když nedosáhla konce regulárního výrazu. Proto by po úspěchu částečné shody mohlo připojení znaků k cílové sekvenci způsobit pozdější selhání částečné shody. Po neúspěchu částečné shody však připojení znaků k cílové sekvenci nemůže způsobit pozdější úspěch částečné shody. Například v případě částečné shody odpovídá „ab“ cílové sekvenci „a“, ale nikoli „ac“.

## <a name="formatflags"></a> Příznaky formátu

|Pravidla formátu jazyka ECMAScript|Pravidla formátu SED|Náhradní text|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Posloupnost znaků, který odpovídá celé regulární výraz (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (dolaru následované zpětné uvozovky)||Sekvence znaků, která předchází dalším, který odpovídá regulárnímu výrazu (`[match.prefix().first, match.prefix().second)`)|
|„$'“ (znak dolaru následovaný počáteční uvozovkou)||Posloupnost znaků, který následuje dalším, který odpovídá regulárnímu výrazu (`[match.suffix().first, match.suffix().second)`)|
|„$n“|„\n“|Posloupnost znaků, který odpovídá skupině zachycení na pozici `n`, kde `n` je číslo mezi 0 a 9 (`[match[n].first, match[n].second)`)|
||"\\\n"|„\n“|
|„$nn“||Posloupnost znaků, který odpovídá skupině zachycení na pozici `nn`, kde `nn` je v rozmezí 10 až 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
