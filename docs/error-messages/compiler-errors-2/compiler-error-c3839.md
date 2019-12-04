---
title: Chyba kompilátoru C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 19a1055a461d76856cc3bccbd9f8af0f0dcff356
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754924"
---
# <a name="compiler-error-c3839"></a>Chyba kompilátoru C3839

nejde změnit zarovnání v spravovaném nebo WinRT typu.

Zarovnání proměnných v spravovaných nebo prostředí Windows Runtimech typech je řízeno modulem CLR nebo prostředí Windows Runtime a nelze je upravovat pomocí [Zarovnání](../../cpp/align-cpp.md).

Následující ukázka generuje C3839:

```cpp
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
