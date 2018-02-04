---
title: Shoda jazyka Visual C++ | Microsoft Docs
ms.date: 11/15/2017
ms.technology:
- cpp-language
ms.topic: article
dev_langs:
- C++
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 49aabbcc746470815db40f15fa00774d5e05bfe5
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="visual-c-language-conformance"></a>Shoda jazyka Visual C++

Toto téma shrnuje ISO C ++ 03, C ++ 11, C ++ 14, C ++ 17 a konceptu C ++ 20 jazyk standardy shoda kompilátoru funkce a funkce standardní knihovny pro kompilátor C++ ve Visual Studio 2017 a starší verze. Každý kompilátoru a standardní knihovny funkce název odkazy na standardní C++ ISO papíru návrh, který popisuje funkci, pokud je k dispozici v době publikace. Podporované sloupec uvádí verzi sady Visual Studio, ve které podporu pro funkci se poprvé objevil.

Podrobnosti o shoda vylepšení a jiné změny ve Visual Studio 2017 najdete v tématu [C++ shoda vylepšení v nástroji Visual Studio 2017](cpp-conformance-improvements-2017.md) a [co je nového pro Visual C++ v aplikaci Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md). Shoda změny v dřívějších verzích, najdete v části [historie změn Visual C++](porting/visual-cpp-change-history-2003-2015.md) a [Visual C++ Co je nového 2003 až 2015](porting/visual-cpp-what-s-new-2003-through-2015.md). Aktuální informace od týmu C++, najdete [blogu týmu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

> [!NOTE]
> Neexistují žádné binární nejnovější změny mezi Visual Studio 2015 a Visual Studio 2017.

## <a name="compiler-features"></a>Funkce kompilátoru

|Oblast funkcí| |
|----|---|
|__C ++ 11. 03 základní jazykové funkce__|__Podporované__|
|&nbsp;&nbsp;Všem ostatním|VS 2015 <sup> [A](#note_A)</sup>|
|&nbsp;&nbsp;Vyhledání dvoufázového názvu|Částečné <sup> [B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 Expression SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|Částečné <sup> [C](#note_C)</sup>|
|&nbsp;&nbsp;[N1653 C99 preprocesoru](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Částečné <sup> [D](#note_D)</sup>|
|&nbsp;&nbsp;[Rozšířené N1988 typy celého čísla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|NENÍ K DISPOZICI <sup> [E](#note_E)</sup>|
|__C ++ 14 základní jazykové funkce__|__Podporované__|
|&nbsp;&nbsp;[N3323 Tweaked slov pro kontextové převody](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[Binární N3472 literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[Automaticky N3638 a decltype(auto) návratové typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[Init – N3648-zachycení snímku](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[Obecné N3649 lambdas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[[[Zastaralé]] N3760 atribut](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[Zrušení přidělení N3778 s nastavenou velikostí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[Oddělovače N3781 číslice](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 proměnných šablony](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[Rozšířené N3652 constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 NSDMIs pro agregace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 Jak se vyhnout virům nebo znamená začlenění přidělení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|NENÍ K DISPOZICI <sup> [F](#note_F)</sup>|
|__C ++ 17 základní jazykové funkce__|__Podporované__|
|&nbsp;&nbsp;[Odebrání N4086 trigraph](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 nová pravidla pro automatické s braced seznamy init](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Typename N4051 v šabloně parametry šablony](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Atributy N4266 pro obory názvů a výčty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 u8 znakové literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Vnořené N4230 definice oboru názvů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Ve formátu Terse zasílaná N3928 static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 zobecněn na základě rozsahu pro – smyčky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 atribut [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 odebrání registrace klíčové slovo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0002R1 operator ++ pro bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Zaznamenání P0018R3 * to podle hodnoty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Pomocí P0028R4 atribut obory názvů bez opakování](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 Direct seznamu init pevné výčtů z celých čísel](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 constexpr lambdas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 atribut [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 atribut [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Strukturované P0217R3 vazby](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Pokud constexpr P0292R2 – příkazy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup> [G](#note_G)</sup>|
|&nbsp;&nbsp;[Příkazy výběru P0305R1 s inicializátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Hexfloat literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Povolení N4268 další šablony bez typu argumentů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Fold – N4295 výrazy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0003R5 dynamické--specifikace výjimek](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Přidání P0012R1 noexcept systém typů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 přepsání zarovnaný dynamické přidělování paměti](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 vložené proměnné](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Odpovídající P0522R0 šablony parametry šablony k kompatibilní argumentů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Odebrání P0036R0 některé prázdný unární složení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Oprava N4261 kvalifikace převody](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|Ne|
|&nbsp;&nbsp;[Rozšířené P0017R1 inicializace agregace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|Ne|
|&nbsp;&nbsp;[Odvození argumentu šablony P0091R3 pro šablony třídy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[Problémy odvození argumentu šablony P0512R0 – třída](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|Ne|
|&nbsp;&nbsp;[P0127R2 deklarace parametry šablon bez typu s automatickým](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|Ne|
|&nbsp;&nbsp;[Zaručit P0135R1 elision kopie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|Ne <sup> [H](#note_H)</sup>|
|&nbsp;&nbsp;[P0136R1 rozdělit dědění konstruktory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|Ne|
|&nbsp;&nbsp;[Upřesnění P0145R3 pořadí vyhodnocení výrazu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 pořadí vyhodnocení argumenty funkce](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|Ne|
|&nbsp;&nbsp;[Rozšíření P0195R2 Pack v pomocí deklarace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|Ne|
|&nbsp;&nbsp;[P0283R2 ignoruje se nerozpoznaný atributy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|Ne|
|&nbsp;&nbsp;[Oprava P0702R1 třída odvození argumentu šablony pro ctors inicializátoru seznamu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0702r1.html)|Ne|
|__Funkce jazyka 20 jader c ++__|__Podporované__|
|&nbsp;&nbsp;[Přidání P0306R4 &#95; &#95; VA_OPT &#95; &#95; pro vynechání čárkami a odstranění čárkami](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0306r4.pdf)|Ne|
|&nbsp;&nbsp;[Určený P0329R4 inicializace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|Ne|
|&nbsp;&nbsp;[Povolení P0409R2 lambda zachycení [=, to]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|Ne|
|&nbsp;&nbsp;[P0428R2 známé syntaxe šablony pro obecné lambdas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Ne|
|&nbsp;&nbsp;[P0683R1 výchozí inicializátory člena pro bitová pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|Ne|
|&nbsp;&nbsp;[Oprava P0704R1 const lvalue kvalifikovaný ref ukazatelé na členy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|Ne|
|&nbsp;&nbsp;[Koncepty P0734R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|Ne|


## <a name="standard-library-features"></a>Funkce standardní knihovny

|Oblast funkcí| |
|---|---|
|__Funkce c ++ 20 standardní knihovny__|__Podporované__|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Ne|
|&nbsp;&nbsp;[P0674R1 make_shared() pro pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Ne|
|__Funkce c ++ 17 standardní knihovny__|__Podporované__|
|&nbsp;&nbsp;[Integrace P0433R2 odvození šablony pro šablony třídy do standardní knihovny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[Vylepšení P0739R0 – třída argument odvození integraci šablony do standardní knihovny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|Ne|
|&nbsp;&nbsp;[P0426R1 constexpr For char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|Ne|
|&nbsp;&nbsp;[Hypot – P0030R1 (x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|Ne|
|&nbsp;&nbsp;[P0220R1 knihovny základy V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|Částečné <sup> [J](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 základní řetězec převody](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|Ne|
|&nbsp;&nbsp;[N4562 Základy knihovny: \<memory_resource >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[Odstranění P0337R0 polymorphic_allocator přiřazení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|Ne|
|&nbsp;&nbsp;[Paralelní algoritmy P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 přejmenování paralelní zpracování zásad](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[Paralelní algoritmy P0394R4 terminate() měli pro výjimky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1 sjednotit \<číselné > paralelní algoritmy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|Ne|
|&nbsp;&nbsp;[Matematické funkce speciální P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|Ne|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 relativní cesty k systému souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[Záznam adresáře P0317R1 ukládání do mezipaměti pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p03179r1.html)<br />&nbsp;&nbsp;[Podpora P0392R0 string_view v cestách souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 podpora jiných POSIX systémy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 komentáře NB řešení pro systém souborů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|Ne <sup> [kB](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 odebrání specifikace dynamické výjimek](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 Fixes For not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0033R1 Rewording enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0083R3 splétání mapuje a nastaví](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0, které toto vyjasňují insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 místo začne Vestigial knihovny částí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Std::function P0302R1 odebrání Allocator podpory v](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[Oprava P0497R0 shared_ptr pro pole](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Místo začne P0521R0 shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Vložené proměnné P0607R0 standardní knihovny](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Místo začne P0618R0 \<codecvt – >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|2017 VS 15,5 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Základy knihovny: Boyer Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 opravě osobou hledající návratové typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 constexpr pro \<pole > (opětovně) a \<iterator >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Nástroje pro správu P0040R3 rozšíření paměti](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Emplace P0084R2 – návratový typ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, etc.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Přejmenování Variadická P0156R2 zámku\_guard do oboru\_zámku](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r2.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup> [L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup> [17](#note_17), [bajtů](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 UDLs pro \<string_view > ("meow" sv atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[Memory_order P0418R2 atomic compare_exchange – požadavky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Common_type P0435R1 Overhauling](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[Postupně je upravujte P0548R1 běžné\_typ a doba trvání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 constexpr pro \<typu chrono > (opětovně)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[P0513R0 Poisoning hash](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[Hodnota hash noexcept P0599R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Označení P0516R0 shared_future kopírování jako noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Vytváření P0517R0 future_error z future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 řešení atomic<T> s názvem nekonzistence Base – třída](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Změna P0604R0 je\_volatelná aplikacemi nebo výsledky\_z k vyvolání\_dojít, je\_invocable, je\_nothrow\_invocable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup> [17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Základy knihovny: \<algoritmus > sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Základy knihovny: \<žádné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Základy knihovny: \<volitelné >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017|
|&nbsp;&nbsp;[N4562 Základy knihovny: \<string_view >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 Základy knihovny: \<řazené kolekce členů > apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[Rozhraní pro homogenní P0032R3 variant/any/volitelný](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Integrace P0254R2 string_view a std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 provádění volitelné větší rovná znovu](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[Provádění P0393R3 Variant větší rovná](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[Opětovné návštěvy P0504R0 in_place_t/in_place_type_t\<T > nebo in_place_index_t\<I >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[Odmítat P0510R0 variant z nic, pole, odkazy a neúplné typy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[Vylepšení N4387 pár a řazené kolekce členů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Odebrání P0004R1 zastaralé Iostreams Aliases](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup> [rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 proměnných šablony pro typové vlastnosti (is_same_v atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 logický operátor typové vlastnosti (spojení, atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Owner_less – P0074R0\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<typu chrono > floor(), ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Variadická P0156R0 lock_guard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Převody v nouzovém N4089 unique_ptr\<[T] >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Invoke N4169](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Odebrání N4190 auto_ptr, random_shuffle() a starý \<funkční > vlastní položky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup> [rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 noexcept uvolnění](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Reference_wrapper – N4277 Trivially kopírovatelná](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() pro mapu/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Unique_ptr N4366 přesněji chovaly přiřazení](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup> [14](#note_14)</sup>|
|&nbsp;&nbsp;[Standardní knihovna C11 P0063R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 podpora neúplné typy v vektoru nebo seznamu nebo forward_list –](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup> [14](#note_14)</sup>|
|__Funkce c ++ 14 standardní knihovny__|__Podporované__|
|&nbsp;&nbsp;[Result_of N3462 podporou sfinae u výrazů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr pro \<komplexní >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr pro \<typu chrono >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr pro \<pole >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr pro \<initializer_list >, \<řazené kolekce členů >, \<nástroj >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDLs pro \<typu chrono >, \<řetězec > (1729ms, "meow" s atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Null dopředného iterátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Heterogenní asociativní vyhledávání](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (časované)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[Oprava N3669 constexpr členské funkce bez const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T >)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 Dual-Range equal(), is_permutation(), mismatch()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Zrušení přidělení velikostí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDLs pro \<komplexní > (3.14i, atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr pro \<funkční >](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[Přejmenování N3891 shared_mutex (časované) shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Požadavky na Element minimální kontejneru](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[Operátor Functors transparentní N3421 (méně\<> atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Alias šablony pro \<type_traits > (decay_t, atd.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 Odradit rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|Není k dispozici|

Skupiny plánů uvedené společně označuje, že byla funkce hlasováno do standardní a pak byly také hlasováno jeden nebo více dokumenty Paper vylepšit nebo rozšířit tuto funkci. Tyto funkce jsou implementované společně.

### <a name="supported-values"></a>Podporované hodnoty

__Ne__ znamená ještě nebyla implementována.  
__Částečné__ znamená implementace ve Visual Studio 2017 je nekompletní. Další podrobnosti naleznete v části poznámky.  
__Není k dispozici__ znamená dokumenty návrh Paper popisují funkce. Tyto dokumenty Paper změnit jazyk standardní, ale nevytvořili veškerou práci pro implementátory informačních technologií. Jakém jsou uvedeny zde pro úplnost.  
__VS 2010__ určuje funkce, které jsou podporovány v sadě Visual Studio 2010.  
__VS 2013__ určuje funkce, které jsou podporovány v sadě Visual Studio 2013.  
__VS 2015__ určuje funkce, které jsou podporovány v aplikaci Visual Studio 2015 RTM.  
__VS 2015.2__ a __VS 2015.3__ označit součásti, které jsou podporovány v sadě Visual Studio 2015 Update 2 a Visual Studio 2015 Update 3, v uvedeném pořadí.  
__VS 2017__ určuje funkce, které jsou podporovány v aplikaci Visual Studio 2017 RTM.  
__VS 2017 15.3__ určuje funkce, které jsou podporovány v aplikaci Visual Studio 2017 verze 15.3.  
__VS 2017 15,5__ určuje funkce, které jsou podporovány v aplikaci Visual Studio 2017 verze 15,5.

### <a name="notes"></a>Poznámky

<a name="note_A"></a>__A__ to ignoruje specifikace C ++ 03's dynamické výjimek, které byly ve C ++ 11 zastaralá. Neexistuje žádný plán zavedení, v očekávání, budete ji odebrat z budoucí C++ Standard.  
<a name="note_B"></a>__B__ podpora kompilátoru pro vyhledání dvoufázového názvu je vyšší, ale stále neúplné.  
<a name="note_C"></a>__C__ kompilátoru podpora sfinae u výrazů výraz byl dostatek standardní knihovny od Visual Studio 2015 Update 2, ale podpora zůstane neúplné.  
<a name="note_D"></a>__D__ podpora kompilátoru pro preprocesor C99 pravidla je nekompletní v Visual Studio 2017. Variadická makra jsou podporované, ale v chování preprocesor jsou celou řadu chyb.  
<a name="note_E"></a>__E__ to je označena jako není k dispozici, protože kompilátory jsou povolené, ale není vyžadována k podpoře typy rozšířené celé číslo.  Jako RSZ a Clang jsme zvolili není je podporují.  
<a name="note_F"></a>__F__ podobně to je označena jako není k dispozici protože kompilátory jsou povolené, ale není vyžadována k implementaci optimalizace.  
<a name="note_G"></a>__G__ podporován v rámci [/std: c ++ 14](./build/reference/std-specify-language-standard-version.md) suppressible upozornění.  
<a name="note_H"></a>__H__ tato funkce byla k dispozici v náhledy Visual Studio 2017 verze 15.3, ale protože byly nalezeny chyby, byla odebrána z verze.  
<a name="note_J"></a>__J__ jsou funkce, které nebyly dokončeny v sadě Visual Studio 2015 rozdělená jinde v této tabulce.  
<a name="note_K"></a>__K__ Terminálové služby systému souborů je implementována v obou \<experimentální/filesystem > a \<filesystem > pro historické důvodů, ale jeho implementace musí být opraveny předtím, než se přesune jeho obor názvů. Až to uděláte, tato funkce je označena jako ještě nebyla implementována.  
<a name="note_L"></a>__L__ nepodporuje kompilátor vnitřní. Tento vnitřní ještě není k dispozici v Clang. Tato funkce je k dispozici, ale není ještě povoleno v technologii Intellisense.   
<a name="note_14"></a>__14__ tyto funkce C ++ 17 jsou vždy povolena, i v případě [/std: c ++ 14](./build/reference/std-specify-language-standard-version.md) (výchozí) je zadán. Je to způsobeno funkci byl implementován před zavedením **/std** možnosti, nebo protože podmíněného implementace bylo by složité.  
<a name="note_17"></a>__17__ tyto funkce jsou povolené [/std: c ++ 17](./build/reference/std-specify-language-standard-version.md) (nebo [/std: c ++ nejnovější](./build/reference/std-specify-language-standard-version.md)) – možnost kompilátoru.  
<a name="note_byte"></a>__Byte__ `std::byte` je povoleno podle [/std: c ++ 17](./build/reference/std-specify-language-standard-version.md) (nebo [/std: c ++ nejnovější](./build/reference/std-specify-language-standard-version.md)), ale protože můžete v konfliktu s Windows SDK hlavičky v některých případech, má podrobných výslovný nesouhlas s makro. Lze ji vypnout tak, že definujete `_HAS_STD_BYTE` jako `0`.  
<a name="note_C11"></a>__C11__ The Universal CRT implementována části C11 standardní knihovny, které jsou vyžadované C ++ 17, s výjimkou C99 `strftime()` E/O alternativní převod specifikátory, C11 `fopen()` výhradním režimu a C11 `aligned_alloc()`. Je pravděpodobně třeba implementovat, protože zadaný C11 `aligned_alloc()` způsobem, který není kompatibilní s implementací Microsoft `free()`, a to, který `free()` musí být schopna zpracovávat vysoce zarovnaný přidělení.  
<a name="note_rem"></a>__rem__ funkce odstraněny, kdy [/std: c ++ 17](./build/reference/std-specify-language-standard-version.md) (nebo [/std: c ++ nejnovější](./build/reference/std-specify-language-standard-version.md)) je zadána možnost kompilátoru. Tyto funkce mají výslovný nesouhlas s makra: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`, a `_HAS_UNEXPECTED`.
  
## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](cpp/cpp-language-reference.md)  
[Standardní knihovna C++](standard-library/cpp-standard-library-reference.md)   
[Vylepšení shody C++ se sadou Visual Studio 2017](cpp-conformance-improvements-2017.md)  
[Novinky v jazyce Visual C++ v sadě Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md)  
[Visual C++ historie změn 2003 až 2015](porting/visual-cpp-change-history-2003-2015.md)  
[Novinky Visual C++ 2003–2015](porting/visual-cpp-what-s-new-2003-through-2015.md)  
[Blogu týmu Visual C++](https://blogs.msdn.microsoft.com/vcblog/)  
