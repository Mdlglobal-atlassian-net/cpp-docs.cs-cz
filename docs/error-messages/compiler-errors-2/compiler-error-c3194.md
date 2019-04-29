---
title: Compiler Error C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 181a18dde45c3363f1f77bc0cbbd5b0ffca3e898
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397455"
---
# <a name="compiler-error-c3194"></a>Compiler Error C3194

'member': hodnotový typ nemůže mít operátor přiřazení

Speciální členské funkce, které vyžadují automatické volání kompilátorem, jako je kopírovací konstuktor ani operátor copy assignment nejsou podporovány v hodnotové třídě.

## <a name="example"></a>Příklad

Následující ukázka generuje C3194.

```
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```