---
title: Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 17d260f522432a78729c9998c518398dfa41275a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102882"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek
Někteří poskytovatelé může zjistit, které sloupce v řádku změn, ale nelze mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud je odkaz na řádek, který se pokoušíte aktualizovat. Chcete-li tento problém vyřešit, vytvořte samostatně přistupující objekt obsahující pouze sloupce, které chcete změnit. Předat číslo přistupujícího objektu do `SetData`.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)