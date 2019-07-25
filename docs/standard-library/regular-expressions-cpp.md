---
title: Regulární výrazy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: db5a7eacc136b3f30187692c7ea10792b84eb3fc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451379"
---
# <a name="regular-expressions-c"></a>Regulární výrazy (C++)

C++ Standardní knihovna podporuje několik gramatik regulárních výrazů. Toto téma popisuje gramatické variace, které jsou k dispozici při použití regulárních výrazů.

## <a name="regexgrammar"></a>Gramatika regulárního výrazu

Gramatika regulárního výrazu, která se má použít, je určena použitím jedné z `std::regex_constants::syntax_option_type` hodnot výčtu. Tyto gramatiky regulárních výrazů jsou definovány v std:: regex_constants:

- `ECMAScript`: Toto je nejblíže gramatice používané v jazycích JavaScript a .NET.
- `basic`: Základní regulární výrazy POSIX nebo BRE.
- `extended`: Rozšířené regulární výrazy POSIX nebo ERE.
- `awk`: Je `extended`to, ale obsahuje další řídicí znaky pro netisknutelné znaky.
- `grep`: To je `basic`, ale také umožňuje oddělit střídající se znaky nového řádku (' \n ').
- `egrep`: To je `extended`, ale také umožňuje znakům nového řádku oddělit střídající se.

Ve výchozím nastavení platí, že pokud není zadána `ECMAScript` žádná gramatika, předpokládá se. Může být zadána pouze jedna gramatika.

Kromě gramatiky lze použít několik příznaků:
- `icase`: Ignorovat velikost písmen při shodě
- `nosubs`: Ignorovat označené shody (tj. výrazy v závorkách); neukládají se žádné náhrady.
- `optimize`: Zajištění rychlejšího porovnání s možnými náklady na vyšší dobu stavby.
- `collate`: Použijte posloupnosti kolace závislé na národním prostředí (například rozsahy ve formátu "[a-z]").

K určení chování modulu regulárních výrazů lze kombinovat nula nebo více příznaků s gramatikou. Pokud jsou zadány pouze příznaky `ECMAScript` , je považována za gramatiku.

### <a name="element"></a>Prvek

Prvek může být jeden z následujících:

- *Běžný znak* , který odpovídá stejnému znaku v cílové sekvenci.

- *Zástupný znak* ".", který odpovídá jakémukoli znaku v cílové sekvenci s výjimkou nového řádku.

- *Výraz závorky* ve formátu "[`expr`]", který odpovídá znaku nebo prvku kolace v cílové sekvenci, která je také v množině definované výrazem `expr`nebo ve formátu "[^`expr`]", který odpovídá znaku nebo element kolace v cílové sekvenci, který není v množině definované výrazem `expr`.

   Výraz `expr` může obsahovat libovolnou kombinaci následujících věcí:

   - Jednotlivý znak. Přidá tento znak do množiny definované `expr`.

   - *Rozsah znaků* ve tvaru "`ch1`-`ch2`". Přidá znaky, které jsou reprezentovány hodnotami v uzavřeném rozsahu`ch1`[ `ch2`,], `expr`do množiny definované.

   - *Třída znaků* ve formátu "[:`name`:]". Přidá znaky v pojmenované třídě do množiny definované `expr`.

   - *Třída ekvivalence* ve formátu "[=`elt`=]". Přidá prvky kompletování, které jsou ekvivalentní `elt` k sadě definované pomocí. `expr`

   - *Symbol kompletování* ve formátu "[.`elt`..]". Přidá element `elt` kolace do množiny `expr`definované.

- *Kotva*. Ukotvení „^“ odpovídá začátku cílové sekvence; ukotvení „$“ odpovídá konci cílové sekvence.

*Skupina zachycení* ve formátu "(dílčí *výraz* )"\\nebo "(dílčí *výraz* \\)" v `basic` a `grep`, která odpovídá sekvenci znaků v cílové sekvenci, které odpovídají vzor mezi oddělovači.

- *Řídicí znak identity* ve tvaru\\"`k`", který odpovídá znaku `k` v cílové sekvenci.

