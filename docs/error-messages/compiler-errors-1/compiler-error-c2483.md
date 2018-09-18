---
title: Chyba kompilátoru C2483 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be2a2caef9e1252bf1ab36253a7f5f715b94d5a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031610"
---
# <a name="compiler-error-c2483"></a>Chyba kompilátoru C2483

>"*identifikátor*': nelze použít deklaraci objektu se konstruktor nebo destruktor"vlákno"

Tato chybová zpráva je zastaralé v sadě Visual Studio 2015 a novější verze. V předchozích verzích, jsou proměnné deklarovány s `thread` atribut se nedá inicializovat pomocí konstruktoru nebo jiný výraz, který se vyžaduje vyhodnocení za běhu. Statický výraz je potřeba inicializovat `thread` data.

## <a name="example"></a>Příklad

Následující ukázka generuje C2483 v sadě Visual Studio 2013 a dřívějších verzích.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Viz také

[thread](../../cpp/thread.md)