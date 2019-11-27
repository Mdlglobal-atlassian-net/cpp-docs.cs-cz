---
title: Zpracování výjimek v MSVC
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246595"
---
# <a name="exception-handling-in-msvc"></a>Zpracování výjimek v MSVC

Výjimka je chybový stav, nacházející se případně i mimo řízení programu, který brání programu pokračovat dle jeho pravidelné cesty spuštění. Určité operace, včetně vytvoření objektu, vstupu a výstupu souboru a volání funkcí z jiných modulů, představují možné zdroje výjimek i v případě, že program pracuje správně. Robustní kód je na výjimky připraven a zpracovává je. Pro zjištění logických chyb použijte kontrolní výrazy namísto výjimek (viz [použití kontrolních výrazů](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Druhy výjimek

Kompilátor Microsoft C++ (MSVC) podporuje tři druhy zpracování výjimek:

- [C++zpracování výjimek](errors-and-exception-handling-modern-cpp.md)

   Ve většině aplikací jazyka C++ by mělo být použito zpracování výjimek jazyka C++, které je typově bezpečné a zajišťuje, že jsou v průběhu odvíjení zásobníku vyvolány destruktory objektu.

- [Strukturované zpracování výjimek](structured-exception-handling-c-cpp.md)

   Systém Windows nabízí svůj vlastní mechanismus zpracování výjimek zvaný SEH. Jeho použití není vhodné pro programování v jazyce C++ ani při použití knihovny MFC. Použijte SEH jenom v aplikacích, které nejsou v MFC C.

- [Výjimky knihovny MFC](../mfc/exception-handling-in-mfc.md)

Použijte možnost kompilátoru [/eh](../build/reference/eh-exception-handling-model.md) k určení typu zpracování výjimek, který se má použít v projektu. C++ výchozím nastavením je zpracování výjimek. Nekombinujte mechanismy zpracování chyb. Nepoužívejte C++ například výjimky se strukturovaným zpracováním výjimek. Pomocí C++ zpracování výjimek je váš kód lépe přenosný a umožňuje zpracovat výjimky jakéhokoliv typu. Další informace o nevýhodách strukturovaného zpracování výjimek naleznete v tématu [strukturované zpracování výjimek](structured-exception-handling-c-cpp.md). Rady týkající se kombinování maker a C++ výjimek knihovny MFC naleznete v tématu [výjimky: použití C++ maker a výjimek knihovny MFC](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md)

- [Jak navrhovat pro bezpečnost výjimek](how-to-design-for-exception-safety.md)

- [Jak rozhraní mezi výjimečným a nevýjimečným kódem](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Příkazy try, Catch a throw](try-throw-and-catch-statements-cpp.md)

- [Postup vyhodnocení bloků catch](how-catch-blocks-are-evaluated-cpp.md)

- [Výjimky a odvíjení zásobníku](exceptions-and-stack-unwinding-in-cpp.md)

- [Specifikace výjimek](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nezpracované výjimky jazyka C++](unhandled-cpp-exceptions.md)

- [Kombinace výjimek v jazycích C (strukturované) a C++](mixing-c-structured-and-cpp-exceptions.md)

- [Strukturované zpracování výjimek (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](cpp-language-reference.md)</br>
[x64 – zpracování výjimek](../build/exception-handling-x64.md)</br>
[Zpracování výjimek (C++/CLI a C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
