---
title: Volání holé funkce
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 14bc64314cf64e7d13c076c314419e3d636432d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177934"
---
# <a name="naked-function-calls"></a>Volání holé funkce

**Specifické pro společnost Microsoft**

Funkce deklarované **s atributem** s možností zprovoznění jsou generovány bez kódu prologu nebo epilogu, což vám umožní napsat vlastní sekvenci prologu/epilogu pomocí [vloženého assembleru](../assembler/inline/inline-assembler.md). Holé funkce jsou k dispozici jako pokročilá funkce. Umožňují deklarovat funkci, která je volána z kontextu jiné než C/C++, a tak učinit různé předpoklady o tom, kde jsou parametry nebo které Registry jsou zachovány. Mezi příklady patří rutiny, jako jsou například obslužné rutiny přerušení. Tato funkce je zvláště užitečná pro autory ovladačů virtuálních zařízení (VxDs).

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [naked](../cpp/naked-cpp.md)

- [Pravidla holých funkcí a jejich omezení](../cpp/rules-and-limitations-for-naked-functions.md)

- [Předpoklady pro zápis kódu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence volání](../cpp/calling-conventions.md)
