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
ms.openlocfilehash: 6f0f60a1096c070d28be3b7af161bbb924fb20dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3389"></a>C3389 chyby kompilátoru
__declspec(Keyword) nelze použít s/clr: pure nebo/CLR: safe  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 A [__declspec](../../cpp/declspec.md) znamená modifikátor používá za stav procesu.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) znamená za [appdomain](../../cpp/appdomain.md) stavu.  Tedy deklarace proměnné s `keyword` **__declspec** modifikátor a kompilace s **/CLR: pure** není povolen.  
  
 Následující ukázka generuje C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```