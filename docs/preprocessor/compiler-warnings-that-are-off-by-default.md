---
title: Upozornění kompilátoru, která jsou ve výchozím natavení vypnuta.
ms.date: 05/30/2018
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: e189ead864fe2be6e0ccb3bc76a58f2441740076
ms.sourcegitcommit: a901c4acbfc80ca10663d37c09921f04c5b6dd17
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2019
ms.locfileid: "58142557"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Upozornění kompilátoru, které jsou ve výchozím nastavení vypnuta

Kompilátor podporuje upozornění, která jsou vypnuté ve výchozím nastavení, protože většina vývojářů nenajdete je užitečné. V některých případech upozorňují stylistické možnost volby, ani s společné idiomy ve starším kódu. Další varování jsou týkajících se používání rozšíření společnosti Microsoft pro jazyk. V ostatních případech označují oblast, ve které programátoři často vytvářet nesprávné předpoklady, které mohou vést k neočekávaným nebo nedefinované chování. Pokud je povoleno, může některá tato upozornění se zobrazí v mnoha případech v záhlaví knihovny. Knihovny runtime jazyka C a standardní knihovny C++ jsou určeny k emitování žádná upozornění pouze na úrovni upozornění [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Povolit upozornění, které jsou ve výchozím nastavení vypnuta

Můžete povolit upozornění, která jsou obvykle vypnuto ve výchozím nastavení pomocí jedné z následujících možností:

- **#pragma warning (výchozí:** *warning_number* **)**

   Zadané upozornění (*warning_number*) je na výchozí úrovni povoleno. Dokumentace pro upozornění obsahuje výchozí úroveň upozornění.

- **#pragma warning (** *warning_level* **:** *warning_number* **)**

   Zadané upozornění (*warning_number*) je na zadané úrovni povoleno (*warning_level*).

- [/ Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` Povolí všechna upozornění, které jsou ve výchozím nastavení vypnuta. Pokud použijete tuto možnost, můžete vypnout jednotlivých upozornění pomocí [/wd](../build/reference/compiler-option-warning-level.md) možnost.

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   Tato možnost povolí upozornění *nnnn* na úrovni *L*.

## <a name="warnings-that-are-off-by-default"></a>Upozornění, která jsou ve výchozím nastavení vypnuta

Následující upozornění jsou vypnuté ve výchozím nastavení v sadě Visual Studio 2015 a novější verze:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (úroveň 4)|Enumerátor "*identifikátor*"v přepnutí výčtu'*výčet*' není explicitně zpracován popisek případu|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (úroveň 4)|Enumerátor "*identifikátor*"v přepnutí výčtu'*výčet*' není zpracován|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (úroveň 1) | "HRESULT" je převáděn na 'bool'; jste si jisti, že je to, co chcete? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (úroveň 3)|"*operátor*': nebezpečný převod z '*type_of_expression*"do"*type_required*"|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (úroveň 4)|"*identifikátor*': převod z '*type1*"do"*type2*", může dojít ke ztrátě dat.|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (úroveň 4)|"*operátor*': převod z '*type1*"do"*type2*", může dojít ke ztrátě dat|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (úroveň 4)|"*funkce*': zadaný žádný prototyp funkce: převod '(') '(void).|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (úroveň 4)|"*funkce*': členská funkce nepřepisuje žádnou virtuální členskou funkci základní třídy|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (úroveň 1)|"*virtual_function*': přepsání není k dispozici pro virtuální členskou funkci ze základní"*třídy*'; funkce je skrytá.|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (úroveň 3)|"*třídy*': třída má virtuální funkce, ale destruktor není virtuální|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (úroveň 4)|"*funkce*': přepsání není k dispozici pro virtuální členskou funkci ze základní"*typ*'; funkce je skrytá.|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (úroveň 3)|"*operátor*': unsigned/negative – neshoda konstanty|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (úroveň 4)|používá se nestandardní rozšíření: '*var*': Proměnná ovládacího prvku smyčky deklarovaná ve smyčce for-loop se používá mimo obor smyčky for loop|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (úroveň 4)|"*operátor*': výraz je vždy nepravda|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (úroveň 4)|"*typ*': použití nedefinovaného typu zjistil v metadat CLR – použití tohoto typu může vést k výjimce modulu runtime|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (úroveň 1)|Změna chování: "*funkce*" volá se, ale operátor členu byl zavolán v předchozích verzích|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (úroveň 1)|Změna chování: "*member1*"volá namísto"*člen2*.|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : použito v inicializačním seznamu základních členů|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (úroveň 4)|"*akce*': převod z '*type_1*"do"*type_2*", podepsaný/unsigned – neshoda|
|C4370 (úroveň 3)|došlo ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení|
|[C4371](../error-messages/compiler-warnings/c4371.md) (úroveň 3)|"*classname*': může mít ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení člena '*člen*.|
|C4388 (úroveň 4)|neshoda se znaménkem, nebo bez znaménka|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (úroveň 2)|"*funkce*': podpis funkce obsahuje typ"*typ*'; Jsou objekty C++ není bezpečné předávat mezi čistým kódem a kombinovaným nebo nativním kódem|
|C4426 (úroveň 1)|příznaky optimalizace se nemění, včetně záhlaví, může být #pragma optimize() <sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (úroveň 4)|"*class1*": Rozložení objektu pod: / vd2 se změní z důvodu virtuální base '*class2*.|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (úroveň 4)|přetypování dynamic_cast z virtuální base '*class1*"do"*class2*' může v některých kontextech selhat|
|C4444 (úroveň 3)|v tomto kontextu není implementována nejvyšší úroveň '__unaligned'|
|[C4464](../error-messages/compiler-warnings/c4464.md) (úroveň 4)|relativní cestu zahrnutí obsahuje '..'|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (úroveň 4)|Dopředná deklarace výčtu bez oboru musí mít základní typ (předpokládá se int) <sup>Perm</sup>|
|C4472 (úroveň 1)|"*identifikátor*' je nativní výčet: přidejte specifikátor přístupu (private/public) pro deklaraci spravovaného výčtu|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (úroveň 4)|"*funkce*': neodkazovaná vložená funkce se odebrala.|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (úroveň 4)|'type name': název typu překračuje limit metadat '*limit*"znaky|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (úroveň 1)|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (úroveň 1)|volání funkce před čárkou nemá seznamu argumentů|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (úroveň 1)|"*operátor*': operátor před čárkou nemá žádný vliv; očekával se operátor s vedlejším účinkem|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (úroveň 1)|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (úroveň 1)|"*operator1*': operátor před čárkou nemá žádný vliv; nechtěli jste použít '*operator2*'?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (úroveň 1)|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (úroveň 3)|'__assume' obsahuje efekt '*efekt*.|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (úroveň 4)|Informační: sémantika catch(...) se od verze Visual C++ 7.1; změnila strukturované výjimky (SEH) už se nezachycují.|
|C4574 (úroveň 4)|"*identifikátor*'je definován jako ' 0': chtěli jste použít ' #if *identifikátor*"?|
|C4577 (úroveň 1)|použít bez výjimky režimu; zpracování noexcept ukončení při výjimce není zaručena. Zadejte/EHsc|
|C4582 (úroveň 4)|"*typ*': konstruktor se nevolá implicitně|
|C4583 (úroveň 4)|"*typ*': destructor se nevolá implicitně|
|C4587 (úroveň 1)|"*anonymous_structure*': Změna chování: konstruktor se nevolá implicitně už|
|C4588 (úroveň 1)|"*anonymous_structure*': Změna chování: destruktor je už nevolá implicitně|
|C4596 (úroveň 4)|"*identifikátor*': Neplatný kvalifikovaný název v deklaraci člena <sup>14.3</sup> <sup>Perm</sup>|
|C4598 (úroveň 1 a úroveň 3)|"#include"*záhlaví*"!: číslo hlavičky *číslo* Předkompilovaná hlavička se neshoduje s aktuální kompilace na této pozici <sup>14.3</sup>|
|C4599 (úroveň 3)|"*možnost* *cesta*': argument příkazového řádku číslo *číslo* neodpovídá Předkompilovaná hlavička <sup>14.3</sup>|
|C4605 (úroveň 1)|! /D *– makro*"zadaný na aktuálním příkazovém řádku, ale nebyl zadán, kdy byla vytvořena předkompilované hlavičky|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (úroveň 3)|"*union_member*'již byl inicializován jiným členem Unie v seznamu inicializátorů,'*union_member*" <sup>Perm</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (úroveň 3)|#pragma warning: neexistuje číslo upozornění '*číslo*.|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (úroveň 4)|'derived class': výchozí konstruktor nelze generovat, protože výchozí konstruktor základní třídy je nedostupný|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (úroveň 4)|'derived class': kopírovací konstruktor nelze generovat, protože kopírovací konstruktor základní třídy je nedostupný|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (úroveň 4)|'derived class': operátor přiřazení nelze generovat, protože operátor přiřazení základní třídy je nedostupný|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (úroveň 1)|spřežky nejsou podporovány se -Ze. Posloupnosti znaků "*digraph*'není interpretována jako alternativní token pro'*char*.|
|[C4640 týkajícího](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (úroveň 3)|"*instance*': konstrukce lokálního statického objektu není bezpečná pro vlákno|
| C4643 (úroveň 4) | Předat dál deklarace "*identifikátor*' v oboru názvů std není povolen podle standardu jazyka C++. <sup>15.8</sup> |
|C4647 (úroveň 3)|Změna chování: __is_pod (*typ*) má jinou hodnotu v předchozích verzích|
|C4654 (úroveň 4)|Kód umístěný před vložení předkompilované hlavičky řádku budou ignorovány. Přidejte kód do předkompilované hlavičky. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (úroveň 4)|"*symbol*'není definován jako preprocesor makro, nahraďte '0' pro'*direktivy*.|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (úroveň 4)|"*symbol*': žádný parametr směrového atributu zadán, výchozí [v]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (úroveň 3)|"*uživatelem definovaného typu*': možné změny v chování, změna ve vrácení konvence volání|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (úroveň 1)|"*funkce*': podpis nesoukromého členu obsahuje sestavení privátního nativního typu '*native_type*.|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (úroveň 4)|"*funkce*': funkce není vložena|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (úroveň 3)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|přístup typu "*výraz*' / volatile:\<iso&#124;ms > nastavení; zvažte použití vnitřních funkcí Using __iso_volatile_load/store|
|C4749 (úroveň 4)|podmíněně podporováno: na které se netýkají nestandardním rozložením typu se použil offsetof '*typ*.|
|C4767 (úroveň 4)|Název oddílu "*symbol*" je delší než 8 znaků a bude zkrácen linkerem.|
|C4768 (úroveň 3)|atributy __declspec před specifikací propojení se ignorují.|
|C4774 (úroveň 4)|"*řetězec*': formátovací řetězec očekávaný v argumentu *číslo* není řetězcový literál|
|C4777 (úroveň 4)|"*funkce*': řetězec formátu"*řetězec*"vyžaduje argument typu"*type1*", ale variadický argument *číslo* má typ"*type2*.|
|C4786 (úroveň 3)|"*symbol*': název objektu byl zkrácen na"*číslo*"znaky v informacích o ladění|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (úroveň 4) | Implicitní převod z '*typ*' na typ bool. Ztráty informací možné <sup>16.0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (úroveň 4)|"*bajtů*"bajtů výplně se přidalo po konstrukci"*member_name*.|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (úroveň 1) | "*člen*': členská funkce lokální třídy nemá tělo. |
|C4826 (úroveň 2)|Převod z '*type1*"do"*type2*"je rozšířen o znaménko. To může způsobit neočekávané chování za běhu.|
|C4837 (úroveň 4)|zjistil se trigraph: "?? *znak*"nahrazuje"*znak*.|
|C4841 (úroveň 4)|nestandardní rozšíření: v offsetof použilo složené označení člena|
|C4842 (úroveň 4)|není zaručeno, že výsledek offsetof použitý pro typ pomocí vícenásobného dědění bude konzistentní napříč verzemi kompilátoru.|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (úroveň 4)|"_souboru_(*line_number*)' kompilátor nemůže vynutit pořadí vyhodnocování zleva doprava v inicializačního seznamu v závorkách|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (úroveň 1)|široký řetězcový literál přetypován na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (úroveň 1)|řetězcový literál přetypován na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (úroveň 1)|"*deklarátor*': identifikátor GUID lze přidružit pouze pomocí třídy, rozhraní nebo oboru názvů|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (úroveň 1)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (úroveň 4)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (úroveň 1)|reinterpret_cast použito mezi souvisejícími třídami: '*class1*"a"*class2*.|
|C4962|"*funkce*': profilováním řízené optimalizace zakázány, protože optimalizace způsobily nekonzistenci dat profilu|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (úroveň 4)|"*symbol*': specifikace výjimky se neshoduje s předchozí deklarací.|
|C4987 (úroveň 4)|použito nestandardní rozšíření: 'throw (...)'|
|C4988 (úroveň 4)|"*symbol*': proměnná deklarována mimo rozsah třídy a funkce|
|C5022|"*typ*': zadaných víc konstruktorů move|
|C5023|"*typ*': zadaných víc operátorů přiřazení přesunutí|
|C5024 (úroveň 4)|"*typ*': přesunout konstruktor byl implicitně definovaný jako odstraněný|
|C5025 (úroveň 4)|"*typ*': Přesuňte operátor přiřazení je implicitně definovaný jako odstraněný|
|C5026 (úroveň 1 a 4)|"*typ*': přesunout konstruktor byl implicitně definovaný jako odstraněný|
|C5027 (úroveň 1 a 4)|"*typ*': Přesuňte operátor přiřazení je implicitně definovaný jako odstraněný|
|C5029 (úroveň 4)|používá se nestandardní rozšíření: atributy zarovnání v C++ použít pro proměnné, datové členy a pouze typy značek|
|C5031 (úroveň 4)|#pragma warning(pop): pravděpodobně o neshodu, stav automaticky otevíraného upozornění vložil do jiného souboru <sup>14.1</sup>|
|C5032 (úroveň 4)|zjištěna #pragma warning(push) bez odpovídajícího příkazu #pragma warning(pop) <sup>14.1</sup>|
|C5034|použití vnitřních "*vnitřní*" způsobí, že funkce *funkce* se zkompiluje jako kód hosta <sup>15.3</sup>|
|C5035|použití funkce '*funkce*"způsobí, že funkce *funkce* se zkompiluje jako kód hosta. <sup>15.3</sup>|
|C5036 (úroveň 1)|převod ukazatele funkci VarArgs při kompilování x86arm64 "*type1*"do"*type2*" <sup>15.3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (úroveň 4)|datový člen "*member1*'bude inicializován po datovém členu'*člen2*" <sup>15.3</sup>|
|C5039 (úroveň 4)|"*funkce*': ukazatel nebo odkaz na potenciální vyvolávací funkci předán do funkce extern C v - EHc. Pokud tato funkce vyvolá výjimku, může dojít k nedefinovanému chování. <sup>15.5</sup>|
|C5042 (úroveň 3)|"*funkce*': deklarace funkcí v blokovém rozsahu nemůže být zadané"vložené"ve standardním jazyce C++; odeberte specifikátor inline' <sup>15.5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|Kompilátor vloží zmírnění hrozby Spectre pro zatížení paměti, pokud zadaný přepínač/qspectre <sup>15.7</sup>|

<sup>14.1</sup> toto upozornění je k dispozici od verze Visual Studio 2015 Update 1.<br/>
<sup>14.3</sup> toto upozornění je k dispozici od verze Visual Studio 2015 Update 3.<br/>
<sup>15.3</sup> toto upozornění je k dispozici od verze Visual Studio 2017 verze 15.3.<br/>
<sup>15.5</sup> toto upozornění je k dispozici od verze Visual Studio 2017 verze 15.5.<br/>
<sup>15.7</sup> toto upozornění je k dispozici od verze Visual Studio 2017 verze 15.7.<br/>
<sup>15.8</sup> toto upozornění je k dispozici od verze Visual Studio 2017 verze 15.8.<br/>
::: moniker range=">= vs-2019"
<sup>16.0</sup> toto upozornění je k dispozici od verze Visual Studio. 2019 RTM.<br/>
::: moniker-end
<sup>Jako trvalé</sup> toto upozornění je vypnuté, pokud [/ permissive-](../build/reference/permissive-standards-conformance.md) – možnost kompilátoru je nastavena.<br/>

## <a name="warnings-off-by-default-in-earlier-versions"></a>Upozornění vypnuto ve výchozím nastavení v dřívějších verzích

Tato upozornění bylo vypnuto ve výchozím nastavení ve verzích kompilátoru před Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (úroveň 2)|"*převod*': zkrácení z '*type1*"do"*type2*"|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (úroveň 1)|"*proměnnou*': zkrácení ukazatele z '*typ*"do"*typ*"|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (úroveň 1)|"*operace*': převod z '*type1*"do"*type2*' větší velikosti|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (úroveň 1)|"*operátor*': nulové rozšíření"*type1*"do"*type2*' větší velikosti|

Toto upozornění je vypnuto ve výchozím nastavení ve verzích kompilátoru před Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (úroveň 4)|chybějící specifikátor typu: předpokládá se int Poznámka: C už nepodporuje typ default int.|

## <a name="see-also"></a>Viz také

[warning](../preprocessor/warning.md)