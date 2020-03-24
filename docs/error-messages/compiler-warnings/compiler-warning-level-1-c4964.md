---
title: Upozornění kompilátoru (úroveň 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 7852340bc056e126238a2d9c7493887ef3caf93e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174489"
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
