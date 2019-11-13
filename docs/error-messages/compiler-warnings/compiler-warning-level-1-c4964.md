---
title: Upozornění kompilátoru (úroveň 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 2a75a1b7d3738794046ac697113c3c746bb6fcff
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052250"
---
# <a name="compiler-warning-level-1-c4964"></a>Upozornění kompilátoru (úroveň 1) C4964

Nebyly zadány žádné možnosti optimalizace; informace o profilu nebudou shromažďovány.

Byly zadány [/GL](../../build/reference/gl-whole-program-optimization.md) a [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) , ale nebyly požadovány žádné optimalizace, takže nebudou vygenerovány žádné soubory. pgc, a proto nebude možné provádět žádné optimalizace na základě profilu.

Pokud chcete, aby byly soubory. pgc generovány při spuštění aplikace, zadejte jednu z možností kompilátoru [/o](../../build/reference/o-options-optimize-code.md) .

Následující ukázka generuje C4964:

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```