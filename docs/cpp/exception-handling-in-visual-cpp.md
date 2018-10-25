---
title: Zpracování výjimek v jazyce Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b168bf95e44a41973d92230f559246b03f275601
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073081"
---
# <a name="exception-handling-in-visual-c"></a>Zpracování výjimek v jazyce Visual C++

Výjimka je chybový stav, nacházející se případně i mimo řízení programu, který brání programu pokračovat dle jeho pravidelné cesty spuštění. Určité operace, včetně vytvoření objektu, vstupu a výstupu souboru a volání funkcí z jiných modulů, představují možné zdroje výjimek i v případě, že program pracuje správně. Robustní kód je na výjimky připraven a zpracovává je.

Ke zjištění logických chyb v rámci programu nebo modulu, použít kontrolní výrazy místo výjimek (viz [použití kontrolních výrazů](/visualstudio/debugger/c-cpp-assertions)).

Jazyk Visual C++ podporuje tři druhy zpracování výjimek:

- [Zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md)

   Ve většině aplikací jazyka C++ by mělo být použito zpracování výjimek jazyka C++, které je typově bezpečné a zajišťuje, že jsou v průběhu odvíjení zásobníku vyvolány destruktory objektu.

- [Strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md)

   Systém Windows nabízí svůj vlastní mechanismus zpracování výjimek zvaný SEH. Jeho použití není vhodné pro programování v jazyce C++ ani při použití knihovny MFC. SEH lze používejte pouze v aplikacích MFC C.

- [Výjimky MFC](../mfc/exception-handling-in-mfc.md)

   Od verze 3.0 používá MFC výjimky jazyka C++, ale stále podporuje jeho starší makra pro zpracování výjimek, jejichž forma se podobá výjimkám jazyka C++. Přestože nejsou tato makra vhodná pro nové programování, jsou z důvodu zpětné kompatibility stále podporována. V aplikacích používajících makra lze volně používat i výjimky jazyka C++. Během předběžného zpracování provádějí makra vyhodnocování na základě klíčových slov zpracování výjimek definovaných v implementaci Visual C++ jazyka C++ stejně jako u Visual C++ verze 2.0. Stávající makra zpracování výjimek lze při použití výjimek jazyka C++ ponechat.

Použít [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru k určení typu zpracování výjimek pro použití v projektu. Zpracování výjimek jazyka C++ je výchozí hodnota. Nekombinujte mechanismy; zpracování chyb výjimky jazyka C++ například nepoužívejte při zpracování strukturovaných výjimek. Pomocí zpracování výjimek jazyka C++ činí váš kód a umožňuje zpracovat výjimky libovolného typu. Další informace o nevýhod strukturované zpracování výjimek naleznete v tématu [strukturovaného zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md). Nápovědu o kombinování maker MFC a výjimek jazyka C++, naleznete v tématu [výjimky: použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Informace o zpracování výjimek v aplikacích CLR naleznete v tématu [zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md).

Informace o zpracování výjimek na x64 procesory, naleznete v tématu [Exception Handling (x64)](../build/exception-handling-x64.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)