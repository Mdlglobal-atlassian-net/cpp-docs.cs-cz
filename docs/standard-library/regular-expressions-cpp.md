---
title: Regulární výrazy (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, regular expressions
- regular expressions, Visual C++
- regular expressions
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca3d636b1dffdb3237fb94fade41c90057543b9d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861561"
---
# <a name="regular-expressions-c"></a>Regulární výrazy (C++)

Standardní knihovny C++ podporuje více gramatikách regulárního výrazu. Toto téma popisuje gramatiku změny k dispozici při používání regulárních výrazů.

## <a name="regexgrammar"></a> Gramatika regulárních výrazů

Gramatika regulárních výrazů používat podle určena pomocí jednoho z `std::regex_constants::syntax_option_type` hodnot výčtu. Tyto gramatikách regulárního výrazu jsou definovány v std::regex_constants:

- `ECMAScript`: Toto je nejblíže gramatiky používá JavaScript a jazyky .NET.
- `basic`: Základní regulární výrazy POSIX nebo BRE.
- `extended`: POSIX rozšířené regulární výrazy nebo ERE.
- `awk`: Toto je `extended`, ale má další řídicí sekvence pro netisknutelné znaky.
- `grep`: Toto je `basic`, ale umožňuje také znaku nového řádku ('\n') znaků k oddělení alternací.
- `egrep`: Toto je `extended`, ale umožňuje také znaky nového řádku k oddělení alternací.

Ve výchozím nastavení, pokud není zadána žádná gramatika `ECMAScript` se předpokládá, že. Je možné zadat jenom jedna gramatika.

Kromě gramatiku můžete použít několik příznaků:
- `icase`: Ignorujte velikost písmen při porovnávání.
- `nosubs`: Ignorujte označené shody (tj. výrazy v závorkách); jsou uloženy žádné nahrazení.
- `optimize`: Ujistěte se, rychlejší, odpovídající na úkor větší době konstrukce.
- `collate`: Použijte v pořadí řazení citlivé na národní prostředí (například. rozsahy ve formátu "[a-z]").

Nula nebo více příznaků lze kombinovat s gramatiky k určení chování modulu regulárních výrazů. Pokud pouze příznaky jsou zadané, `ECMAScript` se předpokládá, že jako gramatiky.

### <a name="element"></a>Prvek

Prvek může být jeden z následujících:

- *Běžný znak* , který odpovídá stejnému znaku v cílové sekvenci.

- A *zástupný znak* '.', který odpovídá libovolnému znaku v cílové sekvenci, s výjimkou nového řádku.

- A *párování výraz* ve formátu "[`expr`]", který odpovídá znaku nebo prvku kolace v cílové sekvenci, která je také do množiny definované výrazem `expr`, nebo ve formátu "[^`expr`]", který odpovídá znaku nebo prvku kolace v cílové sekvenci, který není v sadě definována výrazem `expr`.

   Výraz `expr` může obsahovat libovolnou kombinaci následujících akcí:

   - Jednotlivý znak. Přidá daný znak do množiny definované `expr`.

   - A *rozsah znaků* ve tvaru "`ch1`-`ch2`". Přidá znaky, které jsou reprezentovány hodnotami v uzavřeném intervalu [`ch1`, `ch2`] do množiny definované `expr`.

   - A *třídy znaků* ve formátu "[:`name`:]". Přidá znaky v pojmenované třídě do množiny definované `expr`.

   - *Třída ekvivalence* ve formátu "[=`elt`=]". Přidá kolační prvky, které jsou ekvivalentem `elt` do množiny definované `expr`.

   - A *kolační symbol* ve formátu "[.`elt`.]". Přidá kolační prvek `elt` do množiny definované `expr`.

- *Ukotvení*. Ukotvení „^“ odpovídá začátku cílové sekvence; ukotvení „$“ odpovídá konci cílové sekvence.

A *skupina zachycení* ve formátu "( *dílčí výraz* )", nebo "\\( *dílčí výraz* \\)" v `basic` a `grep`, který odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači.

- *Řídicí znak identity* ve tvaru "\\`k`", který odpovídá znaku `k` v cílové sekvenci.

Příklady:

- „a“ odpovídá cílové sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

- „.“ odpovídá všem cílovým sekvencím „a“, „B“, „b“ a „c“.

- „[b-z]“ odpovídá cílovým sekvencím „b“ a „c“, ale neodpovídá cílovým sekvencím „a“ nebo „B“.

- „[:lower:]“ odpovídá cílovým sekvencím „a“, „b“ a „c“, ale neodpovídá cílové sekvenci „B“.

- „(a)“ odpovídá cílové sekvenci „a“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

V `ECMAScript`, `basic`, a `grep`, element může být také *zpětný odkaz* ve tvaru "\\`dd`", kde `dd` představuje desítkovou hodnotu N, která odpovídá posloupnosti znaky v cílové sekvenci, který je stejný jako posloupnost znaků, které odpovídá n-té *skupina zachycení*. Například „(a)\1“ odpovídá cílové sekvenci „aa“, protože první (a jediná) skupina zachycení odpovídá počáteční sekvenci „a“ a \1 odpovídá závěrečné sekvenci „a“.

V `ECMAScript`, element může být také jednu z následujících akcí:

- A *skupina bez zachycení* ve formátu "(?: *dílčí výraz* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači.

- Omezené *řídicí znak formátu souboru* z formátu "\f", "\n", "\r", "\t" nebo "\v". Tyto odpovídají znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- A *kladný kontrolní výraz* ve formátu "(= *dílčí výraz* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači, ale nemění pozici shody v cílové sekvenci.

- A *záporný kontrolní výraz* ve formátu "(! *dílčí výraz* ) ". Odpovídá jakékoli sekvenci znaků v cílové sekvenci, která neodpovídá vzorci mezi oddělovači a nemění pozici shody v cílové sekvenci.

- A *šestnáctková řídicí sekvence* ve formátu "\x`hh`". Odpovídá znaku v cílové sekvenci, který je reprezentován dvěma šestnáctkovými číslicemi `hh`.

- A *řídicí sekvence unicode* ve formátu "\u`hhhh`". Odpovídá znaku v cílové sekvenci, který je reprezentován čtyřmi šestnáctkovými číslicemi `hhhh`.

- A *řídit řídicí sekvence* ve formátu "\c`k`". Odpovídá řídicímu znaku, který je pojmenován podle znaku `k`.

- A *výraz hranice slova* ve formátu "\b". Odpovídá, pokud aktuální pozice v cílové sekvenci je ihned po *hranice slova*.

- A *kontrolní výraz hranice slova negativní* ve formátu "\B". Odpovídá, pokud aktuální pozice v cílové sekvenci je ihned po *hranice slova*.

- A *řídicí znak dsw* ve formátu "\d", "\D", "\s", "\S", "\w", "\W". Poskytuje krátký název pro třídu znaků.

Příklady:

- „(?:a)“ odpovídá cílové sekvenci „a“, ale „(?:a) \1“ je neplatné, protože není k dispozici žádná skupina zachycení 1.

- "(=a)" odpovídá cílové sekvenci "a". Kladný kontrolní výraz odpovídá počáteční sekvenci „a“ v cílové sekvenci a závěrečné „a“ v regulárním výrazu odpovídá počáteční sekvenci „a“ v cílové sekvenci.

- "(!a)" neodpovídá cílové sekvenci "a".

- "a\b." odpovídá cílové sekvenci "~", ale neodpovídá cílové sekvenci "ab".

- "a\B." odpovídá cílové sekvenci "ab", ale neodpovídá cílové sekvenci "~".

V `awk`, element může být také jednu z následujících akcí:

- A *řídicí znak formátu souboru* ve tvaru "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" nebo "\v". Tyto odpovídají zpětnému lomítku, upozornění, klávese Backspace, znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- *Osmičkové řídicí sekvence* ve tvaru "\\`ooo`". Odpovídá znaku v cílové sekvenci, jehož vyjádření je hodnota reprezentovaná jeden, dvěma nebo třemi osmičkovými číslicemi `ooo`.

### <a name="repetition"></a>Opakování

Libovolný prvek jiný než *kladný kontrolní výraz*, *záporný kontrolní výraz*, nebo *ukotvení* může být následován počtem opakování. Nejobecnější typ počtu opakování má podobu "{`min`,`max`}", nebo "\\{`min`,`max`\\}" v `basic` a `grep`. Element, který je následován touto formou počtu opakování, odpovídá minimálně `min` po sobě jdoucím výskytům a ne více než `max` po sobě jdoucím výskytům sekvence, která odpovídá elementu. Například "{2,3}" odpovídá cílové sekvenci "aa" a cílové sekvenci "aaa", ale nikoli cílové sekvenci "a" nebo cílové sekvenci "aaaa".

Počet opakování může mít také jednu z následujících forem:

- "{`min`}", nebo "\\{`min`\\}" v `basic` a `grep`. Ekvivalentní "{`min`,`min`}".

- "{`min`,}", nebo "\\{`min`,\\}" v `basic` a `grep`. Ekvivalentní "{`min`, unbounded}".

- "\*". Ekvivalentní „{0,unbounded}“.

Příklady:

- "{2}" odpovídá cílové sekvenci "aa", ale nikoli cílové sekvenci "a" nebo cílové sekvenci "aaa".

- "{2,}" odpovídá cílové sekvenci "aa", cílové sekvenci "aaa" a tak dále, ale neodpovídá cílové sekvenci "a".

- "\*" odpovídá cílové sekvenci "", cílové sekvenci "a", cílové sekvenci "aa" a tak dále.

Pro všechny gramatiky s výjimkou `basic` a `grep`, počet opakování může mít také jednu z následujících forem:

- "?". Ekvivalentní "{0,1}".

- "+". Ekvivalentní "{1, unbounded}".

Příklady:

- "a"? odpovídá cílové sekvenci "" a cílové sekvenci "a", ale nikoli cílové sekvenci "aa".

- „a+“ odpovídá cílové sekvenci „a“, cílové sekvenci „aa“ atd., ale nikoli cílové sekvenci „“.

V `ECMAScript`, všemi formami počtu opakování může následovat znak "?", který udává *opakování bez metody greedy*.

### <a name="concatenation"></a>Zřetězení

Prvky regulárního výrazu, s nebo bez něj *počtů opakování*, mohou být zřetězeny do delších regulárních výrazů. Výsledný výraz odpovídá cílové sekvenci, která je zřetězením sekvencí odpovídajících jednotlivým prvkům. Například "{2,3}b" odpovídá cílové sekvenci "aab" a cílové sekvenci "aaab", ale neodpovídá cílové sekvenci "ab" nebo cílové sekvenci "aaaab".

### <a name="alternation"></a>Alternace

Ve všech gramatikách regulárního výrazu s výjimkou `basic` a `grep`, může za zřetězeným regulárním výrazem následovat znak "&#124;" a jiný zřetězený regulární výraz. Tímto způsobem lze spojit libovolný počet zřetězených regulárních výrazů. Výsledný výraz odpovídá jakékoli cílové sekvenci, která odpovídá jednomu nebo více zřetězeným regulárním výrazům.

Když více zřetězeným regulárním výrazům odpovídá cílové sekvenci, `ECMAScript` vybere první ze zřetězených regulárních výrazů, který odpovídá sekvenci jako shodu (*první shoda*); druhé Vyberte si metodu, která dosahuje gramatikách regulárního výrazu *nejdelší shody*. Například "ab&#124;cd" odpovídá cílové sekvenci "ab" a cílové sekvenci "cd", ale neodpovídá cílové sekvenci "abd" nebo cílové sekvenci "acd".

V `grep` a `egrep`, lze znak nového řádku ('\n') lze použít k oddělení alternací.

### <a name="subexpression"></a>Dílčí výraz

V `basic` a `grep`, je dílčí výraz zřetězení. V ostatních gramatikách regulárního výrazu je dílčí výraz změnou.

## <a name="grammarsummary"></a> Souhrn gramatiky

Následující tabulka shrnuje funkce, které jsou k dispozici v různých gramatikách regulárního výrazu:

|Prvek|Základní|rozšířené|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternace pomocí "&#124;.||+|+||+|+|
|alternace pomocí „\n“||||+|+||
|ukotvení|+|+|+|+|+|+|
|zpětný odkaz|+||+|+|||
|výraz závorky|+|+|+|+|+|+|
|skupina zachycení používající „()“||+|+||+|+|
|Skupina zachycení používající "\\(\\)"|+|||+|||
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
|opakování pomocí "\*.|+|+|+|+|+|+|
|opakování pomocí „?“ a „+“||+|+||+|+|
|řídicí sekvence Unicode|||+||||
|zástupný znak|+|+|+|+|+|+|
|kontrolní výraz hranice slova|||+||||

## <a name="semanticdetails"></a> Sémantické podrobnosti

### <a name="anchor"></a>Ukotvení

Ukotvení odpovídá pozici v cílovém řetězci, nikoli znaku. „^“ odpovídá začátku cílového řetězce; „$“ odpovídá konci cílového řetězce.

### <a name="back-reference"></a>Zpětný odkaz

Zpětný odkaz je zpětné lomítko, za kterým následuje Desítková hodnota N. Odpovídá obsahu n-té *skupina zachycení*. Hodnota N nesmí být větší než počet skupin zachycení, které zpětnému odkazu předcházejí. V `basic` a `grep`, je hodnota n určena podle desítková číslice, který následuje za zpětným lomítkem. V `ECMAScript`, hodnota N je určena všemi desítkovými čísly, které bezprostředně následují zpětné lomítko. Proto v `basic` a `grep`, je hodnota N se nikdy víc než 9, i když má více než devět skupin zachycení regulárních výrazů. V `ECMAScript`, je hodnota N je bez vazby.

Příklady:

- „((a+)(b+))(c+)\3“ odpovídá cílové sekvenci „aabbbcbbb“. Zpětný odkaz „\3“ odpovídá textu ve třetí skupině zachycení, tedy „(b+)“. Neodpovídá cílové sekvenci „aabbbcbb“.

- „(a)\2“ není platné.

- "(b (((a))) \10" má v různé významy `basic` a `ECMAScript`. V `basic` je zpětný odkaz "\1". Zpětný odkaz odpovídá obsahu první skupiny zachycení (to znamená skupiny, která začíná na „(b“ a končí posledním znakem „)“ a předchází zpětnému odkazu) a závěrečný znak 0 odpovídá běžnému znaku 0. V `ECMAScript`, je zpětný odkaz "\10". Odpovídá desáté skupině zachycení, tedy té nejvíce uvnitř.

### <a name="bracket-expression"></a>Výraz závorky

Výraz závorky definuje množinu znaků a *kolační prvky*. Když výraz závorky začíná znakem ,^ʻ, porovnávání je úspěšné, pokud žádné prvky v množině neodpovídají aktuálnímu znaku v cílové sekvenci. Porovnání je jinak úspěšné, pokud jakýkoli z prvků v množině odpovídá aktuálnímu prvku v cílové sekvenci.

Množinu znaků lze definovat uvedením jakékoli kombinace *jednotlivých znaků*, *znak rozsahy*, *znaku třídy*, *ekvivalence třídy*, a *kolačních symbolů*.

### <a name="capture-group"></a>Skupina zachycení

Skupina zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu a označuje popiskem cílový text, který odpovídá jejímu obsahu. Popisek, který je spojen s každou skupinou zachycení, je číslo, které je určeno výpočtem úvodních závorek, jež označují skupiny zachycení až do úvodní závorky včetně, která označuje aktuální skupinu zachycení. V této implementaci je maximální počet skupin zachycení 31.

Příklady:

- „ab+“ odpovídá cílové sekvenci „abb“, ale neodpovídá cílové sekvenci „abab“.

- „(ab)+“ neodpovídá cílové sekvenci „abb“, ale odpovídá cílové sekvenci „abab“.

- „((a+)(b+))(c+)“ odpovídá cílové sekvenci „aabbbc“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „aabbb“, skupinu zachycení 2 k dílčí sekvenci „aa“, skupinu zachycení 3 k dílčí sekvenci „bbb“ a skupinu zachycení 4 k dílčí sekvenci „c“.

### <a name="character-class"></a>Třída znaků

Třída znaků ve výrazu závorky přidá všechny znaky v pojmenované třídě do množiny znaků, která je definována výrazem závorky. Chcete-li vytvořit třídu znaků, použijte „[:“, dále název třídy a nakonec „:]“. Vnitřně jsou názvy tříd znaků rozpoznávány voláním `id = traits.lookup_classname`. Znak `ch` patří do takové třídy, pokud `traits.isctype(ch, id)` vrací hodnotu true. Výchozí hodnota `regex_traits` šablona podporuje názvy tříd v následující tabulce.

|Název třídy|Popis|
|----------------|-----------------|
|„alnum“|malá písmena, velká písmena a číslice|
|„alpha“|malá písmena a velká písmena|
|„blank“|mezera nebo tabulátor|
|„cntrl“|*řídicí znak formátu souboru* znaků|
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

Kolační symbol ve výrazu závorky přidá *kolační prvek* do sady, která je definována výrazem závorky. Chcete-li vytvořit kolační symbol, použijte "[." dále kolační prvek a nakonec "."].

