---
title: Upozornění linkerů Lnk4006 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 261d5dcc27c44291ddc6de4a6440cde040a84ed7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302552"
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