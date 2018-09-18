---
title: Chyba kompilátoru C2665 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b442e1de0481ef3d00742ed201575526332decff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109142"
---
# <a name="compiler-error-c2665"></a>Chyba kompilátoru C2665

'function': Parametr číslo2 žádná přetížení Číslo1 lze převést z typu 'type'

Parametr přetížené funkce nelze převést na požadovaný typ.  Možná řešení:

- Zadejte operátor převodu.

- Použijte explicitní převod.

## <a name="example"></a>Příklad

Následující ukázka generuje C2665.

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```