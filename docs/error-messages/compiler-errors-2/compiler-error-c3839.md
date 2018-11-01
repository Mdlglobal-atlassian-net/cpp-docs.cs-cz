---
title: Chyba kompilátoru C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: b8382213fbe7cc953dafd9610bfb993ba7837947
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613007"
---
# <a name="compiler-error-c3839"></a>Chyba kompilátoru C3839

nejde změnit zarovnání v spravované nebo typ WinRT

Zarovnání proměnné ve spravované nebo typy Windows Runtime se řídí CLR nebo prostředí Windows Runtime a nelze ji změnit pomocí [zarovnat](../../cpp/align-cpp.md).

Následující ukázka generuje C3839:

```
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```