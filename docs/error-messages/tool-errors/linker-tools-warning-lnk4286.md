---
title: Upozornění linkerů LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173865"
---
# <a name="linker-tools-warning-lnk4286"></a>Upozornění linkerů LNK4286

> symbol '*symbol*' definovaný v '*filename_1. obj*' je importován '*filename_2. obj*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro *symbol* , i když je symbol definován v objektovém souboru *filename_1. obj* ve stejné imagi. Odeberte modifikátor `__declspec(dllimport)` pro vyřešení tohoto upozornění.

## <a name="remarks"></a>Poznámky

Warning LNK4286 je obecnější verze [linkerů LNK4217 nástrojů linkeru upozornění](linker-tools-warning-lnk4217.md). Linker vygeneruje upozornění LNK4286, když může zjistit, který objekt odkazoval na symbol, ale nikoli na funkci.

Chcete-li vyřešit LNK4286, odeberte modifikátor deklarace `__declspec(dllimport)` z dopředné deklarace *symbolu* , na který je odkazováno v *filename_2. obj*.

I když se výsledný generovaný kód chová správně, kód vygenerovaný pro volání importované funkce je méně efektivní než volání funkce přímo. Toto upozornění se nezobrazí při kompilaci pomocí možnosti [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Další informace o importu a exportu dat deklarace naleznete v tématu [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Viz také

[Linkerů lnk4049 \ upozornění na nástroje linkeru](linker-tools-warning-lnk4049.md)
[Linkerů lnk4217 \ upozornění na nástroje linkeru](linker-tools-warning-lnk4217.md)
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
