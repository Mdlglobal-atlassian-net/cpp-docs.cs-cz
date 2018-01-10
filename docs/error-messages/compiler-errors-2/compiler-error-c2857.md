---
title: "C2857 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2857
dev_langs: C++
helpviewer_keywords: C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c4bf637f0abb5affdb21deb8e081c8b5156afd88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2857"></a>C2857 chyby kompilátoru
' #include ' příkaz určený s možností příkazového řádku /Ycfilename nebyl nalezen ve zdrojovém souboru  
  
 [/Yc](../../build/reference/yc-create-precompiled-header-file.md) možnost určuje název souboru zahrnout, které nejsou součástí zdrojového souboru kompilován.  
  
 Tato chyba může být způsobeno `#include` příkaz v bloku Podmíněná kompilace, která není zkompilovat.