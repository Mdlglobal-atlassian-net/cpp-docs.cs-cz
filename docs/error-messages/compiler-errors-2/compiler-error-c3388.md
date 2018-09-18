---
title: Chyba kompilátoru C3388 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3388
dev_langs:
- C++
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4447d2d72c2a0a56df9f3a64549f201f86ddf129
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073470"
---
# <a name="compiler-error-c3388"></a>Chyba kompilátoru C3388

'type': nelze použít jako omezení; přepokládá se: ref class' Chcete pokračovat s analýzou.

Byla zadána omezení u obecného typu, ale nebyl správně zadán omezení. Zobrazit [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.

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