---
title: Chyba kompilátoru C3633 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3633
dev_langs:
- C++
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aaa4712fb571d56166204655aff95153ac328ce6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078267"
---
# <a name="compiler-error-c3633"></a>Chyba kompilátoru C3633

nelze definovat 'člen' jako člen spravovaného 'typu'

Datové členy referenční třídy CLR nemůže být typu POD C++.  Můžete vytvořit pouze instanci nativní typ POD typu CLR.  Například typ POD nemůže obsahovat kopírovací konstuktor ani operátor přiřazení.

## <a name="example"></a>Příklad

Následující ukázka generuje C3633.

```
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```
