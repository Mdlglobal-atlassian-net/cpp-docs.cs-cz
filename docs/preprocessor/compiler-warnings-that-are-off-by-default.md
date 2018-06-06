---
title: Upozornění kompilátoru, která jsou ve výchozím nastavení vypnuté | Microsoft Docs
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d311c730781aee70d4b77723ddec98a79407e42a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705563"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Upozornění kompilátoru, která jsou ve výchozím nastavení vypnuté

Kompilátor obsahuje upozornění, která jsou vypnuté ve výchozím nastavení, protože většina vývojářů nechcete zobrazovat. V některých případech se představují stylových výběr, nebo jsou běžné idioms ve starším kódu nebo využívat výhod rozšíření Microsoft pro jazyk. V ostatních případech označují oblast, kde programátory často provést nesprávný předpoklady, které mohou vést k neočekávaným nebo nedefinované chování. Některá tato upozornění může být velmi aktivní v hlavičkách knihovny. Knihovny jazyka C runtime a standardní knihovny C++ jsou určené pro vydávání žádná varování jenom na úrovni upozornění [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Povolit upozornění, která jsou ve výchozím nastavení vypnuté

Můžete povolit upozornění, která jsou obvykle vypnout ve výchozím nastavení pomocí jedné z následujících možností:

- **#pragma – upozornění (výchozí:** *warning_number* **)**

   Zadaný upozornění (*warning_number*) je povoleno na výchozí úrovni. Dokumentace pro upozornění obsahuje výchozí úroveň upozornění.

- **#pragma – upozornění (** *warning_level* **:** *warning_number* **)**

   Zadaný upozornění (*warning_number*) je povolena na zadané úrovni (*warning_level*).

- [/ Wall](../build/reference/compiler-option-warning-level.md)

   **/ Horní** umožňuje všech upozornění, které jsou ve výchozím nastavení vypnuté. Pokud použijete tuto možnost, můžete vypnout jednotlivé upozornění pomocí [/wd](../build/reference/compiler-option-warning-level.md) možnost.

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   To umožňuje upozornění *nnnn* na úrovni *L*.

## <a name="warnings-that-are-off-by-default"></a>Upozornění, která jsou ve výchozím nastavení vypnuté

Ve výchozím nastavení v sadě Visual Studio 2015 a novějších verzích jsou vypnuté následující upozornění:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (úroveň 4)|Enumerátor '*identifikátor*"v switch výčtu'*– výčet*' není explicitně zpracovávaných případu štítek|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (úroveň 4)|Enumerátor '*identifikátor*"v switch výčtu'*– výčet*' nejsou zpracovávány|
|C4191 (úroveň 3)|'*operátor*': unsafe převod z '*type_of_expression*'do'*type_required*.|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (úroveň 4)|'*identifikátor*': převod '*type1*'do'*type2*', možné ztrátě dat.|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (úroveň 4)|'*operátor*': převod '*type1*'do'*type2*', možné ztrátě dat.|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (úroveň 4)|'*funkce*': žádné funkce prototypu zadané: převádění (')' do '(void).|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (úroveň 4)|'*funkce*': členská funkce nepřepisuje všechny základní třídy člena virtuální funkce|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (úroveň 1)|'*virtual_function*': přepsání není k dispozici pro člena virtuální funkci z základní '*– třída*'; funkce je skrytá.|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (úroveň 3)|'*třída*': třída má virtuální funkce, ale není virtuální – destruktor|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (úroveň 4)|'*funkce*': přepsání není k dispozici pro člena virtuální funkci z základní '*typ*'; funkce je skrytá.|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (úroveň 3)|'*operátor*': Neshoda konstantní bez znaménka nebo záporná|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (úroveň 4)|nestandardní rozšíření používané: '*var*': mimo obor cyklu for se používá proměnná řízení smyčky deklarované v pro – smyčky|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (úroveň 4)|'*operátor*': výraz je vždy false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (úroveň 4)|'*typ*': použití nedefinované typu zjistil v CLR meta-data - použití tohoto typu může vést k výjimku modulu runtime|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (úroveň 1)|Změna v chování: '*funkce*se volá, ale byla zavolána operátor členů v předchozích verzích|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (úroveň 1)|Změna v chování: '*člen1*'názvem místo'*člen2*.|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : použito v inicializačním seznamu základních členů|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (úroveň 4)|'*akce*': převod '*type_1*'do'*type_2*', podepsané nepodepsaných neshoda|
|C4370 (úroveň 3)|došlo ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení|
|[C4371](../error-messages/compiler-warnings/c4371.md) (úroveň 3)|'*classname*': mohlo dojít ke změně rozložení třídy z předchozí verze kompilátoru kvůli lepší okolních člena '*člen*.|
|C4388 (úroveň 4)|neshoda se znaménkem, nebo bez znaménka|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (úroveň 2)|'*funkce*': podpis funkce obsahuje typ '*typ*'; Objekty C++ jsou unsafe předat mezi čistý kód a smíšený nebo nativní|
|C4426 (úroveň 1)|Optimalizace příznaky změněno poté, co včetně záhlaví, může být způsobeno #pragma optimize() <sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (úroveň 4)|'*class1*': objekt rozložení pod /vd2 se změní z důvodu virtuální základní '*class2*.|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (úroveň 4)|dynamic_cast z virtuální základní '*class1*'do'*class2*' by mohlo selhat v některých kontextech|
|C4444 (úroveň 3)|v tomto kontextu není implementována nejvyšší úroveň '__unaligned'|
|[C4464](../error-messages/compiler-warnings/c4464.md) (úroveň 4)|zahrnují relativní cesta obsahuje '..'|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (úroveň 4)|deklaraci předat dál bez ohledu na obor výčtu musí mít základní typ (int předpokládá, že) <sup>oprávnění</sup>|
|C4472 (úroveň 1)|'*identifikátor*' je nativní výčet: přidejte specifikátor přístupu (soukromého a veřejného) deklarovat spravované výčtu|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (úroveň 4)|'*funkce*': byl odebrán neregistrované vložené funkce|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (úroveň 4)|"název typu": název typu překračuje limit meta-data "*limit*' znaků|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (úroveň 1)|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (úroveň 1)|volání funkce před čárkou nemá seznamu argumentů|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (úroveň 1)|'*operátor*': operátor před čárkou nemá žádný vliv; očekávaný operátoru s vedlejším účinkem|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (úroveň 1)|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (úroveň 1)|'*operator1*': operátor před čárkou nemá žádný vliv; nebyla hodláte '*operator2*'?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (úroveň 1)|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (úroveň 3)|'__assume' obsahuje vliv '*vliv*.|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (úroveň 4)|Informační: catch(...) sémantiku změněné od Visual C++ 7.1; strukturované výjimky (SEH) jsou již zachyceny|
|C4574 (úroveň 4)|'*identifikátor*'je definován jako ' 0': měli jste na mysli používat ' #if *identifikátor*'?|
|C4577 (úroveň 1)|použít s žádná výjimka zpracování zadaný; režim noexcept ukončení na výjimka není zaručena. Zadejte /EHsc|
|C4582 (úroveň 4)|'*typ*': konstruktor není volán implicitně|
|C4583 (úroveň 4)|'*typ*': implicitně nevolá – destruktor|
|C4587 (úroveň 1)|'*anonymous_structure*': změna v chování: už implicitně volání konstruktoru|
|C4588 (úroveň 1)|'*anonymous_structure*': změna v chování: už implicitně destruktoru|
|C4596 (úroveň 4)|'*identifikátor*': Neplatný kvalifikovaný název do deklarace členů <sup>14.3</sup> <sup>oprávnění</sup>|
|C4598 (úroveň 1 a úroveň 3)|' #include "*záhlaví*"': číslo záhlaví *číslo* v předkompilovaných hlaviček neodpovídá aktuální kompilace na této pozici <sup>14.3</sup>|
|C4599 (úroveň 3)|'*možnost* *cesta*': argument příkazového řádku číslo *číslo* neodpovídá předem kompilovaném záhlaví <sup>14.3</sup>|
|C4605 (úroveň 1)|' /D*makro*' zadaný u aktuálního příkazového řádku, ale nebyl zadán, pokud byl vytvořený předkompilovaných hlaviček|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (úroveň 3)|'*union_member*'již byl inicializován jiný union člen v seznamu inicializátor'*union_member*' <sup>oprávnění</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (úroveň 3)|#pragma – upozornění: neexistuje číslo upozornění "*číslo*.|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (úroveň 4)|'derived class': výchozí konstruktor nelze generovat, protože výchozí konstruktor základní třídy je nedostupný|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (úroveň 4)|'derived class': kopírovací konstruktor nelze generovat, protože kopírovací konstruktor základní třídy je nedostupný|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (úroveň 4)|'derived class': operátor přiřazení nelze generovat, protože operátor přiřazení základní třídy je nedostupný|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (úroveň 1)|spřežky nejsou podporovány se -Ze. Znak pořadí '*spřežka*'nebyl interpretován jako alternativní token pro'*char*.|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (úroveň 3)|'*instance*': vytváření místní statické objektu není bezpečné pro přístup z více vláken|
|C4647 (úroveň 3)|Změna v chování: __is_pod (*typu*) má jinou hodnotu v předchozích verzích|
|C4654 (úroveň 4)|Kód umístěna před patří předkompilovaných hlaviček řádek bude ignorován. Přidávání kódu do předkompilovaných hlaviček. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (úroveň 4)|'*symbol*'není definován jako makro preprocesoru, nahraďte '0' pro'*direktivy*.|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (úroveň 4)|'*symbol*': atribut směrovou parametr zadán, jako výchozí bude použit [v]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (úroveň 3)|'*uživatelsky definovaný typ.*': vrátit změnu v hodnotě UDT možné změnu v chování konvence volání|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (úroveň 1)|'*funkce*': podpis privátního člena obsahuje privátní nativní typ sestavení '*native_type*.|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (úroveň 4)|'*funkce*': není vložená funkce|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (úroveň 3)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|volatile přístup '*výraz*' podléhá/volatile:\<iso&#124;ms > nastavení; zvažte použití __iso_volatile_load/úložiště vnitřní funkce|
|C4749 (úroveň 4)|podmíněná podporována: offsetof – použít u typu standard non-rozložení '*typ*.|
|C4767 (úroveň 4)|název sekce '*symbol*' je delší než 8 znaků a bude zkrácen podle linkeru|
|C4768 (úroveň 3)|atributy __declspec před specifikaci propojení se ignorují.|
|C4774 (úroveň 4)|'*řetězec*': v argument byl očekáván řetězec formátu *číslo* není řetězec literálu|
|C4777 (úroveň 4)|'*funkce*': řetězec formátu,*řetězec*, vyžaduje argument typu'*type1*', ale argument variadická *číslo* má typ '*type2*.|
|C4786 (úroveň 3)|'*symbol*': název objektu byl zkrácen na '*číslo*' znaků informace o ladění|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (úroveň 4)|'*bajtů*'bajtů odsazení přidat po konstrukce'*member_name*.|
|C4826 (úroveň 2)|Převod z '*type1*'do'*type2*' je rozšířeny. To může způsobit neočekávané modul runtime chování.|
|C4837 (úroveň 4)|trigraph zjistil: '?? *znak*"nahradit"*znak*.|
|C4841 (úroveň 4)|nestandardní rozšíření používané: označení složené člen použít v offsetof –|
|C4842 (úroveň 4)|výsledek offsetof "–", které se použijí k typu pomocí vícenásobná dědičnost nemusí být konzistentní mezi verzemi kompilátoru|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (úroveň 4)|'_soubor_(*line_number*), kompilátor nemusí vynutit pořadí vyhodnocení zleva doprava v seznamu braced inicializace|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (úroveň 1)|široký řetězcový literál přetypován na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (úroveň 1)|řetězcový literál přetypován na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (úroveň 1)|'*deklarátor*': identifikátor GUID může být přidružen pouze třídu, rozhraní nebo obor názvů|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (úroveň 1)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (úroveň 4)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (úroveň 1)|reinterpret_cast – používá se mezi související třídy: '*class1*'a'*class2*.|
|C4962|'*funkce*': optimalizace na základě profilu zakázán, protože optimalizace způsobily nekonzistenci dat profilu|
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
|C5031 (úroveň 4)|#pragma warning(pop): pravděpodobně neshoda, odebrání stavu s varováním nabídnutých v jiném souboru <sup>14.1</sup>|
|C5032 (úroveň 4)|zjištěna #pragma warning(push) se žádné odpovídající warning(pop) #pragma <sup>14.1</sup>|
|C5034|použití vnitřní '*vnitřní*' způsobí, že funkce *funkce* sestavují jako kód hosta <sup>15.3</sup>|
|C5035|pomocí funkce '*funkce*' způsobí, že funkce *funkce* sestavují jako kód hosta <sup>15.3</sup>|
|C5036 (úroveň 1)|vararg funkce Převod ukazatele, když kompilujete s /hybrid:x86arm64 '*type1*'do'*type2*' <sup>15.3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (úroveň 4)|– datový člen '*člen1*'bude inicializován po – datový člen'*člen2*' <sup>15.3</sup>|
|C5039 (úroveň 4)|'*funkce*': ukazatel nebo odkaz na potenciálně vyvolání funkce předaný funkci extern C v části - EHc. Nedefinované chování může dojít, pokud je tato funkce vyvolá výjimku. <sup>15,5</sup>|
|C5042 (úroveň 3)|'*funkce*': deklarace funkcí v oboru bloku nemůže být zadaný, vložené' ve standardní C++; odebrat, vložené' specifikátor <sup>15,5</sup>|

