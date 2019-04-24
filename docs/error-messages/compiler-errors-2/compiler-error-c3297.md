---
title: Chyba kompilátoru C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: e4661119680dff34dfaa43fb9ce71bf97150a8bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222489"
---
# <a name="compiler-error-c3297"></a>Chyba kompilátoru C3297

"constraint_2": 'constraint_1' nelze použít jako omezení, protože 'constraint_1' má omezení hodnoty

Hodnota třídy jsou zapečetěné. Pokud omezení hodnotové třídy, můžete z něj nikdy odvodit další omezení.

Další informace najdete v tématu [omezení parametrů obecných typů (C++vyhodnocovací)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3297.

```
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```