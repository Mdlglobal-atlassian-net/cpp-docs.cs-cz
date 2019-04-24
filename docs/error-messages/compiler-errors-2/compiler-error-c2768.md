---
title: Chyba kompilátoru C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: 9c0fb8fb0a98830aaf061ba980e7bdd7903f25e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257611"
---
# <a name="compiler-error-c2768"></a>Chyba kompilátoru C2768

'function': Neplatné použití explicitních argumentů šablony

Kompilátor nebyl schopen určit, jestli definici funkce, byl by mělo být explicitní specializace šablony funkcí nebo pokud definice funkce měla být pro novou funkci.

Tato chyba byla zavedena v Visual Studio .NET 2003, vylepšení kompilátoru shoda v rámci.

Následující ukázka generuje C2768:

```
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