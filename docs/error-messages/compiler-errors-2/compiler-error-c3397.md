---
title: Chyba kompilátoru C3397 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3397
dev_langs:
- C++
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80db76886b4de529b75fd402a70af7c9fa2a892c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064071"
---
# <a name="compiler-error-c3397"></a>Chyba kompilátoru C3397

Inicializace agregace není povolena ve výchozích argumentů

Pole je deklarován nesprávně.  Zobrazit [pole](../../windows/arrays-cpp-component-extensions.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3397.

```
// C3397.cpp
// compile with: /clr
// /clr /c
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397
void Func2(array<int> ^p = gcnew array<int> (3));   // OK

int main() {
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK
}
```