Příklady:

- „a“ odpovídá cílové sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

- „.“ odpovídá všem cílovým sekvencím „a“, „B“, „b“ a „c“.

- „[b-z]“ odpovídá cílovým sekvencím „b“ a „c“, ale neodpovídá cílovým sekvencím „a“ nebo „B“.

- „[:lower:]“ odpovídá cílovým sekvencím „a“, „b“ a „c“, ale neodpovídá cílové sekvenci „B“.

- „(a)“ odpovídá cílové sekvenci „a“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „a“, ale neodpovídá cílovým sekvencím „B“, „b“ nebo „c“.

V `ECMAScript`, `dd`  a, elementmůže\\býttakézpětný odkaz formuláře "",kdepředstavujedesítkovouhodnotuN,kteráodpovídásekvenciznakůvcíli.`dd` `grep` `basic` sekvence, která je stejná jako sekvence znaků, které jsou porovnány s n-tý *skupinou zachycení*. Například „(a)\1“ odpovídá cílové sekvenci „aa“, protože první (a jediná) skupina zachycení odpovídá počáteční sekvenci „a“ a \1 odpovídá závěrečné sekvenci „a“.

V `ECMAScript`nástroji může být prvkem také jedna z následujících akcí:

- *Skupina bez zachycení* ve formátu "(?: dílčí *výraz* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači.

- Omezený *řídicí znak formátu souboru* ve formátu "\f", "\n", "\r", "\t" nebo "\v". Tyto odpovídají znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- *Kladný kontrolní* výraz ve formátu "(= dílčí *výraz* )". Odpovídá sekvenci znaků v cílové sekvenci, které odpovídá vzorec mezi oddělovači, ale nemění pozici shody v cílové sekvenci.

- *Negativní kontrolní* výraz ve formátu "(! dílčí *výraz* ) ". Odpovídá jakékoli sekvenci znaků v cílové sekvenci, která neodpovídá vzorci mezi oddělovači a nemění pozici shody v cílové sekvenci.

- *Hexadecimální řídicí sekvence* ve formátu "\x`hh`". Odpovídá znaku v cílové sekvenci, který je reprezentován dvěma šestnáctkovými číslicemi `hh`.

- *Řídicí sekvence Unicode* ve formátu "\u`hhhh`". Odpovídá znaku v cílové sekvenci, který je reprezentován čtyřmi šestnáctkovými číslicemi `hhhh`.

- Řídicí *sekvence ovládacího prvku* ve formátu "\c`k`". Odpovídá řídicímu znaku, který je pojmenován znakem `k`.

- *Kontrolní výraz hranice slova* ve formátu "\b". Odpovídá, pokud aktuální pozice v cílové sekvenci je ihned za *hranicí slova*.

- *Negativní kontrolní výraz hranice slova* ve formátu "\b". Odpovídá, pokud aktuální pozice v cílové sekvenci není hned za hranicí *slova*.

- *Řídicí znak dsw* ve formátu "\d", "\d", "\s", "\s", "\w", "\w". Poskytuje krátký název pro třídu znaků.

Příklady:

- „(?:a)“ odpovídá cílové sekvenci „a“, ale „(?:a) \1“ je neplatné, protože není k dispozici žádná skupina zachycení 1.

- "(= a) a" odpovídá cílové sekvenci "a". Kladný kontrolní výraz odpovídá počáteční sekvenci „a“ v cílové sekvenci a závěrečné „a“ v regulárním výrazu odpovídá počáteční sekvenci „a“ v cílové sekvenci.

- "(! a) a" neodpovídá cílové sekvenci "a".

- a\B. odpovídá cílové sekvenci "a ~", ale neodpovídá cílové sekvenci "AB".

- A\B. odpovídá cílové sekvenci "AB", ale neodpovídá cílové sekvenci "a ~".

V `awk`nástroji může být prvkem také jedna z následujících akcí:

