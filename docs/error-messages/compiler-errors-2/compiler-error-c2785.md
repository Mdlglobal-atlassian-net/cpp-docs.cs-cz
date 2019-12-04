---
title: Chyba kompilátoru C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: 6aff2e5c96e3c79fc748d8a95779d6a08647ab03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739620"
---
# <a name="compiler-error-c2785"></a>Chyba kompilátoru C2785

' declaration1 ' a ' declaration2 ' mají rozdílné návratové typy

Návratový typ specializace šablony funkce se liší od návratového typu šablony primární funkce.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Kontroluje konzistenci všech specializací šablony funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C2785:

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
