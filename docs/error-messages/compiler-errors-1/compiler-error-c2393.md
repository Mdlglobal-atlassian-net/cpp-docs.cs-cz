---
title: Chyba kompilátoru C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: cc3c124f1a4daea0f2517a93c6b354b8233aa5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205982"
---
# <a name="compiler-error-c2393"></a>Chyba kompilátoru C2393

> '*symbol*': symbol na základě třídy AppDomain nelze přidělit v segmentu '*segment*'

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Použití proměnných [AppDomain](../../cpp/appdomain.md) znamená, že kompilujete s možností **/clr: Pure** nebo **/clr: Safe**a bezpečný nebo čistý obrázek nemůže obsahovat datové segmenty.

Další informace najdete v tématu věnovaném [kompilaci/clr (Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C2393. Chcete-li tento problém vyřešit, nevytvářejte datový segment.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
