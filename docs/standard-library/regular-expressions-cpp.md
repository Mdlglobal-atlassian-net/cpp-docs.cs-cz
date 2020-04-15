---
title: Regulární výrazy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: a6ff0fafce9f4b3e029be053d27ca68d096ec108
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368518"
---
# <a name="regular-expressions-c"></a>Regulární výrazy (C++)

Standardní knihovna Jazyka C++ podporuje více gramatik regulárních výrazů. Toto téma popisuje gramatické varianty, které jsou k dispozici při použití regulárních výrazů.

## <a name="regular-expression-grammar"></a><a name="regexgrammar"></a>Gramatika regulárního výrazu

Gramatika regulárního výrazu, která se `std::regex_constants::syntax_option_type` má použít, je určena použitím jedné z hodnot výčtu. Tyto gramatiky regulárních výrazů jsou definovány v std::regex_constants:

- `ECMAScript`: Toto je nejblíže k gramatice používané jazyky JavaScript a jazyky .NET.
- `basic`: Základní regulární výrazy POSIX nebo BRE.
- `extended`: PoSIX rozšířené regulární výrazy nebo ERE.
- `awk`: Toje `extended`, ale má další úniky pro netisknutelné znaky.
- `grep`: Toje `basic`, ale také umožňuje newline ('\n') znaky oddělit alternace.
- `egrep`: To `extended`je , ale také umožňuje znaky nového řádku oddělit změny.

Ve výchozím nastavení, pokud `ECMAScript` není zadána žádná gramatika, se předpokládá. Může být zadána pouze jedna gramatika.

Kromě gramatiky lze použít několik příznaků:

- `icase`: Ignorovat případ při porovnávání.
- `nosubs`: Ignorovat označené shody (to znamená výrazy v závorce); nejsou uloženy žádné náhrady.
- `optimize`: Aby párování rychleji, na možné náklady na větší dobu výstavby.
- `collate`: Používejte sekvence řazení citlivé na národní prostředí (například rozsahy formuláře "[a-z]").

Nula nebo více příznaků může být kombinováno s gramatikou k určení chování modulu regulárních výrazů. Pokud jsou zadány `ECMAScript` pouze příznaky, předpokládá se jako gramatika.

### <a name="element"></a>Prvek

Prvek může být jeden z následujících:

- *Běžný znak,* který odpovídá stejnému znaku v cílové sekvenci.

- Zástupný *znak* '., který odpovídá libovolnému znaku v cílové sekvenci s výjimkou nového řádku.

- *Výraz závorky* `expr`formuláře "[ ]", který odpovídá znaku nebo prvku řazení v cílové sekvenci, který je také v sadě definované výrazem `expr`, nebo ve tvaru "[^`expr`]", který odpovídá znaku nebo prvku řazení v cílové sekvenci, který není v sadě definované výrazem `expr`.

   Výraz `expr` může obsahovat libovolnou kombinaci následujících věcí:

  - Jednotlivý znak. Přidá tento znak do `expr`sady definované uživatelem .

  - *Rozsah znaků* formuláře "`ch1`-`ch2`". Přidá znaky, které jsou reprezentovány hodnotami `ch2`v uzavřeném `expr`rozsahu [`ch1`, ], do sady definované .

  - *Třída znaků* formuláře "[:`name`:]". Přidá znaky v pojmenované třídě do `expr`sady definované uživatelem .

  - *Třída ekvivalence* formuláře "[=`elt`=]". Přidá kompletační prvky, `elt` které jsou ekvivalentní `expr`sadě definované aplikací .

  - Symbol *kompletování* formuláře "[.`elt`.]". Přidá prvek `elt` řazení do sady `expr`definované rozhraním .

- *Kotva*. Ukotvení „^“ odpovídá začátku cílové sekvence; ukotvení „$“ odpovídá konci cílové sekvence.

*Skupina zachycení* formuláře "( *podvýraz* )",\\nebo " ( `basic` `grep` *podvýraz* \\)" v a , která odpovídá posloupnosti znaků v cílové sekvenci, která je porovnána se vzorkem mezi oddělovači.

