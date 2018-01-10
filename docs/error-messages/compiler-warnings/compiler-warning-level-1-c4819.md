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
ms.workload: cplusplus
ms.openlocfilehash: b515a3f5e840bbc93f37420866023ee778b404ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4819"></a>C4819 kompilátoru upozornění (úroveň 1)
Tento soubor obsahuje znak, který není možné vyjádřit v aktuální znakové stránky (number). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.  
  
 C4819 nastane, když kompiluje soubor zdroj ANSI v systému pomocí znakové stránky, které nelze vyjádřit všechny znaky v souboru.  
  
 Chcete-li vyřešit C4819, uložte soubor ve formátu Unicode. V sadě Visual Studio, vyberte **soubor**, **rozšířené možnosti ukládání**. V **rozšířené možnosti ukládání** dialogovém okně vyberte kódování, které může představovat všechny znaky v souboru – například UTF-8 – a potom zvolte **OK**.