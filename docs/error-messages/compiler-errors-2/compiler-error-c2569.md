---
title: Chyba kompilátoru C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 7299fe8daa1fa0fc6e1291bf8c683b33235e8bbf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755522"
---
# <a name="compiler-error-c2569"></a>Chyba kompilátoru C2569

' EnumOrUnion ': výčet/sjednocení nejde používat jako základní (Base) třídu.

Pokud musíte odvodit typ ze zadaného sjednocení nebo výčtu, změňte sjednocení nebo výčet na třídu nebo strukturu.

Následující ukázka generuje C2569:

```cpp
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```