- Únik *identity* formuláře "\\`k`", který `k` odpovídá znaku v cílové sekvenci.

Příklady:

- „a“ odpovídá cílové sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

- „.“ odpovídá všem cílovým sekvencím „a“, „B“, „b“ a „c“.

- „[b-z]“ odpovídá cílovým sekvencím „b“ a „c“, ale neodpovídá cílovým sekvencím „a“ nebo „B“.

- „[:lower:]“ odpovídá cílovým sekvencím „a“, „b“ a „c“, ale neodpovídá cílové sekvenci „B“.

- „(a)“ odpovídá cílové sekvenci „a“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

V `ECMAScript` `basic`, `grep`, a , prvek může být také\\`dd` *zpětný odkaz* na formulář " ", kde `dd` představuje desetinnou hodnotu N, která odpovídá posloupnosti znaků v cílové sekvenci, která je stejná jako posloupnost znaků, která je porovnána *skupinou zachycení*N-tého . Například „(a)\1“ odpovídá cílové sekvenci „aa“, protože první (a jediná) skupina zachycení odpovídá počáteční sekvenci „a“ a \1 odpovídá závěrečné sekvenci „a“.

V `ECMAScript`aplikaci může být prvek také jednou z následujících věcí:

- *Skupina bez zachycení* formuláře "(?: *podvýraz* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači.

- Omezený *formát souboru uniknout* ve tvaru "\f", "\n", "\r", "\t", nebo "\v". Tyto odpovídají znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- *Pozitivní vyhodnocení* formuláře "(= *podvýraz* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači, ale nemění pozici shody v cílové sekvenci.

- *Negativní tvrzení* formuláře "(! *podvýraz* )". Odpovídá jakékoli sekvenci znaků v cílové sekvenci, která neodpovídá vzorci mezi oddělovači a nemění pozici shody v cílové sekvenci.

- *Šestnáctková řídicí sekvence* formuláře \x`hh`. Odpovídá znaku v cílové sekvenci, který je reprezentován `hh`dvěma šestnáctkovými číslicemi .

- Řídicí *sekvence unicode* formuláře "\u`hhhh`". Odpovídá znaku v cílové sekvenci, který je reprezentován `hhhh`čtyřmi šestnáctkovými číslicemi .

- *Řídicí sekvence* ovládacího prvku formuláře`k`\c . Odpovídá řídicímu znaku pojmenovanému `k`znakem .

- Výraz *hranice slova* formuláře \b. Odpovídá, když je aktuální pozice v cílové sekvenci bezprostředně za *hranicí slova*.

- Negativní *slovo hranice assert* formuláře "\B". Odpovídá, když aktuální pozice v cílové sekvenci není bezprostředně za *hranicí slova*.

- Řídicí znak *dsw* formuláře "\d", "\D", "\s", "\S", "\w", "\w", "\W". Poskytuje krátký název pro třídu znaků.

Příklady:

- „(?:a)“ odpovídá cílové sekvenci „a“, ale „(?:a) \1“ je neplatné, protože není k dispozici žádná skupina zachycení 1.

- "(=a)a" odpovídá cílové sekvenci "a". Kladný kontrolní výraz odpovídá počáteční sekvenci „a“ v cílové sekvenci a závěrečné „a“ v regulárním výrazu odpovídá počáteční sekvenci „a“ v cílové sekvenci.

- "(!a)a" neodpovídá cílové sekvenci "a".

- "a\b." odpovídá cílové sekvenci "a~", ale neodpovídá cílové sekvenci "ab".

- "a\B." odpovídá cílové sekvenci "ab", ale neodpovídá cílové sekvenci "a~".

V `awk`aplikaci může být prvek také jednou z následujících věcí:

- Únik *formátu souboru* formuláře\\\\" ", \a", "\b", "\f", "\n", "\r", "\r", "\t" nebo "\v". Tyto odpovídají zpětnému lomítku, upozornění, klávese Backspace, znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- *Osmičková řídicí sekvence* formuláře\\`ooo`" ". Odpovídá znaku v cílové sekvenci, jehož reprezentace je hodnota `ooo`reprezentovaná jednou, dvěma nebo třemi osmičkovými číslicemi .

