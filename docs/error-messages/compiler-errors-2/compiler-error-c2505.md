---
title: Chyba kompilátoru C2505 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2505
dev_langs:
- C++
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6bd22d7a25311b14ed599c6693bfa0c7913b304
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109168"
---
# <a name="compiler-error-c2505"></a>Chyba kompilátoru C2505

'symbol': "__declspec(modifer)" dá používat jedině pro deklarace nebo definice globálních objektů nebo statických datových členů

A `__declspec` modifikátor, který je navržený pro použití pouze v globálním oboru byla použita ve funkci.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [procesu](../../cpp/process.md).

Následující ukázka generuje C2505:

```
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```