---
title: "Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4c5fdf37cedd2c20430f87e15446244321c68bdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek
Někteří poskytovatelé může zjistit, které sloupce v řádku změn, ale nelze mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud je odkaz na řádek, který se pokoušíte aktualizovat. Chcete-li tento problém vyřešit, vytvořte samostatně přistupující objekt obsahující pouze sloupce, které chcete změnit. Předat číslo přistupujícího objektu do `SetData`.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)