### <a name="repetition"></a>Opakování

Po libovolném prvku než *kladné masce*, *záporném vyhodnocení*nebo *kotvě* může následovat počet opakování. Nejobecnější druh opakování má podobu`min``max`"{ , }",`max`\\nebo `basic` " `grep`\\{`min`, }" v a . Prvek, za kterým následuje tato forma počtu `min` opakování, odpovídá alespoň `max` po sobě jdoucím výskytům a ne více než po sobě jdoucím výskytům sekvence, která odpovídá prvku. Například "a{2,3}" odpovídá cílové sekvenci "aa" a cílové sekvenci "aaa", ale ne cílové sekvence "a" nebo cílové sekvence "aaaa".

Počet opakování může mít také jednu z následujících forem:

- "{`min`}",\\nebo`min`\\" `basic` { `grep`}" v a . Odpovídá "{`min``min`, }".

- "{`min`,}" nebo\\`min`"\\{ `basic` , `grep`}" v aplikaci a . Ekvivalent "{`min`,unbounded}".

- "\*". Ekvivalentní „{0,unbounded}“.

Příklady:

- "a{2}" odpovídá cílové sekvenci "aa", ale ne cílové sekvenci "a" nebo cílové sekvenci "aaa".

- "a{2,}" odpovídá cílové sekvenci "aa", cílové sekvenci "aaa" a tak dále, ale neodpovídá cílové sekvenci "a".

- "a\*" odpovídá cílové sekvenci "", cílové sekvenci "a", cílové sekvenci "aa" a tak dále.

Pro všechny gramatiky s výjimkou `basic` a `grep`, počet opakování může mít také jednu z následujících forem:

- "?". Odpovídá "{0,1}".

- "+". Ekvivalent "{1,unbounded}".

Příklady:

- "A?" odpovídá cílové sekvenci "" a cílové sekvenci "a", ale ne cílové sekvenci "aa".

- „a+“ odpovídá cílové sekvenci „a“, cílové sekvenci „aa“ atd., ale nikoli cílové sekvenci „“.

V `ECMAScript`posled všech forem opakování může následovat znak '?', který označuje *nechamtivé opakování*.

### <a name="concatenation"></a>Zřetězení

Prvky regulárních výrazů, s nebo bez *opakování počty*, mohou být zřetězené tvořit delší regulární výrazy. Výsledný výraz odpovídá cílové sekvenci, která je zřetězením sekvencí odpovídajících jednotlivým prvkům. Například "a{2,3}b" odpovídá cílové sekvenci "aab" a cílové sekvenci "aaab", ale neodpovídá cílové sekvenci "ab" nebo cílové sekvenci "aaaab".

### <a name="alternation"></a>Alternace

Ve všech gramatikách `basic` regulárních výrazů s výjimkou a `grep`, může být zřetězený regulární výraz následován znakem "&#124;" a jiným zřetězenýrem regulárním výrazem. Tímto způsobem lze spojit libovolný počet zřetězených regulárních výrazů. Výsledný výraz odpovídá jakékoli cílové sekvenci, která odpovídá jednomu nebo více zřetězeným regulárním výrazům.

Pokud více než jeden z zřetězených regulárních výrazů odpovídá cílové sekvenci, vybere první z zřetězených regulárních výrazů, `ECMAScript` které odpovídají sekvenci jako shoda *(první shoda*); ostatní gramatiky regulárních výrazů zvolí ten, který dosáhne *nejdelší shody*. Například "ab&#124;cd" odpovídá cílové sekvenci "ab" a cílové sekvenci "cd", ale neodpovídá cílové sekvenci "abd" nebo cílové sekvenci "acd".

V `grep` `egrep`a , znak nového řádku ('\n') lze použít k oddělení alternací.

### <a name="subexpression"></a>Dílčí výraz

V `basic` `grep`aplikaci a , je dílčí výraz zřetězení. V ostatních gramatikách regulárního výrazu je dílčí výraz změnou.

