---
title: Reference jazyka C++
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 4d184e70e6a7284d07e706ce8b8c247c96442750
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031262"
---
# <a name="c-language-reference"></a>Reference jazyka C++

Tento přehled popisuje programovací jazyk C++ tak, jak je implementován v sadě Microsoft Visual C++. Organizace je založena na [ *The manuálu C++ s poznámkami odkaz* ](http://www.stroustrup.com/arm.html) od Margaret Ellis a Bjarne Stroustrup a ANSI/ISO C++ mezinárodním standardu (ISO/IEC FDIS 14882). Součástí jsou implementace funkcí jazyka C++ specifické pro společnost Microsoft.

Přehled programovací postupy v moderním jazyce C++, naleznete v tématu [Vítejte zpět do C++](welcome-back-to-cpp-modern-cpp.md).

Pokud chcete rychle vyhledat klíčové slovo nebo operátora, nahlédněte do následujících tabulek:

- [Klíčová slova jazyka C++](../cpp/keywords-cpp.md)

- [Operátory jazyka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>V tomto oddílu

[Lexikální konvence](../cpp/lexical-conventions.md)<br/>
Základní lexikální prvky programu C++: tokeny, komentáře, operátory, klíčová slova, interpunkční znaky, literály. Také překlad souborů, přednost/asociativita operátorů.

[Základní koncepty](../cpp/basic-concepts-cpp.md)<br/>
Rozsah, navázání, spuštění a ukončení programu, třídy úložiště a typy.

[Standardní převody](../cpp/standard-conversions.md)<br/>
Převody typů mezi integrovanými nebo „základními“ typy. Také aritmetické převody a převody mezi typy ukazatele, odkazu a ukazatele–odkazu.

[Operátory, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
Operátory v jazyce C++.

[Výrazy](../cpp/expressions-cpp.md)<br/>
Typy výrazů, sémantika výrazů, referenční témata operátorů, obsazení a operátory obsazení, typ běhových informací.

[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
Programovací technika, která implicitně definuje třídu funkčního objektu a vytvoří funkční objekt tohoto typu třídy.

[Příkazy](../cpp/statements-cpp.md)<br/>
Výraz, null, složený příkaz, výběr, iterace, skok a deklarace.

[Deklarace a definice](declarations-and-definitions-cpp.md)<br/>
Specifikátory paměťových tříd, definice funkce, inicializace, výčty, **třídy**, **struktura**, a **sjednocení** deklarace, a **– typedef**  deklarace. Navíc **vložené** funkce, **const** – klíčové slovo, obory názvů.

[Třídy, struktury a sjednocení](../cpp/classes-and-structs-cpp.md)<br/>
Úvod do tříd, struktur a union. Také členské funkce, zvláštní členské funkce, datové členy, bitová pole, **to** ukazatel, vnořené třídy.

[Odvozené třídy](../cpp/inheritance-cpp.md)<br/>
Jednotná a vícenásobná dědičnost, **virtuální** funkce, více základních tříd, **abstraktní** třídy, pravidla rozsahu. Také **__super** a **__interface** klíčová slova.

[Řízení přístupu členů](../cpp/member-access-control-cpp.md)<br/>
Řízení přístupu ke členům třídy: **veřejné**, **privátní**, a **chráněné** klíčová slova. Přátelské funkce a třídy.

[Přetížení](operator-overloading.md)<br/>
Přetížené operátory, pravidla přetížení operátoru.

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
Zpracování výjimek v jazyce C++, strukturované zpracování výjimek (SEH), klíčová slova používaná při psaní příkazů pro zpracování výjimek.

[Kontrolní výraz a uživatelem zadané zprávy](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error` Direktiva, **static_assert** – klíčové slovo, `assert` – makro.

[Šablony](../cpp/templates-cpp.md)<br/>
Specifikace šablony, šablony funkce, šablony třídy **typename** – klíčové slovo, šablony vs. makra, šablony a inteligentní ukazatele.

[Zpracování událostí](../cpp/event-handling.md)<br/>
Deklarování událostí a obslužných rutin událostí.

[Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md)<br/>
Modifikátory specifické pro jazyk C++ společnosti Microsoft. Paměť adresování, konvence volání, **naked** funkce, rozšířené atributy třídy úložiště (**__declspec**), **__w64**.

[Vkládaný assembler](../assembler/inline/inline-assembler.md)<br/>
Použití jazyku sestavení a C++ v **__asm** bloky.

[Podpora kompilátoru COM](../cpp/compiler-com-support.md)<br/>
Odkaz na třídy specifické pro společnost Microsoft a globální funkce používané pro podporu typů modelu COM.

[Rozšíření Microsoft](../cpp/microsoft-extensions.md)<br/>
Rozšíření Microsoft C++.

[Nestandardní chování](../cpp/nonstandard-behavior.md)<br/>
Informace o nestandardní chování kompilátoru jazyka Visual C++.

[C++ vás vítá zpět](welcome-back-to-cpp-modern-cpp.md)<br/>
Přehled o moderním programování C++ postupů pro psaní programů bezpečné, správné a efektivní.

## <a name="related-sections"></a>Související oddíly

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)<br/>
Referenční materiál pro používání jazyka Visual C++ k cílení modulu CLR.

[Referenční zdroje k sestavení programu v jazyce C/C++](../build/reference/c-cpp-building-reference.md)<br/>
Možnosti kompilátoru, možnosti linkeru a další nástroje sestavení.

[C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Referenční materiál pro pragmy, direktivy preprocesoru, předdefinovaná makra a preprocesor.

[Knihovny Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Seznam odkazů na referenční spouštěcí stránky pro různé knihovny jazyka Visual C++.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C](../c-language/c-language-reference.md)
