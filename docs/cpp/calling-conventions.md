---
title: Konvence volání
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: cc79a0636f900aa49e31f0dc35ee19657c3e1ccb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345122"
---
# <a name="calling-conventions"></a>Konvence volání

Kompilátor Visual C/C++ poskytuje několik různých konvencí volání vnitřních a vnějších funkcí. Pochopení těchto různých přístupů může pomoci ladit program a propojit kód s rutinami jazyka symbolických adres.

Témata o této skutečnosti vysvětlují rozdíly mezi konvencemi volání, způsobu předávání argumentů a způsobu vracení hodnot funkcemi. Také pojednávají o voláních neviditelných funkcí, tedy o pokročilé funkci umožňující psaní vlastního kódu prologu a epilogu.

Informace o konvencích volání pro x64 procesory, naleznete v tématu [konvence volání](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Témata v této části

- [Předávání argumentů a zásady vytváření názvů](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`a další)

- [Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)

- [Použití volání neviditelných funkcí pro psaní vlastního kódu prologu/epilogu](../cpp/naked-function-calls.md)

- [Koprocesor plovoucí desetinné čárky a konvence volání](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Viz také:

[Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md)