<sup>14.1</sup> toto upozornění je k dispozici od ve Visual Studiu 2015 Update 1.<br>
<sup>14.3</sup> toto upozornění je k dispozici od Visual Studio 2015 Update 3.<br>
<sup>15.3</sup> toto upozornění je k dispozici od Visual Studio 2017 verze 15.3.<br>
<sup>15,5</sup> toto upozornění je k dispozici od Visual Studio 2017 verze 15,5.<br>
<sup>Oprávnění</sup> toto upozornění je vypnutý, pokud [/ projektovou-](../build/reference/permissive-standards-conformance.md) – možnost kompilátoru nastavena.

## <a name="warnings-off-by-default-in-earlier-versions"></a>Upozornění vypnutí ve výchozím nastavení v dřívějších verzích

Tato upozornění byly vypnout ve výchozím nastavení ve verzích kompilátoru před Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (úroveň 2)|'*převod*': zkrácení z '*type1*'do'*type2*.|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (úroveň 1)|'*proměnná*': zkrácení ukazatel z '*typ*'do'*typu*.|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (úroveň 1)|'*operace*': převod '*type1*'do'*type2*' větší velikosti|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (úroveň 1)|'*operátor*': nulové rozšíření '*type1*'do'*type2*' větší velikosti|

Toto upozornění se vypnout ve výchozím nastavení ve verzích kompilátoru před Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (úroveň 4)|chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.|

## <a name="see-also"></a>Viz také

[warning](../preprocessor/warning.md)
