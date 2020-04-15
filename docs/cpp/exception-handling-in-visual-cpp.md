---
title: Zpracování výjimek v MSVC
description: Přehled zpracování výjimek jazyka Jazyka C++.
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396274"
---
# <a name="exception-handling-in-msvc"></a>Zpracování výjimek v MSVC

Výjimka je chybový stav, nacházející se případně i mimo řízení programu, který brání programu pokračovat dle jeho pravidelné cesty spuštění. Některé operace, včetně vytváření objektů, vstupu a výstupu souboru a volání funkcí z jiných modulů, jsou všechny potenciální zdroje výjimek, i když je program spuštěn správně. Robustní kód je na výjimky připraven a zpracovává je. Chcete-li zjistit chyby logiky, použijte kontrolní výrazy spíše než výjimky (viz [Použití kontrolních výrazů).](/visualstudio/debugger/c-cpp-assertions)

## <a name="kinds-of-exceptions"></a>Druhy výjimek

Kompilátor Microsoft C++ (MSVC) podporuje tři druhy zpracování výjimek:

- [Zpracování výjimek jazyka C++](errors-and-exception-handling-modern-cpp.md)

   Pro většinu programů jazyka C++ byste měli použít zpracování výjimek jazyka C++. Je typově bezpečné a zajišťuje, že destruktory objektu jsou vyvolány během odvíjení zásobníku.

- [Strukturované zpracování výjimek](structured-exception-handling-c-cpp.md)

   Systém Windows dodává vlastní mechanismus výjimek, nazývaný strukturované zpracování výjimek (SEH). Nedoporučuje se pro programování jazyka C++ nebo MFC. SEH používejte pouze v programech jiných než MFC C.

- [Výjimky knihovny MFC](../mfc/exception-handling-in-mfc.md)

   Od verze 3.0 knihovna MFC používá výjimky jazyka C++. Stále podporuje jeho starší výjimky zpracování makra, které jsou podobné výjimky jazyka C++ ve formě. Rady týkající se míchání maker knihovny MFC a výjimek jazyka C++ naleznete v [tématu Výjimky: Použití maker knihovny MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Pomocí možnosti kompilátoru [/EH](../build/reference/eh-exception-handling-model.md) určete model zpracování výjimek, který se má použít v projektu jazyka C++. Standardní zpracování výjimek jazyka C++ (**/EHsc**) je výchozí v nových projektech jazyka C++ v sadě Visual Studio.

Nedoporučujeme kombinovat mechanismy zpracování výjimek. Například nepoužívejte výjimky jazyka C++ se strukturovaným zpracováním výjimek. Pomocí zpracování výjimek jazyka C++ výhradně umožňuje váš kód přenosnější a umožňuje zpracovávat výjimky libovolného typu. Další informace o nevýhodách strukturovaného zpracování výjimek naleznete [v tématu Strukturované zpracování výjimek](structured-exception-handling-c-cpp.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Moderní osvědčené postupy jazyka C++ pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md)

- [Jak navrhnout pro bezpečnost výjimek](how-to-design-for-exception-safety.md)

- [Jak propojit výjimečný a nevýjimečný kód](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Příkazy try, catch a throw](try-throw-and-catch-statements-cpp.md)

- [Postup vyhodnocení bloků catch](how-catch-blocks-are-evaluated-cpp.md)

- [Výjimky a odvíjení zásobníku](exceptions-and-stack-unwinding-in-cpp.md)

- [Specifikace výjimek](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nezpracované výjimky jazyka C++](unhandled-cpp-exceptions.md)

- [Kombinace výjimek v jazycích C (strukturované) a C++](mixing-c-structured-and-cpp-exceptions.md)

- [Strukturované ošetření výjimek (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](cpp-language-reference.md)</br>
[x64 – zpracování výjimek](../build/exception-handling-x64.md)</br>
[Zpracování výjimek (C++/CLI a C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
