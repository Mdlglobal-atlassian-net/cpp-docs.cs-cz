---
title: Chyba kompilátoru C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: 890dae7aa34103bde0168f1933bb42343d84100b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408579"
---
# <a name="compiler-error-c2528"></a>Chyba kompilátoru C2528

"name": ukazatel na odkaz je neplatný

Nelze deklarovat ukazatel na odkaz. Před deklarací ukazatele k němu přistoupit přes ukazatel proměnnou.

Následující ukázka generuje C2528:

```
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```