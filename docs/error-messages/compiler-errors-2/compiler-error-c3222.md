---
title: Chyba kompilátoru C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 96a6b1b81d2d82328dcb4ceaca376f247f785c13
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737943"
---
# <a name="compiler-error-c3222"></a>Chyba kompilátoru C3222

' Parameter ': nelze deklarovat výchozí argumenty pro členské funkce spravovaného nebo typu WinRT nebo obecných funkcí

Není povoleno deklarovat parametr metody s výchozím argumentem. Přetížená forma metody je jedním ze způsobů, jak tento problém obejít. To znamená definovat metodu se stejným názvem bez parametrů a následně inicializovat proměnnou v těle metody.

Následující ukázka generuje C3222:

```cpp
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