### <a name="control-escape-sequence"></a>Řídicí sekvence

Řídicí sekvence je zpětné lomítko následované písmenem „c“ a poté jedním z písmen od „a“ do „z“ nebo od „A“ do „Z“. Odpovídá řídicímu znaku ASCII, který je pojmenován podle daného písmena. Například "\ci" odpovídá cílové sekvenci "\x09", protože \<ctrl-i > má hodnotu 0x09.

### <a name="dsw-character-escape"></a>Řídicí znak DSW

Řídicí znak dsw je krátký název pro třídu znaků, jak je znázorněno v následující tabulce.

|Řídicí sekvence|Třída s ekvivalentním názvem|Třída s výchozím názvem|
|---------------------|----------------------------|-------------------------|
|„\d“|„[[:d:]]“|„[[:digit:]]“|
|„\D“|„[^[:d:]]“|„[^[:digit:]]“|
|„\s“|„[[:s:]]“|„[[:space:]]“|
|„\S“|„[^[:s:]]“|„[^[:space:]]“|
|„\w“|„[[:w:]]“|"[-zA-Z0-9_]"\*|
|„\W“|„[^[:w:]]“|"[^-zA-Z0-9_]"\*|

\*Znaková sada ASCII

### <a name="equivalence-class"></a>Třída ekvivalence

