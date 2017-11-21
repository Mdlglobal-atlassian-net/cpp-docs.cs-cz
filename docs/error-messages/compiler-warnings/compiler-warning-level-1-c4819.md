---
title: "Kompilátoru (úroveň 1) upozornění C4819 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4819
dev_langs: C++
helpviewer_keywords: C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea22f9462ee674610ae3bbd2a55d86a048a63c83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4819"></a>C4819 kompilátoru upozornění (úroveň 1)
Tento soubor obsahuje znak, který není možné vyjádřit v aktuální znakové stránky (number). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.  
  
 C4819 nastane, když kompiluje soubor zdroj ANSI v systému pomocí znakové stránky, které nelze vyjádřit všechny znaky v souboru.  
  
 Chcete-li vyřešit C4819, uložte soubor ve formátu Unicode. V sadě Visual Studio, vyberte **soubor**, **rozšířené možnosti ukládání**. V **rozšířené možnosti ukládání** dialogovém okně vyberte kódování, které může představovat všechny znaky v souboru – například UTF-8 – a potom zvolte **OK**.