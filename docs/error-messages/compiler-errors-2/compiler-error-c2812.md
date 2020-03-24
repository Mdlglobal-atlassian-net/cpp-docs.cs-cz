---
title: Chyba kompilátoru C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202095"
---
# <a name="compiler-error-c2812"></a>Chyba kompilátoru C2812

> Import \#není podporován s možností/CLR: Pure a/CLR: safe.

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

[direktiva #import](../../preprocessor/hash-import-directive-cpp.md) není podporována s možností **/clr: Pure** a **/clr: Safe** , protože `#import` vyžaduje použití nativních knihoven podpory kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
