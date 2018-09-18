---
title: Upozornění (úroveň 1) C4964 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f1644e4603bae36ec9d407294dea78a27e60539
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086665"
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