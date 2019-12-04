---
title: Chyba kompilátoru C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761813"
---
# <a name="compiler-error-c3161"></a>Chyba kompilátoru C3161

Interface: vnořování třídy, struktury, sjednocení nebo rozhraní v rozhraní je neplatné. Vnořování rozhraní ve třídě, struktuře nebo sjednocení je neplatné.

[__Interface](../../cpp/interface.md) se může vyskytovat jenom v globálním oboru nebo v rámci oboru názvů. Třída, struktura nebo sjednocení se nemohou vyskytovat v rozhraní.

## <a name="example"></a>Příklad

Následující ukázka generuje C3161.

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
