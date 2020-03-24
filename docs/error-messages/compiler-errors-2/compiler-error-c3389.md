---
title: Chyba kompilátoru C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201133"
---
# <a name="compiler-error-c3389"></a>Chyba kompilátoru C3389

> __declspec (*klíčové slovo*) nelze použít s možností/CLR: pure nebo/CLR: safe.

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Použitý modifikátor [__declspec](../../cpp/declspec.md) implikuje stav každého procesu.  [/clr: Pure](../../build/reference/clr-common-language-runtime-compilation.md) implikuje stav na jednu [doménu AppDomain](../../cpp/appdomain.md) .  Proto není povolená deklarace proměnné s modifikátorem `keyword` **__declspec** a kompilování s možností **/clr: Pure** .

## <a name="example"></a>Příklad

Následující ukázka generuje C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
