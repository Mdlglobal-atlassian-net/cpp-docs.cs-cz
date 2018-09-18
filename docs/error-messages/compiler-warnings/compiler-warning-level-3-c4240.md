---
title: Upozornění (úroveň 3) C4240 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4240
dev_langs:
- C++
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f3c059e63bcca9bbde9e863cc17c9e240e4f78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057012"
---
# <a name="compiler-warning-level-3-c4240"></a>Kompilátor upozornění (úroveň 3) C4240

používá se nestandardní rozšíření: přístup k "classname" teď definovaný jako "specifikátor přístupu", dřív byl definovaný jako "přístup specifikátor"

V části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), nelze změnit přístup na vnořenou třídu. V části výchozí rozšíření Microsoft (/Ze) je to možné, se toto upozornění.

## <a name="example"></a>Příklad

```
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```