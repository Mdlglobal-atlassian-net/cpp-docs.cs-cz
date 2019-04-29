---
title: Chyba kompilátoru C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: 88b071f38cf41db9c929d25ffd526b3f2b7ca468
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382954"
---
# <a name="compiler-error-c2812"></a>Chyba kompilátoru C2812

> \#Import není podporován s parametrem/CLR: pure a/CLR: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

[#import – direktiva](../../preprocessor/hash-import-directive-cpp.md) nepodporuje **/CLR: pure** a **/CLR: safe** protože `#import` vyžaduje použití nativního kompilátoru podpůrné knihovny.

## <a name="example"></a>Příklad

Následující ukázka generuje C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```