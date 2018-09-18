---
title: Chyba kompilátoru C2879 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2879
dev_langs:
- C++
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 632142ea0efd8a9d009f18b898213cfa92514b16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042473"
---
# <a name="compiler-error-c2879"></a>Chyba kompilátoru C2879

'symbol': pouze existujícího oboru názvů může být dán alternativní název definice aliasu oboru názvů

Nelze vytvořit [aliasu oboru názvů](../../cpp/namespaces-cpp.md#namespace_aliases) symbol než obor názvů.

Následující ukázka generuje C2879:

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```