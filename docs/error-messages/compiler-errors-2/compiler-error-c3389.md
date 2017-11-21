---
title: "C3389 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3389
dev_langs: C++
helpviewer_keywords: C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 561359afcd9cf694369bd1addb4f641a33a3f989
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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