---
title: Chyba kompilátoru C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: e400c181f987a83588f8aedc63ecdedb82be310f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568674"
---
# <a name="compiler-error-c3399"></a>Chyba kompilátoru C3399

'type': při vytváření instance obecného parametru nelze zadat argumenty

Pokud zadáte `gcnew()` omezení, můžete určit, zda typ omezení bude mít konstruktor bez parametrů. Proto jedná se o chybu, pokusí se vytvořit instanci tohoto typu a předat parametr.

Zobrazit [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3399.

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```