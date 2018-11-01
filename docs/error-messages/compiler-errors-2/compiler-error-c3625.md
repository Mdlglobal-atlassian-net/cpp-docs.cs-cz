---
title: Chyba kompilátoru C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: 08ad1d09cb9149811566f67a585a718340254de9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635391"
---
# <a name="compiler-error-c3625"></a>Chyba kompilátoru C3625

'native_type': nativní typ nejde odvodit ze spravované nebo WinRT typu 'type'

Nativní třída nemůže dědit z WinRT nebo spravované třídy. Další informace najdete v tématu [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3625:

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
