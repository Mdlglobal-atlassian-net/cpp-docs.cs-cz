---
title: Chyba linkerů LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: ae1a397cdcc10cd89fd046a94e78c15dd46dceed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581321"
---
# <a name="linker-tools-error-lnk1237"></a>Chyba linkerů LNK1237

Při generování kódu zavedl kompilátor odkaz na symbolu symbol definovaný v modulu 'module' zkompilovaném pomocí/GL.

Při generování kódu kompilátoru nesmí zavést symboly, které jsou novější přeložit na definice zkompilována **/GL**. `symbol` je třeba otazník, která byla zavedená a později přeložen na definici zkompilovaná **/GL**.

Další informace najdete v tématu [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).

LNK1237 vyřešíte, nejde zkompilovat symbol **/GL** nebo použijte [parametr/include (vynucení odkazů na symboly)](../../build/reference/include-force-symbol-references.md) přinutit odkaz na symbol.

## <a name="example"></a>Příklad

Následující ukázka generuje LNK1237. Chcete-li vyřešit tuto chybu, není inicializace pole v LNK1237_a.cpp a přidejte **/ include: funkce __chkstk** příkazu link.

```
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```