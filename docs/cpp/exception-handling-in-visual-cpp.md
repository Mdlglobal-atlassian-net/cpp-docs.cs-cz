---
title: Zpracování výjimek v MSVC
ms.date: 05/07/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 47443f1b7021aac7755d77f797a4f7b7410281f8
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222074"
---
# <a name="exception-handling-in-msvc"></a>Zpracování výjimek v MSVC

Výjimka je chybový stav, nacházející se případně i mimo řízení programu, který brání programu pokračovat dle jeho pravidelné cesty spuštění. Určité operace, včetně vytvoření objektu, vstupu a výstupu souboru a volání funkcí z jiných modulů, představují možné zdroje výjimek i v případě, že program pracuje správně. Robustní kód je na výjimky připraven a zpracovává je.

Ke zjištění logických chyb v rámci programu nebo modulu, použít kontrolní výrazy místo výjimek (viz [použití kontrolních výrazů](/visualstudio/debugger/c-cpp-assertions)).

Microsoft C++ kompilátor (MSVC) podporuje tři druhy zpracování výjimek:

- [Zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md)

   Ve většině aplikací jazyka C++ by mělo být použito zpracování výjimek jazyka C++, které je typově bezpečné a zajišťuje, že jsou v průběhu odvíjení zásobníku vyvolány destruktory objektu.

- [Strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md)

   Systém Windows nabízí svůj vlastní mechanismus zpracování výjimek zvaný SEH. Jeho použití není vhodné pro programování v jazyce C++ ani při použití knihovny MFC. SEH lze používejte pouze v aplikacích MFC C.

- [Výjimky MFC](../mfc/exception-handling-in-mfc.md)

   Od verze 3.0 používá MFC výjimky jazyka C++, ale stále podporuje jeho starší makra pro zpracování výjimek, jejichž forma se podobá výjimkám jazyka C++. Přestože nejsou tato makra vhodná pro nové programování, jsou z důvodu zpětné kompatibility stále podporována. V aplikacích používajících makra lze volně používat i výjimky jazyka C++. Během předběžného zpracování provádějí makra vyhodnocování podle MSVC provádění klíčových slov zpracování výjimek C++ jazyk od jazyka Visual C++ verze 2.0. Stávající makra zpracování výjimek lze při použití výjimek jazyka C++ ponechat.

Použít [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru k určení typu zpracování výjimek pro použití v projektu. Zpracování výjimek jazyka C++ je výchozí hodnota. Nekombinujte mechanismy; zpracování chyb výjimky jazyka C++ například nepoužívejte při zpracování strukturovaných výjimek. Pomocí zpracování výjimek jazyka C++ činí váš kód a umožňuje zpracovat výjimky libovolného typu. Další informace o nevýhod strukturované zpracování výjimek naleznete v tématu [strukturovaného zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md). Nápovědu o kombinování maker MFC a výjimek jazyka C++, naleznete v tématu [výjimky: Použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Informace o zpracování výjimek v aplikacích CLR naleznete v tématu [zpracování výjimek (C++vyhodnocovací a C++/CX)](../extensions/exception-handling-cpp-component-extensions.md).

Informace o zpracování výjimek na x64 procesory, naleznete v tématu [x64 zpracování výjimek](../build/exception-handling-x64.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)