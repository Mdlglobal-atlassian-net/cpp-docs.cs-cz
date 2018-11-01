---
title: Chyba kompilátoru C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 7659c17d999a8720ffb0ccdcdb631b27949167b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572676"
---
# <a name="compiler-error-c3084"></a>Chyba kompilátoru C3084

'function': finalizační metodu nebo destruktor nemůže být "– klíčové slovo.

Finalizační metodu nebo destruktor byl deklarován nesprávně.

Například by neměla destruktor označené jako sealed.  Destruktor nebudou k dispozici pro odvozené typy.  Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md) a [destruktory a finalizační metody v tom, jak: definice a používání tříd a struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3084.

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```