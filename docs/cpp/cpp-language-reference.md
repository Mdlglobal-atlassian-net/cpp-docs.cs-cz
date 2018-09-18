---
title: Referenční dokumentace jazyka C++ | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 708db2b20cdbbe2e322075789f64433ff70612a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025513"
---
# <a name="c-language-reference"></a>Reference jazyka C++

Tento přehled popisuje programovací jazyk C++ tak, jak je implementován v sadě Microsoft Visual C++. Organizace je založena na *The manuálu C++ s poznámkami odkaz* od Margaret Ellis a Bjarne Stroustrup a ANSI/ISO C++ mezinárodním standardu (ISO/IEC FDIS 14882). Součástí jsou implementace funkcí jazyka C++ specifické pro společnost Microsoft.

Přehled programovací postupy v moderním jazyce C++, naleznete v tématu [Vítejte zpět do C++](welcome-back-to-cpp-modern-cpp.md).

Pokud chcete rychle vyhledat klíčové slovo nebo operátora, nahlédněte do následujících tabulek:

- [Klíčová slova jazyka C++](../cpp/keywords-cpp.md)

- [Operátory jazyka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>V tomto oddílu

[Lexikální pravidla](../cpp/lexical-conventions.md) základní lexikální prvky programu C++: tokeny, komentáře, operátory, klíčová slova, interpunkční znaky, literály. Také překlad souborů, přednost/asociativita operátorů.

[Základní koncepty](../cpp/basic-concepts-cpp.md) rozsah, navázání, spuštění programu a ukončení, úložiště tříd a typů.

[Standardní převody](../cpp/standard-conversions.md) převody typů mezi integrovanými nebo "základními" typy. Také aritmetické převody a převody mezi typy ukazatele, odkazu a ukazatele–odkazu.

[Operátory, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md) operátory v jazyce C++.

[Výrazy](../cpp/expressions-cpp.md) typy výrazů, sémantika výrazů, referenční témata operátorů, přetypování a operátorů přetypování, informace o typu za běhu.

[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md) programovací technika, která implicitně definuje třídu funkčního objektu a vytvoří funkční objekt tohoto typu třídy.

[Příkazy](../cpp/statements-cpp.md) výrazu, příkazy null, složeného, výběr, iterace, skok a deklarace.

[Deklarace a definice](declarations-and-definitions-cpp.md) Specifikátory paměťových tříd, definice funkce, inicializace, výčty, **třídy**, **struktura**, a **sjednocení** deklarace, a **typedef** deklarace. Navíc **vložené** funkce, **const** – klíčové slovo, obory názvů.

[Třídy, struktury a sjednocení](../cpp/classes-and-structs-cpp.md) Úvod do tříd, struktur a sjednocení. Také členské funkce, zvláštní členské funkce, datové členy, bitová pole, **to** ukazatel, vnořené třídy.

[Odvozené třídy](../cpp/inheritance-cpp.md) jednotná a vícenásobná dědičnost, **virtuální** funkce, více základních tříd, **abstraktní** třídy, pravidla rozsahu. Také **__super** a **__interface** klíčová slova.

[Řízení přístupu členů](../cpp/member-access-control-cpp.md) řízení přístupu ke členům třídy: **veřejné**, **privátní**, a **chráněné** klíčová slova. Přátelské funkce a třídy.

[Přetížení](operator-overloading.md) přetížené operátory, pravidla přetížení operátoru.

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) zpracování výjimek jazyka C++, strukturované výjimky (SEH) zpracování, klíčová slova používaná při psaní příkazy zpracování výjimek.

[Kontrolní výraz a User-Supplied zprávy](../cpp/assertion-and-user-supplied-messages-cpp.md) 
 `#error` směrnice, **static_assert** – klíčové slovo, `assert` – makro.

[Šablony](../cpp/templates-cpp.md) specifikace šablony, šablony funkce, šablony třídy **typename** – klíčové slovo, šablony vs. makra, šablony a inteligentní ukazatele.

[Zpracování událostí](../cpp/event-handling.md) deklarování událostí a obslužných rutin událostí.

[Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md) Modifikátory specifické pro Microsoft C++. Paměť adresování, konvence volání, **naked** funkce, rozšířené atributy třídy úložiště (**__declspec**), **__w64**.

[Vložený Assembler](../assembler/inline/inline-assembler.md) použití jazyku sestavení a C++ v **__asm** bloky.

[Podpora kompilátoru modelu COM](../cpp/compiler-com-support.md) odkaz na třídy specifické pro společnost Microsoft a globální funkce používané pro podporu typů modelu COM.

[Microsoft Extensions](../cpp/microsoft-extensions.md) rozšíření Microsoft C++.

[Nestandardní chování](../cpp/nonstandard-behavior.md) informace o nestandardní chování kompilátoru Visual C++.

[Vítejte zpět v C++](welcome-back-to-cpp-modern-cpp.md) přehled o moderním programování C++ postupů pro psaní programů bezpečné, správné a efektivní.

## <a name="related-sections"></a>Související oddíly

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md) referenční materiál pro používání Visual C++ k cílení modulu common language runtime.

[Reference sestavení C/C++](../build/reference/c-cpp-building-reference.md) kompilátoru možnosti, možnosti linkeru a další nástroje sestavení.

[Reference preprocesoru C/C++](../preprocessor/c-cpp-preprocessor-reference.md) referenční materiály na direktiv pragma, direktivy preprocesoru, předdefinovaná makra a preprocesor.

[Knihovny Visual C++](../standard-library/cpp-standard-library-reference.md) seznam odkazů na referenční spouštěcí stránky pro různé knihovny jazyka Visual C++.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C](../c-language/c-language-reference.md)