- Řídicí\\znakformátu *souboru ve formátu* "","\a","\b","\f","\n","\r","\t"nebo"\v".\\ Tyto odpovídají zpětnému lomítku, upozornění, klávese Backspace, znaku posunu strany, novému řádku, návratovému znaku, horizontálnímu, resp. vertikálnímu tabulátoru v cílové sekvenci.

- *Osmičková řídicí sekvence* ve formátu "\\`ooo`". Odpovídá znaku v cílové sekvenci, jejíž reprezentace je hodnota reprezentovaná jednou, dvěma nebo tři osmičkovou číslicí `ooo`.

### <a name="repetition"></a>Opakování

Libovolný element jiný než *kladný kontrolní*výraz, *negativní kontrolní*výraz nebo ukotvení  může následovat po počtu opakování. Nejobecnější typ opakování má podobu "`min`{,`max`}" nebo "\\{`min`,`max`\\}" v `basic` a `grep`. Element, za nímž následuje tento tvar počtu opakování, odpovídá alespoň `min` dalším výskytům a neobsahuje více než `max` po sobě jdoucí výskyty sekvence, která odpovídá prvku. Například "a{2,3}" odpovídá cílové sekvenci "AA" a cílové sekvenci "AAA", ale nikoli cílové sekvenci "a" nebo cílové sekvenci "AAAA".

Počet opakování může mít také jednu z následujících forem:

- "{`min`}" nebo "\\{`min`\\}" v `basic` a `grep`. Odpovídá "{`min`,`min`}".

- "{`min`,}" nebo "\\{`min`,\\}" v `basic` a `grep`. Odpovídá "{`min`, Unbounded}".

- "\*". Ekvivalentní „{0,unbounded}“.

Příklady:

- "a{2}" odpovídá cílové sekvenci "AA", ale nikoli cílové sekvenci "a" nebo cílové sekvenci "AAA".

- "a{2,}" odpovídá cílové sekvenci "AA", cílové sekvenci "AAA" atd., ale neodpovídá cílové sekvenci "a".

- "a\*" odpovídá cílové sekvenci "", cílové sekvenci "a", cílové sekvenci "AA" atd.

Pro všechny gramatiky s `basic` výjimkou a `grep`může mít počet opakování také jednu z následujících forem:

- "?". Ekvivalentní s "{0,1}".

- "+". Odpovídá "{1, Unbounded}".

Příklady:

- "a?" odpovídá cílové sekvenci "" a cílové sekvenci "a", ale nikoli cílové sekvenci "AA".

- „a+“ odpovídá cílové sekvenci „a“, cílové sekvenci „aa“ atd., ale nikoli cílové sekvenci „“.

V `ECMAScript`nástroji mohou být všechny formy počtu opakování následovány znakem "?", který označuje nehladé *opakování*.

### <a name="concatenation"></a>Zřetězení

Prvky regulárního výrazu s *počtem opakování*nebo bez nich lze zřetězit, aby bylo možné vytvořit delší regulární výrazy. Výsledný výraz odpovídá cílové sekvenci, která je zřetězením sekvencí odpovídajících jednotlivým prvkům. Například "a{2,3}b" odpovídá cílové sekvenci "aab" a cílové sekvenci "aaab", ale neodpovídá cílové sekvenci "AB" nebo cílové sekvenci "aaaab".

### <a name="alternation"></a>Alternace

Ve všech gramatikách regulárních výrazů `basic` s `grep`výjimkou a může být zřetězený regulární výraz následován znakem&#124;a jiným zřetězeným regulárním výrazem. Tímto způsobem lze spojit libovolný počet zřetězených regulárních výrazů. Výsledný výraz odpovídá jakékoli cílové sekvenci, která odpovídá jednomu nebo více zřetězeným regulárním výrazům.

Pokud se v cílové sekvenci shoduje více než jeden ze zřetězených regulárních `ECMAScript` výrazů, zvolí první z zřetězených regulárních výrazů, které odpovídají sekvenci jako porovnávání (*První shoda*); druhý regulární výraz gramatiky volí ten, který dosáhne *nejdelší shody*. Například "AB&#124;CD" odpovídá cílové sekvenci "AB" a cílové sekvenci "CD", ale neodpovídá cílové sekvenci "Abd" nebo cílové sekvenci "ACD".