Třída ekvivalence ve výrazu závorky přidá všechny znaky a *kolační prvky* , které jsou ekvivalentní kolačnímu prvku v definici třídy ekvivalence množině, která je definována výrazem závorky. Chcete-li vytvořit třídu ekvivalence, použijte „[=“, dále kolační prvek a nakonec „=]“. Interně jsou dva kolační prvky `elt1` a `elt2` jsou ekvivalentní Pokud `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Řídicí znak formátu souboru

Řídicí znak formátu souboru se skládá z obvyklé C jazyka znak sekvence escape, "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Ty mají obvyklý význam, to znamená, zpětné lomítko, upozornění, backspace, posun, nový řádek, návrat vozíku, horizontálního tabulátoru a vertikální tabulátor. V `ECMAScript`, "\a" a "\b" nejsou povoleny. ("\\\\" může, ale je řídicí znak identity, ne řídicí znak formátu souboru).

### <a name="hexadecimal-escape-sequence"></a>Šestnáctková řídicí sekvence

Šestnáctková řídicí sekvence je zpětné lomítko následované písmenem „x“ a dvěma šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí dvou číslic. Například „\x41“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="identity-escape"></a>Řídicí znak identity

Řídicí znak identity je zpětné lomítko následované jedním znakem. Odpovídá danému znaku. Je vyžadován, když má znak zvláštní význam; pomocí řídicího znaku identity je zvláštní výraz odebrán. Příklad:

- "\*" odpovídá cílové sekvenci "aaa", ale neodpovídá cílové sekvenci "\*".

- "\\\*" neodpovídá cílové sekvenci "aaa", ale odpovídá cílové sekvenci "\*".

Množina znaků, které jsou v řídicím znaku identity povoleny, závisí na gramatice regulárního výrazu, viz následující tabulka.

|Gramatika|Povolené řídicí znaky identity|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended` a navíc {"" ","/"}|
|`ECMAScript`|Všechny znaky kromě těch, které mohou být součástí identifikátoru. Obvykle obsahuje písmena, číslice, "$", "\_" a řídicí sekvence unicode. Další informace naleznete ve specifikacích jazyka ECMAScript.|

### <a name="individual-character"></a>Jednotlivý znak

Jednotlivý znak ve výrazu závorky přidá daný znak do množiny znaků, která je definována výrazem závorky. Kdekoli ve výrazu závorky s výjimkou na začátku představuje znak '^' sám sebe.

Příklady:

- „[abc]“ odpovídá cílové sekvenci „a“, „b“ a „c“, ale nikoli sekvenci „d“.

- „[^abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“ nebo „c“.

- „[a^bc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „^“, ale nikoli cílové sekvenci „d“.

Ve všech gramatikách regulárního výrazu s výjimkou `ECMAScript`, pokud "]" je první znak, který následuje otevírací ' [' nebo je první znak, který následuje po počátečním ' ^', představuje sám sebe.

Příklady:

- „[]a“ je neplatné, protože není k dispozici žádný znak ']' pro ukončení výrazu závorky.

- „[]abc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „]“, ale nikoli cílové sekvenci „d“.

- „[^]abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“, „c“ nebo „]“.

V `ECMAScript`, použijte '\\]' k reprezentaci znaku ']' ve výrazu závorky.

Příklady:

- „[]a“ odpovídá cílové sekvenci „a“, protože výraz závorky je prázdný.

- "[\\] [abc]" odpovídá cílovým sekvencím "a", "b", "c" a "]", ale nikoli cílové sekvenci "d".

### <a name="negative-assert"></a>Záporný kontrolní výraz

Záporný kontrolní výraz odpovídá všemu kromě svého obsahu. Nespotřebovává žádné znaky v cílové sekvenci. Například "(!aa) (\*)" odpovídá cílové sekvenci "a" a přiřazuje skupinu zachycení 1 k dílčí sekvenci "a". Neodpovídá cílové sekvenci „aa“, ale cílové sekvenci „aaa“.

### <a name="negative-word-boundary-assert"></a>Záporný kontrolní výraz hranice slova

Záporná hranice slova odpovídá, pokud aktuální pozice v cílovém řetězci nenásleduje ihned za *hranice slova*.

### <a name="non-capture-group"></a>Skupina bez zachycení

Skupina bez zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu, ale neoznačuje popiskem cílový text. Například "(a)(?:b)\*(c)" odpovídá cílovému textu "abbc" a přiřadí skupinu zachycení 1 k dílčí sekvenci ""a skupinu zachycení 2 k dílčí sekvenci "c".

### <a name="non-greedy-repetition"></a>Opakování bez metody Greedy

Opakování bez metody Greedy spotřebovává nejkratší dílčí sekvenci cílové sekvence, která odpovídá vzoru. Opakování s metodou Greedy spotřebovává nejdelší sekvenci. Například "(a+) (\*b)" odpovídá cílové sekvenci "aaab". Je-li použito opakování bez metody Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „a“ na začátku cílové sekvence a skupinu zachycení 2 k dílčí sekvenci „aab“ na konci cílové sekvence. Je-li použita shoda s metodou Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „aaa“ a skupinu zachycení 2 k dílčí sekvenci „b“.

### <a name="octal-escape-sequence"></a>Osmičková řídicí sekvence

Osmičková řídicí sekvence je zpětné lomítko následované jednou, dvěma nebo třemi osmičkovými číslicemi (0-7). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí těchto číslic. Jsou-li všechny číslice „0“, sekvence je neplatná. Například „\101“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="ordinary-character"></a>Běžný znak

Běžný znak je jakýkoli platný znak, který nemá v aktuální gramatice zvláštní význam.

V `ECMAScript`, mají následující znaky zvláštní význam:

- ^  $  \  .  \*  +  ?  (  )  \[  ]  {  }&#124;

V `basic` a `grep`, mají následující znaky zvláštní význam:

- .   \[   \

Také v `basic` a `grep`, mají následující znaky zvláštní význam, pokud jsou použity v konkrétním kontextu:

- "\*' má zvláštní význam ve všech případech, kromě případů, kdy je první znak v o regulární výraz nebo první znak, který následuje po počátečním ' ^' v regulárním výrazu, nebo pokud je to první znak digitalizace skupiny nebo první znak, který následuje po počátečním ' ^' ve skupině zachycení.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

V `extended`, `egrep`, a `awk`, mají následující znaky zvláštní význam:

- .   \[   \   (   \*   +   ?   {   &#124;

Také v `extended`, `egrep`, a `awk`, mají následující znaky zvláštní význam, pokud jsou použity v konkrétním kontextu.

- ') má zvláštní význam v případě, že odpovídá předchozímu znaku '('.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

Běžný znak odpovídá stejnému znaku v cílové sekvenci. Ve výchozím nastavení to znamená, že porovnání se zdaří, pokud jsou dva znaky zastoupeny stejnou hodnotou. Ve velkých a malých písmen, dva znaky `ch0` a `ch1` splněno, pokud `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. Porovnání citlivé na národní prostředí, dva znaky `ch0` a `ch1` splněno, pokud `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Kladný kontrolní výraz

Kladný kontrolní výraz odpovídá svému obsahu, ale nespotřebovává žádné znaky v cílové sekvenci.

Příklady:

- "(=AA) (\*)" odpovídá cílové sekvenci "aaaa" a přiřadí skupinu zachycení 1 k dílčí sekvenci "aaaa".

- "(aa) (\*)" odpovídá cílové sekvenci "aaaa" a přiřadí skupinu zachycení 1 k dílčí sekvenci "aa" na začátku k cílové sekvence a skupinu zachycení 2 k dílčí sekvenci "aa" na konci cílové sekvence.

- "(=aa)(a)&#124;(a)" odpovídá cílové sekvenci "a" a přiřazuje skupinu zachycení 1 k prázdné sekvenci (protože kladný kontrolní výraz neuspěl) a skupinu zachycení 2 k dílčí sekvenci "a". Také odpovídá cílové sekvenci „aa“ a přiřadí skupinu zachycení 1 k dílčí sekvenci „aa“ a skupinu zachycení 2 k prázdné sekvenci.

### <a name="unicode-escape-sequence"></a>Řídicí sekvence Unicode

Řídicí sekvence Unicode je zpětné lomítko následované písmenem „u“ a čtyřmi šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí čtyř číslic. Například „\u0041“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="wildcard-character"></a>Zástupný znak

Zástupný znak odpovídá libovolnému znaku v cílovém výrazu, s výjimkou nového řádku.

### <a name="word-boundary"></a>Hranice slova

Hranice slova se vyskytuje v následujících situacích:

- Aktuální znak je na začátku cílové sekvence a je jedním ze znaků slova `A-Za-z0-9_.`

- Aktuální poloha znaku je za koncem cílové sekvence a poslední znak v cílové sekvenci je jedním ze znaků slova.

- Aktuální znak je jedním ze znaků slova a předchozí znak není.

- Aktuální znak není jedním ze znaků slova a předchozí znak je.

### <a name="word-boundary-assert"></a>Kontrolní výraz hranice slova

Hranice slova odpovídá, pokud je aktuální pozice v cílovém řetězci ihned po *hranice slova*.

## <a name="matchingandsearching"></a> Párování a vyhledávání

Aby regulární výraz odpovídal cílové sekvenci, musí celý regulární výraz odpovídat celé cílové sekvenci. Například regulární výraz „bcd“ odpovídá cílové sekvenci „bcd“, ale nikoli cílové sekvenci „abcd“ ani cílové sekvenci „bcde“.

Aby hledání regulárního výrazu bylo úspěšné, někde v cílové sekvenci se musí nacházet dílčí sekvence, která odpovídá regulárnímu výrazu. Hledání obvykle najde odpovídající dílčí sekvenci nejvíce vlevo.

Příklady:

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcd" je úspěšné a odpovídá celé sekvenci. Stejné vyhledávání v cílové sekvenci "abcd" je také úspěšné a odpovídá posledním třem znakům. Stejné vyhledávání v cílové sekvenci "bcde" je také úspěšné a odpovídá prvním třem znakům.

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcdbcd" je úspěšné a odpovídá prvním třem znakům.

Pokud existuje více než jedna dílčí sekvence, která odpovídá v určitém umístění cílové sekvence, můžete odpovídající vzor vybrat dvěma způsoby. *První shoda* zvolí dílčí sekvenci, která byla nalezena jako první při regulární výraz spárován. *Nejdelší shoda* zvolí nejdelší dílčí sekvenci z těch, které v daném umístění odpovídají. Pokud existuje více než jedna dílčí sekvence, která má maximální délku, nejdelší shoda zvolí tu, která byla nalezena jako první. Například když se použije první shoda, vyhledávání regulárního výrazu "b&#124;bc" v cílové sekvenci "abcd" odpovídá dílčí sekvenci "b", protože levý termín změny odpovídá dané dílčí sekvenci; proto první shoda nepokusí pravém termín změny. Při použití nejdelší shody stejné vyhledávání odpovídá „bc“, protože „bc“ je delší než „b“.

Částečná shoda bude úspěšná, pokud shoda dosáhne konce cílové sekvence bez selhání, i když nedosáhla konce regulárního výrazu. Proto by po úspěchu částečné shody mohlo připojení znaků k cílové sekvenci způsobit pozdější selhání částečné shody. Po neúspěchu částečné shody však připojení znaků k cílové sekvenci nemůže způsobit pozdější úspěch částečné shody. Například v případě částečné shody odpovídá „ab“ cílové sekvenci „a“, ale nikoli „ac“.

## <a name="formatflags"></a> Příznaky formátu

|Pravidla formátu jazyka ECMAScript|Pravidla formátu SED|Náhradní text|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Sekvence znaků, která odpovídá celému regulárnímu výrazu (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (znak dolaru následovaný závěrečnou uvozovkou)||Sekvence znaků, která předchází dílčí sekvenci odpovídající regulárnímu výrazu (`[match.prefix().first, match.prefix().second)`)|
|„$'“ (znak dolaru následovaný počáteční uvozovkou)||Sekvence znaků, který následuje za dílčí sekvencí odpovídající regulárnímu výrazu (`[match.suffix().first, match.suffix().second)`)|
|„$n“|„\n“|Sekvence znaků, který odpovídá skupině zachycení na pozici `n`, kde `n` je číslo mezi 0 a 9 (`[match[n].first, match[n].second)`)|
||"\\\n"|„\n“|
|„$nn“||Sekvence znaků, který odpovídá skupině zachycení na pozici `nn`, kde `nn` je číslo mezi 10 a 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
