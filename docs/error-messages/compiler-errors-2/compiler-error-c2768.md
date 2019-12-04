---
title: Chyba kompilátoru C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: bcc801bb5802598e936d577f08729214bb7e13a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759786"
---
# <a name="compiler-error-c2768"></a>Chyba kompilátoru C2768

' function ': Neplatné použití explicitních argumentů šablony

Kompilátor nemohl určit, jestli by definice funkce měla být explicitní specializací šablony funkce, nebo jestli by definice funkce měla být pro novou funkci.

Tato chyba byla představena v aplikaci Visual Studio .NET 2003 jako součást vylepšení shody kompilátoru.

Následující ukázka generuje C2768:

```cpp
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```
