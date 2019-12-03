---
title: Upozornění kompilátoru (úroveň 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 102e9bdb2804988875d8c535eb8c266bd8fb03df
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683072"
---
# <a name="compiler-warning-level-4-c4431"></a>Upozornění kompilátoru (úroveň 4) C4431

chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.

Tato chyba se může vygenerovat v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio C++ 2005: vizuál už ve výchozím nastavení nevytváří netypové identifikátory jako int. Typ identifikátoru musí být explicitně zadán.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4431.

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```