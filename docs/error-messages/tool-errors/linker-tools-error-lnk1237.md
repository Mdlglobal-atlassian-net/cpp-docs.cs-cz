---
title: Chyba Linkerů LNK1237 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9ada38fcf3a706f7852f49f60f677fb5dc10d7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065293"
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