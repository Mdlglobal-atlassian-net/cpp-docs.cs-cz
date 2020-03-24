---
title: Upozornění kompilátoru (úroveň 1) C4068
ms.date: 11/04/2016
f1_keywords:
- C4068
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
ms.openlocfilehash: 9a19acd42836ed678c7e615e1606434f2572c187
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200236"
---
# <a name="compiler-warning-level-1-c4068"></a>Upozornění kompilátoru (úroveň 1) C4068

Neznámá direktiva pragma

Kompilátor ignoroval nerozpoznanou [direktivu pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md). Ujistěte se, že kompilátor, který používáte, povoluje **direktivu pragma** . Následující ukázka generuje C4068:

```cpp
// C4068.cpp
// compile with: /W1
#pragma NotAValidPragmaName   // C4068, use valid name to resolve
int main()
{
}
```
