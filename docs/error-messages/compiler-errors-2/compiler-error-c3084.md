---
title: Chyba kompilátoru C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 337cd7f37bf94c7a3d5cffe6b167d4661e3b0a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751453"
---
# <a name="compiler-error-c3084"></a>Chyba kompilátoru C3084

' function ': finalizační metoda/destruktor nemůže být ' klíčové slovo '

Finalizační metoda nebo destruktor byl nesprávně deklarována.

Například destruktor by neměl být označen jako Sealed.  Destruktor nebude přístupný pro odvozené typy.  Další informace naleznete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md) a [destruktory a finalizační metody v tématu How to: Define and spotřebovávají Classes andC++Structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3084.

```cpp
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```