V `grep` a`egrep`se dá znak nového řádku (' \n ') použít k oddělení střídajících se.

### <a name="subexpression"></a>Dílčí výraz

V `basic` a`grep`je dílčí výraz zřetězení. V ostatních gramatikách regulárního výrazu je dílčí výraz změnou.

## <a name="grammarsummary"></a>Souhrn gramatiky

Následující tabulka shrnuje funkce, které jsou k dispozici v různých gramatikách regulárního výrazu:

|Prvek|Basic|rozšířené|Objektu|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternace pomocí '&#124;'||+|+||+|+|
|alternace pomocí „\n“||||+|+||
|ukotvení|+|+|+|+|+|+|
|zpětný odkaz|+||+|+|||
|výraz závorky|+|+|+|+|+|+|
|skupina zachycení používající „()“||+|+||+|+|
|zachytit skupinu pomocí "\\(\\)"|+|||+|||
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
|opakování pomocí '\*'|+|+|+|+|+|+|
|opakování pomocí „?“ a „+“||+|+||+|+|
|řídicí sekvence Unicode|||+||||
|zástupný znak|+|+|+|+|+|+|
|kontrolní výraz hranice slova|||+||||

## <a name="semanticdetails"></a>Sémantické podrobnosti

### <a name="anchor"></a>Ukotvení

Ukotvení odpovídá pozici v cílovém řetězci, nikoli znaku. „^“ odpovídá začátku cílového řetězce; „$“ odpovídá konci cílového řetězce.

### <a name="back-reference"></a>Zpětný odkaz

Zpětný odkaz je zpětné lomítko, po kterém následuje Desítková hodnota N. Odpovídá obsahu n-tý *skupiny zachycení*. Hodnota N nesmí být větší než počet skupin zachycení, které zpětnému odkazu předcházejí. V `basic` a`grep`je hodnota N určena desítkovou číslicí, která následuje po zpětném lomítku. V `ECMAScript`, hodnota N je určena všemi desítkovými číslicemi, které bezprostředně následují zpětné lomítko. Proto hodnota N `basic` není `grep`nikdy více než 9, a to i v případě, že má regulární výraz více než devět skupin zachycení. V `ECMAScript`není hodnota N ohraničena.

Příklady:

- „((a+)(b+))(c+)\3“ odpovídá cílové sekvenci „aabbbcbbb“. Zpětný odkaz „\3“ odpovídá textu ve třetí skupině zachycení, tedy „(b+)“. Neodpovídá cílové sekvenci „aabbbcbb“.

- „(a)\2“ není platné.

- "(b (((((((((((((((a) `basic` `ECMAScript`))))))))))))))))))))))))) V `basic` odkazu zpět je "\ 1". Zpětný odkaz odpovídá obsahu první skupiny zachycení (to znamená skupiny, která začíná na „(b“ a končí posledním znakem „)“ a předchází zpětnému odkazu) a závěrečný znak 0 odpovídá běžnému znaku 0. V `ECMAScript`je zpětný odkaz "\ 10". Odpovídá desáté skupině zachycení, tedy té nejvíce uvnitř.

### <a name="bracket-expression"></a>Výraz závorky

Výraz závorky definuje sadu znaků a kompletování *prvků*. Když výraz závorky začíná znakem ,^ʻ, porovnávání je úspěšné, pokud žádné prvky v množině neodpovídají aktuálnímu znaku v cílové sekvenci. Porovnání je jinak úspěšné, pokud jakýkoli z prvků v množině odpovídá aktuálnímu prvku v cílové sekvenci.

Sadu znaků lze definovat výpisem jakékoli kombinace *jednotlivých znaků*, *rozsahů znaků*, *tříd znaků*, *tříd ekvivalence*a *řazení symbolů*.

### <a name="capture-group"></a>Skupina zachycení

Skupina zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu a označuje popiskem cílový text, který odpovídá jejímu obsahu. Popisek, který je spojen s každou skupinou zachycení, je číslo, které je určeno výpočtem úvodních závorek, jež označují skupiny zachycení až do úvodní závorky včetně, která označuje aktuální skupinu zachycení. V této implementaci je maximální počet skupin zachycení 31.

