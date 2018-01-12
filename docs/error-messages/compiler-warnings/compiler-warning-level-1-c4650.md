---
title: "Kompilátoru (úroveň 1) upozornění C4650 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4650
dev_langs: C++
helpviewer_keywords: C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af10d05562c0c60c6a010e105441533362d058df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4650"></a>C4650 kompilátoru upozornění (úroveň 1)
informace o ladění není v předkompilovaných hlaviček; pouze globální symboly z hlavičky bude k dispozici  
  
 Předkompilovaný hlavičkový soubor nebyl kompilovat s symbolické ladicí informace společnosti Microsoft.  
  
 Při propojení, bude výsledný soubor knihovny DLL nebo spustitelný soubor nebude zahrnovat ladicí informace pro lokální symboly obsažené v předkompilovaných hlaviček.  
  
 Toto upozornění předejít nutnosti rekompilace předkompilovaný hlavičkový soubor s [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost příkazového řádku.