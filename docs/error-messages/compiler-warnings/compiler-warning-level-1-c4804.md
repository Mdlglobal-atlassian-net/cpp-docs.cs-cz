---
title: Upozornění (úroveň 1) C4804 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd1d1659ad6c8716cebf37a99f234af7b41f5745
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094803"
---
# <a name="compiler-warning-level-1-c4804"></a>Kompilátor upozornění (úroveň 1) C4804

'operation': potenciálně nebezpečné používání typu 'bool' v operaci

Toto upozornění je při použití `bool` proměnné nebo hodnota neočekávaným způsobem. Například C4804 se vygeneruje, pokud používáte operátorů, například záporné unární operátor (**-**) nebo doplňkovým operátorem (`~`). Kompilátor vyhodnotí výraz.

## <a name="example"></a>Příklad

Následující ukázka generuje C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```