---
title: Tabulka C++ shody jazyka Microsoft
description: Tabulka aktualizací shody C++ Microsoftu podle verze sady Visual Studio
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 8a5ffb5b3ab4bc80cb200b41752b19d1c958ece6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079361"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabulka C++ shody jazyka Microsoft

Soulad s normami pro kompilátor Microsoft C++ v rámci sady Visual Studio (MSVC) je Nedokončená práce. Tady je souhrn našeho standardu C++ ISO a shody knihoven podle verze sady Visual Studio. Každý kompilátor a název funkce standardní knihovny odkazují na dokument standardní C++ návrh ISO, který popisuje funkci, pokud je k dispozici v době publikování. Ve sloupci **podporováno** se zobrazí verze sady Visual Studio, ve které se poprvé zobrazuje podpora funkce.

Podrobnosti o vylepšeních dodržování MSVC sady Visual Studio 2017 nebo Visual Studio 2019 najdete v tématu [ C++ vylepšení shody v aplikaci Visual Studio](cpp-conformance-improvements.md). Seznam dalších změn najdete v tématu [co je nového pro Visual C++ v aplikaci Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Změny shody v dřívějších verzích najdete v článku o [historii vizuálních C++ změn](../porting/visual-cpp-change-history-2003-2015.md) a [o C++ tom, co je nového 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Aktuální novinky od C++ týmu najdete na [ C++ blogu týmu](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Mezi Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 neexistují žádné binární změny. Další informace najdete v tématu [ C++ binární kompatibilita mezi Visual Studio 2015, 2017 a 2019.](../porting/binary-compat-2015-2017.md)

## <a name="compiler-features"></a>Funkce kompilátoru

|  |  |
|--|--|
| __Základní funkce jazyka c++ 03/11__ | __Podporuje se__ |
| &nbsp;&nbsp;vše ostatní | VS 2015 <sup> [A](#note_A)</sup> |
| &nbsp;&nbsp;vyhledávání názvů ve dvou fázích | VS 2017 15,7 <sup> [B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 výrazu SFINAE](https://wg21.link/N2634) | VS 2017 15.7 |
| preprocesor &nbsp;&nbsp;[N1653 C99](https://wg21.link/N1653) | Částečný <sup> [C](#note_C)</sup> |
| __Základní funkce jazyka c++ 14__ | __Podporuje se__ |
| &nbsp;&nbsp;[N3323 vylepšení pro kontextové převody](https://wg21.link/N3323) | VS 2013 |
| [binární literály](https://wg21.link/N3472) &nbsp;&nbsp;N3472 | VS 2015 |
| &nbsp;&nbsp;[N3638 návratové typy auto a decltype (auto)](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-Captures](https://wg21.link/n3648) | VS 2015 |
| [Obecné lambda](https://wg21.link/n3649) &nbsp;&nbsp;N3649 | VS 2015 |
| &nbsp;&nbsp;[N3760 \[\[zastaralý atribut\]\]](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[N3778 velikosti přidělení](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3781 oddělovače číslic](https://wg21.link/n3781) | VS 2015 |
| [šablony proměnných](https://wg21.link/n3651) &nbsp;&nbsp;N3651 | VS 2015.2 |
| &nbsp;&nbsp;[N3652 rozšířený constexpr](https://wg21.link/n3652) | VS 2017 15,0 |
| &nbsp;&nbsp;[N3653 výchozích inicializátorů členů pro agregace](https://wg21.link/n3653) | VS 2017 15,0 |
| __Základní funkce jazyka c++ 17__ | __Podporuje se__ |
| &nbsp;&nbsp;[N4086 odebrání trigraphs](https://wg21.link/n4086) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 nová pravidla pro automatické pomocí závorek-init-Listes](https://wg21.link/n3922) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4051 TypeName v šabloně šablony – parametry](https://wg21.link/n4051) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4266 atributy pro obory názvů a enumerátory](https://wg21.link/n4266) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267ch znakových literálů U8](https://wg21.link/n4267) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4230 vnořené definice oboru názvů](https://wg21.link/n4230) | VS 2015,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 stručný static_assert](https://wg21.link/n3928) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 generalizované smyčky na základě rozsahu](https://wg21.link/p0184r0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0188R1 \[\[fallthrough\]\] atributu](https://wg21.link/p0188r1) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 odebrání klíčového slova Register](https://wg21.link/p0001r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 odebrání operátoru + + pro bool](https://wg21.link/p0002r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 zachycení * this podle hodnoty](https://wg21.link/p0018r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 pomocí oborů názvů atributů bez opakování](https://wg21.link/p0028r4) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1 \_\_has_include](https://wg21.link/p0061r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 Direct-list-init s pevnými výčty z celých čísel](https://wg21.link/p0138r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 lambda výrazů constexpr](https://wg21.link/p0170r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1 \[\[atribut\]zrušit \]](https://wg21.link/p0189r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0212R1 \[\[maybe_unused](https://wg21.link/p0212r1)\]\] atributu | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| [strukturované vazby](https://wg21.link/p0217r3) &nbsp;&nbsp;P0217R3 | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 constexpr if-statements](https://wg21.link/p0292r2) | VS 2017 15,3 <sup> [D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 příkazů výběru s Inicializátory](https://wg21.link/p0305r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 literály Hexfloat](https://wg21.link/p0245r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268, které povolují více argumentů šablony bez typu](https://wg21.link/n4268) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| N4295 &nbsp;[výrazy skládání](https://wg21.link/n4295) &nbsp; | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 odebrání dynamické-výjimky-specifikace](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 přidávání s výjimkou do systému typů](https://wg21.link/p0012r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 zarovnaný do dynamického přidělování paměti](https://wg21.link/p0035r4) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| [vložené proměnné](https://wg21.link/p0386r2) &nbsp;&nbsp;P0386R2 | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 vyhovující šabloně šablony – parametry pro kompatibilní argumenty](https://wg21.link/p0522r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 odebrání některých prázdných unárních ohybů](https://wg21.link/p0036r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 opravit převody kvalifikací](https://wg21.link/n4261) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 Extended Aggregate – inicializace](https://wg21.link/p0017r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;odvození [argumentu šablony P0091R3 pro šablony tříd](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;P0512R0 vydaných [srážek v argumentu šablony třídy](https://wg21.link/p0512r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 deklarovat parametry šablony bez typu s automatickým](https://wg21.link/p0127r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 garantované kopírování Elizi](https://wg21.link/p0135r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0136R1 přebírající konstruktory](https://wg21.link/p0136r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std:: praní](https://wg21.link/p0137r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| [pořadí vyhodnocení výrazu](https://wg21.link/p0145r3) &nbsp;&nbsp;P0145R3<br/>&nbsp;&nbsp;[P0400R0 pořadí vyhodnocení argumentů funkce](https://wg21.link/p0400r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;[rozšíření balíčků &nbsp;P0195R2 v deklaracích using-Declarations](https://wg21.link/p0195r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 ignorovat nerozpoznané atributy](https://wg21.link/p0283r2) | VS 2015 <sup> [14](#note_14)</sup> |
| __Základní funkce jazyka c++ 17 (sestavy vad)__ | __Podporuje se__ |
| &nbsp;&nbsp;[P0702R1 oprava argumentu šablony třídy pro inicializátor-list ctors](https://wg21.link/p0702r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 požadavků – pravidla hledání strukturovaných vazeb pro body přizpůsobení](https://wg21.link/p0961r1) | VS 2019 16,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 umožňuje strukturované vazby na přístupné členy](https://wg21.link/p0969r0) . | VS 2019 16,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 zjednodušení implicitního zachycení lambda](https://wg21.link/p0588r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[\[zahodit\]\] pro konstruktory](https://wg21.link/p1771r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 Sloučená slova pro P0527R1 a P1155R3, implicitní přesuny](https://wg21.link/p1825r0) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 kontrolu abstraktních typů tříd](https://wg21.link/P0929R2) | Ne |
| &nbsp;&nbsp;[P0962R2 požadavků pravidlo pro hledání bodů přizpůsobení rozsahu pro smyčku](https://wg21.link/p0962r1) | Ne |
| &nbsp;&nbsp;[P0859R0 CWG 1581: když jsou definované členské funkce constexpr](https://wg21.link/p0859r0) | Ne |
| &nbsp;&nbsp;[Velikost pole P1009R2 v New-Expressions](https://wg21.link/P1009R2) | Ne |
| &nbsp;&nbsp;[P1286R2 kontraindikace CWG DR1778](https://wg21.link/P1286R2) | Ne |
| __Základní funkce jazyka c++ 20__ | __Podporuje se__ |
| &nbsp;&nbsp;[P0704R1 oprava ukazatelů const lvalue s odkazem na členy](https://wg21.link/p0704r1) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4, že řetězcové literály char16_t/char32_t mají UTF-16/32](https://wg21.link/P1041R4) . | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 změny aktivního člena sjednocení uvnitř constexpr](https://wg21.link/P1330R0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 s výjimkou \<chrono > Zero (), min (), Max ()](https://wg21.link/P0972R0) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 porovnávací operátor (kosmické prostory), < = >](https://wg21.link/P0515R3) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| [makra testu funkcí](https://wg21.link/P0941R2) &nbsp;&nbsp;P0941R2 | VS 2019 16,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 znemožňují agregace s uživatelsky deklarovanými konstruktory](https://wg21.link/P1008R1) . | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 určenou inicializaci](https://wg21.link/p0329r4) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 ADL a šablony funkcí, které nejsou viditelné](https://wg21.link/P0846R0) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 povolení zachycení lambda \[=, tento\]](https://wg21.link/p0409r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 známá syntaxe šablon pro obecné výrazy lambda](https://wg21.link/p0428r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 výchozí constructible a přiřaditelné lambda bez stavů](https://wg21.link/P0624R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 povolení rozšíření balíčku v lambda init-Capture](https://wg21.link/P0780R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 zastaralá implicitní zachytávání tohoto přes \[=\]](https://wg21.link/P0806R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 vylepšení konzistence pro < = > a jiné operátory porovnání](https://wg21.link/P1120R0) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \<=\>! = =](https://wg21.link/P1185R2) = | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| Koncepty &nbsp;&nbsp;[P0734R0](https://wg21.link/P0734R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 opravy mezer v omezeních funkcí](https://wg21.link/P0857R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 v dnešní době návratový typ – požadavky jsou nedostatečné](https://wg21.link/P1084R2) . | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 podmíněné explicitní](https://wg21.link/P0892R2) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 rozšíření strukturovaných vazeb tak, aby byly větší, jako deklarace proměnných](https://wg21.link/P1091R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 pomocí výčtu](https://wg21.link/P1099R5) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3, když ve skutečnosti používáte \<=>](https://wg21.link/P1186R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[, které P1630R1 využívané místo vyžaduje ladění](https://wg21.link/P1630R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 přidání \_\_VA_OPT\_\_ pro vynechání čárky a odstranění čárky](https://wg21.link/P0306R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 smyčky for-based for – s Inicializátory](https://wg21.link/P0614R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 výchozí Inicializátory členů pro bitové pole](https://wg21.link/P0683R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| [bloky try-catch pro &nbsp;&nbsp;P1002R1 ve funkcích constexpr](https://wg21.link/P1002R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 zastaralá použití operátoru čárky ve výrazech pro podscripting](https://wg21.link/P1161R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[\[zrušit ("zpráva")\]\]](https://wg21.link/P1301R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1, které depoznává import jednotek hlaviček, vyžaduje úplné předzpracování](https://wg21.link/P1703R1) . | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 umožňují výchozí porovnání hodnotou](https://wg21.link/P1946R0) . | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2 se neshoduje s výchozím kopírovacím konstruktorem](https://wg21.link/P0641R2) | Částečné |
| [korutiny](https://wg21.link/P0912R5) &nbsp;&nbsp;P0912R5 | Částečné |
| &nbsp;&nbsp;[P1103R3 moduly](https://wg21.link/P1103R3) | Částečné |
| &nbsp;&nbsp;[P0315R4 povolení výrazů lambda v nehodnocených kontextech](https://wg21.link/P0315R4) | Ne |
| &nbsp;&nbsp;[P0388R4 povolují převody na pole neznámého typu Bound](https://wg21.link/P0388R4) | Ne |
| &nbsp;&nbsp;[P0479R5 \[\[pravděpodobně\]\] a \[\[nepravděpodobné\]\] ch atributů](https://wg21.link/P0479R5) | Ne |
| &nbsp;&nbsp;[P0634R3 dolů pomocí typeName.](https://wg21.link/P0634R3) | Ne |
| &nbsp;&nbsp;[P0692R1 kontrolu přístupu na specializace](https://wg21.link/P0692R1) | Ne |
| &nbsp;&nbsp;[P0722R3 odstranění velikosti pro třídy velikosti proměnných](https://wg21.link/P0722R3) | Ne |
| &nbsp;&nbsp;[typy tříd P0732R2 v parametrech šablony bez typu](https://wg21.link/P0732R2) | Ne |
| &nbsp;&nbsp;[P0735R1 interakce memory_order_consume s sekvencemi vydání](https://wg21.link/P0735R1) | Ne |
| &nbsp;&nbsp;[P0784R7 více kontejnerů constexpr](https://wg21.link/P0784R7) | Ne |
| &nbsp;&nbsp;[P0840R2 \[\[no_unique_address](https://wg21.link/P0840R2)\]\] atributu | Ne |
| &nbsp;&nbsp;[P0848R3 bezpodmínečně triviálních speciálních členských funkcí](https://wg21.link/P0848R3) | Ne |
| &nbsp;&nbsp;[P0960R3 umožňují inicializovat agregace ze seznamu hodnot v závorkách](https://wg21.link/P0960R3) . | Ne |
| &nbsp;&nbsp;[P1064R0, které povolují volání virtuální funkce v konstantních výrazech](https://wg21.link/P1064R0) | Ne |
| &nbsp;&nbsp;[P1073R3 okamžité funkce](https://wg21.link/P1073R3) | Ne |
| &nbsp;&nbsp;[P1094R2 vnořené vložené obory názvů](https://wg21.link/P1094R2) | Ne |
| &nbsp;&nbsp;[P1139R2 problémy související s ISO 10646](https://wg21.link/P1139R2) | Ne |
| &nbsp;&nbsp;[P1141R2 ještě jiný přístup pro deklarace s omezením](https://wg21.link/P1141R2) . | Ne |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | Ne |
| &nbsp;&nbsp;[P1152R4 zastaralá o volatili](https://wg21.link/P1152R4) | Ne |
| &nbsp;&nbsp;[P1236R1 celá čísla se znaménkem jsou dva doplněk](https://wg21.link/P1236R1) . | Ne |
| &nbsp;&nbsp;[P1327R1 povolení dynamic_cast, polymorfní identifikátor TypeId v konstantních výrazech](https://wg21.link/P1327R1) | Ne |
| &nbsp;&nbsp;[P1331R2 povoluje triviální výchozí inicializaci v kontextech constexpr](https://wg21.link/P1331R2) . | Ne |
| &nbsp;&nbsp;[P1353R0 chybějící makra pro test funkcí](https://wg21.link/P1353R0) | Ne |
| zachytávání [strukturovaných vazeb](https://wg21.link/P1381R1) &nbsp;&nbsp;P1381R1 | Ne |
| &nbsp;&nbsp;[P1452R2 na nejednotnou sémantiku u požadavků na vrácení typu](https://wg21.link/P1452R2) | Ne |
| &nbsp;&nbsp;[P1616R1 pomocí neomezeně TTPs s omezenými šablonami](https://wg21.link/P1616R1) | Ne |
| &nbsp;&nbsp;[P1668R1 povolení nehodnoceného vloženého sestavení ve funkcích constexpr](https://wg21.link/P1668R1) | Ne |
| &nbsp;&nbsp;[P1766R1 zmírňující drobné moduly maladies](https://wg21.link/P1766R1) | Ne |
| &nbsp;&nbsp;[omezení předefinování požadavků P1811R0 pro opětovné vyexportování](https://wg21.link/P1811R0) | Ne |
| &nbsp;&nbsp;[P1814R0 CTAD pro šablony aliasů](https://wg21.link/P1814R0) | Ne |
| &nbsp;&nbsp;[P1816R0 CTAD pro agregace](https://wg21.link/P1816R0) | Ne |
| [v modulech se &nbsp;&nbsp;P1874R1 dynamického pořadí inicializace proměnných mimo místní prostředí](https://wg21.link/P1874R1) . | Ne |
| &nbsp;&nbsp;[P1907R1 nekonzistence s parametry šablony bez typu](https://wg21.link/P1907R1) | Ne |
| &nbsp;&nbsp;[P1971R0 se v rámci schůzky v 2019 (Belfast) základní změny pro komentáře NB](https://wg21.link/P1971R0) | Ne |
| &nbsp;&nbsp;[P1972R0 při vytváření ukazatele na funkci US105 kontrolu dodržování omezení pro neexistující šablony](https://wg21.link/P1972R0) . | Ne |
| &nbsp;&nbsp;[P1975R0 oprava slov agregace v závorkách – inicializace](https://wg21.link/P1975R0) | Ne |
| &nbsp;&nbsp;[rozlišení P1979R0 do US086](https://wg21.link/P1979R0) | Ne |
| &nbsp;&nbsp;[P1980R0 CA096: deklarace deklarací pro nezávisle vyžadování klauzule](https://wg21.link/P1980R0) | Ne |

## <a name="standard-library-features"></a>Funkce standardní knihovny

|  |  |
|--|--|
| __C++ 20 – standardní funkce knihovny__ | __Podporuje se__ |
| &nbsp;&nbsp;[P0809R0, které porovnávají neuspořádané kontejnery](https://wg21.link/p0809r0) | VS 2010 <sup> [14](#note_14)</sup> |
| Požadavky na [iterátory Constexpr](https://wg21.link/p0858r0) &nbsp;&nbsp;P0858R0 | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 vyhnout se zbytečnému Decay](https://wg21.link/p0777r1) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1 vytváření create_directory () intuitivní](https://wg21.link/P1164R1) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2 remove_cvref](https://wg21.link/p0550r2) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 starts_with ()/ends_with () pro basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 obsahuje () pro seřazené a neuspořádané asociativní kontejnery](https://wg21.link/p0458r2) . | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 list/forward_list Remove ()/remove_if ()/Unique () Return size_type](https://wg21.link/p0646r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left (), shift_right ()](https://wg21.link/p0769r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6 atom\<float >, atomická\<dvojitá >, atomická\<dlouhá dvojitá >](https://wg21.link/p0020r6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: typ pro znaky a řetězce znakové sady UTF-8](https://wg21.link/P0482R6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 \[\[zrušte\]\] STL, část 1](https://wg21.link/p0600r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address ()](https://wg21.link/p0653r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<verze >](https://wg21.link/p0754r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1, s výjimkou konstruktoru Move std:: Function](https://wg21.link/P0771R1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1 > > (basic_istream &, graf *)](https://wg21.link/P0487R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 pomocí Move () v \<číselné >](https://wg21.link/p0616r0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| [Koncepty knihovny Standard](https://wg21.link/P0898R3) &nbsp;&nbsp;P0898R3 | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 heterogenní vyhledávání pro neuspořádané kontejnery](https://wg21.link/P0919R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 přejmenování konceptů na standard_case](https://wg21.link/P1754R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array z LFTS s aktualizacemi](https://wg21.link/P0325R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 underlying_type](https://wg21.link/P0340R3) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front ()](https://wg21.link/P0356R5) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[třídy výčtu P0439R0 memory_order](https://wg21.link/p0439r0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bitových > funkcí pro otočení a počítání](https://wg21.link/P0553R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit > ispow2 (), ceil2 (), floor2 (), log2p1 ()](https://wg21.link/P0556R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated ()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<čísla > matematické konstanty](https://wg21.link/P0631R8) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 Istream_iterator vyčištění](https://wg21.link/P0738R2) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 Zastaralá is_pod](https://wg21.link/P0767R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 řetězec:: Reserve () se nesmí zmenšovat.](https://wg21.link/P0966R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if (), Erase ()](https://wg21.link/P1209R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 podepsané std:: ssize (), unsigned span:: Size ()](https://wg21.link/P1227R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 úzký kontrakt pro ceil2 ()](https://wg21.link/P1355R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 přemístění endian na \<bit >](https://wg21.link/P1612R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front () by nemělo rozbalit reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 zpřesnění heterogenního vyhledávání pro neuspořádané kontejnery](https://wg21.link/P1690R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 chybějících maker funkcí – Test 2017-2019](https://wg21.link/P1902R1) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | Ne |
| &nbsp;&nbsp;[P0053R7 \<syncstream >](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[osyncstreamy P0753R2](https://wg21.link/p0753r2) | Ne |
| &nbsp;&nbsp;[P0122R7 \<rozpětí >](https://wg21.link/p0122r7) | Ne |
| &nbsp;&nbsp;[P0202R3 constexpr pro \<algoritmus > a Exchange ()](https://wg21.link/p0202r3) | Ne |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator < >](https://wg21.link/P0339R6) | Ne |
| &nbsp;&nbsp;[P0355R7 \<chrono > kalendáře a časová pásma](https://wg21.link/p0355r7) | Ne |
| &nbsp;&nbsp;[P0357R3 podporují neúplné typy v reference_wrapper](https://wg21.link/P0357R3) | Ne |
| &nbsp;&nbsp;[P0415R1 constexpr pro \<složitých > (znovu)](https://wg21.link/p0415r1) | Ne |
| &nbsp;&nbsp;[P0475R1 garantuje Elizi kopírování pro vytváření konstantní](https://wg21.link/P0475R1) | Ne |
| &nbsp;&nbsp;[P0476R2 \<bit > bit_cast](https://wg21.link/P0476R2) | Ne |
| &nbsp;&nbsp;[P0528R3 atomed Compare-and-Exchange s naplňováním](https://wg21.link/P0528R3) výplní | Ne |
| [funkce nástroje &nbsp;&nbsp;P0591R4 pro konstrukci použití](https://wg21.link/P0591R4) | Ne |
| &nbsp;&nbsp;[P0608R3 vylepšení převodu konstruktoru nebo přiřazení variant](https://wg21.link/P0608R3) | Ne |
| &nbsp;&nbsp;[P0619R4 odebrání funkcí zastaralých na jazyk C + +17 v c++ 20](https://wg21.link/P0619R4) | Ne |
| &nbsp;&nbsp;[P0653R2 to_address ()](https://wg21.link/p0653r2) | Ne |
| &nbsp;&nbsp;[P0655R1 navštivte\<R > ()](https://wg21.link/P0655R1) | Ne |
| &nbsp;&nbsp;[P0674R1 make_shared () pro pole](https://wg21.link/p0674r1) | Ne |
| &nbsp;&nbsp;[P0718R2 atom\<shared_ptr\<t > >, atomická\<weak_ptr\<t > >](https://wg21.link/p0718r2) | Ne |
| &nbsp;&nbsp;[Podpora knihoven P0768R1 pro operátor porovnávání prostorů \<=>](https://wg21.link/p0768r1) | Ne |
| &nbsp;&nbsp;[P0811R3 střední bod (), lerp ()](https://wg21.link/P0811R3) | Ne |
| &nbsp;&nbsp;[P0879R0 constexpr pro prohození funkcí](https://wg21.link/P0879R0) | Ne |
| &nbsp;&nbsp;[P0896R4 \<rozsahy\>](https://wg21.link/P0896R4) | Ne |
| [Podpora P0912R5 knihovny pro korutiny v knihovně](https://wg21.link/P0912R5) &nbsp;&nbsp; | Ne |
| &nbsp;&nbsp;[P0920R2 vypočítaná hodnota hash pro vyhledávání](https://wg21.link/P0920R2) | Ne |
| &nbsp;&nbsp;[P0935R0 eradikaci zbytečně explicitních výchozích konstruktorů](https://wg21.link/P0935R0) | Ne |
| &nbsp;&nbsp;[P1001R2 provádění:: unseq](https://wg21.link/P1001R2) | Ne |
| &nbsp;&nbsp;[P1006R1 constexpr pro pointer_traits < t * >::p ointer_to ()](https://wg21.link/P1006R1) | Ne |
| &nbsp;&nbsp;[P1007R3 assume_aligned ()](https://wg21.link/P1007R3) | Ne |
| &nbsp;&nbsp;[vytvoření inteligentního ukazatele P1020R1 s výchozí inicializací](https://wg21.link/P1020R1) | Ne |
| &nbsp;&nbsp;[P1023R0 constexpr pro porovnání std:: Array](https://wg21.link/P1023R0) | Ne |
| &nbsp;&nbsp;[P1032R1 různých constexpr](https://wg21.link/P1032R1) | Ne |
| &nbsp;&nbsp;[P1165R1 konzistentně šířící stavové přidělování v operátoru basic_string + ()](https://wg21.link/P1165R1) | Ne |
| &nbsp;&nbsp;[P1285R0 vylepšení požadavků na úplnost u vlastností typu](https://wg21.link/P1285R0) | Ne |
| __Funkce standardní knihovny c++ 17__ | __Podporuje se__ |
| &nbsp;&nbsp;[LWG 2221 naformátovaný výstupní operátor pro nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16.1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 bezpečné převody v unique_ptr\<t [] >](https://wg21.link/n4089) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 Invoke ()](https://wg21.link/n4169) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 odebrání auto_ptr, random_shuffle () a starých \<funkčních > věcí](https://wg21.link/n4190) | VS 2015 <sup> [Zbýv](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 s výjimkou vyčištění](https://wg21.link/n4258) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions ()](https://wg21.link/n4259) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 triviálním kopírováním reference_wrapper](https://wg21.link/n4277) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign ()/try_emplace () pro mapu/unordered_map](https://wg21.link/n4279) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 Size (), Empty (), data ()](https://wg21.link/n4280) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 přesně omezení Unique_ptr přiřazení](https://wg21.link/n4366) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 vylepšení páru a řazené kolekce členů](https://wg21.link/n4387) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (nedlouhod)](https://wg21.link/n4508) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510, které podporují neúplné typy v Vector/list/forward_list](https://wg21.link/n4510) | VS 2013 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 knihovny: základní informace o knihovně \<algoritmus > Sample ()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15,0 |
| &nbsp;&nbsp;[základní knihovny N4562: \<libovolné >](https://wg21.link/n4562#any) | VS 2017 15,0 |
| &nbsp;&nbsp;[základní knihovny N4562: \<memory_resource >](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 odstranění polymorphic_allocatorho přiřazení](https://wg21.link/p0337r0) | VS 2017 15,6 |
| &nbsp;&nbsp;[základní knihovny N4562: \<volitelné >](https://wg21.link/n4562#optional) | VS 2017 15,0 |
| &nbsp;&nbsp;[základní knihovny N4562: \<string_view >](https://wg21.link/n4562#string.view) | VS 2017 15,0 |
| &nbsp;&nbsp;[N4562 knihovny: základní informace o knihovně: \<tuple > Apply ()](https://wg21.link/n4562#tuple) | VS 2017 15,0 |
| &nbsp;&nbsp;[základy knihovny N4562: hledání Boyer-Moore ()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 opravy návratových typů hledání](https://wg21.link/p0253r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 odebrání dynamických specifikací výjimek](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 odebrání zastaralých aliasů iostreams](https://wg21.link/p0004r1) | VS 2015,2 <sup> [Zbýv](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn ()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 opravy pro not_fn ()](https://wg21.link/p0358r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[šablony proměnných P0006R0 pro typové vlastnosti (is_same_v atd.)](https://wg21.link/p0006r0) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const ()](https://wg21.link/p0007r1) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0013R1 vlastností typu logického operátoru (spojení atd.)](https://wg21.link/p0013r1) | VS 2015,2 <sup> [14](#note_14)</sup> |
| [paralelní algoritmy](https://wg21.link/p0024r2) &nbsp;&nbsp;P0024R2<br/>&nbsp;&nbsp;[P0336R1 přejmenování zásad paralelního spouštění](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 paralelní algoritmy by se měly ukončit () pro výjimky](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 sjednocení \<číselné > paralelní algoritmy](https://wg21.link/p0452r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0025R1 svorka ()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot – (x, y, z)](https://wg21.link/p0030r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0031R0 constexpr pro \<pole > (znovu) a \<iterátoru >](https://wg21.link/p0031r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 homogenní rozhraní pro variantu/libovolnou/volitelnou](https://wg21.link/p0032r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0033R1 přeformulování enable_shared_from_this](https://wg21.link/p0033r1) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 rozšíření nástrojů pro správu paměti](https://wg21.link/p0040r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| [Standardní knihovna &nbsp;&nbsp;P0063R3 C11](https://wg21.link/p0063r3) | VS 2015 <sup> [C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[základní převody řetězců P0067R5](https://wg21.link/p0067r5) | VS 2019 16,4 <sup> [charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0083R3 spojování map a sad](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 Objasnění insert_return_type](https://wg21.link/p0508r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| [návratový typ &nbsp;&nbsp;P0084R2 emplace](https://wg21.link/p0084r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0088R3 \<variant >](https://wg21.link/p0088r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0092R1 \<chrono > Floor (); ceil – (); Round (); ABS ()](https://wg21.link/p0092r1) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 Atomic:: is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size atd.](https://wg21.link/p0154r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 variadické lock_guard](https://wg21.link/p0156r0) | VS 2015,2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 přejmenování\_ochrany variadické Lock na vymezený\_zámek](https://wg21.link/p0156r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr:: weak_type](https://wg21.link/p0163r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0174R2 zastaralá část knihovny starší](https://wg21.link/p0174r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple ()](https://wg21.link/p0209r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0218R1 \<systému souborů >](https://wg21.link/p0218r1)<br/>[relativní cesty k systému souborů](https://wg21.link/p0219r1) &nbsp;&nbsp;P0219R1<br/>&nbsp;&nbsp;[ukládání položek adresáře P0317R1 do mezipaměti pro systém souborů](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 podporující String_view v cestách systému souborů](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2, které podporují systémy souborů jiných než POSIX](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 překládání komentářů NB pro systém souborů](https://wg21.link/p0492r2) | VS 2017 15,7 <sup> [E](#note_E)</sup> |
| &nbsp;&nbsp;[základy knihovny P0220R1 v1](https://wg21.link/p0220r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0226R1 matematických speciálních funkcí](https://wg21.link/p0226r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0254R2 integrující String_view a std:: String](https://wg21.link/p0254r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15,3 <sup> [G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 bez const basic_string::d ATA ()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 GCD (), LCM ()](https://wg21.link/p0295r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std:: Byte](https://wg21.link/p0298r3) | VS 2017 15,3 <sup> [17](#note_17),&nbsp;[Byte](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 odebrání podpory přidělování v std:: Function](https://wg21.link/p0302r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 provádění volitelného většího rovnosti](https://wg21.link/p0307r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0393R3, že je variace větší](https://wg21.link/p0393r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0403R1 UDL pro \<string_view > ("Meow" sv atd.)](https://wg21.link/p0403r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<t [] >, shared_ptr\<t [N] >](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 opravy Shared_ptr pro pole](https://wg21.link/p0497r0) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 atom compare_exchange Memory_order požadavky](https://wg21.link/p0418r2) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr pro char_traits](https://wg21.link/p0426r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0433R2 integrování odpočtů šablon pro šablony tříd do standardní knihovny](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 zvyšuje integraci odvození argumentu šablony třídy do standardní knihovny](https://wg21.link/p0739r0) . | VS 2017 15.7 |
| &nbsp;&nbsp;[P0435R1 přetažení common_type](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1, jak se vylepšit společný\_typ a doba trvání](https://wg21.link/p0548r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 přenavštěvování in_place_t/in_place_type_t\<t >/in_place_index_t\<I](https://wg21.link/p0504r0) > | VS 2017 15,0 |
| &nbsp;&nbsp;[P0505R0 constexpr pro \<chrono > (znovu)](https://wg21.link/p0505r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 odmítnutí variant Nothing, polí, odkazů a neúplných typů](https://wg21.link/p0510r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[hodnota hash poškození P0513R0](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 s výjimkou hodnoty hash](https://wg21.link/p0599r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 označení Shared_future kopírování jako s výjimkou](https://wg21.link/p0516r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 vytváření Future_error od future_errc](https://wg21.link/p0517r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 Zastaralá shared_ptr:: Unique ()](https://wg21.link/p0521r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 řešení atomických\<t > s názvem nekonzistence základní třídy](https://wg21.link/p0558r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std:: is_constant_evaluated ()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 šíření kopírování/přesunutí v variantě (volitelné](https://wg21.link/P0602R4) ) | VS 2017 15,3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 změna je\_vyvolat/výsledek\_pro vyvolání\_výsledek,\_nevyvolatelný, je\_nevyvolatelný\_](https://wg21.link/p0604r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[vložené proměnné P0607R0 pro standardní knihovnu](https://wg21.link/p0607r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[p0618r0; Zastaralá \<codecvt >](https://wg21.link/p0618r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 opravy základních převodů řetězců](https://wg21.link/P0682R1) | VS 2015 15,7 <sup> [17](#note_17)</sup> |
| __Funkce standardní knihovny c++ 14__ | __Podporuje se__ |
| &nbsp;&nbsp;[N3462 result_of](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr pro \<složitá >](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr pro \<chrono >](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr pro \<pole >](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr pro \<initializer_list >, \<řazené kolekce členů > \<utility >](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant:: operator () ()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 UDL For \<chrono >, \<string > (1729ms, "Meow" s atd.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644y dopředné iterátory s hodnotou null](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 v uvozovkách ()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 heterogenní asociativní vyhledávání](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (časované)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 Exchange ()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 opravy členských funkcí constexpr bez const](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670 získat\<t > ()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 se rovná (), is_permutation (), neshoda ()](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[N3778 velikosti přidělení](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 UDL pro \<složitých > (3.14 i atd.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr pro \<funkční >](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 přejmenování shared_mutex (časované) na shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 minimální požadavky na prvky kontejneru](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 transparentní operátor funktory (méně\<> atd.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[šablony aliasů N3655 pro \<type_traits > (decay_t atd.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique ()](https://wg21.link/n3656) | VS 2013 |

Skupina popsaných dokumentů indikuje standardní funkci spolu s jedním nebo více schválenými vylepšeními nebo rozšířeními. Tyto funkce jsou implementovány společně.

### <a name="supported-values"></a>Podporované hodnoty

__Žádné__ prostředky, které ještě nebyly implementovány. \
__Částečný__ znamená, že implementace je nekompletní. Další informace najdete v části poznámky. \
__VS 2010__ označuje funkce, které jsou podporovány v sadě Visual Studio 2010. \
__VS 2013__ označuje funkce, které jsou podporované v Visual Studio 2013. \
__VS 2015__ označuje funkce, které jsou podporovány v sadě Visual Studio 2015 (RTW). \
__Vs 2015,2__ a __vs 2015,3__ označují funkce podporované v sadě Visual Studio 2015 Update 2 a Visual Studio 2015 Update 3 v uvedeném pořadí. \
__VS 2017 15,0__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,0 (RTW). \
__VS 2017 15,3__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,3. \
__VS 2017 15,5__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,5. \
__VS 2017 15,7__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,7. \
__VS 2019 16,0__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,0 (RTW). \
__VS 2019 16,1__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,1. \
__VS 2019 16,2__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,2. \
__VS 2019 16,3__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,3. \
__VS 2019 16,4__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,4. \
__VS 2019 16,5__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,5.

### <a name="notes"></a>Poznámky:

<a name="note_A"></a>__A__ v [/std: režim c++ 14](../build/reference/std-specify-language-standard-version.md) , specifikace dynamických výjimek zůstávají neimplementovány a `throw()` jsou stále považovány za synonymum pro `__declspec(nothrow)`. V jazyce C++ 17 specifikace dynamických výjimek byly většinou odebrány pomocí P0003R5, přičemž jedna vestige: `throw()` je zastaralá a musí se chovat jako synonymum pro `noexcept`. V [/std: režim c++ 17](../build/reference/std-specify-language-standard-version.md) , MSVC teď vyhovuje standardu tím, že `throw()` stejné chování jako `noexcept`, což je vynucování prostřednictvím ukončení.

Možnost kompilátoru [/Zc: noexceptTypes](../build/reference/zc-noexcepttypes.md) žádá o staré chování `__declspec(nothrow)`. Je možné, že se `throw()` v C++ 20 odeberou. Pro usnadnění migrace kódu v reakci na tyto změny v rámci Standard a naší implementace byly do/STD přidány nové výstrahy kompilátoru pro chyby specifikace výjimky [: c++ 17](../build/reference/std-specify-language-standard-version.md) a [/Permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ podporuje se v režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) ve Visual Studiu 2017 verze 15,7. Další informace najdete v článku [Podpora vyhledávání názvů se dvěma fázemi se dodává do MSVC](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a>__C__ Podpora kompilátoru pro pravidla preprocesoru C99 je v aplikaci Visual Studio 2017 nekompletní. Předáváme preprocesor a začali dodávat tyto změny ve Visual Studiu 2017 verze 15,8 pomocí přepínače kompilátoru [/Experimental: preprocesor](../build/reference/experimental-preprocessor.md) .

<a name="note_D"></a>__D__ podporován v rámci [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) s upozorněním Suppressible, [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a>__Jedná se__ o zcela novou implementaci, která není kompatibilní s předchozí `std::experimental` verzí, kterou vyžaduje podpora symlink, opravy chyb a změny v chování vyžadovaném standardem. V současné době, včetně \<systému souborů > poskytuje nové `std::filesystem` a předchozí `std::experimental::filesystem`, včetně \<experimentální/FileSystem > poskytuje jenom starou experimentální implementaci. Experimentální implementace bude ODEBRÁNA v další vydaných vydáních knihovny ABI.

<a name="note_G"></a>__G__ podporované vnitřním kompilátorem

<a name="note_14"></a>__14__ tyto funkce c++ 17/20 jsou vždycky povolené, i když je [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) (výchozí). Důvodem je, že funkce byla implementována před zavedením možností **/STD** nebo vzhledem k tomu, že podmíněná implementace byla nepřáníně složitá.

<a name="note_17"></a>__17__ tyto funkce jsou povolené pomocí možnosti kompilátoru [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (nebo [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a>__20__ těchto funkcí je povoleno pomocí možnosti [nejnovější kompilátor/std: c + +](../build/reference/std-specify-language-standard-version.md) . Po dokončení implementace C++ 20 bude přidána nová možnost kompilátoru **/std: c++ 20** , v rámci které budou tyto funkce také k dispozici.

<a name="note_byte"></a>__bajt__ `std::byte` je povolený pomocí [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (nebo [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md)), ale protože může v některých případech kolidovat s hlavičkou Windows SDK, obsahuje podrobné makro pro výslovný odkaz. Můžete ji zakázat definováním `_HAS_STD_BYTE` jako `0`.

<a name="note_C11"></a>__C11__ Univerzální CRT implementoval součásti standardní knihovny C11, které jsou požadovány v C++ 17, s výjimkou C99 `strftime()` alternativní specifikátory převodu, C11 `fopen()` exkluzivní režim a C11 `aligned_alloc()`. Druhý z těchto důvodů není pravděpodobně implementován, protože C11 určený `aligned_alloc()` způsobem, který je nekompatibilní s implementací `free()`od společnosti Microsoft: `free()` konkrétně musí být schopna zvládnout vysoce zarovnané přidělení.

<a name="note_rem"></a>__rem__ Funkce odebrané v případě, že je zadána možnost kompilátoru [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (nebo [/std: c + + + poslední](../build/reference/std-specify-language-standard-version.md)). Tyto funkce se dají znovu povolit, aby se usnadnil přechod do novějších jazykových režimů pomocí těchto maker: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`a `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ `from_chars()` a `to_chars()` jsou k dispozici pro celá čísla. Časová osa pro `from_chars()` s plovoucí desetinnou čárkou a plovoucí desetinnou čárkou `to_chars()` je následující:
- VS 2017 15,7: celé číslo `from_chars()` a `to_chars()`.
- VS 2017 15,8: `from_chars()`s plovoucí desetinnou čárkou.
- VS 2017 15,9: `to_chars()` přetížení s plovoucí desetinnou čárkou pro nejkratší desetinné číslo.
- VS 2019 16,0: `to_chars()` přetížení s plovoucí desetinnou čárkou pro nejkratší hex a přesnost Hex.
- VS 2019 16,2: `to_chars()` přetížení s plovoucí desetinnou čárkou pro pevnou přesnost a vědeckou přesnost.
- VS 2019 16,4: `to_chars()` přetížení s plovoucí desetinnou čárkou pro metodu Precision General.

<a name ="note_parallel"></a>__paralelní__ Knihovna paralelních algoritmů c++ 17 je dokončená. Hodnota dokončit neznamená, že každý algoritmus je v každém případě paralelně paralelní. Nejdůležitější algoritmy byly paralelní a signatury zásad spouštění jsou k dispozici i v případě, že se algoritmy neparalelismuují. Hlavní interní hlavička naší implementace, yvals_core. h, obsahuje následující "paralelní poznámky k algoritmům": C++ umožňuje implementaci paralelních algoritmů jako volání na sériové algoritmy. Tato implementace parallelizes několik běžných volání algoritmů, ale ne všechny.

Následující algoritmy jsou paralelní:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until``mismatch``none_of``partition``reduce`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce``remove``remove_if``replace``replace_if``search``search_n`

Následující nejsou předposílány v předsoučasném paralelismu:

- Bez znatelného zvýšení výkonu u cílového hardwaru; všechny algoritmy, které pouze kopírují nebo permute – prvky bez větví, jsou obvykle omezeny šířkou pásma paměti:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Nejasnost nad požadavky uživatelů na paralelismus existuje; nejspíš v výše uvedené kategorii přesto:
  - `generate`, `generate_n`
- Efektivní paralelismus podezřelý z neproveditelnosti:
  - `partial_sort`, `partial_sort_copy`
- Ještě nevyhodnoceno; paralelismus se dá implementovat v budoucí verzi a má podezření, že je to užitečné:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Viz také

Referenční informace o jazyce\ [ C++ ](../cpp/cpp-language-reference.md)
[ C++\ standardní knihovny](../standard-library/cpp-standard-library-reference.md)
[vylepšení shody v aplikaci Visual Studio\ C++ ](cpp-conformance-improvements.md)
[Novinky pro vizuál C++ v aplikaci Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historie C++ vizuálních změn 2003 až 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Visual C++ What 's New 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[C++Blog týmu](https://devblogs.microsoft.com/cppblog/)
