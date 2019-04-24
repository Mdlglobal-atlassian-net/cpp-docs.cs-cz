---
title: Chyba kompilátoru C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: a3c69b05e22c2d267ad07f19a0d0ab60f3eebb94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221863"
---
# <a name="compiler-error-c3625"></a>Chyba kompilátoru C3625

'native_type': nativní typ nejde odvodit ze spravované nebo WinRT typu 'type'

Nativní třída nemůže dědit z WinRT nebo spravované třídy. Další informace najdete v tématu [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3625:

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
