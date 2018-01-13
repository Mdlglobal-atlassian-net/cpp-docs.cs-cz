---
title: "Upozornění linkerů Lnk4006 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4006
dev_langs: C++
helpviewer_keywords: LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 021961029d274172119ae92aa10cc6a236dd973b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4006"></a>Upozornění linkerů LNK4006
symbol již definována v objektu. druhý definice ignorovat  
  
 V dané `symbol`, zobrazují v jeho dekorované formuláře, násobkem byl definován. Když je zjištěna toto upozornění, `symbol` bude přidán dvakrát, ale použije se jenom jeho první formulář.  
  
 Toto upozornění můžete získat, pokud se pokusíte sloučit dva knihovny importu do jednoho.  
  
 Pokud se znovu sestavit běhové knihovny jazyka C, můžete tuto zprávu ignorovat.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  V dané `symbol` může být zabalené funkce, vytvořený kompilací s [/Gy](../../build/reference/gy-enable-function-level-linking.md). Tento symbol byl součástí více než jeden soubor, ale byl změněn mezi kompilace. Znovu zkompiluje všechny soubory, které zahrnují `symbol`.  
  
2.  V dané `symbol` může byla definována jinak v dva objekty člen v různé knihovny.  
  
3.  Absolutní může mít dvakrát, definována s jinou hodnotou v každé definici.  
  
4.  Pokud při kombinování knihovny, neobdrží chybovou zprávu `symbol` již existuje v knihovně, který se přidává do.