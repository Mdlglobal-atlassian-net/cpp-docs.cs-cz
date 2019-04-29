---
title: Kompilátor upozornění (úroveň 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 556c6e0963fc41d76cd123373cc4cd85edc66962
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384137"
---
# <a name="compiler-warning-level-1-c4964"></a>Kompilátor upozornění (úroveň 1) C4964

Nebyly zadány žádné možnosti optimalizace; informace o profilu se nebudou shromažďovat.

[/GL](../../build/reference/gl-whole-program-optimization.md) a [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) byly zadány, ale žádné optimalizace vyžádali, tak, aby se nevygeneruje žádné soubory .pgc, a proto nebude možná bez optimalizace na základě profilu.

Pokud chcete soubory .pgc generovat, když spustíte svou aplikaci, zadejte jeden z [/O](../../build/reference/o-options-optimize-code.md) – možnosti kompilátoru.

Následující ukázka generuje C4964:

```
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```