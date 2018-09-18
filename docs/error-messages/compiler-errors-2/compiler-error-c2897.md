---
title: Chyba kompilátoru C2897 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2897
dev_langs:
- C++
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d05663b913a3e310c091b62a81483f28bbf2c09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049824"
---
# <a name="compiler-error-c2897"></a>Chyba kompilátoru C2897

destruktor nebo finalizační metoda nemůže být šablona – funkce

Destruktory a finalizační metody nemohou být přetíženy, tak deklarace destruktoru jako šablona (které by se definovat sadu destruktory) není povolený.

Následující ukázka generuje C2897:

## <a name="example"></a>Příklad

Následující ukázka generuje C2897.

```
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C2897.

```
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```