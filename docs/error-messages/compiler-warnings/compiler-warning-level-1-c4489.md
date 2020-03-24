---
title: Upozornění kompilátoru (úroveň 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: e9811e9f9c17463fdcd550ffd82af4f81a40bb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186605"
---
# <a name="compiler-warning-level-1-c4489"></a>Upozornění kompilátoru (úroveň 1) C4489

' specifikátor ': není povoleno pro metodu rozhraní ' Method '; Specifikátory přepsání jsou povolené jenom pro metody třídy ref class a value class.

Klíčové slovo specifikátoru bylo v metodě rozhraní nesprávně použito.

Další informace najdete v tématu [specifikátory přepisu](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4489.

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```
