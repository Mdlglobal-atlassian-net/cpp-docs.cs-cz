---
title: Chyba kompilátoru C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: 88b071f38cf41db9c929d25ffd526b3f2b7ca468
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531817"
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