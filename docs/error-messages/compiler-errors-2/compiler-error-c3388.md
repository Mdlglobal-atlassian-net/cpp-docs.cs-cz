---
title: Chyba kompilátoru C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 3b56aae115b1a1721f3f8a8688e36b25edc7f33f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780025"
---
# <a name="compiler-error-c3388"></a>Chyba kompilátoru C3388

'type': nelze použít jako omezení; přepokládá se: ref class' Chcete pokračovat s analýzou.

Byla zadána omezení u obecného typu, ale nebyl správně zadán omezení. Zobrazit [omezení parametrů obecných typů (C + +/ CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3388.

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```