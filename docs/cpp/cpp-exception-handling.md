---
title: Zpracování výjimek jazyka C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling
- Visual C++, exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41abebbd73dc1cf72e35dcce88aa551be181061b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019639"
---
# <a name="c-exception-handling"></a>Zpracovávání výjimek v jazyce C++

Jazyk C++ obsahuje integrovanou podporu pro vyvolávání a zachycování výjimek. Při programování v jazyce C++ byste téměř vždy měli používat integrovanou podporu výjimek jazyka C++ popsanou v tomto oddíle.

Pokud chcete povolit ve vašem kódu zpracování výjimek jazyka C++, použijte [/EHsc](../build/reference/eh-exception-handling-model.md).

## <a name="in-this-section"></a>V tomto oddílu

Tato diskuse o zpracování výjimek jazyka C++ obsahuje:

- [Try, catch a throw – příkazy](../cpp/try-throw-and-catch-statements-cpp.md)

- [Postup vyhodnocení bloků catch](../cpp/how-catch-blocks-are-evaluated-cpp.md)

- [Výjimky a uvolnění zásobníku](../cpp/exceptions-and-stack-unwinding-in-cpp.md)

- [Specifikace výjimek](../cpp/exception-specifications-throw-cpp.md)

- [noexcept](../cpp/noexcept-cpp.md)

- [Nezpracované výjimky jazyka C++](../cpp/unhandled-cpp-exceptions.md)

- [Kombinace výjimek v jazycích C (strukturované) a C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)

## <a name="support-for-earlier-mfc-exceptions"></a>Podpora starších výjimek knihovny MFC

Od verze 4.0 knihovna MFC začaly využívat mechanismus zpracování výjimek jazyka C++. I když jste v novém kódu vedeni k používání zpracování výjimek jazyka C++, knihovna MFC verze 4.0 a novější zachovává makra z předchozích verzí knihovny MFC z důvodu kompatibility se starším kódem. Tato makra a nový mechanismus lze také kombinovat. Informace o kombinování maker a zpracování výjimek jazyka C++ a o převodu starého kódu pro použití s novým mechanismem naleznete v článcích [výjimky: použití maker MFC a výjimek jazyka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) a [výjimky: převádění z knihovny MFC Makra výjimek](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starší výjimky maker knihovny MFC, pokud je stále používáte, se vyhodnotí jako klíčová slova výjimek jazyka C++. Zobrazit [výjimky: změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)