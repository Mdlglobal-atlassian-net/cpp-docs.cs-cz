---
title: Compiler Error C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 314b75a9d0ab8cde2886a7466fa0f95b5bbdd8f1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58778049"
---
# <a name="compiler-error-c3299"></a>Compiler Error C3299

'member_function': nelze zadat omezení, dědí se ze základní metody

Při přepisování obecné členskou funkci, nelze zadat klauzule omezení (s opakováním, omezení znamená, že nejsou děděna omezení).

Klauzule omezení u obecných funkce, které jsou přepsání se budou dědit.

Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3299.

```
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```