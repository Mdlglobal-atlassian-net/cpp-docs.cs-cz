---
title: LNK4286 upozornění Linkerů
ms.date: 04/09/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: f4ab9104c68534eaf1278a6cacb91623c24a237b
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477438"
---
# <a name="linker-tools-warning-lnk4286"></a>LNK4286 upozornění Linkerů

> symbol '*symbol*"definované v"*filename_1.obj*"importovaných pomocí"*filename_2.obj*.

[__declspec(dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro *symbol* i v případě, že je definován symbol do souboru objektu *filename_1.obj* v stejnou bitovou kopii. Odeberte `__declspec(dllimport)` modifikátor, chcete-li vyřešit tato upozornění.

## <a name="remarks"></a>Poznámky

Upozornění LNK4286 je obecnější verze [LNK4217 upozornění nástrojů Linkeru](linker-tools-warning-lnk4217.md). Linker generuje LNK4286 upozornění, pokud mu sdělí, soubor, který objekt odkazovaný symbol, ale není funkce.

Chcete-li vyřešit LNK4286, odeberte `__declspec(dllimport)` modifikátoru deklarace z Dopředná deklarace *symbol* odkazované v *filename_2.obj*.

I když konečné generovaný kód pracuje správně, je méně efektivní než přímého volání funkce kód generovaný pro volání importované funkce. Toto upozornění nezobrazí při kompilaci pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnost.

Další informace o import a export dat deklarace, naleznete v tématu [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Viz také:

[Upozornění Linkerů LNK4049](linker-tools-warning-lnk4049.md) \
[LNK4286 upozornění Linkerů](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)