Příklady:

- „ab+“ odpovídá cílové sekvenci „abb“, ale neodpovídá cílové sekvenci „abab“.

- „(ab)+“ neodpovídá cílové sekvenci „abb“, ale odpovídá cílové sekvenci „abab“.

- „((a+)(b+))(c+)“ odpovídá cílové sekvenci „aabbbc“ a přidružuje skupinu zachycení 1 k dílčí sekvenci „aabbb“, skupinu zachycení 2 k dílčí sekvenci „aa“, skupinu zachycení 3 k dílčí sekvenci „bbb“ a skupinu zachycení 4 k dílčí sekvenci „c“.

### <a name="character-class"></a>Třída znaků

Třída znaků ve výrazu závorky přidá všechny znaky v pojmenované třídě do množiny znaků, která je definována výrazem závorky. Chcete-li vytvořit třídu znaků, použijte „[:“, dále název třídy a nakonec „:]“. Interně jsou názvy tříd znaků rozpoznávány voláním `id = traits.lookup_classname`. Znak `ch` patří do takové třídy, pokud `traits.isctype(ch, id)` vrátí hodnotu true. Výchozí `regex_traits` šablona podporuje názvy tříd v následující tabulce.

|Název třídy|Popis|
|----------------|-----------------|
|„alnum“|malá písmena, velká písmena a číslice|
|„alpha“|malá písmena a velká písmena|
|„blank“|mezera nebo tabulátor|
|„cntrl“|*řídicí znaky formátu souboru*|
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

Symbol kompletování ve výrazu závorky přidá *prvek kompletování* do sady, která je definována výrazem závorky. Chcete-li vytvořit symbol kompletování, použijte "[." následováno prvkem kompletování následovaným znakem ".]".

### <a name="control-escape-sequence"></a>Řídicí sekvence

Řídicí sekvence je zpětné lomítko následované písmenem „c“ a poté jedním z písmen od „a“ do „z“ nebo od „A“ do „Z“. Odpovídá řídicímu znaku ASCII, který je pojmenován podle daného písmena. Například "\ci" odpovídá cílové sekvenci "\x09", protože \<kombinace kláves CTRL-i > má hodnotu 0x09.

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

Třída ekvivalence ve výrazu závorky přidá všechny znaky a kompletování *prvků* , které jsou ekvivalentní prvku kompletování v definici třídy ekvivalence, do sady, která je definována výrazem závorky. Chcete-li vytvořit třídu ekvivalence, použijte „[=“, dále kolační prvek a nakonec „=]“. Interně dva prvky `elt1` kompletování a `elt2` jsou ekvivalentní, `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`Pokud.

### <a name="file-format-escape"></a>Řídicí znak formátu souboru

Řídicí znak formátu souboru se skládá z obvyklých řídicích sekvencí znaků jazyka\\C,\\"", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Jedná se o běžné významy, tedy zpětné lomítko, výstrahu, Backspace, znak formuláře, nový řádek, návrat do konce řádku, horizontální tabulátor a svislá karta v uvedeném pořadí. V `ECMAScript`nejsou povoleny "\a" a "\b". ("\\\\" je povoleno, ale jedná se o řídicí znak identity, nikoli řídicí znak formátu souboru).

### <a name="hexadecimal-escape-sequence"></a>Šestnáctková řídicí sekvence

Šestnáctková řídicí sekvence je zpětné lomítko následované písmenem „x“ a dvěma šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí dvou číslic. Například „\x41“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="identity-escape"></a>Řídicí znak identity

Řídicí znak identity je zpětné lomítko následované jedním znakem. Odpovídá danému znaku. Je vyžadován, když má znak zvláštní význam; pomocí řídicího znaku identity je zvláštní výraz odebrán. Příklad:

- "a\*" odpovídá cílové sekvenci "AAA", ale neodpovídá cílové sekvenci "a\*".

- "a\\\*" neodpovídá cílové sekvenci "AAA", ale odpovídá cílové sekvenci "a\*".

