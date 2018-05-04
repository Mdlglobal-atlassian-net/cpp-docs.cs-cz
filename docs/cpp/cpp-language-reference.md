---
title: Referenční příručka jazyka C++ | Microsoft Docs
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
ms.openlocfilehash: 25315121d3004601914c5b8872b496e57acec99f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-language-reference"></a>Reference jazyka C++
Tento přehled popisuje programovací jazyk C++ tak, jak je implementován v sadě Microsoft Visual C++. Organizace je založena na *The poznámkou ruční C++ odkaz* Margaret Ellis a Bjarnem Stroustrupem a ANSI/ISO C++ mezinárodní standardní (ISO/IEC FDIS 14882). Součástí jsou implementace funkcí jazyka C++ specifické pro společnost Microsoft.  

Přehled programování postupy moderní verze jazyka C++, najdete v části [Vítá zpět do C++](welcome-back-to-cpp-modern-cpp.md).
  
 Pokud chcete rychle vyhledat klíčové slovo nebo operátora, nahlédněte do následujících tabulek:  
  
-   [Klíčová slova jazyka C++](../cpp/keywords-cpp.md)  
  
-   [Operátory jazyka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [Lexikální konvence](../cpp/lexical-conventions.md)  
 Základní lexikální prvky programu C++: tokeny, komentáře, operátory, klíčová slova, interpunkční znaky, literály. Také překlad souborů, přednost/asociativita operátorů.  
  
 [Základní koncepty](../cpp/basic-concepts-cpp.md)  
 Rozsah, navázání, spuštění a ukončení programu, třídy úložiště a typy.  
  
 [Standardní převody](../cpp/standard-conversions.md)  
 Převody typů mezi integrovanými nebo „základními“ typy. Také aritmetické převody a převody mezi typy ukazatele, odkazu a ukazatele–odkazu.  
  
 [Operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 Operátory v jazyce C++.  
  
 [Výrazy](../cpp/expressions-cpp.md)  
 Typy výrazů, sémantika výrazů, referenční témata operátorů, obsazení a operátory obsazení, typ běhových informací.  
  
 [Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)  
 Programovací technika, která implicitně definuje třídu funkčního objektu a vytvoří funkční objekt tohoto typu třídy.  
  
 [Příkazy](../cpp/statements-cpp.md)  
 Výraz, null, složený příkaz, výběr, iterace, skok a deklarace.  
  
 [Deklarace a definice](declarations-and-definitions-cpp.md)  
 Specifikátory paměťových tříd, definice funkce, inicializace, výčty, třídy, struktury a deklarace unie a typedef. Také vložené funkce, klíčové slovo const, obory názvů.  
  
 [Deklarátory](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)  
 Část příkazu deklarace, která pojmenuje objekt, typ nebo funkci. Abstraktní deklarátory, názvy typů, inicializátory, deklarace a definice funkcí, pole, odkazy.  
  
 [Tříd, struktur a sjednocení](../cpp/classes-and-structs-cpp.md)  
 Úvod do tříd, struktur a union. Navíc členské funkce, speciální členské funkce, datové členy, bitových polí, tento ukazatel, vnořené třídy.  
  
 [Odvození tříd](../cpp/inheritance-cpp.md)  
 Jednotná a vícenásobná dědičnost, virtuální funkce, více základních tříd, abstraktní třídy, pravidla rozsahu. Navíc __super a \__interface klíčová slova.  
  
 [Řízení přístup ke členu](../cpp/member-access-control-cpp.md)  
 Řízení přístupu ke členům třídy: klíčová slova Public, Private a Protected. Přátelské funkce a třídy.  
  
 [Přetížení](operator-overloading.md)  
 Přetížené operátory pravidla přetížení operátoru.  
  
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)  
 Zpracování výjimek v jazyce C++, strukturované zpracování výjimek (SEH), klíčová slova používaná při psaní příkazů pro zpracování výjimek.  
  
 [Kontrolní výraz a uživatelem zadané zprávy](../cpp/assertion-and-user-supplied-messages-cpp.md)  
 `#error` Direktiva, `static_assert` – klíčové slovo, `assert` makro.  
  
 [Šablony](../cpp/templates-cpp.md)  
 Specifikace šablony, šablony funkce, šablony třídy, klíčové slovo pro název typu, šablony vs. makra, šablony a inteligentní ukazatele.  
  
 [Zpracování událostí](../cpp/event-handling.md)  
 Deklarování událostí a obslužných rutin událostí.  
  
 [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md)  
 Modifikátory specifické pro jazyk C++ společnosti Microsoft. Paměť adresování, konvence, holé funkce Rozšířené atributy třídy úložiště (__declspec), volání \__w64.  
  
 [Vkládaný assembler](../assembler/inline/inline-assembler.md)  
 Použití jazyku sestavení a jazyku C++ v blocích __asm.  
  
 [Podpora kompilátoru COM](../cpp/compiler-com-support.md)  
 Odkaz na třídy specifické pro společnost Microsoft a globální funkce používané pro podporu typů modelu COM.  
  
 [Rozšíření Microsoft](../cpp/microsoft-extensions.md)  
 Rozšíření Microsoft pro C++  
  
 [Nestandardní chování](../cpp/nonstandard-behavior.md)  
 Informace o nestandardní chování – kompilátor Visual C++.  

 [Vítejte zpět do C++](welcome-back-to-cpp-modern-cpp.md) přehled moderní programování v C++ postupů pro psaní programů bezpečnost, správné a efektivní.
  
## <a name="related-sections"></a>Související oddíly  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)  
 Referenční materiál pro používání jazyka Visual C++ k cílení modulu CLR.  
  
 [Referenční zdroje k sestavení programu v jazyce C/C++](../build/reference/c-cpp-building-reference.md)  
 Možnosti kompilátoru, možnosti linkeru a další nástroje sestavení.  
  
 [C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)  
 Referenční materiál pro pragmy, direktivy preprocesoru, předdefinovaná makra a preprocesor.  
  
 [Knihovny jazyka Visual C++](../standard-library/cpp-standard-library-reference.md)  
 Seznam odkazů na referenční spouštěcí stránky pro různé knihovny jazyka Visual C++.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C](../c-language/c-language-reference.md)