---
title: C3389 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b540f87458c75ddf7d57626b6251248652b96213
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704302"
---
# <a name="compiler-error-c3389"></a>C3389 chyby kompilátoru

> __declspec (*– klíčové slovo*) nelze použít s/clr: pure nebo/CLR: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

A [__declspec](../../cpp/declspec.md) znamená modifikátor používá za stav procesu.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) znamená za [appdomain](../../cpp/appdomain.md) stavu.  Tedy deklarace proměnné s `keyword` **__declspec** modifikátor a kompilace s **/CLR: pure** není povolen.

## <a name="example"></a>Příklad

Následující ukázka generuje C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```