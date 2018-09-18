---
title: Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek | Dokumentace Microsoftu
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
ms.openlocfilehash: 6d2d3509b51d083290339514083a541ef9a86b64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030656"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek

Někteří poskytovatelé dokáže detekovat sloupce, které při změně řádku, ale nikoli mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud je odkaz na řádek, který se pokoušíte aktualizovat. Pokud chcete tento problém vyřešit, vytvořte samostatné přístupový objekt obsahující pouze sloupce, které chcete změnit. Předejte počet přistupujícího objektu do `SetData`.  
  
## <a name="see-also"></a>Viz také  

[Použití přístupových objektů](../../data/oledb/using-accessors.md)