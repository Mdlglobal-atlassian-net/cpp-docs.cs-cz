---
title: Upozornění (úroveň 1) C4688 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4688
dev_langs:
- C++
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aff10e34fd2dde20059ccbe2845b199486beb865
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027827"
---
# <a name="compiler-warning-level-1-c4688"></a>Kompilátor upozornění (úroveň 1) C4688

"omezení": seznam omezení obsahuje typ sestavení private 'type'

Seznam omezení obsahuje privátní typ sestavení, což znamená, že nebude k dispozici při typu přistupuje z mimo sestavení. Další informace najdete v tématu [obecných typů](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4688.

```
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```