## <a name="grammar-summary"></a><a name="grammarsummary"></a>Souhrn gramatiky

Následující tabulka shrnuje funkce, které jsou k dispozici v různých gramatikách regulárního výrazu:

|Prvek|Základní|rozšířené|Ecmascript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|střídání pomocí "&#124;"||+|+||+|+|
|alternace pomocí „\n“||||+|+||
|ukotvení|+|+|+|+|+|+|
|zpětný odkaz|+||+|+|||
|výraz závorky|+|+|+|+|+|+|
|skupina zachycení používající „()“||+|+||+|+|
|skupina zachycení\\pomocí\\" ( )"|+|||+|||
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
|opakování pomocí{}" "||+|+||+|+|
|opakování pomocí\\"\\{ }"|+|||+|||
|opakování pomocí\*"|+|+|+|+|+|+|
|opakování pomocí „?“ a „+“||+|+||+|+|
|řídicí sekvence Unicode|||+||||
|zástupný znak|+|+|+|+|+|+|
|kontrolní výraz hranice slova|||+||||

## <a name="semantic-details"></a><a name="semanticdetails"></a>Sémantické detaily

### <a name="anchor"></a>Ukotvení

Ukotvení odpovídá pozici v cílovém řetězci, nikoli znaku. „^“ odpovídá začátku cílového řetězce; „$“ odpovídá konci cílového řetězce.

### <a name="back-reference"></a>Zpětný odkaz

Zpětný odkaz je zpětné lomítko následované desetinnou hodnotou N. Odpovídá obsahu *skupiny zachycení*Nth . Hodnota N nesmí být větší než počet skupin zachycení, které zpětnému odkazu předcházejí. V `basic` `grep`písmenech a) a , je hodnota N určena desetinnou číslicí, která následuje za zpětným lomítkem. V `ECMAScript`písmenu a) je hodnota N určena všemi desetinnými číslicemi, které bezprostředně následují za zpětným lomítkem. Proto v `basic` `grep`a , hodnota N není nikdy větší než 9, i v případě, že regulární výraz má více než devět skupin zachycení. V `ECMAScript`, hodnota N je neohraničený.

Příklady:

- „((a+)(b+))(c+)\3“ odpovídá cílové sekvenci „aabbbcbbb“. Zpětný odkaz „\3“ odpovídá textu ve třetí skupině zachycení, tedy „(b+)“. Neodpovídá cílové sekvenci „aabbbcbb“.

- „(a)\2“ není platné.

- "(b((((((((((((()))))))))\10" má `basic` různé `ECMAScript`významy v a . V `basic` zadní referenci je "\1". Zpětný odkaz odpovídá obsahu první skupiny zachycení (to znamená skupiny, která začíná na „(b“ a končí posledním znakem „)“ a předchází zpětnému odkazu) a závěrečný znak 0 odpovídá běžnému znaku 0. V `ECMAScript`souboru je zpětný odkaz "\10". Odpovídá desáté skupině zachycení, tedy té nejvíce uvnitř.

### <a name="bracket-expression"></a>Výraz závorky

Výraz závorky definuje sadu znaků a *kompletačních prvků*. Když výraz závorky začíná znakem ,^ʻ, porovnávání je úspěšné, pokud žádné prvky v množině neodpovídají aktuálnímu znaku v cílové sekvenci. Porovnání je jinak úspěšné, pokud jakýkoli z prvků v množině odpovídá aktuálnímu prvku v cílové sekvenci.

Sadu znaků lze definovat vypisováním libovolné kombinace *jednotlivých znaků*, *rozsahů znaků*, *tříd znaků*, tříd *ekvivalence*a *kompletačních symbolů*.

### <a name="capture-group"></a>Skupina zachycení

Skupina zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu a označuje popiskem cílový text, který odpovídá jejímu obsahu. Popisek, který je spojen s každou skupinou zachycení, je číslo, které je určeno výpočtem úvodních závorek, jež označují skupiny zachycení až do úvodní závorky včetně, která označuje aktuální skupinu zachycení. V této implementaci je maximální počet skupin zachycení 31.

Příklady:

