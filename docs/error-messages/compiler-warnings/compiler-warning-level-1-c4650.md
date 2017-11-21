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
ms.openlocfilehash: 8671b72e244a29698fa31da40de8147cdd348130
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4650"></a>C4650 kompilátoru upozornění (úroveň 1)
informace o ladění není v předkompilovaných hlaviček; pouze globální symboly z hlavičky bude k dispozici  
  
 Předkompilovaný hlavičkový soubor nebyl kompilovat s symbolické ladicí informace společnosti Microsoft.  
  
 Při propojení, bude výsledný soubor knihovny DLL nebo spustitelný soubor nebude zahrnovat ladicí informace pro lokální symboly obsažené v předkompilovaných hlaviček.  
  
 Toto upozornění předejít nutnosti rekompilace předkompilovaný hlavičkový soubor s [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost příkazového řádku.