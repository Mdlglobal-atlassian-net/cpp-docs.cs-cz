---
title: "Závažná chyba kompilátoru prostředků RC1120 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1120
dev_langs: C++
helpviewer_keywords: RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9cc1006dad4b0427a4254f4798b206d975e89e03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Závažná chyba kompilátoru prostředků RC1120
Nedostatek paměti potřeby počet bajtů  
  
 Kompilátor prostředků nemá dostatek paměti pro položky, které je uložený v jeho haldy. Obvykle je to výsledek má příliš mnoho symboly.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zvětšete místo odkládacího souboru Windows. Další informace o zvětšení místa odkládacího souboru najdete v části virtuální paměti v nápovědě k systému Windows.  
  
2.  Vyloučení nepotřebných vložené soubory, zejména nepotřebné `#define`prototypy s a funkce.  
  
3.  Rozdělit do dvou nebo více souborů aktuální soubor a jejich kompilace samostatně.  
  
4.  Odeberte jiné programy a ovladače, které jsou spuštěné v systému, což může být využívají poměrně velké množství paměti.