- „ab+“ odpovídá cílové sekvenci „abb“, ale neodpovídá cílové sekvenci „abab“.

- „(ab)+“ neodpovídá cílové sekvenci „abb“, ale odpovídá cílové sekvenci „abab“.

- „((a+)(b+))(c+)“ odpovídá cílové sekvenci „aabbbc“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „aabbb“, skupinu zachycení 2 k dílčí sekvenci „aa“, skupinu zachycení 3 k dílčí sekvenci „bbb“ a skupinu zachycení 4 k dílčí sekvenci „c“.

### <a name="character-class"></a>Třída znaků

Třída znaků ve výrazu závorky přidá všechny znaky v pojmenované třídě do množiny znaků, která je definována výrazem závorky. Chcete-li vytvořit třídu znaků, použijte „[:“, dále název třídy a nakonec „:]“. Interně jsou názvy tříd znaků `id = traits.lookup_classname`rozpoznány voláním . Znak `ch` patří do takové `traits.isctype(ch, id)` třídy, pokud vrátí true. Výchozí `regex_traits` šablona podporuje názvy tříd v následující tabulce.

|Název třídy|Popis|
|----------------|-----------------|
|„alnum“|malá písmena, velká písmena a číslice|
|„alpha“|malá písmena a velká písmena|
|„blank“|mezera nebo tabulátor|
|„cntrl“|řídicí znaky *formátu souboru*|
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

Symbol kompletování ve výrazu závorky přidá do sady *prvek kompletování,* který je definován výrazem závorky. Chcete-li vytvořit symbol řazení, použijte "[." následuje kompletační prvek následovaný ".]".

### <a name="control-escape-sequence"></a>Řídicí sekvence

Řídicí sekvence je zpětné lomítko následované písmenem „c“ a poté jedním z písmen od „a“ do „z“ nebo od „A“ do „Z“. Odpovídá řídicímu znaku ASCII, který je pojmenován podle daného písmena. Například "\ci" odpovídá cílové sekvenci "\x09", protože \<ctrl-i> má hodnotu 0x09.

### <a name="dsw-character-escape"></a>Řídicí znak DSW

Řídicí znak dsw je krátký název pro třídu znaků, jak je znázorněno v následující tabulce.

|Řídicí sekvence|Třída s ekvivalentním názvem|Třída s výchozím názvem|
|---------------------|----------------------------|-------------------------|
|„\d“|„[[:d:]]“|„[[:digit:]]“|
|„\D“|„[^[:d:]]“|„[^[:digit:]]“|
|„\s“|„[[:s:]]“|„[[:space:]]“|
|„\S“|„[^[:s:]]“|„[^[:space:]]“|
|„\w“|„[[:w:]]“|"[a-zA-Z0-9_]"\*|
|„\W“|„[^[:w:]]“|"[^a-zA-Z0-9_]"\*|

\*Znaková sada ASCII

### <a name="equivalence-class"></a>Třída ekvivalence

Třída ekvivalence ve výrazu závorky přidá všechny znaky a *kompletační prvky,* které jsou rovnocenné prvku řazení v definici třídy ekvivalence, k sadě, která je definována výrazem závorky. Chcete-li vytvořit třídu ekvivalence, použijte „[=“, dále kolační prvek a nakonec „=]“. Interně dva kompletační `elt1` `elt2` prvky `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`a jsou rovnocenné, pokud .

### <a name="file-format-escape"></a>Řídicí znak formátu souboru

Escape ve formátu souboru se skládá z obvyklých\\\\sekvencí escape znaků jazyka C , " ", "a", "\b", "\f", "\n", "\r", "\t", "\v". Ty mají obvyklé významy, to znamená zpětné lomítko, výstraha, backspace, informační kanál formuláře, nový řádek, návrat vozíku, vodorovná karta a svislá karta. V `ECMAScript`, "\a" a "\b" nejsou povoleny. ("\\\\" je povoleno, ale je to únik identity, nikoli únik formátu souboru).

### <a name="hexadecimal-escape-sequence"></a>Šestnáctková řídicí sekvence

