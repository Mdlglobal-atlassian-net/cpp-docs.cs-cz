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
ms.openlocfilehash: f9d8a8747d4a808d040b814005782ed8187bf274
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301575"
---
# <a name="naked-function-calls"></a>Volání holé funkce

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Funkce deklarované s **naked** atribut jsou emitovány bez kódu prologu nebo epilogu umožňuje napsat vlastní sekvence vlastního kódu prologu/epilogu pomocí [vložený assembler](../assembler/inline/inline-assembler.md). Neviditelné funkce jsou k dispozici jako o pokročilou funkci. Umožňují deklarovat funkci, která je volána v jiném kontextu než C/C++ a proto vytvořit jiné předpoklady o kde parametry mají, nebo která registruje se zachovají. Příklady rutin, jako je například obslužné rutiny přerušení. Tato funkce je zvláště užitečná pro zápis ovladačů virtuálních zařízení (VxD).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [naked](../cpp/naked-cpp.md)

- [Pravidla holých funkcí a jejich omezení](../cpp/rules-and-limitations-for-naked-functions.md)

- [Důležité informace k zápisu kódu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)