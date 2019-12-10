---
title: Chyba linkerů LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: c56b2eb86c7605fb3330d7b1bb01e3235466ede6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990957"
---
# <a name="linker-tools-error-lnk1237"></a>Chyba linkerů LNK1237

Při generování kódu zavedl kompilátor odkaz na symbol symbol definovaný v modulu Module kompilovaný s/GL.

Během generování kódu by kompilátor neměl zavádět symboly, které jsou později vyřešeny na definice zkompilované **/GL**. `symbol` je symbol, který byl představen a později vyřešen do definice zkompilované pomocí **/GL**.

Další informace naleznete v tématu [/GL (celá optimalizace programu)](../../build/reference/gl-whole-program-optimization.md).

Chcete-li vyřešit LINKERŮ LNK1237, nezkompilujte symbol s **/GL** nebo použijte [/include (vynucení odkazů na symboly)](../../build/reference/include-force-symbol-references.md) k vynucení odkazu na symbol.

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK1237. Tuto chybu lze vyřešit tak, že neinicializujete pole v LNK1237_a. cpp a přidáte **/include: __chkstk** do příkazu Link.

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