Šestnáctková řídicí sekvence je zpětné lomítko následované písmenem „x“ a dvěma šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí dvou číslic. Například „\x41“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="identity-escape"></a>Řídicí znak identity

Řídicí znak identity je zpětné lomítko následované jedním znakem. Odpovídá danému znaku. Je vyžadován, když má znak zvláštní význam; pomocí řídicího znaku identity je zvláštní výraz odebrán. Příklad:

- "a\*" odpovídá cílové sekvenci "aaa", ale\*neodpovídá cílové sekvenci "a".

- "a\\\*" neodpovídá cílové sekvenci "aaa",\*ale odpovídá cílové sekvenci "a".

Množina znaků, které jsou v řídicím znaku identity povoleny, závisí na gramatice regulárního výrazu, viz následující tabulka.

|Gramatika|Povolené řídicí znaky identity|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.',\\'[', ',, ',\*', ',^', '$', '+', '?', '&#124;' }|
|`awk`|`extended`plus { '',, '/' }|
|`ECMAScript`|Všechny znaky kromě těch, které mohou být součástí identifikátoru. Obvykle to zahrnuje písmena, číslice, '$', '\_', ', a unicode escape sekvence. Další informace naleznete ve specifikacích jazyka ECMAScript.|

### <a name="individual-character"></a>Jednotlivý znak

Jednotlivý znak ve výrazu závorky přidá daný znak do množiny znaků, která je definována výrazem závorky. Kdekoli ve výrazu závorky s výjimkou na začátku představuje znak '^' sám sebe.

Příklady:

- „[abc]“ odpovídá cílové sekvenci „a“, „b“ a „c“, ale nikoli sekvenci „d“.

- „[^abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“ nebo „c“.

- „[a^bc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „^“, ale nikoli cílové sekvenci „d“.

Ve všech gramatikách `ECMAScript`regulárních výrazů s výjimkou , pokud je ']' prvním znakem, který následuje za otevřením [nebo je prvním znakem, který následuje za počátečním '^', představuje sám sebe.

Příklady:

- „[]a“ je neplatné, protože není k dispozici žádný znak ']' pro ukončení výrazu závorky.

- „[]abc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „]“, ale nikoli cílové sekvenci „d“.

- „[^]abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“, „c“ nebo „]“.

V `ECMAScript`aplikaci\\použijte znak ']' k reprezentaci znaku ']' ve výrazu závorky.

Příklady:

- „[]a“ odpovídá cílové sekvenci „a“, protože výraz závorky je prázdný.

- "[\\]abc]" odpovídá cílovým sekvencí "a", "b", "c" a "]", ale ne cílové sekvenci "d".

### <a name="negative-assert"></a>Záporný kontrolní výraz

Záporný kontrolní výraz odpovídá všemu kromě svého obsahu. Nespotřebovává žádné znaky v cílové sekvenci. Například "(!aa)(a\*)" odpovídá cílové sekvenci "a" a přidružuje skupinu zachycení 1 s dílčí sekvenci "a". Neodpovídá cílové sekvenci „aa“, ale cílové sekvenci „aaa“.

### <a name="negative-word-boundary-assert"></a>Záporný kontrolní výraz hranice slova

Negativní slovo hranice assert odpovídá, pokud aktuální pozice v cílovém *řetězci*není bezprostředně za hranice slova .

### <a name="non-capture-group"></a>Skupina bez zachycení

Skupina bez zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu, ale neoznačuje popiskem cílový text. Například "(a)(?:b)\*(c)" odpovídá cílovému textu "abbc" a přidružuje skupinu zachycení 1 s dílčí sekvencí "a" a skupinou zachycení 2 s dílčí sekvenci "c".

### <a name="non-greedy-repetition"></a>Opakování bez metody Greedy

Opakování bez metody Greedy spotřebovává nejkratší dílčí sekvenci cílové sekvence, která odpovídá vzoru. Opakování s metodou Greedy spotřebovává nejdelší sekvenci. Například "(a+)(a\*b)" odpovídá cílové sekvenci "aaab". Je-li použito opakování bez metody Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „a“ na začátku cílové sekvence a skupinu zachycení 2 k dílčí sekvenci „aab“ na konci cílové sekvence. Je-li použita shoda s metodou Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „aaa“ a skupinu zachycení 2 k dílčí sekvenci „b“.

### <a name="octal-escape-sequence"></a>Osmičková řídicí sekvence

Osmičková řídicí sekvence je zpětné lomítko následované jednou, dvěma nebo třemi osmičkovými číslicemi (0-7). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí těchto číslic. Jsou-li všechny číslice „0“, sekvence je neplatná. Například „\101“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="ordinary-character"></a>Běžný znak

Běžný znak je jakýkoli platný znak, který nemá v aktuální gramatice zvláštní význam.

V `ECMAScript`písmenu a) mají následující znaky zvláštní význam:

