---
title: Chyba kompilátoru C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d05a861a2baedb86482503b6860098f12c41bd78
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776454"
---
# <a name="compiler-error-c3399"></a>Chyba kompilátoru C3399

'type': při vytváření instance obecného parametru nelze zadat argumenty

Pokud zadáte `gcnew()` omezení, můžete určit, zda typ omezení bude mít konstruktor bez parametrů. Proto jedná se o chybu, pokusí se vytvořit instanci tohoto typu a předat parametr.

Zobrazit [omezení parametrů obecných typů (C++vyhodnocovací)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

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