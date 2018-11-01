---
title: Chyba kompilátoru C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: fcf2bbb01f2aac668ff52884a6ccfb36c66aa89d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445836"
---
# <a name="compiler-error-c2785"></a>Chyba kompilátoru C2785

"declaration1" a 'declaration2' mají rozdílné návratové typy

Návratový typ specializace šablony funkce se liší od návratový typ šablony primární funkce.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte všechny specializace šablony funkce pro zajištění konzistence.

## <a name="example"></a>Příklad

Následující ukázka generuje C2785:

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```