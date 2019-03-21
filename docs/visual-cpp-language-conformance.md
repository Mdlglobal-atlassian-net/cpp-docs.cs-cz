---
title: Shoda jazyka Visual C++
ms.date: 11/15/2017
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: db2feac37ace8e90a893aac2b663a6a45baae516
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278564"
---
# <a name="visual-c-language-conformance"></a>Shoda jazyka Visual C++

Toto téma shrnuje ISO C ++ 03, C ++ 11, C ++ 14, C ++ 17 a koncept C ++ 20 jazyk shoda se standardy funkce kompilátoru a standardní knihovna funkcí pro kompilátor jazyka C++ v sadě Visual Studio 2017 a dřívějších verzích. Každý kompilátor a standardní knihovny funkce název odkazy na standardu ISO C++ papíru návrh, který popisuje funkci, pokud je k dispozici v době publikace. Podporované sloupec uvádí verze sady Visual Studio, ve které podporují, pro funkci se poprvé objevil.

Podrobnosti o vylepšení a jiné změny v sadě Visual Studio 2017 najdete v tématu [vylepšení shody C++ v sadě Visual Studio 2017](cpp-conformance-improvements-2017.md) a [co je nového v jazyce Visual c++ v sadě Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md). Změny přizpůsobení v dřívějších verzích, najdete v části [historie změn Visual C++](porting/visual-cpp-change-history-2003-2015.md) a [Visual C++ co na nový 2003 – 2015](porting/visual-cpp-what-s-new-2003-through-2015.md). Aktuální novinky od týmu, C++, přejděte [blogu týmu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

> [!NOTE]
> Neexistují žádná binární rozbíjející změny mezi Visual Studio 2015 a Visual Studio 2017.

## <a name="compiler-features"></a>Funkce kompilátoru

|Oblast funkcí| |
|----|---|
|__C ++ 03/11 základní funkce jazyka__|__Podporuje se__|
|&nbsp;&nbsp;Všechno ostatní|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Dvoufázové vyhledávání názvů|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 Expression SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[Preprocesor C99 N1653](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Partial <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[N1988 rozšířené celočíselné typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|NENÍ K DISPOZICI <sup> [E](#note_E)</sup>|
|__C ++ 14 základní funkce jazyka__|__Podporuje se__|
|&nbsp;&nbsp;[N3323 Tweaked formulace pro kontextové převody](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 binární literály:](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[Automaticky N3638 a decltype(auto) návratové typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init zachycení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 obecné výrazy lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[Atribut N3760 [[deprecated]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 velikostí dealokace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[Oddělovače číslic N3781](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 variabilní šablony](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[Rozšířené N3652 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 Nsdmi pro agregace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 Jak se vyhnout virům/znamená začlenění přidělení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|NENÍ K DISPOZICI <sup> [F](#note_F)</sup>|
|__C ++ 17 základní funkce jazyka__|__Podporuje se__|
|&nbsp;&nbsp;[Odebrání N4086 trigraphs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 nová pravidla pro automatické s braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 typename v šabloně parametrů šablony](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Atributy N4266 pro obory názvů a enumerátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 u8 znakové literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Vnořené N4230 definice oboru názvů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Stručný N3928 static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Generalizované P0184R0 založený na rozsahu – smyčky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 atribut [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0001R1 register – klíčové slovo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0002R1 operator ++ pro bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zachytávání P0018R3 * tím, že hodnota](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 pomocí atributu obory názvů bez opakování](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 Direct seznam init pevné výčtů od celých čísel](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Výrazy lambda P0170R1 constexpr.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 atribut [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 atribut [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 strukturovaných vazeb](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[If constexpr P0292R2 – příkazy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[Příkazy výběru P0305R1 s inicializátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Literálů P0245R1 Hexfloat](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Povolení N4268 další argumenty šablony bez typu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Výrazy N4295 Fold](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0003R5 dynamic--specifikace výjimek](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Přidání P0012R1 noexcept systém typů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 nadbytečně zarovnané dynamické přidělování paměti](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 vložené proměnné](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 odpovídající šablonu – parametry šablony na kompatibilní argumenty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0036R0 některé prázdný unární složení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Oprava N4261 převodů kvalifikace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7  <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Rozšířené P0017R1 inicializace agregace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7  <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Odvození argumentu šablony P0091R3 pro šablony třídy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[Problémy odvození argumentu šablony P0512R0 třídy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Parametry šablony bez typu deklarace P0127R2 pomocí automatického](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zaručené P0135R1 elize kopírování](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6<sup>[H](#note_H)</sup>|
|&nbsp;&nbsp;[P0136R1 přeformulování dědění konstruktorů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Upřesnění P0145R3 pořadí vyhodnocování výrazů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 pořadí vyhodnocování argumentů funkce](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 rozšíření balíčků v deklaracích using-](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 ignoruje se nerozpoznaný atributy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|

|Oblast funkcí| |
|----|---|
|__C ++ 17 základních funkcí jazyka (zprávy o chybách)__|__Podporuje se__|
|&nbsp;&nbsp;[Oprava P0702R1 třídy odvození argumentu šablony pro konstruktory seznam inicializátorů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Zjednodušení P0588R1 zachycení lambdy implicitní](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Ne|
|&nbsp;&nbsp;[CWG 1581: Když jsou definovány členské funkce constexpr.](https://wg21.cmeerw.net/cwg/issue1581)|Ne|
|&nbsp;&nbsp;[P0962R1 uvolnit přizpůsobení strukturovaných vazeb bodu pravidla hledání](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|Ne|
|&nbsp;&nbsp;[P0962R2 uvolnit rozsahu-pro přizpůsobení bod smyčky hledání pravidla](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Ne|
|&nbsp;&nbsp;[Povolení P0969R0 strukturované vazby přístupní členové](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|Ne|

|Oblast funkcí| |
|----|---|
|__20 základní funkce jazyka c ++__|__Podporuje se__|
|&nbsp;&nbsp;[Přidání P0306R4 &#95; &#95;VA_OPT&#95; &#95; pro vynechání čárkami a odstranění čárkami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0306r4.html)|Ne|
|&nbsp;&nbsp;[Určený P0329R4 inicializace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|Ne|
|&nbsp;&nbsp;[Povolení P0409R2 lambda-capture [=, tato]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|Ne|
|&nbsp;&nbsp;[P0428R2 známou syntaxi šablony pro obecné výrazy lambda](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Ne|
|&nbsp;&nbsp;[Výchozí P0683R1 inicializátory členů pro bitová pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|Ne|
|&nbsp;&nbsp;[Oprava P0704R1 const l-hodnoty kvalifikaci ref ukazatelů na členy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|Ne|
|&nbsp;&nbsp;[P0734R0 Concepts](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|Ne|

## <a name="standard-library-features"></a>Funkce standardní knihovny

|Oblast funkcí| |
|---|---|
|__Funkce c ++ 20 standardní knihovny__|__Podporuje se__|
|&nbsp;&nbsp; [P0777R1, jak se vyhnout zbytečným Decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Ne|
|&nbsp;&nbsp;[P0674R1 make_shared() pro pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Ne|
|&nbsp;&nbsp;[Požadavky na Constexpr iterátor P0858R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Porovnání P0809R0 neuspořádaná kontejnery](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 atomic\<float >, atomické\<double >, atomické\<long double >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Ne|
|&nbsp;&nbsp; [P0053R7 \<syncstream >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp; [P0753R2 osyncstream manipulátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Ne|
|&nbsp;&nbsp; [P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Ne|
|&nbsp;&nbsp; [P0202R3 constexpr pro \<algoritmus > a Exchange():](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Ne|
|&nbsp;&nbsp; [P0355R7 \<chrono > kalendáře a časových pásem](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Ne|
|&nbsp;&nbsp; [P0415R1 constexpr pro \<komplexní > (znovu)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Ne|
|&nbsp;&nbsp; [Memory_order třídy výčtu P0439R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Ne|
|&nbsp;&nbsp; [P0457R2 starts_with()/ends_with() pro basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|Ne|
|&nbsp;&nbsp; [P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|Ne|
|&nbsp;&nbsp; [P0551R3 Zvu tě Shalt není Specialize šablony funkce std!](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf)|Ne|
|&nbsp;&nbsp; [P0600R1 \[ \[nodiscard\] \] pro STL, část 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Ne|
|&nbsp;&nbsp; [Pomocí P0616R0 move() v \<číselné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Ne|
|&nbsp;&nbsp; [P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Ne|
|&nbsp;&nbsp; [P0718R2 atomic\<shared_ptr\<T >>, atomické\<weak_ptr\<T >>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Ne|
|&nbsp;&nbsp; [P0754R2 \<verze >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Ne|
|&nbsp;&nbsp; [Is_pod – P0767R1 ukončení podpory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Ne|
|&nbsp;&nbsp; [Podpora knihovny P0768R1 pro operátor porovnání kosmické lodě \<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Ne|
|&nbsp;&nbsp; [P0966R1 řetězec:: reserve() by měl není zmenšit.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html)|Ne|
|__Funkce c ++ 17 standardní knihovny__|__Podporuje se__|
|&nbsp;&nbsp;[Integrace P0433R2 odvození šablony pro šablony třídy do standardní knihovny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[Zlepšení P0739R0 třídy šablony argument odvození integrace do standardní knihovny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 constexpr pro char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0220R1 Library Fundamentals V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6 <sup>[J](#note_J)</sup>|
|&nbsp;&nbsp;[Převody P0067R5 základní řetězec](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup> [charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<memory_resource >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[Odstraňuje se P0337R0 polymorphic_allocator přiřazení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0024R2 paralelní algoritmy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[Paralelní provádění pro přejmenování P0336R1 zásady](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[Paralelní algoritmy P0394R4 terminate() měli pro výjimky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[Sjednotit P0452R1 \<číselné > paralelní algoritmy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[Matematické funkce speciální P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 relativní cesty k systému souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[Položka adresáře P0317R1 ukládání do mezipaměti pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br />&nbsp;&nbsp;[Podpora P0392R0 string_view v systému souborů cesty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 podpůrné systémy – specifikace POSIX](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 komentáře NB řešení pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 odebrání specifikace dynamických výjimek](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[Opravy P0358R1 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Enable_shared_from_this – P0033R1 přeformulování](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0083R3 spojení map a sad](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[Ujasnění P0508R0 insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 vyřazení zbytkových součástí knihovny částí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Std::function P0302R1 odebrání Allocator podpory v](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[Oprava P0497R0 shared_ptr pro pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Ukončení podpory pro P0521R0 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 vložené proměnné pro standardní knihovnu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Ukončení podpory pro P0618R0 \<codecvt – >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Library Fundamentals: Boyer Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 stanovení vyhledávač návratové typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 constexpr pro \<pole > (znovu) a \<iterátor >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0040R3 rozšíření paměti nástroje pro správu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 emplace – návratový typ.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size atd.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Přejmenování Variadické P0156R2 Zámek\_ochranu do oboru\_zámku](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup> [17](#note_17), [bajtů](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 UDL pro \<string_view > ("meow" sv atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Memory_order atomické compare_exchange P0418R2 požadavky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Common_type – P0435R1 Overhauling](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[Úprava P0548R1 běžné\_typ a doba trvání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 constexpr pro \<chrono > (znovu)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Hodnota hash P0513R0 (Cache poisoning)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[Hodnota hash P0599R1 noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Označení P0516R0 shared_future – kopírování jako noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Vytváření P0517R0 future_error z future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Řešení atomic P0558R1<T> s názvem nekonzistence třídy Base](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Změna P0604R0 je\_volatelná aplikacemi nebo výsledky\_z k vyvolání\_výsledek, ale není\_nevyvolatelný, je\_nothrow\_nevyvolatelný](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<algoritmus > sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<žádné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<volitelné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<string_view >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<řazené kolekce členů > apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 homogenní rozhraní pro typ variant/any nebo volitelné](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<typ variant >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Integrace P0254R2 string_view a std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 provádění volitelné větší rovná znovu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Varianty větší rovná P0393R3 provádění](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[Přehodnocení P0504R0 in_place_t/in_place_type_t\<T > / in_place_index_t\<můžu >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[Odmítnutí P0510R0 varianty z nic, pole, odkazy a neúplných typů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[Zlepšení N4387 pár a řazené kolekce členů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Odebrání P0004R1 zastaralé Iostreams Aliases](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup> [rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 proměnné šablony pro typové vlastnosti (is_same_v atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 logický operátor typové vlastnosti (spojení atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono > floor() ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Lock_guard – P0156R0 Variadické](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 Safe Conversions In unique_ptr\<T[]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Odebrání N4190 auto_ptr, random_shuffle() a staré \<funkční > věci](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[Noexcept N4258 čištění](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Reference_wrapper N4277 Triviálně Kopírovatelné –](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() pro map/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Unique_ptr N4366 přesně omezení přiřazení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[Standardní knihovna P0063R3 C11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 podpora nekompletní typy ve vektoru/list/forward_list –](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|__Funkce c ++ 14 standardní knihovny__|__Podporuje se__|
|&nbsp;&nbsp;[Result_of – N3462 přívětivá SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr pro \<komplexní >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr pro \<chrono >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr pro \<pole >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr For \<initializer_list>, \<tuple>, \<utility>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDL pro \<chrono >, \<řetězec > (1729ms, "meow" s atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Null dopředných iterátorů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[QUOTED(): N3654](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Heterogenní asociativní vyhledávání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (časované)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[Exchange() N3668:](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[Oprava N3669 constexpr členské funkce bez const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 EQUAL() equal(), is_permutation() a mismatch()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Velikostí Dealokace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDL pro \<komplexní > (3.14i, atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr pro \<funkční >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 alias typu tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[Přejmenování N3891 shared_mutex (časované) shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Požadavky na Element minimální kontejneru](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[Transparentní Funktory operátorů N3421 (méně\<> atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Alias šablony pro \<type_traits > (decay_t, atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 Odradit rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|Není k dispozici|

Skupina Paper uvedené společně označuje, že funkce byla prosazena do standardu a potom jeden nebo více papírů zlepšit nebo rozšířit tuto funkci také odhlasování. Tyto funkce jsou implementované společně.

### <a name="supported-values"></a>Podporované hodnoty

__Ne__ znamená, že ještě nebyla implementována.<br/>
__Částečné__ znamená, že implementace v sadě Visual Studio 2017 je neúplná. Další podrobnosti najdete v části poznámky.<br/>
__Není k dispozici__ znamená, že návrh Paper popisují funkce. Tyto doklady změnit jazyk standardní, ale veškeré pracovní pro implementátory nevytvořili. Jsou uvedeny zde pro úplnost.<br/>
__VS 2010__ určuje funkce, které jsou podporovány v sadě Visual Studio 2010.<br/>
__VS 2013__ určuje funkce, které jsou podporovány v sadě Visual Studio 2013.<br/>
__VS 2015__ určuje funkce, které jsou podporovány v sadě Visual Studio 2015 RTM.<br/>
__VS 2015.2__ a __VS 2015.3__ označení funkce, které jsou podporovány v aplikaci Visual Studio 2015 Update 2 a Visual Studio 2015 Update 3, v uvedeném pořadí.<br/>
__VS 2017__ určuje funkce, které jsou podporovány v sadě Visual Studio 2017 RTM.<br/>
__VS 2017 15.3__ určuje funkce, které jsou podporovány v sadě Visual Studio 2017 verze 15.3.<br/>
__VS 2017 15.5__ určuje funkce, které jsou podporovány v sadě Visual Studio 2017 verze 15.5.<br/>
__VS 2017 15.7__ určuje funkce, které jsou podporovány v sadě Visual Studio 2017 verze 15.7.<br/>

### <a name="notes"></a>Poznámky

<a name="note_A"></a>__A__ v/std: c ++ 14 režimu, zůstane neimplementovaná specifikace dynamických výjimek a throw() je stále považovány za synonymum pro \_ \_declspec(nothrow). V C ++ 17, byla specifikace dynamických výjimek většinou odstraněna P0003R5, ponechat jeden vestige: throw(), je zastaralé a chovat jako synonymum pro noexcept. V/std: c ++ 17 režimu MSVC nyní odpovídá standardu zadáním throw() stejné chování jako noexcept, například vynucení prostřednictvím ukončení.

Možnost kompilátoru /Zc:noexceptTypes-požadavky našich staré chování \_ \_declspec(nothrow). Je pravděpodobné, že throw() se odebere v C ++ 20. Abychom vám pomohli s migrací kódu v reakci na tyto změny standardní a naše implementace nová upozornění kompilátoru problémů specifikace výjimek byly přidány pod **/std: c ++ 17** a **/permissive-**.

<a name="note_B"></a>__B__ podporované v /permissive-mode v sadě Visual Studio 2017 verze 15.7. Zobrazit [jde o název pro dvoufázové vyhledávání podpory MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) Další informace.

<a name="note_C"></a>__C__ kompilátoru podpora sfinae u výrazů byla dostatečná pro standardní knihovnu od verze Visual Studio 2015 Update 2. Podporované ve verzi Visual Studio 2017 15.7 bez ohledu na to, zda /permissive-mode nastavena. Zůstanou některé chyby opravit. Alternativní řešení "jedinečný značku typu" již není nezbytné a odebrali jsme toto řešení od našich implementace STL.

<a name="note_D"></a>__D__ neúplná podporu kompilátoru pro preprocesor C99 pravidla v sadě Visual Studio 2017. Variadická makra jsou podporované, ale existuje mnoho chyb v chování bude preprocesor.  Jsme jsou overhauling preprocesoru a experimentálně plánujeme tyto změny v rámci **/ permissive-** brzy režimu.

<a name="note_E"></a>__Elektronické__ to je označen jako není k dispozici, protože kompilátory jsou povolené, ale není nutné pro podporu rozšířené celočíselné typy.  Stejně jako GCC a Clang jsme zvolili není pro jejich podporu.

<a name="note_F"></a>__F__ podobně, to je označen jako není k dispozici protože kompilátory jsou povolené, ale není nutné implementovat tyto optimalizace.

<a name="note_G"></a>__G__ podporované v rámci [/std: c ++ 14](./build/reference/std-specify-language-standard-version.md) suppressible upozornění.

<a name="note_J"></a>__J__ funkce, které nebyly dokončeny v sadě Visual Studio 2015 jsou rozdělená jinde v této tabulce.

<a name="note_K"></a>__K__ to je úplně nové implementaci, nekompatibilní s předchozí verzí std::experimental vyžadovaných symlink podpory, opravy chyb a změny v chování vyžaduje standard. V současné době včetně \<systému souborů > poskytuje nové std::filesystem a předchozí std::experimental::filesystem a včetně \<experimentální/filesystem > poskytuje pouze původní experimentální implementaci. ODEBERE experimentální implementace v další vydané verzi ABI ukončování knihoven.

<a name="note_L"></a>__L__ vnitřní kompilátor nepodporuje.

<a name="note_14"></a>__14__ tyto 17/20 funkce C ++ jsou vždy povoleny, i v případě [/std: c ++ 14](build/reference/std-specify-language-standard-version.md) (výchozí nastavení) je definováno. Je to způsobeno funkce byla implementována před zavedením **/std** možnosti, nebo protože podmíněné implementace bylo by složité.

<a name="note_17"></a>__17__ tyto funkce jsou povolené [/std: c ++ 17](./build/reference/std-specify-language-standard-version.md) (nebo [/std: c ++ nejnovější](./build/reference/std-specify-language-standard-version.md)) – možnost kompilátoru.

<a name="note_byte"></a>__bajtů__ `std::byte` zajišťuje [/std: c ++ 17](./build/reference/std-specify-language-standard-version.md) (nebo [/std: c ++ nejnovější](./build/reference/std-specify-language-standard-version.md)), ale vzhledem k tomu, že ji může dojít ke konfliktu se záhlavím Windows SDK v některých případech, má podrobných – makro odhlásit. Je možné ho zakázat tak, že definujete `_HAS_STD_BYTE` jako `0`.

<a name="note_C11"></a>__C11__ části C11 standardní knihovny, které jsou vyžadované C ++ 17, s výjimkou C99 implementován Universal CRT `strftime()` jen pro čtení E alternativní převod specifikátory C11 `fopen()` výhradním režimu a C11 `aligned_alloc()`. Je nepravděpodobné, že by k implementaci, protože zadaný C11 `aligned_alloc()` způsobem, který není kompatibilní s implementací Microsoft `free()`, jmenovitě, který `free()` musí být schopna zpracovávat vysoce zarovnané přidělení.

<a name="note_rem"></a>__rem__ odebrané, kdy [/std: c ++ 17](./build/reference/std-specify-language-standard-version.md) (nebo [/std: c ++ nejnovější](./build/reference/std-specify-language-standard-version.md)) je zadána možnost kompilátoru. Tyto funkce mají odhlásit makra: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`, a `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ from_chars() a to_chars() jsou k dispozici pro celá čísla. Aktuálně pracujeme na s plovoucí desetinnou čárkou from_chars() následovat to_chars() s plovoucí desetinnou čárkou.

<a name ="note_parallel"></a> __paralelní__ paralelní algoritmy knihovny C ++ 17. dokončení. Všimněte si, že to ale neznamená, že je každý algoritmus paralelizovaná v každém případě; Nejdůležitější algoritmy mají paralelizována. a spuštění zásady podpisy jsou k dispozici i kde nejsou paralelizovaná algoritmy. Centrální hlavička interní implementace naše STL yvals.h, obsahuje následující "paralelní algoritmy poznámky": Jazyk C++ umožňuje implementaci provádět paralelní algoritmy jako volání sériového portu algoritmy.   Tato implementace parallelizes několik běžných volání algoritmu, ale ne pro všechny.

Tyto algoritmy jsou paralelizovaná:

- adjacent_difference adjacent_find, all_of, any_of, count, count_if, stejné, exclusive_scan, hledání, find_end –, find_first_of, find_if, for_each, for_each_n, inclusive_scan, neshoda, none_of, snížit, odebrání, remove_if –, vyhledávání, search_n –, řazení, stable_ řazení, transform_exclusive_scan, transform_inclusive_scan, transform_reduce transformace.

Následující není paralelizovaná v současné době:

- Žádná zlepšení výkonu zřejmý paralelismu na cíl hardware. Všechny algoritmy, které pouze zkopírujte nebo permute – prvky s žádné větve jsou obvykle omezená šířka pásma paměti:
  - kopírování, copy_backward, copy_n, výplň, fill_n, přesunutí, move_backward, odebrat, remove_if –, nahradit, replace_if, zpětné, reverse_copy, otáčet, rotate_copy, swap_ranges –
- Existuje záměně přes požadavky uživatelů paralelismu pravděpodobně do této kategorie přesto:
  - Generovat generate_n
- Efektivní paralelismu podezření, že se neřešitelné:
  - partial_sort, partial_sort_copy
- Ještě není vyhodnocen; paralelismus mohou být implementovány v budoucí verzi a by mohlo být užitečné:
  - copy_if, zahrnuje, inplace_merge, is_heap, is_heap_until –, is_partitioned, is_sorted, is_sorted_until –, lexicographical_compare –, max_element, sloučení, min_element, minmax_element, nth_element, partition_copy –, remove_copy, remove_copy_if, replace_ kopírování, replace_copy_if, set_difference –, set_intersection –, set_symmetric_difference –, set_union –, stable_partition –, jedinečné, unique_copy –

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](standard-library/cpp-standard-library-reference.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio 2017](cpp-conformance-improvements-2017.md)<br/>
[Novinky v jazyce Visual C++ v sadě Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historie změn Visual C++ 2003 – 2015](porting/visual-cpp-change-history-2003-2015.md)<br/>
[Novinky Visual C++ 2003–2015](porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Blog týmu Visual C++](https://blogs.msdn.microsoft.com/vcblog/)
