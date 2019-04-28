---
title: Upozornění linkerů LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 43ed18808ba5ce632dd7dc7095f7bc30e4497ec9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352434"
---
# <a name="linker-tools-warning-lnk4286"></a>Upozornění linkerů LNK4286

> symbol '*symbol*"definované v"*filename_1.obj*"importovaných pomocí"*filename_2.obj*.

[__declspec(dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro *symbol* i v případě, že je definován symbol do souboru objektu *filename_1.obj* v stejnou bitovou kopii. Odeberte `__declspec(dllimport)` modifikátor, chcete-li vyřešit tato upozornění.

## <a name="remarks"></a>Poznámky

Upozornění LNK4286 je obecnější verze [LNK4217 upozornění nástrojů Linkeru](linker-tools-warning-lnk4217.md). Linker generuje LNK4286 upozornění, pokud mu sdělí, soubor, který objekt odkazovaný symbol, ale není funkce.

Chcete-li vyřešit LNK4286, odeberte `__declspec(dllimport)` modifikátoru deklarace z Dopředná deklarace *symbol* odkazované v *filename_2.obj*.

I když konečné generovaný kód pracuje správně, je méně efektivní než přímého volání funkce kód generovaný pro volání importované funkce. Toto upozornění nezobrazí při kompilaci pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnost.

Další informace o import a export dat deklarace, naleznete v tématu [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Viz také:

[Upozornění Linkerů LNK4049](linker-tools-warning-lnk4049.md) \
[Upozornění Linkerů LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)