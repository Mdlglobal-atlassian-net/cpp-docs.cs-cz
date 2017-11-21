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
ms.openlocfilehash: cac57f2f4a1175fa1d9f4009e10fd3d0fae2a3b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek
Někteří poskytovatelé může zjistit, které sloupce v řádku změn, ale nelze mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud je odkaz na řádek, který se pokoušíte aktualizovat. Chcete-li tento problém vyřešit, vytvořte samostatně přistupující objekt obsahující pouze sloupce, které chcete změnit. Předat číslo přistupujícího objektu do `SetData`.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)