Množina znaků, které jsou v řídicím znaku identity povoleny, závisí na gramatice regulárního výrazu, viz následující tabulka.

|Gramatika|Povolené řídicí znaky identity|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended`Plus {' "', '/'}|
|`ECMAScript`|Všechny znaky kromě těch, které mohou být součástí identifikátoru. Obvykle to zahrnuje písmena, číslice, ' $ ', '\_' a řídicí sekvence Unicode. Další informace naleznete ve specifikacích jazyka ECMAScript.|

### <a name="individual-character"></a>Jednotlivý znak

Jednotlivý znak ve výrazu závorky přidá daný znak do množiny znaků, která je definována výrazem závorky. Kdekoli ve výrazu závorky s výjimkou na začátku představuje znak '^' sám sebe.

Příklady:

- „[abc]“ odpovídá cílové sekvenci „a“, „b“ a „c“, ale nikoli sekvenci „d“.

- „[^abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“ nebo „c“.

- „[a^bc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „^“, ale nikoli cílové sekvenci „d“.

Ve všech gramatikách regulárních výrazů `ECMAScript`s výjimkou, pokud je '] ' první znak, který následuje po otevření ' [' nebo je prvním znakem, který následuje po počátečním ' ^ ', představuje sám sebe.

Příklady:

- „[]a“ je neplatné, protože není k dispozici žádný znak ']' pro ukončení výrazu závorky.

- „[]abc]“ odpovídá cílovým sekvencím „a“, „b“, „c“ a „]“, ale nikoli cílové sekvenci „d“.

- „[^]abc]“ odpovídá cílové sekvenci „d“, ale nikoli cílovým sekvencím „a“, „b“, „c“ nebo „]“.

V `ECMAScript`použijte znak '\\] ' pro reprezentaci znaku '] ' ve výrazu závorky.

Příklady:

- „[]a“ odpovídá cílové sekvenci „a“, protože výraz závorky je prázdný.

- "[\\] ABC]" odpovídá cílovým sekvencím "a", "b", "c" a "]", ale nikoli cílové sekvenci "d".

### <a name="negative-assert"></a>Záporný kontrolní výraz

Záporný kontrolní výraz odpovídá všemu kromě svého obsahu. Nespotřebovává žádné znaky v cílové sekvenci. Například "(! AA) (a\*)" odpovídá cílové sekvenci "a" a přidruží skupinu zachycení 1 k dílčí sekvenci "a". Neodpovídá cílové sekvenci „aa“, ale cílové sekvenci „aaa“.

### <a name="negative-word-boundary-assert"></a>Záporný kontrolní výraz hranice slova

Negativní kontrolní výraz hranice slova odpovídá, pokud aktuální pozice v cílovém řetězci není hned za *hranicí slova*.

### <a name="non-capture-group"></a>Skupina bez zachycení

Skupina bez zachycení označuje svůj obsah jako jednu jednotku v gramatice regulárního výrazu, ale neoznačuje popiskem cílový text. Například "(a) (?: b)\*(c)" odpovídá cílovému textu "abbc" a přidruží skupinu zachycení 1 k dílčí sekvenci "a" a skupinu zachycení 2 k dílčí sekvenci "c".

### <a name="non-greedy-repetition"></a>Opakování bez metody Greedy

Opakování bez metody Greedy spotřebovává nejkratší dílčí sekvenci cílové sekvence, která odpovídá vzoru. Opakování s metodou Greedy spotřebovává nejdelší sekvenci. Například "(a +) (a\*b)" odpovídá cílové sekvenci "aaab". Je-li použito opakování bez metody Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „a“ na začátku cílové sekvence a skupinu zachycení 2 k dílčí sekvenci „aab“ na konci cílové sekvence. Je-li použita shoda s metodou Greedy, přiřadí skupinu zachycení 1 k dílčí sekvenci „aaa“ a skupinu zachycení 2 k dílčí sekvenci „b“.

### <a name="octal-escape-sequence"></a>Osmičková řídicí sekvence

Osmičková řídicí sekvence je zpětné lomítko následované jednou, dvěma nebo třemi osmičkovými číslicemi (0-7). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí těchto číslic. Jsou-li všechny číslice „0“, sekvence je neplatná. Například „\101“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="ordinary-character"></a>Běžný znak

Běžný znak je jakýkoli platný znak, který nemá v aktuální gramatice zvláštní význam.

V `ECMAScript`má následující znaky zvláštní význam:

- ^  $  \  .  \*+  ?  (  )  \[  ]  {  }  &#124;

V `basic` a`grep`mají následující znaky zvláštní význam:

- .   \[   \

Také v `basic` a `grep`mají následující znaky zvláštní význam při použití v konkrétním kontextu:

- \*má zvláštní význam ve všech případech, s výjimkou toho, že se jedná o první znak v regulárním výrazu nebo první znak, který následuje po počátečním znaku ' ^ ' v regulárním výrazu, nebo pokud se jedná o první znak skupiny zachycení nebo první znak, který Následuje počáteční ' ^ ' ve skupině zachycení.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

V `extended`, `egrep` a`awk`mají následující znaky zvláštní význam:

- .   \[\   (   \*   +   ?   {   &#124;

Také v `extended`, `egrep`a `awk`mají následující znaky zvláštní význam při použití v konkrétním kontextu.

- ') má zvláštní význam v případě, že odpovídá předchozímu znaku '('.

- '^' má zvláštní význam, pokud je to první znak regulárního výrazu.

- '$' má zvláštní význam, pokud je to poslední znak regulárního výrazu.

Běžný znak odpovídá stejnému znaku v cílové sekvenci. Ve výchozím nastavení to znamená, že porovnání se zdaří, pokud jsou dva znaky zastoupeny stejnou hodnotou. V případě shody bez rozlišení velkých a malých písmen, `ch0` jsou `ch1` dva znaky `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`a shoda v případě. V případě shody závislé na národním prostředí, dvou `ch0` znaků `ch1` a porovnávání `traits.translate(ch0) == traits.translate(ch1)`, pokud.

### <a name="positive-assert"></a>Kladný kontrolní výraz

Kladný kontrolní výraz odpovídá svému obsahu, ale nespotřebovává žádné znaky v cílové sekvenci.

Příklady:

- "(= AA) (a\*)" odpovídá cílové sekvenci "AAAA" a přidruží skupinu zachycení 1 k dílčí sekvenci "AAAA".

- "(AA)" (\*a) "odpovídá cílové sekvenci" AAAA "a přidruží skupinu zachycení 1 k dílčí sekvenci" AA "na začátku cílové sekvence a skupinu zachycení 2 k dílčí sekvenci" AA "na konci cílové sekvence.

- "(= AA) (a)&#124;(a)" odpovídá cílové sekvenci "a" a přidruží skupinu zachycení 1 k prázdné sekvenci (protože pozitivní kontrolní výraz se nezdařil) a skupina zachycení 2 k dílčí sekvenci "a". Také odpovídá cílové sekvenci „aa“ a přiřadí skupinu zachycení 1 k dílčí sekvenci „aa“ a skupinu zachycení 2 k prázdné sekvenci.

### <a name="unicode-escape-sequence"></a>Řídicí sekvence Unicode

Řídicí sekvence Unicode je zpětné lomítko následované písmenem „u“ a čtyřmi šestnáctkovými číslicemi (0-9a-fA-F). Odpovídá znaku v cílové sekvenci, který má hodnotu určenou pomocí čtyř číslic. Například „\u0041“ odpovídá cílové sekvenci „A“, pokud se používá kódování znaků ASCII.

### <a name="wildcard-character"></a>Zástupný znak

Zástupný znak odpovídá libovolnému znaku v cílovém výrazu, s výjimkou nového řádku.

### <a name="word-boundary"></a>Hranice slova

Hranice slova se vyskytuje v následujících situacích:

- Aktuální znak je na začátku cílové sekvence a je jedním ze znaků slova.`A-Za-z0-9_.`

- Aktuální poloha znaku je za koncem cílové sekvence a poslední znak v cílové sekvenci je jedním ze znaků slova.

- Aktuální znak je jedním ze znaků slova a předchozí znak není.

- Aktuální znak není jedním ze znaků slova a předchozí znak je.

### <a name="word-boundary-assert"></a>Kontrolní výraz hranice slova

Kontrolní výraz hranice slova odpovídá, pokud aktuální pozice v cílovém řetězci následuje hned za hranicí *slova*.

## <a name="matchingandsearching"></a>Porovnání a hledání

Aby regulární výraz odpovídal cílové sekvenci, musí celý regulární výraz odpovídat celé cílové sekvenci. Například regulární výraz „bcd“ odpovídá cílové sekvenci „bcd“, ale nikoli cílové sekvenci „abcd“ ani cílové sekvenci „bcde“.

Aby hledání regulárního výrazu bylo úspěšné, někde v cílové sekvenci se musí nacházet dílčí sekvence, která odpovídá regulárnímu výrazu. Hledání obvykle najde odpovídající dílčí sekvenci nejvíce vlevo.

Příklady:

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcd" je úspěšné a odpovídá celé sekvenci. Stejné vyhledávání v cílové sekvenci "abcd" je také úspěšné a odpovídá posledním třem znakům. Stejné vyhledávání v cílové sekvenci "bcde" je také úspěšné a odpovídá prvním třem znakům.

- Hledání regulárního výrazu "bcd" v cílové sekvenci "bcdbcd" je úspěšné a odpovídá prvním třem znakům.

Pokud existuje více než jedna dílčí sekvence, která odpovídá v určitém umístění cílové sekvence, můžete odpovídající vzor vybrat dvěma způsoby. *První shoda* zvolí dílčí sekvenci, která byla nalezena jako první, když se regulární výraz shoduje. *Nejdelší shoda* zvolí nejdelší dílčí sekvenci z těch, které se v daném umístění shodují. Pokud existuje více než jedna dílčí sekvence, která má maximální délku, nejdelší shoda zvolí tu, která byla nalezena jako první. Například pokud je použita první shoda, hledání regulárního výrazu "b&#124;BC" v cílové sekvenci "abcd" odpovídá dílčí sekvenci "b", protože levý termín alternace odpovídá této podsekvenci; Proto první porovnávání nezkouší pravou stranu alternace. Při použití nejdelší shody stejné vyhledávání odpovídá „bc“, protože „bc“ je delší než „b“.

Částečná shoda bude úspěšná, pokud shoda dosáhne konce cílové sekvence bez selhání, i když nedosáhla konce regulárního výrazu. Proto by po úspěchu částečné shody mohlo připojení znaků k cílové sekvenci způsobit pozdější selhání částečné shody. Po neúspěchu částečné shody však připojení znaků k cílové sekvenci nemůže způsobit pozdější úspěch částečné shody. Například v případě částečné shody odpovídá „ab“ cílové sekvenci „a“, ale nikoli „ac“.

## <a name="formatflags"></a>Příznaky formátu

|Pravidla formátu jazyka ECMAScript|Pravidla formátu SED|Náhradní text|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|Sekvence znaků, která odpovídá celému regulárnímu výrazu`[match[0].first, match[0].second)`()|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (znak dolaru následovaný zadní uvozovkou)||Sekvence znaků, která předchází dílčí sekvenci, která odpovídá regulárnímu výrazu`[match.prefix().first, match.prefix().second)`()|
|„$'“ (znak dolaru následovaný počáteční uvozovkou)||Sekvence znaků, která následuje po podsekvenci, která odpovídá regulárnímu`[match.suffix().first, match.suffix().second)`výrazu ()|
|„$n“|„\n“|Sekvence znaků, která odpovídá skupině zachycení na pozici `n`, kde `n` je číslo mezi 0 a 9 (`[match[n].first, match[n].second)`)|
||\\\n|„\n“|
|„$nn“||Sekvence znaků, která odpovídá skupině zachycení na pozici `nn`, kde `nn` je číslo mezi 10 a 99 (`[match[nn].first, match[nn].second)`)|

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)
