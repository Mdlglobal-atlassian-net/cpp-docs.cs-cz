---
title: Upozornění kompilátoru (úroveň 3) C4265
ms.date: 11/04/2016
f1_keywords:
- C4265
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
ms.openlocfilehash: cfcbd9d9268785b87e45a833b332c276eec01522
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161539"
---
# <a name="compiler-warning-level-3-c4265"></a>Upozornění kompilátoru (úroveň 3) C4265

' class ': třída má virtuální funkce, ale destruktor není virtuální.

Pokud třída má virtuální funkce, ale nevirtuální destruktor, objekty typu nemusí být zničeny správně, pokud je třída zničena pomocí ukazatele základní třídy.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4265:

```cpp
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```
