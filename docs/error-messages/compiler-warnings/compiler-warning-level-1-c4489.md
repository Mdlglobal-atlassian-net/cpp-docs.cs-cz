---
title: Kompilátor upozornění (úroveň 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: dd150621ad3474444861982c095ae8a6addb52fa
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779203"
---
# <a name="compiler-warning-level-1-c4489"></a>Kompilátor upozornění (úroveň 1) C4489

"specifikátor": není povolené pro rozhraní metoda "method"; Přepsat specifikátory jsou povolené jenom pro metody třídy ref class a value

Klíčové slovo specifikátor byl nesprávně použit na metodu rozhraní.

Další informace najdete v tématu [specifikátory přepisu](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4489.

```
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```