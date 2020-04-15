---
title: Tabulka shody jazyků Microsoft C++
description: Tabulka aktualizací shody microsoft c++ podle verze sady Visual Studio.
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 18f8db28fab83f795baced82a346f07d73256716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365227"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabulka shody jazyků Microsoft C++

Shoda standardů pro kompilátor Microsoft C++ v sadě Visual Studio (MSVC) je nedokončená práce. Tady je souhrn našeho jazyka ISO Standard C++ a shody knihovny podle verze sady Visual Studio. Každý název kompilátoru a standardní knihovny odkazuje na návrhový dokument ISO Standard C++, který popisuje funkci, pokud je k dispozici v době publikování. Ve **sloupci Podporované** jsou uvedeny verze sady Visual Studio, ve které se poprvé objevila podpora této funkce.

Podrobnosti o vylepšení shody Visual Studio 2017 nebo Visual Studio 2019 MSVC najdete [v tématu Vylepšení shody jazyka C++ v sadě Visual Studio](cpp-conformance-improvements.md). Seznam dalších změn najdete [v tématu Co je nového pro Visual C++ ve Visual Studiu](what-s-new-for-visual-cpp-in-visual-studio.md). Změny shody v dřívějších verzích najdete v [tématu Visual C++ historie změn](../porting/visual-cpp-change-history-2003-2015.md) a [Visual C++ Co je nového 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Aktuální zprávy z týmu C++ najdete na [blogu týmu C++](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Mezi Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 nejsou žádné binární změny. Další informace najdete v tématu [Binární kompatibilita C++ mezi Visual Studio 2015, 2017 a 2019](../porting/binary-compat-2015-2017.md)

## <a name="compiler-features"></a>Funkce kompilátoru

|  |  |
|--|--|
| __C++03/11 Základní jazykové funkce__ | __Podporovány__ |
| &nbsp;&nbsp;Všechno ostatní | VS 2015 <sup> [A](#note_A)</sup> |
| &nbsp;&nbsp;Dvoufázové vyhledávání názvů | VS 2017 15,7 <sup> [B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 Výraz SFINAE](https://wg21.link/N2634) | VS 2017 15,7 |
| &nbsp;&nbsp;[N1653 C99 preprocesor](https://wg21.link/N1653) | Částečná <sup> [C](#note_C)</sup> |
| __Základní funkce jazyka C++14__ | __Podporovány__ |
| &nbsp;&nbsp;[N3323 Vylepšená formulace pro kontextové převody](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 Binární literály](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[Typy návratů n3638 auto a decltype(auto)](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-zachycuje](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 Generické lambdy](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[N3760 \[ \[zastaralá\] \] vlastnost atribut](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[N3778 Velikosti deallocation](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3781 Oddělovače číslic](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[Šablony proměnných N3651](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 Rozšířený constexpr](https://wg21.link/n3652) | VS 2017 15,0 |
| &nbsp;&nbsp;[N3653 Výchozí inicializátory členů pro agregace](https://wg21.link/n3653) | VS 2017 15,0 |
| __Základní funkce jazyka C++17__ | __Podporovány__ |
| &nbsp;&nbsp;[N4086 Odstranění trigrafů](https://wg21.link/n4086) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 Nová pravidla pro auto s vyztuženými-init-seznamy](https://wg21.link/n3922) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Název typu N4051 v parametrech šablony šablony](https://wg21.link/n4051) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4266 Atributy pro obory názvů a čítače výčtů](https://wg21.link/n4266) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267 u8 znak literály](https://wg21.link/n4267) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4230 Vnořené definice oboru názvů](https://wg21.link/n4230) | VS 2015.3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 Stručné static_assert](https://wg21.link/n3928) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 Generalizované rozsah-založené pro smyčky](https://wg21.link/p0184r0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Atribut pádu \[ \[\] \] P0188R1](https://wg21.link/p0188r1) | VS 2017 15,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 Odebrání klíčového slova register](https://wg21.link/p0001r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 Odebrání operátor++ pro bool](https://wg21.link/p0002r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 Zachycení *to podle hodnoty](https://wg21.link/p0018r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 Použití oborů názvů atributů bez opakování](https://wg21.link/p0028r4) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1 \_ \_has_include](https://wg21.link/p0061r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 Přímý seznam-init pevných výčtů z celáčísla](https://wg21.link/p0138r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 constexpr lambdas](https://wg21.link/p0170r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1 \[ \[nodiscard,\] \] atribut](https://wg21.link/p0189r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Atribut \[ \[Maybe_unused\] \] P0212R1](https://wg21.link/p0212r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0217R3 Strukturovaná vázání](https://wg21.link/p0217r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 constexpr if-příkazy](https://wg21.link/p0292r2) | VS 2017 15,3 <sup> [D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 Příkazy výběru s inicializátory](https://wg21.link/p0305r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 Hexfloat literály](https://wg21.link/p0245r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268 Povolení více non-typ šablony args](https://wg21.link/n4268) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4295 Fold výrazy](https://wg21.link/n4295) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Odebrání dynamických specifikací výjimek](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 Přidání noexcept do typového systému](https://wg21.link/p0012r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 Přetížení dynamické paměti](https://wg21.link/p0035r4) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 Inline proměnné](https://wg21.link/p0386r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 Odpovídající parametry šablony ke kompatibilním argumentům](https://wg21.link/p0522r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 Odstranění některých prázdných unárních záhybů](https://wg21.link/p0036r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 Fixační kvalifikační konverze](https://wg21.link/n4261) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 Rozšířená agregátní inicializace](https://wg21.link/p0017r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Odpočet argumentů šablony P0091R3 pro šablony tříd](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0 Problémy s odpočtem argumentů šablony třídy](https://wg21.link/p0512r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 Deklarování parametrů netypové šablony s automatickým](https://wg21.link/p0127r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 Zaručená kopie elision](https://wg21.link/p0135r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0136R1 Přeformulování dědící konstruktory](https://wg21.link/p0136r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std::praní](https://wg21.link/p0137r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 Pořadí vyhodnocení výrazu rafinace](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 Pořadí vyhodnocení argumentů funkcí](https://wg21.link/p0400r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Rozšíření sady P0195R2 Pack v deklaracích použití](https://wg21.link/p0195r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 Ignorování nerozpoznaných atributů](https://wg21.link/p0283r2) | VS 2015 <sup> [14](#note_14)</sup> |
| __C++ 17 Základní jazykové funkce (hlášení závad)__ | __Podporovány__ |
| &nbsp;&nbsp;[P0702R1 Oprava odpočtu argumentů šablony třídy pro ctory seznamu inicializátorů](https://wg21.link/p0702r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 Uvolnění strukturovaných vazeb přizpůsobení bod hledání pravidel](https://wg21.link/p0961r1) | VS 2019 16,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 Povolení strukturovaných vazeb pro přístupné členy](https://wg21.link/p0969r0) | VS 2019 16,0 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 Zjednodušení implicitního zachycení lambda](https://wg21.link/p0588r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[ \[nodiscard\] \] pro konstruktory](https://wg21.link/p1771r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 Sloučené znění pro P0527R1 a P1155R3, více implicitní pohyby](https://wg21.link/p1825r0) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 Kontrola abstraktních typů tříd](https://wg21.link/P0929R2) | Ne |
| &nbsp;&nbsp;[P0962R2 Uvolnění pravidel pro hledání bodů přizpůsobení smyčky pro rozsah pro](https://wg21.link/p0962r1) | Ne |
| &nbsp;&nbsp;[P0859R0 CWG 1581: Kdy jsou definovány členské funkce constexpr](https://wg21.link/p0859r0) | Ne |
| &nbsp;&nbsp;[Odpočet velikosti pole P1009R2 v nových výrazech](https://wg21.link/P1009R2) | Ne |
| &nbsp;&nbsp;[P1286R2 Contra CWG DR1778](https://wg21.link/P1286R2) | Ne |
| __Funkce jazyka C++20 Core__ | __Podporovány__ |
| &nbsp;&nbsp;[P0704R1 Upevnění const lvalue ref-qualified ukazatele na členy](https://wg21.link/p0704r1) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4 Make char16_t/char32_t řetězcové literály jsou UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 Změna aktivního člena unie uvnitř constexpr](https://wg21.link/P1330R0) | VS 2017 15,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 noexcept \<Pro chrono> nula(), min(), max()](https://wg21.link/P0972R0) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 Třícestný (kosmická loď) porovnávací operátor <=>](https://wg21.link/P0515R3) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2 Makra testu funkcí](https://wg21.link/P0941R2) | VS 2019 16,0 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 Zákaz agregátů s konstruktory deklarovanými uživatelem](https://wg21.link/P1008R1) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 Určená inicializace](https://wg21.link/p0329r4) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 ADL a šablony funkcí, které nejsou viditelné](https://wg21.link/P0846R0) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 Povolení lambda-capture \[=, to\]](https://wg21.link/p0409r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 Známá syntaxe šablony pro obecné lambdy](https://wg21.link/p0428r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 Výchozí konstrukční a převoditelné lambdy bez stavové](https://wg21.link/P0624R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 Povolení rozšíření balení v lambda init-capture](https://wg21.link/P0780R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 Zamezet implicitní zachycení tohoto přes\[=\]](https://wg21.link/P0806R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 Zlepšení konzistence pro <=> a další operátory porovnání](https://wg21.link/P1120R0) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \< = \> != ==](https://wg21.link/P1185R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0734R0 Koncepty](https://wg21.link/P0734R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 Fixační mezery v funkcích v omezeních](https://wg21.link/P0857R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 Dnešní požadavky na návratový typ jsou nedostatečné](https://wg21.link/P1084R2) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 Podmíněné explicitní](https://wg21.link/P0892R2) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 Rozšíření strukturovaných vazeb tak, aby byly spíše jako deklarace proměnných](https://wg21.link/P1091R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 Použití výčtu](https://wg21.link/P1099R5) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3 Kdy skutečně používáte\<=>](https://wg21.link/P1186R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1 Kosmická loď potřebuje tune-up](https://wg21.link/P1630R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 \_ \_Přidání\_ \_ VA_OPT pro vynechání čárky a odstranění čárky](https://wg21.link/P0306R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 Range-based for-loops s inicializátory](https://wg21.link/P0614R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 Výchozí inicializátory členů pro bitová pole](https://wg21.link/P0683R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1 try-catch bloky ve funkcích constexpr](https://wg21.link/P1002R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 Zavržení použití operátoru čárky ve výrazech dolního indexu](https://wg21.link/P1161R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[ \[nodiscard("zpráva")\]\]](https://wg21.link/P1301R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 Rozpoznání importu jednotek hlaviček vyžaduje úplné předběžné zpracování.](https://wg21.link/P1703R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 Povolit výchozí porovnání podle hodnoty](https://wg21.link/P1946R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2 const neshoda s výchozí kopie konstruktoru](https://wg21.link/P0641R2) | Částečné |
| &nbsp;&nbsp;[P0912R5 Korutiny](https://wg21.link/P0912R5) | Částečné |
| &nbsp;&nbsp;[P1103R3 Moduly](https://wg21.link/P1103R3) | Částečné |
| &nbsp;&nbsp;[P0315R4 Povolení lambdas v nehodnocených kontextech](https://wg21.link/P0315R4) | Ne |
| &nbsp;&nbsp;[P0388R4 Povolit převody na pole s neznámou vazbou](https://wg21.link/P0388R4) | Ne |
| &nbsp;&nbsp;[P0479R5 \[ \[\] \] pravděpodobné \[ \[\] \] a nepravděpodobné atributy](https://wg21.link/P0479R5) | Ne |
| &nbsp;&nbsp;[P0634R3 Dolů s typename!](https://wg21.link/P0634R3) | Ne |
| &nbsp;&nbsp;[P0692R1 Relaxační kontrola přístupu na specializace](https://wg21.link/P0692R1) | Ne |
| &nbsp;&nbsp;[P0722R3 Efektivní odstranění velikosti pro třídy s proměnnou velikostí](https://wg21.link/P0722R3) | Ne |
| &nbsp;&nbsp;[P0732R2 Typy tříd v parametrech netypové šablony](https://wg21.link/P0732R2) | Ne |
| &nbsp;&nbsp;[P0735R1 Interakce memory_order_consume s sekvencí uvolňování](https://wg21.link/P0735R1) | Ne |
| &nbsp;&nbsp;[P0784R7 Další kontejnery constexpr](https://wg21.link/P0784R7) | Ne |
| &nbsp;&nbsp;[Atribut P0840R2 \[ \[no_unique_address\] \]](https://wg21.link/P0840R2) | Ne |
| &nbsp;&nbsp;[P0848R3 Podmíněně triviální speciální členské funkce](https://wg21.link/P0848R3) | Ne |
| &nbsp;&nbsp;[P0960R3 Povolit inicializaci agregací ze seznamu hodnot v závorce](https://wg21.link/P0960R3) | Ne |
| &nbsp;&nbsp;[P1064R0 Povolení volání virtuálních funkcí v konstantních výrazech](https://wg21.link/P1064R0) | Ne |
| &nbsp;&nbsp;[P1073R3 Okamžité funkce](https://wg21.link/P1073R3) | Ne |
| &nbsp;&nbsp;[P1094R2 Vnořené inline obory názvů](https://wg21.link/P1094R2) | Ne |
| &nbsp;&nbsp;[P1139R2 Řešit formulační otázky týkající se ISO 10646](https://wg21.link/P1139R2) | Ne |
| &nbsp;&nbsp;[P1141R2 Další přístup k omezeným prohlášením](https://wg21.link/P1141R2) | Ne |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | Ne |
| &nbsp;&nbsp;[P1152R4 Zavrženíhodné těkavé](https://wg21.link/P1152R4) | Ne |
| &nbsp;&nbsp;[P1236R1 Podepsaná celá čísla jsou dvojkem](https://wg21.link/P1236R1) | Ne |
| &nbsp;&nbsp;[P1327R1 Povolení dynamic_cast, polymorfní typeid v konstantních výrazech](https://wg21.link/P1327R1) | Ne |
| &nbsp;&nbsp;[P1331R2 Povolení triviální výchozí inicializace v kontextu constexpr](https://wg21.link/P1331R2) | Ne |
| &nbsp;&nbsp;[P1353R0 Chybějící makra testu funkcí](https://wg21.link/P1353R0) | Ne |
| &nbsp;&nbsp;[P1381R1 Referenční zachycení strukturovaných vazeb](https://wg21.link/P1381R1) | Ne |
| &nbsp;&nbsp;[P1452R2 Na nerovnoměrné sémantice požadavků na návratový typ](https://wg21.link/P1452R2) | Ne |
| &nbsp;&nbsp;[P1616R1 Použití neomezených TTP s omezenými šablonami](https://wg21.link/P1616R1) | Ne |
| &nbsp;&nbsp;[P1668R1 Povolení nehodnocené inline montáže ve funkcích constexpr](https://wg21.link/P1668R1) | Ne |
| &nbsp;&nbsp;[P1766R1 Zmírnění drobných modulů neduhy](https://wg21.link/P1766R1) | Ne |
| &nbsp;&nbsp;[P1811R0 Relaxační omezení pro předefinování odolnosti pro zpětný vývoz](https://wg21.link/P1811R0) | Ne |
| &nbsp;&nbsp;[P1814R0 CTAD pro alias šablony](https://wg21.link/P1814R0) | Ne |
| &nbsp;&nbsp;[P1816R0 CTAD pro agregáty](https://wg21.link/P1816R0) | Ne |
| &nbsp;&nbsp;[P1874R1 Pořadí dynamické inicializace nemístních proměnných v modulech](https://wg21.link/P1874R1) | Ne |
| &nbsp;&nbsp;[P1907R1 Nekonzistence s netypovými parametry šablony](https://wg21.link/P1907R1) | Ne |
| &nbsp;&nbsp;[P1971R0 Základní změny pro KOMENTÁŘE NB na zasedání v listopadu 2019 (Belfast)](https://wg21.link/P1971R0) | Ne |
| &nbsp;&nbsp;[P1972R0 US105 Kontrola spokojenosti s omezeními pro jiné než šablony při vytváření ukazatele pro funkci](https://wg21.link/P1972R0) | Ne |
| &nbsp;&nbsp;[P1975R0 Oprava znění agregované inicializace závorek](https://wg21.link/P1975R0) | Ne |
| &nbsp;&nbsp;[Rozlišení P1979R0 k US086](https://wg21.link/P1979R0) | Ne |
| &nbsp;&nbsp;[P1980R0 CA096: Párování deklarací pro nezávislé klauzule vyžaduje](https://wg21.link/P1980R0) | Ne |

## <a name="standard-library-features"></a>Standardní funkce knihovny

|  |  |
|--|--|
| __C++20 Standardní funkce knihovny__ | __Podporovány__ |
| &nbsp;&nbsp;[P0809R0 Porovnání neuspořádaných kontejnerů](https://wg21.link/p0809r0) | VS 2010 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0 Constexpr Iterátor Požadavky](https://wg21.link/p0858r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 Zamezení zbytečnému úpadku](https://wg21.link/p0777r1) | VS 2017 15,7 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1 Intuitivní create_directory()](https://wg21.link/P1164R1) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2 remove_cvref](https://wg21.link/p0550r2) | VS 2019 16,0 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 starts_with()/ends_with() Pro basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 obsahuje() pro objednané a neuspořádané asociativní kontejnery](https://wg21.link/p0458r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 seznam/forward_list remove()/remove_if()/unique() Návrat size_type](https://wg21.link/p0646r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left(), shift_right()](https://wg21.link/p0769r2) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16,1 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6\<atomové\<plovákové\<>, atomové dvojité>, atomové dlouhé dvojité>](https://wg21.link/p0020r6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: Typ pro znaky A řetězce UTF-8](https://wg21.link/P0482R6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 \[ \[nodiscard\] \] pro STL, část 1](https://wg21.link/p0600r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<verze>](https://wg21.link/p0754r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1 noexcept Pro std::function's Move Constructor](https://wg21.link/P0771R1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1 Operátor upevnění>> (basic_istream&, CharT*)](https://wg21.link/P0487R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 Použití move() V \<číselných>](https://wg21.link/p0616r0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[Standardní knihovní koncepty P0898R3](https://wg21.link/P0898R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 Heterogenní vyhledávání pro neobjednané kontejnery](https://wg21.link/P0919R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 Přejmenování konceptů na standard_case](https://wg21.link/P1754R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array od LFTS s aktualizacemi](https://wg21.link/P0325R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 SFINAE-přátelské underlying_type](https://wg21.link/P0340R3) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0 výčtu třídy memory_order](https://wg21.link/p0439r0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bit> otočných a počítacích funkcí](https://wg21.link/P0553R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<čísla> matematických konstant](https://wg21.link/P0631R8) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 istream_iterator vyčištění](https://wg21.link/P0738R2) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 Zavrženíhodné is_pod](https://wg21.link/P0767R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 řetězec::reserve() by se neměl zmenšovat](https://wg21.link/P0966R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if(), mazání()](https://wg21.link/P1209R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 Podepsáno std::ssize(), Nepodepsané rozpětí::size()](https://wg21.link/P1227R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 Úzká smlouva pro ceil2()](https://wg21.link/P1355R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 Přemístění endian u \<bitů>](https://wg21.link/P1612R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front() Neměl by rozbalit reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 Rafinace Heterogenní vyhledávání pro neobjednané kontejnery](https://wg21.link/P1690R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 Chybějící makra testu funkcí 2017-2019](https://wg21.link/P1902R1) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | Ne |
| &nbsp;&nbsp;[P0053R7 \<synchronizační>](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[P0753R2 osyncstream manipulátory](https://wg21.link/p0753r2) | Ne |
| &nbsp;&nbsp;[P0122R7 \<rozpětí>](https://wg21.link/p0122r7) | Ne |
| &nbsp;&nbsp;[P0202R3 constexpr \<Pro algoritmus> a výměny()](https://wg21.link/p0202r3) | Ne |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6) | Ne |
| &nbsp;&nbsp;[P0355R7 \<chrono> kalendáře a časová pásma](https://wg21.link/p0355r7) | Ne |
| &nbsp;&nbsp;[P0357R3 Podpůrné neúplné typy v reference_wrapper](https://wg21.link/P0357R3) | Ne |
| &nbsp;&nbsp;[P0415R1 constexpr \<Pro komplexní> (opět)](https://wg21.link/p0415r1) | Ne |
| &nbsp;&nbsp;[P0475R1 Zaručená kopie Elision pro kusovou konstrukci](https://wg21.link/P0475R1) | Ne |
| &nbsp;&nbsp;[P0476R2 \<> bit_cast](https://wg21.link/P0476R2) | Ne |
| &nbsp;&nbsp;[P0528R3 Atomic Compare-And-Exchange s bity odsazení](https://wg21.link/P0528R3) | Ne |
| &nbsp;&nbsp;[P0591R4 Užitkové funkce pro použití-Alokátor konstrukce](https://wg21.link/P0591R4) | Ne |
| &nbsp;&nbsp;[P0608R3 Zlepšení varianty převodu konstruktoru / přiřazení](https://wg21.link/P0608R3) | Ne |
| &nbsp;&nbsp;[P0619R4 Odebrání c++17-zastaralé funkce v jazyce C++20](https://wg21.link/P0619R4) | Ne |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | Ne |
| &nbsp;&nbsp;[P0655R1\<návštěva R>()](https://wg21.link/P0655R1) | Ne |
| &nbsp;&nbsp;[P0674R1 make_shared() Pro pole](https://wg21.link/p0674r1) | Ne |
| &nbsp;&nbsp;[P0718R2\<atomová\<shared_ptr\<\<T>>, atomová weak_ptr T>>](https://wg21.link/p0718r2) | Ne |
| &nbsp;&nbsp;[P0768R1 Podpora knihovny pro operátora porovnání kosmické lodi\<=>](https://wg21.link/p0768r1) | Ne |
| &nbsp;&nbsp;[P0811R3 střední bod(), lerp()](https://wg21.link/P0811R3) | Ne |
| &nbsp;&nbsp;[P0879R0 constexpr pro výměnu funkcí](https://wg21.link/P0879R0) | Ne |
| &nbsp;&nbsp;[Řady P0896R4 \<\>](https://wg21.link/P0896R4) | Ne |
| &nbsp;&nbsp;[P0912R5 Podpora knihovny pro korutiny](https://wg21.link/P0912R5) | Ne |
| &nbsp;&nbsp;[P0920R2 Předem vypočtené vyhledávání hodnot hash](https://wg21.link/P0920R2) | Ne |
| &nbsp;&nbsp;[P0935R0 Eradikace zbytečně explicitní výchozí konstruktory](https://wg21.link/P0935R0) | Ne |
| &nbsp;&nbsp;[P1001R2 spuštění::unseq](https://wg21.link/P1001R2) | Ne |
| &nbsp;&nbsp;[P1006R1 constexpr pro pointer_traits<T*>::pointer_to()](https://wg21.link/P1006R1) | Ne |
| &nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3) | Ne |
| &nbsp;&nbsp;[Vytvoření inteligentního ukazatele P1020R1 s výchozí inicializací](https://wg21.link/P1020R1) | Ne |
| &nbsp;&nbsp;[P1023R0 constexpr Pro std::array Porovnání](https://wg21.link/P1023R0) | Ne |
| &nbsp;&nbsp;[P1032R1 Různé constexpr](https://wg21.link/P1032R1) | Ne |
| &nbsp;&nbsp;[P1165R1 Konzistentně šíření stavové alokátory v operátoru basic_string+()](https://wg21.link/P1165R1) | Ne |
| &nbsp;&nbsp;[P1285R0 Zlepšení požadavků na úplnost pro vlastnosti typu](https://wg21.link/P1285R0) | Ne |
| __C++ 17 Standardní funkce knihovny__ | __Podporovány__ |
| &nbsp;&nbsp;[LWG 2221 Formátovaný výstupní operátor pro nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16,1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 Bezpečné převody\<v unique_ptr T[]>](https://wg21.link/n4089) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 invoke()](https://wg21.link/n4169) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 Odstranění auto_ptr, random_shuffle(), a staré \<funkční> Stuff](https://wg21.link/n4190) | VS 2015 <sup> [rem](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 noexcept Vyčištění](https://wg21.link/n4258) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions()](https://wg21.link/n4259) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 Triviálně kopírovatelné reference_wrapper](https://wg21.link/n4277) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() Pro mapu/unordered_map](https://wg21.link/n4279) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 velikost(), empty(), data()](https://wg21.link/n4280) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 Přesně omezující přiřazení unique_ptr](https://wg21.link/n4366) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 Zlepšení pár a n-tice](https://wg21.link/n4387) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (bez času)](https://wg21.link/n4508) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 Podpůrné neúplné typy v vektoru/seznamu/forward_list](https://wg21.link/n4510) | VS 2013 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 Knihovna \<Základy: algoritmus> sample()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15,0 |
| &nbsp;&nbsp;[N4562 Knihovna \<Základy: jakýkoli>](https://wg21.link/n4562#any) | VS 2017 15,0 |
| &nbsp;&nbsp;[N4562 Knihovna \<Základy: memory_resource>](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 Odstranění polymorphic_allocator přiřazení](https://wg21.link/p0337r0) | VS 2017 15,6 |
| &nbsp;&nbsp;[N4562 Knihovna \<Základy: volitelné>](https://wg21.link/n4562#optional) | VS 2017 15,0 |
| &nbsp;&nbsp;[N4562 Knihovna \<Základy: string_view>](https://wg21.link/n4562#string.view) | VS 2017 15,0 |
| &nbsp;&nbsp;[N4562 Knihovna \<Základy: n-tice> platí()](https://wg21.link/n4562#tuple) | VS 2017 15,0 |
| &nbsp;&nbsp;[N4562 Knihovna Základy: Boyer-Moore search()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Oprava návratových typů searcher](https://wg21.link/p0253r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Odebrání specifikací dynamických výjimek](https://wg21.link/p0003r5) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 Odebrání zastaralé iostreams aliasy](https://wg21.link/p0004r1) | VS 2015.2 <sup> [rem](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 Opravy pro not_fn()](https://wg21.link/p0358r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Proměnné šablony P0006R0 pro vlastnosti typu (is_same_v atd.)](https://wg21.link/p0006r0) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const()](https://wg21.link/p0007r1) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0013R1 Logické vlastnosti typu operátora (spojka atd.)](https://wg21.link/p0013r1) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Paralelní algoritmy P0024R2](https://wg21.link/p0024r2)<br/>&nbsp;&nbsp;[P0336R1 Přejmenování zásad paralelního provádění](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 Paralelní algoritmy by měly být ukončeny() pro výjimky](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 Sjednocení \<číselných> paralelníalgoritmy](https://wg21.link/p0452r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0025R1 svorka()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot(x, y, z)](https://wg21.link/p0030r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0031R0 constexpr \<Pro> (opět) a \<iterátor>](https://wg21.link/p0031r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 Homogenní rozhraní Pro variantu/libovolnou/volitelnou](https://wg21.link/p0032r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0033R1 Přeformulování enable_shared_from_this](https://wg21.link/p0033r1) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 Rozšíření nástrojů pro správu paměti](https://wg21.link/p0040r3) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Standardní knihovna P0063R3 C11](https://wg21.link/p0063r3) | VS 2015 <sup> [C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0067R5 Elementární řetězec převody](https://wg21.link/p0067r5) | VS 2019 16,4 <sup> [charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0083R3 Splicing mapy a sady](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 Vyjasňující insert_return_type](https://wg21.link/p0508r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 Návratový typ Emplace](https://wg21.link/p0084r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[Varianta P0088R3 \<>](https://wg21.link/p0088r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0092R1 \<chrono> podlaží(), ceil(), kulaté(), abs()](https://wg21.link/p0092r1) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size atd.](https://wg21.link/p0154r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 Variadická lock_guard](https://wg21.link/p0156r0) | VS 2015.2 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 Přejmenování ochranu\_zámku\_Variadic na zámek s vymezeným oborem](https://wg21.link/p0156r2) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](https://wg21.link/p0163r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0174R2 Zavržení zbytkové části knihovny](https://wg21.link/p0174r2) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple()](https://wg21.link/p0209r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[>souborového systému \<P0218R1](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[Relativní cesty Pro souborový systém P0219R1](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[Ukládání položek adresáře P0317R1 do mezipaměti pro souborový systém](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[Podpora p0392R0 string_view v cestách souborového systému](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 Podpora souborů neposix](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 Řešení NB Komentáře pro souborový systém](https://wg21.link/p0492r2) | VS 2017 15,7 <sup> [E](#note_E)</sup> |
| &nbsp;&nbsp;[P0220R1 Základy knihovny V1](https://wg21.link/p0220r1) | VS 2017 15,6 |
| &nbsp;&nbsp;[P0226R1 Matematické speciální funkce](https://wg21.link/p0226r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0254R2 Integrace string_view a std::string](https://wg21.link/p0254r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15,3 <sup> [G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 gcd(), lcm()](https://wg21.link/p0295r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std::bajt](https://wg21.link/p0298r3) | VS 2017 15,3 <sup> [17](#note_17),&nbsp;[bajt](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 Odebrání podpory alokátoru v std::function](https://wg21.link/p0302r1) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 Díky volitelné větší větší rovná znovu](https://wg21.link/p0307r2) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0393R3 Díky variantě větší rovná](https://wg21.link/p0393r3) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0403R1 UDL pro \<string_view> ("mňau"sv, atd.)](https://wg21.link/p0403r1) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 Upevňovací shared_ptr pro pole](https://wg21.link/p0497r0) | VS 2017 15,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[Požadavky na memory_order atomových compare_exchange P0418R2](https://wg21.link/p0418r2) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr pro char_traits](https://wg21.link/p0426r1) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0433R2 Integrace odpočtu šablon pro šablony tříd do standardní knihovny](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 Zlepšení integrace odpočtu argumentů šablony třídy do standardní knihovny](https://wg21.link/p0739r0) | VS 2017 15,7 |
| &nbsp;&nbsp;[P0435R1 Generální oprava common_type](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 Vyladění\_běžného typu a doby trvání](https://wg21.link/p0548r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 Přehodnocení in_place_t/in_place_type_t\<T\<>/in_place_index_t I>](https://wg21.link/p0504r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0505R0 constexpr \<Pro chrono> (opět)](https://wg21.link/p0505r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 Odmítnutí variant nic, pole, odkazy a neúplné typy](https://wg21.link/p0510r0) | VS 2017 15,0 |
| &nbsp;&nbsp;[P0513R0 Otrava hash](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 noexcept hash](https://wg21.link/p0599r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 Značení shared_future kopírování jako noexcept](https://wg21.link/p0516r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 Konstrukce future_error z future_errc](https://wg21.link/p0517r0) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 Zavržení shared_ptr::unikátní()](https://wg21.link/p0521r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 Řešení\<atomových t> nekonzistencí základní třídy](https://wg21.link/p0558r1) | VS 2017 15,3 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 Šíření Kopie/Přesunout Trivialita ve variantě/volitelné](https://wg21.link/P0602R4) | VS 2017 15,3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 Změna\_\_je callable/výsledek\_Chcete-li vyvolat výsledek,\_je\_\_neschůdný, je nothrow nevotožný](https://wg21.link/p0604r0) | VS 2017 15,3 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0607R0 Vložky pro standardní knihovnu](https://wg21.link/p0607r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 Zavrženíhodné \<kodek>](https://wg21.link/p0618r0) | VS 2017 15,5 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 Oprava elementárních řetězových převodů](https://wg21.link/P0682R1) | VS 2015 15,7 <sup> [17](#note_17)</sup> |
| __C++ 14 Standardní funkce knihovny__ | __Podporovány__ |
| &nbsp;&nbsp;[N3462 SFINAE-Přátelské result_of](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr \<Pro komplexní>](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr \<Pro chrono>](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr \<Pro>pole](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr \<pro \<initializer_list>, \<> n-tice, užitkové>](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant::operator()()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 UDLpro \<chrono \<>, řetězec> (1729ms, "mňau" atd.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 Null dopředu iterátory](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 citoval()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 Heterogenní asociativní vyhledávání](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (časované)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 výměna()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 Upevnění konstexpr členských funkcí bez const](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670\<dostat T>()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 Dual-Range equal(), is_permutation(), neshoda()](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[N3778 velikosti Deallocation](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 UDPro \<komplexní> (3.14i, atd.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr \<Pro funkční>](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 Přejmenování shared_mutex (Časované) na shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 Minimální požadavky na prvky kontejneru](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 Transparentní operátor functors (méně\<>, atd.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[N3655 Alias šablony \<pro type_traits> (decay_t, atd.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique()](https://wg21.link/n3656) | VS 2013 |

Skupina dokumentů uvedených společně označuje funkci Standard spolu s jedním nebo více schválenými vylepšeními nebo rozšířeními. Tyto funkce jsou implementovány společně.

### <a name="supported-values"></a>Podporované hodnoty

__Dosud__ nebyly implementovány žádné prostředky.\
__Částečné__ znamená, že implementace je neúplná. Další informace naleznete v části Poznámky.\
__VS 2010__ označuje funkce, které jsou podporovány v sadě Visual Studio 2010.\
__VS 2013__ označuje funkce, které jsou podporovány v sadě Visual Studio 2013.\
__VS 2015__ označuje funkce, které jsou podporované v Sadě Visual Studio 2015 (RTW).\
__VS 2015.2__ a __VS 2015.3__ označují funkce, které jsou podporované v aktualizaci Visual Studio 2015 Update 2 a Visual Studio 2015 Update 3.\
__VS 2017 15.0__ označuje funkce, které jsou podporované ve Visual Studiu 2017 verze 15.0 (RTW).\
__VS 2017 15.3__ označuje funkce, které jsou podporované ve Visual Studiu 2017 verze 15.3.\
__VS 2017 15.5__ označuje funkce, které jsou podporované ve Visual Studiu 2017 verze 15.5.\
__VS 2017 15.7__ označuje funkce, které jsou podporované ve Visual Studiu 2017 verze 15.7.\
__VS 2019 16.0__ označuje funkce, které jsou podporované ve Visual Studiu 2019 verze 16.0 (RTW).\
__VS 2019 16.1__ označuje funkce, které jsou podporované ve Visual Studiu 2019 verze 16.1.\
__VS 2019 16.2__ označuje funkce, které jsou podporované ve Visual Studiu 2019 verze 16.2.\
__VS 2019 16.3__ označuje funkce, které jsou podporované ve Visual Studiu 2019 verze 16.3.\
__VS 2019 16.4__ označuje funkce, které jsou podporované ve Visual Studiu 2019 verze 16.4.\
__VS 2019 16.5__ označuje funkce, které jsou podporované ve Visual Studiu 2019 verze 16.5.

### <a name="notes"></a>Poznámky

<a name="note_A"></a>__A__ V [režimu /std:c++14](../build/reference/std-specify-language-standard-version.md) zůstávají specifikace dynamické `throw()` výjimky neimplementovány `__declspec(nothrow)`a stále se s nimi zachází jako se synonymem pro . V jazyce C++17 byly specifikace dynamických výjimek většinou odebrány pomocí `throw()` P0003R5, takže jeden pozůstatek: je zastaralé a musí se chovat jako synonymum pro `noexcept`. V [režimu /std:c++17](../build/reference/std-specify-language-standard-version.md) msvc nyní odpovídá `throw()` standardu tím, že poskytuje stejné chování jako `noexcept`, to znamená vynucení prostřednictvím ukončení.

Možnost kompilátoru [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) požaduje `__declspec(nothrow)`naše staré chování . Je pravděpodobné, `throw()` že budou odebrány v Jazyce C ++ 20. Chcete-li pomoci s migrací kódu v reakci na tyto změny v Standard a naše implementace, nové překladač upozornění pro problémy specifikace výjimky byly přidány do [/std:c++17](../build/reference/std-specify-language-standard-version.md) a [/tolerantní-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ Podporováno v [/tolerantní-](../build/reference/permissive-standards-conformance.md) režimu ve Visual Studiu 2017 verze 15.7. Další informace naleznete [v tématu Podpora vyhledávání názvů dvou fází přichází do msvc](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a>__C__ Podpora kompilátoru pro pravidla preprocesoru C99 je v sadě Visual Studio 2017 neúplná. Jsme přepracování preprocesoru a začal odesílání těchto změn ve Visual Studio 2017 verze 15.8 s [přepínačem kompilátoru /experimental:preprocessor.](../build/reference/experimental-preprocessor.md)

<a name="note_D"></a>__D__ Podporováno pod [/std:c++14](../build/reference/std-specify-language-standard-version.md) s potlačitelným upozorněním [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a>__E__ Jedná se o zcela novou implementaci, nekompatibilní s předchozí `std::experimental` verzí, nezbytnou podporou symlink, opravami chyb a změnami v chování požadovaném standardem. V současné \<době, včetně souborového systému> poskytuje nové `std::filesystem` a předchozí `std::experimental::filesystem`, a včetně \<experimentální / souborový systém> poskytuje pouze staré experimentální implementace. Experimentální implementace bude odstraněna v příštím ABI-lámání vydání knihoven.

<a name="note_G"></a>__G__ Podporováno kompilátorem vnitřní.

<a name="note_14"></a>__14__ Tyto funkce jazyka C++17/20 jsou vždy povoleny, i když je zadán [parametr /std:c++14](../build/reference/std-specify-language-standard-version.md) (výchozí). Důvodem je buď proto, že funkce byla implementována před zavedením **/std** možnosti nebo protože podmíněné implementace byla nežádoucí složité.

<a name="note_17"></a>__17__ Tyto funkce jsou povoleny volbou kompilátoru [/std:c++17](../build/reference/std-specify-language-standard-version.md) (nebo [/std:c++latest).](../build/reference/std-specify-language-standard-version.md)

<a name="note_20"></a>__20__ Tyto funkce jsou povoleny parametrem [/std:c++latest](../build/reference/std-specify-language-standard-version.md) compiler. Po dokončení implementace C++ 20 bude přidána nová možnost kompilátoru **/std:c++20,** pod kterou budou k dispozici také tyto funkce.

<a name="note_byte"></a>__Bajt__ `std::byte` je povolen [/std:c++17](../build/reference/std-specify-language-standard-version.md) (nebo [/std:c++latest](../build/reference/std-specify-language-standard-version.md)), ale protože může být v konfliktu se záhlavími sady Windows SDK v některých případech, má jemně odstupňované makro pro odhlášení. To může být zakázáno definováním `_HAS_STD_BYTE` jako `0`.

<a name="note_C11"></a>__C11__ Univerzální CRT implementoval části standardní knihovny C11, které jsou vyžadovány C ++ `strftime()` 17, s výjimkou c99 E/ O alternativní specifikátory převodu, C11 `fopen()` výhradní režim a C11 `aligned_alloc()`. Ten je nepravděpodobné, že bude provedena, `aligned_alloc()` protože C11 určené způsobem, který `free()`je neslučitelný s implementací společnosti Microsoft : a sice, že `free()` musí být schopen zpracovat vysoce zarovnané přidělení.

<a name="note_rem"></a>__rem__ Funkce odebrané při zadání možnosti kompilátoru [/std:c++17](../build/reference/std-specify-language-standard-version.md) (nebo [/std:c++latest).](../build/reference/std-specify-language-standard-version.md) Tyto funkce lze znovu povolit, aby se usnadnil přechod na novější `_HAS_AUTO_PTR_ETC` `_HAS_FUNCTION_ALLOCATOR_SUPPORT`jazykové `_HAS_OLD_IOSTREAMS_MEMBERS`režimy pomocí těchto maker: , , , a `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ `from_chars()` `to_chars()` a jsou k dispozici pro celá čísla. Časová osa `from_chars()` pro plovoucí `to_chars()` a plovoucí desetinnou desetinnou desetinnou desetinnou se zobrazí takto:

- VS 2017 15.7: `from_chars()` Celé `to_chars()`číslo a .
- VS 2017 15.8: `from_chars()`Plovoucí bod .
- VS 2017 15.9: `to_chars()` Přetížení s plovoucí desetinnou čárkou pro nejkratší desetinné číslo.
- VS 2019 16.0: `to_chars()` Přetížení s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou se kondenzomem.
- VS 2019 16.2: `to_chars()` Přetížení s plovoucí desetinnou desetinnou desetinnou desetinnou a přesnou a přesnou vědeckou.
- VS 2019 16.4: Přetížení `to_chars()` s plovoucí desetinnou desetinnou tázkem pro přesnost obecné.

<a name ="note_parallel"></a>__paralelní__ Knihovna paralelních algoritmů jazyka C++17 je dokončena. Complete neznamená, že každý algoritmus je paralelizován v každém případě. Nejdůležitější algoritmy byly paralelizovány a podpisy zásad provádění jsou k dispozici i v případě, že algoritmy nejsou paralelizovány. Centrální interní hlavička naší implementace, yvals_core.h, obsahuje následující "Poznámky paralelních algoritmů": C++ umožňuje implementaci paralelních algoritmů jako volání sériových algoritmů. Tato implementace paralelizuje několik běžných volání algoritmu, ale ne všechny.

Následující algoritmy jsou paralelizovány:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Následující nejsou v současné době paralelizovány:

- Žádné znatelné zlepšení výkonu paralelismu na cílovém hardwaru; všechny algoritmy, které pouze kopírují nebo permutují prvky bez větví, jsou obvykle omezeny šířkou pásma paměti:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Nejasnosti ohledně požadavků na paralelismus uživatele existují; pravděpodobně ve výše uvedené kategorii stejně:
  - `generate`, `generate_n`
- Efektivní paralelismus, u kterého existuje podezření, že je neproveditelný:
  - `partial_sort`, `partial_sort_copy`
- Dosud nevyhodnocena; paralelismus může být zaveden v budoucím uvolnění a je podezření, že je přínosný:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)\
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)\
[Vylepšení shody jazyka C++ v sadě Visual Studio](cpp-conformance-improvements.md)\
[Co je nového pro Visual C++ v Visual Studiu](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ historie změn 2003 až 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Visual C++ Co je nového v letech 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[Blog týmu C++](https://devblogs.microsoft.com/cppblog/)
