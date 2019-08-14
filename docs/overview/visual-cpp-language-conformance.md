---
title: Tabulka C++ shody jazyka Microsoft
ms.date: 08/12/2019
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 15226d41991d5a09d104d2edbfb3dbf2f7432b65
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980530"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabulka C++ shody jazyka Microsoft

V tomto tématu najdete souhrn standardů ISO 03, C++ 11, C++ 14, C++ 17 a C++ 20 v souladu s funkcemi kompilátoru a standardními funkcemi knihovny pro kompilátor Microsoft C++ v rámci sady Visual Studio 2019 a starších verzí. Každý kompilátor a název funkce standardní knihovny odkazují na dokument standardní C++ návrh ISO, který popisuje funkci, pokud je k dispozici v době publikování. Ve sloupci podporováno se zobrazí verze sady Visual Studio, ve které se poprvé zobrazuje podpora funkce.

Podrobnosti o vylepšeních shody a dalších změnách v sadě Visual Studio 2017 nebo Visual Studio 2019 získáte tak, že nastavíte selektor verzí v levém horním rohu této stránky, potom v tématu [ C++ vylepšení shody v sadě Visual Studio](cpp-conformance-improvements.md) a [novinky pro vizuál C++v aplikaci Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Změny shody v dřívějších verzích najdete v článku o [historii vizuálních C++ změn](../porting/visual-cpp-change-history-2003-2015.md) a [o C++ tom, co je nového 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Aktuální novinky od C++ týmu najdete na [ C++ blogu týmu](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Mezi Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 neexistují žádné binární změny.

## <a name="compiler-features"></a>Funkce kompilátoru

| | |
|----|---|
|__Základní funkce jazyka c++ 03/11__|__Podporuje se__|
|&nbsp;&nbsp;Všechno ostatní|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Dvoufázové vyhledávání názvů|VS 2017 15,7 <sup> [B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 výrazu SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[Preprocesor N1653 C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Částečný <sup> [C](#note_C)</sup>|
|__Základní funkce jazyka c++ 14__|__Podporuje se__|
|&nbsp;&nbsp;[N3323 vylepšení pro kontextové převody](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[Binární literály N3472](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 auto a decltype (auto) návratové typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init – zachycení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[Obecné výrazy lambda N3649](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 \[ \[zastaralá\] atributu\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[Dealokace N3778 velikosti](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 oddělovače číslic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[Šablony proměnných N3651](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 rozšířený constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017 15,0|
|&nbsp;&nbsp;[N3653 výchozí Inicializátory členů pro agregace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017 15,0|
|__Základní funkce jazyka c++ 17__|__Podporuje se__|
|&nbsp;&nbsp;[N4086 odebrání trigraphs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 nová pravidla pro automatické pomocí závorek-init-Listes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 TypeName v šabloně šablony – parametry](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 atributy pro obory názvů a enumerátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 U8 – znakové literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Definice vnořeného oboru názvů N4230](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 stručný static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 15,0 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 generalizované smyčky na základě rozsahu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 15,0 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 \[ –\[atribut fallthrough\] \]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 15,0 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 odebrání klíčového slova Register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 odebrání operátoru + + pro bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 zachycení * this podle hodnoty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 pomocí oborů názvů atributů bez opakování](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 \_\_has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 Direct-list-init pevných výčtů z celých čísel](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Výrazy lambda P0170R1 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 \[ zrušit\[atribut\] \]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 \[ –\[atribut maybe_unused\] \]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Strukturované vazby P0217R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 constexpr if-statements](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[P0305R1 výběrové příkazy s Inicializátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Hexfloat literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 povolit více argumentů šablony bez typu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Výrazy skládání N4295](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 odebrání dynamické-výjimky – specifikace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 přidávání s výjimkou do systému typů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Přidělení dynamické paměti zarovnaných k P0035R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Vložené proměnné P0386R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 vyhovující šabloně šablony – parametry pro kompatibilní argumenty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 odebrání některých prázdných unárních skládání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 opravit převody kvalifikací](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Inicializace rozšířené agregace P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Odvození argumentu šablony P0091R3 pro šablony tříd](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br/>&nbsp;&nbsp;[Problémy s odpočty argumentu šablony třídy P0512R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 deklarovat parametry šablony bez typu s automatickým](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 garantované kopie Elizi](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15,6|
|&nbsp;&nbsp;[P0136R1 přebírání dědění konstruktorů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std:: praní](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Pořadí vyhodnocení výrazu pro P0145R3 rafinace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br/>&nbsp;&nbsp;[P0400R0 pořadí vyhodnocení argumentů funkce](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Rozšíření P0195R2 Pack v deklaracích using-Declarations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 ignoruje nerozpoznané atributy.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|
|__Základní funkce jazyka c++ 17 (sestavy vad)__|__Podporuje se__|
|&nbsp;&nbsp;[P0702R1 oprava argumentu šablony třídy pro inicializátor – seznam ctors](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0961R1 požadavků – hledání pravidel pro body přizpůsobení strukturovaných vazeb](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|VS 2019 16.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0969R0 umožňuje strukturované vazby na přístupné členy.](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|VS 2019 16.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 zjednodušení implicitního zachycení lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Ne|
|&nbsp;&nbsp;[P0962R2 požadavků pravidla pro hledání bodů přizpůsobení rozsahu pro smyčku](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Ne|
|&nbsp;&nbsp;[P0929R2 kontroly abstraktních typů tříd](https://wg21.link/P0929R2)|Ne|
|&nbsp;&nbsp;[Srážka velikosti pole P1009R2 v New-Expressions](https://wg21.link/P1009R2)|Ne|
|&nbsp;&nbsp;[P1286R2 kontraindikace CWG DR1778](https://wg21.link/P1286R2)|Ne|
|__Základní funkce jazyka c++ 20__|__Podporuje se__|
|&nbsp;&nbsp;[P0704R1 oprava ukazatelů const lvalue s odkazem na členy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1041R4 vytvořit řetězcové literály char16_t/char32_t pro UTF-16/32](https://wg21.link/P1041R4)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1330R0 změny aktivního člena sjednocení v constexpr](https://wg21.link/P1330R0)|VS 2017 15,0 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0972R0 s výjimkou \<Chrono > Zero (), min (), Max ()](https://wg21.link/P0972R0)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0329R4 určená inicializace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0409R2 povolení zachycení \[výrazu lambda =\]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0515R3 operátor porovnání se třemi způsoby (prostor) < = >](https://wg21.link/P0515R3)|VS 2019 16,0 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[Funkce P0941R2 – testovací makra](https://wg21.link/P0941R2)|VS 2019 16.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1008R1 znemožňuje agregace s uživatelsky deklarovanými konstruktory.](https://wg21.link/P1008R1)|VS 2019 16,0 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0846R0 ADL a šablony funkcí, které nejsou viditelné](https://wg21.link/P0846R0)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0641R2 const neshodující s výchozím kopírovacím konstruktorem](https://wg21.link/P0641R2)|Částečné|
|&nbsp;&nbsp;[P0306R4 přidání \_ \_VA_OPT\_ provynecháníčárkyaodstraněníčárky\_](https://wg21.link/P0306R4)|Ne|
|&nbsp;&nbsp;[P0315R4 povolení výrazů lambda v nehodnocených kontextech](https://wg21.link/P0315R4)|Ne|
|&nbsp;&nbsp;[P0428R2 známá syntaxe šablon pro obecné výrazy lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Ne|
|&nbsp;&nbsp;[P0479R5 \[ pravděpodobné\[ a\[nepravděpodobnéatributy\] \] \] \[\]](https://wg21.link/P0479R5)|Ne|
|&nbsp;&nbsp;[P0542R5 smlouvy](https://wg21.link/P0542R5)|Ne|
|&nbsp;&nbsp;[P0614R1 smyčky for na základě rozsahu s Inicializátory](https://wg21.link/P0614R1)|Ne|
|&nbsp;&nbsp;[P0624R2 výchozí constructible a přiřaditelné lambda bez stavů](https://wg21.link/P0624R2)|Ne|
|&nbsp;&nbsp;[P0634R3 dolů pomocí typeName.](https://wg21.link/P0634R3)|Ne|
|&nbsp;&nbsp;[P0683R1 výchozí Inicializátory členů pro bitové pole](https://wg21.link/P0683R1)|Ne|
|&nbsp;&nbsp;[Kontrola přístupu P0692R1 požadavků na specializacích](https://wg21.link/P0692R1)|Ne|
|&nbsp;&nbsp;[Odstranit P0722R3 efektivní velikosti pro třídy velikosti proměnných](https://wg21.link/P0722R3)|Ne|
|&nbsp;&nbsp;[Typy tříd P0732R2 v parametrech šablony bez typu](https://wg21.link/P0732R2)|Ne|
|&nbsp;&nbsp;[P0734R0 Concepts](https://wg21.link/P0734R0)|Ne|
|&nbsp;&nbsp;[P0780R2 povoluje rozšíření balíčku v lambda init-Capture](https://wg21.link/P0780R2)|Ne|
|&nbsp;&nbsp;[P0806R2 vyřazení implicitního zachycení přes\[=\]](https://wg21.link/P0806R2)|Ne|
|&nbsp;&nbsp;[P0840R2 \[ –\[atribut no_unique_address\] \]](https://wg21.link/P0840R2)|Ne|
|&nbsp;&nbsp;[P0857R0 opravuje v omezeních nedostatky funkcí](https://wg21.link/P0857R0)|Ne|
|&nbsp;&nbsp;[P0892R2 podmíněný explicitní](https://wg21.link/P0892R2)|Ne|
|&nbsp;&nbsp;[P0912R5 korutiny](https://wg21.link/P0912R5)|Ne|
|&nbsp;&nbsp;[P0960R3 umožňuje inicializovat agregace ze seznamu hodnot v závorkách.](https://wg21.link/P0960R3)|Ne|
|&nbsp;&nbsp;[Bloky try-catch P1002R1 ve funkcích constexpr](https://wg21.link/P1002R1)|Ne|
|&nbsp;&nbsp;[P1064R0 povolení volání virtuální funkce v konstantních výrazech](https://wg21.link/P1064R0)|Ne|
|&nbsp;&nbsp;[Okamžité funkce P1073R3](https://wg21.link/P1073R3)|Ne|
|&nbsp;&nbsp;[P1084R2 dnešní požadavky na návratový typ jsou nedostatečné.](https://wg21.link/P1084R2)|Ne|
|&nbsp;&nbsp;[P1091R3 rozšiřovat strukturované vazby tak, aby byly větší, jako deklarace proměnných](https://wg21.link/P1091R3)|Ne|
|&nbsp;&nbsp;[Vnořené vložené obory názvů P1094R2](https://wg21.link/P1094R2)|Ne|
|&nbsp;&nbsp;[Moduly P1103R3](https://wg21.link/P1103R3)|Ne|
|&nbsp;&nbsp;[P1120R0 vylepšení konzistence pro < = > a další operátory porovnání](https://wg21.link/P1120R0)|Ne|
|&nbsp;&nbsp;[Problémy s formulací adres P1139R2 souvisejících s ISO 10646](https://wg21.link/P1139R2)|Ne|
|&nbsp;&nbsp;[P1141R2 ještě jiný přístup pro deklarace s omezením](https://wg21.link/P1141R2)|Ne|
|&nbsp;&nbsp;[P1185R2 \< !==\> = =](https://wg21.link/P1185R2)|Ne|
|&nbsp;&nbsp;[P1236R1 celá čísla se znaménkem se dvěma doplňují](https://wg21.link/P1236R1)|Ne|
|&nbsp;&nbsp;[Řízení přístupu P1289R1 v podmínkách smluv](https://wg21.link/P1289R1)|Ne|
|&nbsp;&nbsp;[P1323R2 kontraktu následné podmínky a návratového typu](https://wg21.link/P1323R2)|Ne|
|&nbsp;&nbsp;[P1327R1 povolování dynamic_cast, polymorfní identifikátor TypeId v konstantních výrazech](https://wg21.link/P1327R1)|Ne|
|&nbsp;&nbsp;[P1353R0 chybějících maker funkcí a testů](https://wg21.link/P1353R0)|Ne|
|&nbsp;&nbsp;[P1381R1 zachycení strukturovaných vazeb na odkaz](https://wg21.link/P1381R1)|Ne|

## <a name="standard-library-features"></a>Funkce standardní knihovny

| | |
|---|---|
|__C++ 20 – standardní funkce knihovny__|__Podporuje se__|
|&nbsp;&nbsp;[P0809R0y, které porovnávají neuspořádané kontejnery](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Požadavky na iterátory constexpr P0858R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0777R1 vyhnout se zbytečnému Decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|VS 2019 16,0 <sup> [20](#note_20)</sup>|
|&nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0318r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0457R2 starts_with ()/ends_with () pro basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0458R2 obsahuje () pro seřazené a neuspořádané asociativní kontejnery.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0458r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0646R1 list/forward_list remove()/remove_if()/unique() Return size_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0646r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0769R2 shift_left(), shift_right()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0769r2.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8)|Ne|
|&nbsp;&nbsp;[P0020R6 atomic\<float >, atomická\<dvojitá >\<, atomická dlouhá dvojitá >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Ne|
|&nbsp;&nbsp;[P0053R7 \<syncstream >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br/>&nbsp;&nbsp;[P0753R2 osyncstream – manipulace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Ne|
|&nbsp;&nbsp;[P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Ne|
|&nbsp;&nbsp;[P0202R3 constexpr pro \<algoritmus > a Exchange ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Ne|
|&nbsp;&nbsp;[P0339R6 polymorphic_allocator < >](https://wg21.link/P0339R6)|Ne|
|&nbsp;&nbsp;[P0340R3 SFINAE-Friendly underlying_type](https://wg21.link/P0340R3)|Ne|
|&nbsp;&nbsp;[P0355R7 \<Chrono > kalendáře a časová pásma](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Ne|
|&nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5)|Ne|
|&nbsp;&nbsp;[P0357R3 podporující neúplné typy v reference_wrapper](https://wg21.link/P0357R3)|Ne|
|&nbsp;&nbsp;[P0415R1 constexpr pro \<složité > (znovu)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Ne|
|&nbsp;&nbsp;[P0439R0 enum class memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Ne|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Ne|
|&nbsp;&nbsp;[P0475R1 garantované kopírování Elizi pro konstrukci konstantní](https://wg21.link/P0475R1)|Ne|
|&nbsp;&nbsp;[P0476R2 <bit> bit_cast](https://wg21.link/P0476R2)|Ne|
|&nbsp;&nbsp;[P0482R6 char8_t: Typ pro znaky a řetězce v kódování UTF-8](https://wg21.link/P0482R6)|Ne|
|&nbsp;&nbsp;[P0487R1 – operátor oprav > > (& basic_istream, graf *)](https://wg21.link/P0487R1)|Ne|
|&nbsp;&nbsp;[P0528R3 atomické porovnání a-výměna s naplňováním výplní](https://wg21.link/P0528R3)|Ne|
|&nbsp;&nbsp;[P0556R3 <bit> ispow2 (), ceil2 (), floor2 (), log2p1 ()](https://wg21.link/P0556R3)|Ne|
|&nbsp;&nbsp;[Funkce P0591R4 nástrojů pro vytváření přidělování pro použití](https://wg21.link/P0591R4)|Ne|
|&nbsp;&nbsp;[P0600R1 \[ \[zrušitpro\]STL ,část1\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Ne|
|&nbsp;&nbsp;[P0608R3 zlepšuje převod konstruktoru nebo přiřazení variant](https://wg21.link/P0608R3)|Ne|
|&nbsp;&nbsp;[P0616R0 pomocí Move () v \<číselném >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Ne|
|&nbsp;&nbsp;[P0619R4 odebrání funkcí založených na jazyce C + +17 – nepoužívané funkce v C++ 20](https://wg21.link/P0619R4)|Ne|
|&nbsp;&nbsp;[P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Ne|
|&nbsp;&nbsp;[P0655R1 navštívit<R>()](https://wg21.link/P0655R1)|Ne|
|&nbsp;&nbsp;[P0674R1 make_shared () pro pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Ne|
|&nbsp;&nbsp;[P0718R2 Atom\<shared_ptr\<t > >, atomovou\<weak_ptr\<t > >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Ne|
|&nbsp;&nbsp;[Vyčištění P0738R2 istream_iterator](https://wg21.link/P0738R2)|Ne|
|&nbsp;&nbsp;[> \<Verze P0754R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Ne|
|&nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1)|Ne|
|&nbsp;&nbsp;[P0767R1 zastaralá is_pod](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Ne|
|&nbsp;&nbsp;[Podpora knihovny P0768R1 pro operátor porovnávání prostorů\<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Ne|
|&nbsp;&nbsp;[P0771R1 s výjimkou konstruktoru Move std:: Function](https://wg21.link/P0771R1)|Ne|
|&nbsp;&nbsp;[P0811R3 midpoint(), lerp()](https://wg21.link/P0811R3)|Ne|
|&nbsp;&nbsp;[P0879R0 constexpr pro prohození funkcí](https://wg21.link/P0879R0)|Ne|
|&nbsp;&nbsp;[P0896R4 \<rozsahy\>](https://wg21.link/P0896R4)|Ne|
|&nbsp;&nbsp;[Koncepty standardní knihovny P0898R3](https://wg21.link/P0898R3)|Ne|
|&nbsp;&nbsp;[Podpora knihoven P0912R5 pro korutiny](https://wg21.link/P0912R5)|Ne|
|&nbsp;&nbsp;[P0919R3 heterogenní vyhledávání pro neuspořádané kontejnery](https://wg21.link/P0919R3)|Ne|
|&nbsp;&nbsp;[Vyhledávání předpočítané hodnoty hash P0920R2](https://wg21.link/P0920R2)|Ne|
|&nbsp;&nbsp;[P0935R0 eradikace bezpodmínečně explicitních výchozích konstruktorů](https://wg21.link/P0935R0)|Ne|
|&nbsp;&nbsp;[P0966R1 řetězec:: Reserve () by se neměl zmenšovat.](https://wg21.link/P0966R1)|Ne|
|&nbsp;&nbsp;[Provádění P1001R2:: unseq](https://wg21.link/P1001R2)|Ne|
|&nbsp;&nbsp;[P1006R1 constexpr pro pointer_traits < T * >::p ointer_to ()](https://wg21.link/P1006R1)|Ne|
|&nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3)|Ne|
|&nbsp;&nbsp;[Vytvoření inteligentního ukazatele P1020R1 s výchozí inicializací](https://wg21.link/P1020R1)|Ne|
|&nbsp;&nbsp;[P1023R0 constexpr pro porovnání std:: Array](https://wg21.link/P1023R0)|Ne|
|&nbsp;&nbsp;[P1032R1 různé constexpr](https://wg21.link/P1032R1)|Ne|
|&nbsp;&nbsp;[P1165R1 konzistentně rozšířící stavové přidělování v operátoru basic_string's + ()](https://wg21.link/P1165R1)|Ne|
|&nbsp;&nbsp;[P1209R0 erase_if (), Erase ()](https://wg21.link/P1209R0)|Ne|
|&nbsp;&nbsp;[P1227R2 podepsané std:: ssize (), nepodepsaný rozsah:: Size ()](https://wg21.link/P1227R2)|Ne|
|&nbsp;&nbsp;[P1285R0 vylepšení požadavků na úplnost u vlastností typu](https://wg21.link/P1285R0)|Ne|
|&nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1)|Ne|
|__Funkce standardní knihovny c++ 17__|__Podporuje se__|
|&nbsp;&nbsp;[LWG 2221 naformátovaný výstupní operátor pro nullptr](https://cplusplus.github.io/LWG/issue2221)|VS 2019 16.1|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 bezpečné převody v unique_ptr\<T [] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 Invoke ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 odebrání auto_ptr, random_shuffle () a starých \<funkčních >ch věcí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup> [Zbýv](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 s výjimkou vyčištění](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 triviální kopii reference_wrapper](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign ()/try_emplace () pro mapu/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 Size (), Empty (), data ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 přesné omezení unique_ptr přiřazení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4387 vylepšení páru a řazené kolekce členů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (Nečasově dlouho)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 podporující neúplné typy v Vector/list/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Základy knihovny N4562: \<ukázka > algoritmu ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017 15,0|
|&nbsp;&nbsp;[Základy knihovny N4562: \<libovolné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017 15,0|
|&nbsp;&nbsp;[Základy knihovny N4562: \<memory_resource >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 odstranění přiřazení polymorphic_allocator](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15,6|
|&nbsp;&nbsp;[Základní informace o knihovně N4562 \<: volitelné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 15,0|
|&nbsp;&nbsp;[Základy knihovny N4562: \<string_view >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017 15,0|
|&nbsp;&nbsp;[Základy knihovny N4562: \<řazená kolekce členů > použít ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017 15,0|
|&nbsp;&nbsp;[Základní informace o knihovně N4562: Boyer-Moore – hledání ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 opravit návratové typy hledání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 odebrání dynamických specifikací výjimek](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0004R1 odebrání zastaralých aliasů iostreams](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015,2 <sup> [Zbýv](#note_rem)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br/>&nbsp;&nbsp;[Opravy P0358R1 pro not_fn ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0006R0 variabilní šablony pro typové vlastnosti (is_same_v atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 vlastnosti typu logického operátoru (spojení atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0024R2 paralelní algoritmy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br/>&nbsp;&nbsp;[P0336R1 přejmenování zásad paralelního spouštění](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br/>&nbsp;&nbsp;[P0394R4 paralelní algoritmy by měly končit () pro výjimky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br/>&nbsp;&nbsp;[P0452R1 sjednocení \<číselných > paralelních algoritmů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0030R1 hypot – (x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0031R0 constexpr pro \<pole > (znovu) a \<iterátor >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0032R3 homogenní rozhraní pro variantu/libovolnou/nepovinnou](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0033R1 enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15,5 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0040R3 rozšíření nástrojů pro správu paměti](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Standardní knihovna P0063R3 C11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0067R5 základní převody řetězců](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15,7 <sup> [charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017 15,0|
|&nbsp;&nbsp;[Mapy a sady P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br/>&nbsp;&nbsp;[P0508R0 objasnění insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Návratový typ P0084R2 emplace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0088R3 \<> variant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0092R1 \<Chrono > Floor (); ceil – (); Round (); ABS ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0152R1 Atomic:: is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size atd.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R0 variadické lock_guard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R2 přejmenování variadické zámku\_Guard na\_rozsah zámku](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0174R2 zastaralá části knihovny starší](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br/>&nbsp;&nbsp;[Relativní cesty P0219R1 pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br/>&nbsp;&nbsp;[Ukládání záznamů adresáře P0317R1 do mezipaměti pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br/>&nbsp;&nbsp;[P0392R0 podporující string_view v cestách systému souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br/>&nbsp;&nbsp;[P0430R2 podporující systémy souborů jiného typu než POSIX](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br/>&nbsp;&nbsp;[P0492R2 vyřešit komentáře NB pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15,7 <sup> [E](#note_E)</sup>|
|&nbsp;&nbsp;[Základní informace o knihovně P0220R1 v1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15,6|
|&nbsp;&nbsp;[Matematické speciální funkce P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0254R2 integrování string_view a std:: String](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15,3 <sup> [G](#note_G)</sup>|
|&nbsp;&nbsp;[P0272R1 non-const basic_string::d ATA ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std:: Byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15,3 <sup> [17](#note_17),&nbsp;[Byte](#note_byte)</sup>|
|&nbsp;&nbsp;[P0302R1 odebrání podpory přidělování v std:: Function](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0307R2 se, že se nedobrovolný větší rovnost](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017 15,0|
|&nbsp;&nbsp;[P0393R3, že je větší varianta větší](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0403R1 UDL for \<string_view > ("Meow" sv atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br/>&nbsp;&nbsp;[P0497R0 oprava shared_ptr pro pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15,5 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0418R2 atomické compare_exchange požadavky memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0426R1 constexpr pro char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0433R2 integrování odpočtů šablon pro šablony tříd do standardní knihovny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br/>&nbsp;&nbsp;[P0739R0 vylepšuje integraci odvození argumentu šablony třídy do standardní knihovny.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0435R1 přetažení common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br/>&nbsp;&nbsp;[P0548R1 a běžný\_typ a doba trvání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0504R0 in_place_t/in_place_type_t\<t >/in_place_index_t\<I >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017 15,0|
|&nbsp;&nbsp;[P0505R0 constexpr pro \<Chrono > (znovu)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0510R0 odmítání variant žádného, pole, odkazů a neúplných typů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017 15,0|
|&nbsp;&nbsp;[Hodnota hash otrav P0513R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br/>&nbsp;&nbsp;[P0599R1 s výjimkou hodnoty hash](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 označuje shared_future kopírování jako s výjimkou](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 konstrukce future_error z future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 zastaralá shared_ptr:: Unique ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0558R1 řešení atomických\<T > pojmenované nekonzistence základní třídy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2)|Ne|
|&nbsp;&nbsp;[P0602R4 šíření kopírování/přesunutí v variantě (volitelné)](https://wg21.link/P0602R4)|VS 2017 15.3<sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0604R0 je\_možné volat nebo výsledek\_vyvolání\_\_výsledku,\_je nevyvolatelný, nevyvolatelný\_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 vložené proměnné pro standardní knihovnu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618r0; zastaralá \<codecvt >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0682R1 opravy základních převodů řetězců](https://wg21.link/P0682R1)|VS 2015 15.7 <sup>[17](#note_17)</sup>|
|__Funkce standardní knihovny c++ 14__|__Podporuje se__|
|&nbsp;&nbsp;[N3462 SFINAE – uživatelsky přívětivé result_of](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr pro \<komplexní >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr pro \<Chrono >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr pro \<pole >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr pro \<initializer_list >, \<řazené kolekce \<členů >, > nástroje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant:: operator () ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDL for \<Chrono >, \<String > (1729ms, "Meow" s atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 předávané iterátory s hodnotou null](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 v uvozovkách ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 heterogenní – asociativní vyhledávání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (časované)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 Exchange ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 opravení členských funkcí constexpr bez const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 rovná se dvojitému rozsahu (), is_permutation (), neshoda ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[Dealokace N3778 velikosti](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDL pro \<komplexní > (3.14 i atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr pro \<funkční >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 přejmenování shared_mutex (časované) na shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 minimální požadavky na prvky kontejneru](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 transparentní operátor funktory (méně\<> atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[Šablony aliasů N3655 \<pro type_traits > (decay_t atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|

Skupina popsaných dokladů znamená, že se do standardu připravila funkce a pak jedna nebo víc papírů ke zlepšení nebo rozšíření této funkce se taky hlasovaly v. Tyto funkce jsou implementovány společně.

### <a name="supported-values"></a>Podporované hodnoty

__Žádné__ prostředky, které ještě nebyly implementovány.<br/>
__Částečný__ znamená, že implementace je nekompletní. Další podrobnosti najdete v části poznámky.<br/>
__VS 2010__ označuje funkce, které jsou podporovány v sadě Visual Studio 2010.<br/>
__VS 2013__ označuje funkce, které jsou podporované v Visual Studio 2013.<br/>
__VS 2015__ označuje funkce, které jsou podporovány v sadě Visual Studio 2015 RTW.<br/>
__Vs 2015,2__ a __vs 2015,3__ označují funkce podporované v sadě Visual Studio 2015 Update 2 a Visual Studio 2015 Update 3 v uvedeném pořadí.<br/>
__VS 2017 15,0__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,0 (RTW).<br/>
__VS 2017 15,3__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,3.<br/>
__VS 2017 15,5__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,5.<br/>
__VS 2017 15,7__ označuje funkce podporované v sadě Visual Studio 2017 verze 15,7.<br/>
__VS 2019 16,0__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,0 (RTW).<br/>
__VS 2019 16,1__ označuje funkce podporované v sadě Visual Studio 2019 verze 16,1.

### <a name="notes"></a>Poznámky

<a name="note_A"></a> V [/std: v režimu c++ 14](../build/reference/std-specify-language-standard-version.md) zůstanou specifikace dynamických výjimek neimplementované a `throw()` pořád se považuje za synonymum pro. `__declspec(nothrow)` V jazyce c++ 17 byly specifikace dynamických výjimek většinou odebrané pomocí P0003R5, přičemž jeden vestige: `throw()` je zastaralý a musí se chovat jako synonymum pro. `noexcept` V [/std: režim c++ 17](../build/reference/std-specify-language-standard-version.md) , MSVC nyní odpovídá standardu tím, že poskytuje `throw()` stejné chování jako `noexcept`, tj. vynucování prostřednictvím ukončení.

Možnost kompilátoru [/Zc: noexceptTypes](../build/reference/zc-noexcepttypes.md) žádá o staré chování `__declspec(nothrow)`. Pravděpodobně `throw()` bude odstraněn v c++ 20. Pro usnadnění migrace kódu v reakci na tyto změny v rámci Standard a naší implementace byly do/STD přidány nové výstrahy kompilátoru pro chyby specifikace výjimky [: c++ 17](../build/reference/std-specify-language-standard-version.md) a [/Permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ podporuje se v režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) ve Visual Studiu 2017 verze 15,7. Další informace najdete v tématu [Podpora dvou fází vyhledávání názvů MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) .

<a name="note_C"></a>__C__ Podpora kompilátoru pro pravidla preprocesoru C99 je v aplikaci Visual Studio 2017 nekompletní. Makra variadické jsou podporována, ale v chování preprocesoru existuje mnoho chyb. Předáváme preprocesor a provede experimentální dodávání těchto změn v [/Permissive-](../build/reference/permissive-standards-conformance.md) režimu brzy.

<a name="note_D"></a>__D__ podporován v rámci [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) s upozorněním Suppressible, C4984.

<a name="note_E"></a>__E__ Toto je zcela nová implementace nekompatibilní s předchozí `std::experimental` verzí, kterou vyžaduje podpora symlink, opravy chyb a změny v chování vyžadovaném standardem. V současné době \<, včetně systému souborů > poskytuje `std::filesystem` nové a předchozí `std::experimental::filesystem`, včetně \<experimentální/FileSystem > poskytuje pouze starou experimentální implementaci. Experimentální implementace bude ODEBRÁNA v další vydaných vydáních knihovny ABI.

<a name="note_G"></a>__G__ podporované vnitřním kompilátorem

<a name="note_14"></a>__14__ tyto funkce c++ 17/20 jsou vždycky povolené, i když je [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) (výchozí). To je způsobeno tím, že byla funkce implementována před zavedením možností **/STD** nebo vzhledem k tomu, že podmíněná implementace byla nepřáníně složitá.

<a name="note_17"></a>__17__ tyto funkce jsou povolené pomocí možnosti kompilátoru [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (nebo [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a>__20__ těchto funkcí je povoleno pomocí možnosti [nejnovější kompilátor/std: c + +](../build/reference/std-specify-language-standard-version.md) . Po dokončení implementace C++ 20 bude přidána nová možnost kompilátoru **/std: c++ 20** , v rámci které budou tyto funkce také k dispozici.

<a name="note_byte"></a>__bajt__ je povolená [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (nebo [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md)), ale protože může v některých případech kolidovat s hlavičkou Windows SDK, má jemně odstupňované makro. `std::byte` Může být zakázáno definováním `_HAS_STD_BYTE` as. `0`

<a name="note_C11"></a>__C11__ Univerzální CRT implementoval součásti C11 standardní knihovny, které jsou vyžadovány v c++ 17, s výjimkou alternativních specifikátorů převodu `strftime()` C99 E/O, C11 `fopen()` exkluzivního režimu a C11 `aligned_alloc()`. Druhý z nich není pravděpodobně implementován, protože C11 určený `aligned_alloc()` způsobem, který je nekompatibilní s `free()`implementací společnosti Microsoft, konkrétně, která `free()` musí být schopna zpracovat vysoce zarovnané přidělení.

<a name="note_rem"></a>__rem__ Funkce odebrané v případě, že je zadána možnost kompilátoru [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) (nebo [/std: c + + + poslední](../build/reference/std-specify-language-standard-version.md)). Tyto funkce se dají znovu povolit, aby se usnadnil přechod na novější jazykové režimy pomocí těchto maker `_HAS_AUTO_PTR_ETC`:, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`a `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ `from_chars()` a`to_chars()` jsou k dispozici pro celá čísla. Časová osa pro plovoucí `from_chars()` desetinnou čárku a plovoucí `to_chars()` desetinnou čárku je následující:
- VS 2017 15.7: Integer `from_chars()` a `to_chars()`.
- VS 2017 15,8: Plovoucí desetinná čárka. `from_chars()`
- VS 2017 15,9: Přetížení s `to_chars()` plovoucí desetinnou čárkou pro nejkratší desetinné číslo.
- VS 2019 16,0: `to_chars()` Přetížení plovoucí desetinné čárky pro nejkratší hexadecimální a přesnost Hex.
- VS 2019 16.2: `to_chars()` Přetížení plovoucí desetinné čárky pro pevnou přesnost a vědeckou přesnost.
- Ještě neimplementováno: `to_chars()` Přetížení s plovoucí desetinnou čárkou pro metodu Precision General. 

<a name ="note_parallel"></a>__paralelní__ Knihovna paralelních algoritmů c++ 17 je dokončená. To neznamená, že každý algoritmus je v každém případě paralelní. nejdůležitější algoritmy byly paralelní a signatury zásad spouštění jsou k dispozici i v případě, že se algoritmy neparalelismuují. Hlavní interní hlavička naší implementace yvals_core. h obsahuje následující "poznámky k paralelním algoritmům": C++umožňuje implementaci implementovat paralelní algoritmy jako volání na sériové algoritmy.  Tato implementace parallelizes několik běžných volání algoritmů, ale ne všechny.

Následující algoritmy jsou paralelní:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if` , `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`,`transform_reduce`

Následující nejsou v předsoučasném paralelismuně paralelní:

- Žádná zřejmá zlepšení výkonu u cílového hardwaru; všechny algoritmy, které pouze kopírují nebo permute – prvky bez větví, jsou obvykle omezeny šířkou pásma paměti:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Nejasnost nad požadavky uživatelů na paralelismus existuje; nejspíš v výše uvedené kategorii přesto:
  - `generate`, `generate_n`
- Efektivní paralelismus podezřelý z neproveditelnosti:
  - `partial_sort`, `partial_sort_copy`
- Ještě nevyhodnoceno; paralelismus se dá implementovat v budoucí verzi a má podezření, že je to užitečné:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](cpp-conformance-improvements.md)<br/>
[Novinky pro vizuál C++ v aplikaci Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historie C++ vizuálních změn 2003 až 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Novinky Visual C++ 2003–2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[C++Blog týmu](https://devblogs.microsoft.com/cppblog/)
