---
title: Chyba kompilátoru C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 889d9a108ab0dfb0101fb9ec9c367db9378b1128
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757134"
---
# <a name="compiler-error-c3809"></a>Chyba kompilátoru C3809

' class ': typ spravovaný nebo WinRT nemůže mít žádné funkce/třídy/rozhraní Friend.

Spravované typy a typy prostředí Windows Runtime nedovolují přátele. Chcete-li tuto chybu opravit, Nedeklarujte přátele uvnitř spravovaných nebo prostředí Windows Runtimech typů.

Následující ukázka generuje C3809:

```cpp
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```
