---
title: Chyba kompilátoru C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 39ca693aed3f08e7b2df3d687f94d93384393f23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566852"
---
# <a name="compiler-error-c2393"></a>Chyba kompilátoru C2393

> "*symbol*': symbol na úrovni appdomain nemůže být alokovaný v segmentu"*segmentu*.

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Použití [appdomain](../../cpp/appdomain.md) proměnné znamená, že při kompilaci s **/CLR: pure** nebo **/CLR: safe**, a bezpečné nebo čistě bitové kopie nemůže obsahovat segmenty data.

Zobrazit [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C2393. Chcete-li vyřešit tento problém, nevytvářejte datový segment.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```