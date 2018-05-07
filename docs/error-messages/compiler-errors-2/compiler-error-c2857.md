---
title: C2857 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bb2ec5047646bea420bf109f18a72d87a8f7c44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2857"></a>C2857 chyby kompilátoru
' #include ' příkaz určený s možností příkazového řádku /Ycfilename nebyl nalezen ve zdrojovém souboru  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md) možnost určuje název souboru zahrnout, které nejsou součástí zdrojového souboru kompilován.  
  
 Tato chyba může být způsobeno `#include` příkaz v bloku Podmíněná kompilace, která není zkompilovat.