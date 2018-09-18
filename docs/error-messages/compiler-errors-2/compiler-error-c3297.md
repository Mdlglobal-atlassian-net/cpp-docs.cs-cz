---
title: Chyba kompilátoru C3297 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3297
dev_langs:
- C++
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7aa23cebc7ad7019c375c351f723b7ad1573ab86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069830"
---
# <a name="compiler-error-c3297"></a>Chyba kompilátoru C3297

"constraint_2": 'constraint_1' nelze použít jako omezení, protože 'constraint_1' má omezení hodnoty

Hodnota třídy jsou zapečetěné. Pokud omezení hodnotové třídy, můžete z něj nikdy odvodit další omezení.

Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

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