- ^  $  \  .  \*+  ?  ( \[ ) ] { } &#124;

V `basic` `grep`písmenech a) a d) mají následující znaky zvláštní význam:

- .   \[   \

Také `basic` v `grep`a , následující znaky mají zvláštní význam, pokud jsou použity v určitém kontextu:

- '\*' má zvláštní význam ve všech případech s výjimkou případů, kdy se jedná o první znak v regulárním výrazu nebo první znak, který následuje za počátečním znakem ^v regulárním výrazu, nebo pokud se jedná o první znak skupiny pro zachycení nebo první znak, který následuje za počátečním znakem ^ve skupině zachycení.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

V `extended` `egrep`, `awk`, a , následující znaky mají zvláštní význam:

- .   \[\   (   \*   +   ?   { &#124;

Také `extended`v `egrep`, `awk`, a , následující znaky mají zvláštní význam, pokud jsou použity v určitém kontextu.

- ') má zvláštní význam v případě, že odpovídá předchozímu znaku '('.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

Běžný znak odpovídá stejnému znaku v cílové sekvenci. Ve výchozím nastavení to znamená, že porovnání se zdaří, pokud jsou dva znaky zastoupeny stejnou hodnotou. V případě nerozlišující `ch0` shody dva znaky a `ch1` shoda if `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. V shodě citlivé na národní `ch0` `ch1` prostředí `traits.translate(ch0) == traits.translate(ch1)`dva znaky a shoda if .

### <a name="positive-assert"></a>Kladný kontrolní výraz

Kladný kontrolní výraz odpovídá svému obsahu, ale nespotřebovává žádné znaky v cílové sekvenci.

Příklady:

- "(=a)(a\*)" odpovídá cílové sekvenci "aaaa" a spojuje skupinu zachycení 1 s dílčí sekvencí "aaaa".

- "(a)(a\*)" odpovídá cílové sekvenci "aaaa" a spojuje skupinu zachycení 1 s dílčí sekvencí "aa" na začátku cílové sekvence a zachytit skupinu 2 s dílčí sekvenci "aa" na konci cílové sekvence.

- "(=aa)(a)&#124;(a)" odpovídá cílové sekvenci "a" a přidružuje skupinu zachycení 1 s prázdnou sekvencí (protože kladná vyhodnocení selhala) a zachytávání skupiny 2 s dílčí sekvencí "a". Také odpovídá cílové sekvenci „aa“ a přiřadí skupinu zachycení 1 k dílčí sekvenci „aa“ a skupinu zachycení 2 k prázdné sekvenci.

### <a name="unicode-escape-sequence"></a>Řídicí sekvence Unicode

Řídicí sekvence Unicode je zpětné lomítko následované písmenem „u“ a čtyřmi šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí čtyř číslic. Například „\u0041“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="wildcard-character"></a>Zástupný znak

Zástupný znak odpovídá libovolnému znaku v cílovém výrazu, s výjimkou nového řádku.

### <a name="word-boundary"></a>Hranice slova

Hranice slova se vyskytuje v následujících situacích:

- Aktuální znak je na začátku cílové sekvence a je jedním ze znaků slova`A-Za-z0-9_.`

- Aktuální poloha znaku je za koncem cílové sekvence a poslední znak v cílové sekvenci je jedním ze znaků slova.

- Aktuální znak je jedním ze znaků slova a předchozí znak není.

- Aktuální znak není jedním ze znaků slova a předchozí znak je.

### <a name="word-boundary-assert"></a>Kontrolní výraz hranice slova

Vyhodnocení hranice slova odpovídá, když je aktuální pozice v cílovém *řetězci*bezprostředně za hranicí slova .

## <a name="matching-and-searching"></a><a name="matchingandsearching"></a>Párování a vyhledávání

Aby regulární výraz odpovídal cílové sekvenci, musí celý regulární výraz odpovídat celé cílové sekvenci. Například regulární výraz „bcd“ odpovídá cílové sekvenci „bcd“, ale nikoli cílové sekvenci „abcd“ ani cílové sekvenci „bcde“.

Aby hledání regulárního výrazu bylo úspěšné, někde v cílové sekvenci se musí nacházet dílčí sekvence, která odpovídá regulárnímu výrazu. Hledání obvykle najde odpovídající dílčí sekvenci nejvíce vlevo.

Příklady:

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcd" je úspěšné a odpovídá celé sekvenci. Stejné vyhledávání v cílové sekvenci "abcd" je také úspěšné a odpovídá posledním třem znakům. Stejné vyhledávání v cílové sekvenci "bcde" je také úspěšné a odpovídá prvním třem znakům.

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcdbcd" je úspěšné a odpovídá prvním třem znakům.

Pokud existuje více než jedna dílčí sekvence, která odpovídá v určitém umístění cílové sekvence, můžete odpovídající vzor vybrat dvěma způsoby. *První shoda* zvolí dílčí sekvenci, která byla nalezena jako první, když je regulární výraz spárován. *Nejdelší shoda* vybere nejdelší dílčí sekvenci z té, které se shodují v tomto místě. Pokud existuje více než jedna dílčí sekvence, která má maximální délku, nejdelší shoda zvolí tu, která byla nalezena jako první. Například při použití první shody hledání regulárního výrazu "b&#124;bc" v cílové sekvenci "abcd" odpovídá dílčí sekvenci "b", protože levý termín alternace odpovídá této dílčí sekvenci; proto první shoda nezkouší pravý termín střídání. Při použití nejdelší shody stejné vyhledávání odpovídá „bc“, protože „bc“ je delší než „b“.

Částečná shoda bude úspěšná, pokud shoda dosáhne konce cílové sekvence bez selhání, i když nedosáhla konce regulárního výrazu. Proto by po úspěchu částečné shody mohlo připojení znaků k cílové sekvenci způsobit pozdější selhání částečné shody. Po neúspěchu částečné shody však připojení znaků k cílové sekvenci nemůže způsobit pozdější úspěch částečné shody. Například v případě částečné shody odpovídá „ab“ cílové sekvenci „a“, ale nikoli „ac“.

## <a name="format-flags"></a><a name="formatflags"></a>Formát příznaků

|Pravidla formátu jazyka ECMAScript|Pravidla formátu SED|Náhradní text|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Pořadí znaků, které odpovídá celému regulárnímu výrazu (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"&"\\|"&"|
|"$\`" (znak dolaru následovaný zpětnou uvozovkou)|| Sekvence znaků, která předchází dílčí sekvenci, která odpovídá regulárnímu výrazu (`[match.prefix().first, match.prefix().second)`)|
|„$'“ (znak dolaru následovaný počáteční uvozovkou)||Pořadí znaků, které následuje za dílčí sekvencí, která odpovídá regulárnímu výrazu (`[match.suffix().first, match.suffix().second)`)|
|„$n“|„\n“|Pořadí znaků, které odpovídá skupině `n`zachycení `n` na pozici , kde`[match[n].first, match[n].second)`je číslo mezi 0 a 9 ( )|
||"\\\n"|„\n“|
|„$nn“||Pořadí znaků, které odpovídá skupině `nn`zachycení `nn` na pozici , kde je`[match[nn].first, match[nn].second)`číslo mezi 10 a 99 ( )|

## <a name="see-also"></a>Viz také

[Přehled standardní knihovny jazyka C++](../standard-library/cpp-standard-library-overview.md)
