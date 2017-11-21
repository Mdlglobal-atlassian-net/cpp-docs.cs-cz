---
title: "Upozornění kompilátoru, která jsou ve výchozím nastavení vypnuté | Microsoft Docs"
ms.date: 11/04/2016
ms.technology: cpp-tools
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1dec9728679629f25ddbea93956fd25d9b29ef59
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Upozornění kompilátoru, která jsou ve výchozím natavení vypnuta.

Kompilátor obsahuje upozornění, která jsou ve výchozím nastavení vypnuta, protože většina uživatelů je nechce vidět. Tato varování však můžete povolit pomocí jedné z následujících možností.

`#pragma warning(default : warning_number )`  
Zadaný upozornění (`warning_number`) je povoleno na výchozí úrovni. Dokumentace pro upozornění obsahuje výchozí úroveň upozornění.

`#pragma warning( warning_level : warning_number )`  
Zadaný upozornění (`warning_number`) je povolena na zadané úrovni (`warning_level`).

[/ Wall](../build/reference/compiler-option-warning-level.md)  
**/ Horní** umožňuje všech upozornění, které jsou ve výchozím nastavení vypnuté.

Následující upozornění jsou ve výchozím stavu vypnuta.

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (úroveň 4)|'identifier' výčtu v přepnutí výčtu 'enumeration' není explicitně zpracován popiskem případu|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (úroveň 4)|'identifier' výčtu v přepnutí výčtu 'enumeration' není zpracován|
|C4191 (úroveň 3)|'operator/operation': nebezpečný převod z 'type of expression' na 'type required'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (úroveň 4)|'identifier': převod z 'type1' na 'type2', možná ztráta dat|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (úroveň 4)|'operator': převod z 'type1' na 'type2', možná ztráta dat|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (úroveň 4)|'function': není uveden žádný prototyp funkce: převod '()' na '(void)'|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (úroveň 4)|'function': členská funkce nepřepisuje žádnou virtuální členskou funkci základní třídy.|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (úroveň 1)|'virtual_function': k dispozici není přepsání pro virtuální členskou funkci ze základní třídy 'class'; funkce je skrytá.|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (úroveň 3)|'class': třída má virtuální funkce, ale destruktor není virtuální|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (úroveň 4)|'function': k dispozici není přepsání pro virtuální členskou funkci ze základního typu 'type'; funkce je skrytá.|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (úroveň 3)|'operator': konstantní neshoda bez znaménka nebo negativní|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (úroveň 4)|používá nestandardní rozšíření: 'var': řídicí proměnná smyčky deklarovaná ve smyčce For je použita mimo rozsah smyčky For|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (úroveň 4)|'operator': výraz je vždy nepravda|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (úroveň 4)|'type': zjištěno použití nedefinovaného typu v metadatech CLR – použití tohoto typu může vést k výjimce modulu runtime.|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (úroveň 1)|změna chování: byla volána funkce 'function', ale operátor členu byl zavolán v předchozích verzích|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (úroveň 1)|změna chování: byl zavolán člen 'member1' místo členu 'member2'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : použito v inicializačním seznamu základních členů|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (úroveň 4)|'action': převod z 'type_1' na 'type_2', neshoda se znaménkem, nebo bez znaménka|
|C4370 (úroveň 3)|došlo ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení|
|C4371 (úroveň 3)|mohlo dojít ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení člena 'member'|
|C4388 (úroveň 4)|neshoda se znaménkem, nebo bez znaménka|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (úroveň 2)|'function': podpis funkce obsahuje typ 'type'; není bezpečné předávat objekty jazyka C++ mezi čistým kódem a kombinovaným nebo nativním kódem|
|C4426 (úroveň 1)|Optimalizace příznaky změněno poté, co včetně záhlaví, může být způsobeno #pragma optimize()|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (úroveň 4)|'class1': z důvodu virtuální base 'class2' se změní rozložení objektů v /vd2|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (úroveň 4)|v některých kontextech může dojít k selhání dynamic_cast z virtuální base 'class1' na 'class2'|
|C4444 (úroveň 3)|v tomto kontextu není implementována nejvyšší úroveň '__unaligned'|
|C4464 (úroveň 4)|zahrnují relativní cesta obsahuje '..'|
|C4472 (úroveň 1)|'identifier' je nativní výčet: přidejte specifikátor přístupu (soukromého, nebo veřejného) pro deklaraci spravovaného výčtu.|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (úroveň 4)|'function': vložená funkce, na kterou neexistuje odkaz, byla odebrána.|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (úroveň 4)|'type name': název typu překračuje limit znaků metadat 'limit'|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (úroveň 1)|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (úroveň 1)|volání funkce před čárkou nemá seznamu argumentů|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (úroveň 1)|'operator': operátor před čárkou nemá žádný vliv; očekávaný operátor s vedlejším účinkem|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (úroveň 1)|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (úroveň 1)|'operator': operátor před čárkou nemá žádný vliv; mysleli jste 'operator'?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (úroveň 1)|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (úroveň 3)|'__assume' obsahuje efekt 'effect'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (úroveň 4)|Informační: catch(...) sémantiku změněné od Visual C++ 7.1; strukturované výjimky (SEH) jsou již zachyceny|
|C4574 (úroveň 4)|'identifier' je definován jako '0': chtěli jste použít '#if identifier'?|
|C4582 (úroveň 4)|'*typ*': konstruktor není volán implicitně|
|C4583 (úroveň 4)|'*typ*': implicitně nevolá – destruktor|
|C4587 (úroveň 1)|'*anonymous_structure*': změna v chování: už implicitně volání konstruktoru|
|C4588 (úroveň 1)|'*anonymous_structure*': změna v chování: už implicitně destruktoru|
|C4598 (úroveň 1 a úroveň 3)|' #include "*záhlaví*"': číslo záhlaví *číslo* v předkompilovaných hlaviček neodpovídá aktuální kompilace na této pozici|
|C4599 (úroveň 3)|'*možnost* *cesta*': argument příkazového řádku číslo *číslo* neodpovídá předem kompilovaném záhlaví|
|C4605 (úroveň 1)|' /D*makro*' zadaný u aktuálního příkazového řádku, ale nebyl zadán, pokud byl vytvořený předkompilovaných hlaviček|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (úroveň 3)|#pragma warning: neexistuje číslo upozornění 'number'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (úroveň 4)|'derived class': výchozí konstruktor nelze generovat, protože výchozí konstruktor základní třídy je nedostupný|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (úroveň 4)|'derived class': kopírovací konstruktor nelze generovat, protože kopírovací konstruktor základní třídy je nedostupný|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (úroveň 4)|'derived class': operátor přiřazení nelze generovat, protože operátor přiřazení základní třídy je nedostupný|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (úroveň 1)|spřežky nejsou podporovány se -Ze. Sekvence znaků 'digraph' není interpretována jako alternativní token pro 'char'.|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (úroveň 3)|'instance': stavba místního statického objektu není bezpečná pro přístup z více vláken|
|C4647 (úroveň 3)|Změna v chování: __is_pod (*typu*) má jinou hodnotu v předchozích verzích|
|C4654 (úroveň 4)|Kód umístěna před patří předkompilovaných hlaviček řádek bude ignorován. Přidávání kódu do předkompilovaných hlaviček.|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (úroveň 4)|'*symbol*'není definován jako makro preprocesoru, nahraďte '0' pro'*direktivy*.|
|C4682 (úroveň 4)|'*symbol*': atribut směrovou parametr zadán, jako výchozí bude použit [v]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (úroveň 3)|'*uživatelsky definovaný typ.*': vrátit změnu v hodnotě UDT možné změnu v chování konvence volání|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (úroveň 1)|'*funkce*': podpis privátního člena obsahuje privátní nativní typ sestavení 'native_type.|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (úroveň 4)|'*funkce*': není vložená funkce|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (úroveň 3)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|volatile přístup '*výraz*' podléhá/volatile:\<iso &#124; ms > nastavení; zvažte použití __iso_volatile_load/úložiště vnitřní funkce|
|C4749 (úroveň 4)|podmíněná podporována: offsetof – použít u typu standard non-rozložení '*typ*.|
|C4767 (úroveň 4)|název sekce '*symbol*' je delší než 8 znaků a bude zkrácen podle linkeru|
|C4768 (úroveň 3)|atributy __declspec před specifikaci propojení se ignorují.|
|C4774 (úroveň 4)|'*řetězec*': v argument byl očekáván řetězec formátu *číslo* není řetězec literálu|
|C4786 (úroveň 3)|'*symbol*': název objektu byl zkrácen na znaky "číslo" v informace o ladění|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (úroveň 4)|odsazení 'bytes' bajtů přidáno po vytvoření 'member_name'|
|C4826 (úroveň 2)|Převod z '*type1*'do'*type2*' je rozšířeny. To může způsobit neočekávané modul runtime chování.|
|C4837 (úroveň 4)|trigraph zjistil: '?? *znak*"nahradit"*znak*.|
|C4841 (úroveň 4)|nestandardní rozšíření používané: označení složené člen použít v offsetof –|
|C4842 (úroveň 4)|výsledek offsetof "–", které se použijí k typu pomocí vícenásobná dědičnost nemusí být konzistentní mezi verzemi kompilátoru|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (úroveň 4)|'_soubor_(*line_number*), kompilátor nemusí vynutit pořadí vyhodnocení zleva doprava v seznamu braced inicializace|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (úroveň 1)|široký řetězcový literál přetypován na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (úroveň 1)|řetězcový literál přetypován na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (úroveň 1)|'declarator': identifikátor GUID lze přidružit pouze ke třídám, rozhraním, nebo oborem názvů|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (úroveň 1)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (úroveň 4)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (úroveň 1)|reinterpret_cast použito mezi souvisejícími třídami: 'class1' a 'class2'|
|C4962|'function': profilováním řízené optimalizace zakázány, protože optimalizace způsobily nekonzistenci dat profilu|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (úroveň 4)|'*symbol*': specifikace výjimek neodpovídá předchozí deklarace|
|C4987 (úroveň 4)|použito nestandardní rozšíření: 'throw (...)'|
|C4988 (úroveň 4)|'*symbol*': proměnná deklarována mimo rozsah třídy nebo funkce|
|C5022|'*typ*': více přesunutí konstruktory zadaný|
|C5023|'*typ*': více operátory přiřazení pro přesunutí zadaný|
|C5024 (úroveň 4)|'*typ*': přesunout konstruktor byl implicitně definován jako odstranit|
|C5025 (úroveň 4)|'*typ*': přesunout operátor přiřazení byl implicitně definován jako odstranit|
|C5026 (úroveň 1 a 4)|'*typ*': přesunout konstruktor byl implicitně definován jako odstranit|
|C5027 (úroveň 1 a 4)|'*typ*': přesunout operátor přiřazení byl implicitně definován jako odstranit|
|C5029 (úroveň 4)|nestandardní rozšíření používané: zarovnání atributy v jazyce C++ vztahuje na proměnné, datové členy a pouze typy značek|
|C5031 (úroveň 4)|#pragma warning(pop): pravděpodobně neshoda, odebrání nabídnutých v jiném souboru stavu upozornění|
|C5032 (úroveň 4)|zjištěna #pragma warning(push) se žádné odpovídající warning(pop) #pragma|
|C5035|pomocí funkce '*funkce*' způsobí, že funkce *funkce* sestavují jako kód hosta|
|C5036 (úroveň 1)|vararg funkce Převod ukazatele, když kompilujete s /hybrid:x86arm64 '*type1*'do'*type2*.|

Tato upozornění jsou vypnuté, pokud [/ projektovou-](../build/reference/permissive-standards-conformance.md) nastavena – možnost kompilátoru:

|||
|-|-|
|[C4471 (úroveň 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md)|Dopředná deklarace výčtu bez ohledu na obor musí mít základní typ (předpokládá se int).|
|[C4608 (úroveň 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|' – typ union\_člen ' již byl inicializován jiný union člen v seznamu inicializátor 'union_member.|


Tato upozornění byly vypnout ve výchozím nastavení ve verzích kompilátoru před Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (úroveň 2)|'conversion': zkrácení z 'type1' na 'type2'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (úroveň 1)|'variable': zkrácení ukazatele z 'type' na 'type'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (úroveň 1)|'operation': převod z 'type1' na 'type2' větší velikosti|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (úroveň 1)|'operátor': nulové rozšíření 'type1' na 'type2' větší velikosti|

Tato upozornění byly vypnout ve výchozím nastavení ve verzích kompilátoru před Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (úroveň 4)|chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.|

## <a name="see-also"></a>Viz také

[upozornění](../preprocessor/warning.md)