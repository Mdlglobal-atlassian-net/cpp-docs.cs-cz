---
title: Zpracovávání výjimek v jazyce C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling
ms.assetid: 65f80b44-9d0f-4d17-b910-07205a5c5c40
ms.openlocfilehash: bbdec38bf722ebb1e188af408bf3a413f6d6b8b7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222156"
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

Od verze 4.0 knihovna MFC začaly využívat mechanismus zpracování výjimek jazyka C++. I když jste v novém kódu vedeni k používání zpracování výjimek jazyka C++, knihovna MFC verze 4.0 a novější zachovává makra z předchozích verzí knihovny MFC z důvodu kompatibility se starším kódem. Tato makra a nový mechanismus lze také kombinovat. Informace o kombinování maker a C++ výjimka zpracování a o převodu starého kódu pro použití s novým mechanismem, najdete v článcích [výjimky: Použití maker MFC a C++ výjimky](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) a [výjimky: Převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starší výjimky maker knihovny MFC, pokud je stále používáte, se vyhodnotí jako klíčová slova výjimek jazyka C++. Zobrazit [výjimky: Změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)