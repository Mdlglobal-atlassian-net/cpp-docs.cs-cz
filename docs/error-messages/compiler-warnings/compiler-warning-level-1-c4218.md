---
title: Upozornění kompilátoru (úroveň 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f7553b30a17f50f559351353552fd656fceb8657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199794"
---
# <a name="compiler-warning-level-1-c4218"></a>Upozornění kompilátoru (úroveň 1) C4218

používá se nestandardní rozšíření: musíte zadat aspoň třídu úložiště nebo typ.

S výchozími rozšířeními Microsoft (/ze) můžete deklarovat proměnnou bez určení typu nebo třídy úložiště. Výchozí typ je `int`.

## <a name="example"></a>Příklad

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Deklarace jsou neplatné v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
