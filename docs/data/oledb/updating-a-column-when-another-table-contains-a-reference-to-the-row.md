---
title: Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 2adca735558033aa9324f37b5a61385b5f48096c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519886"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek

Někteří poskytovatelé dokáže detekovat sloupce, které při změně řádku, ale nikoli mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud neexistuje odkaz na řádek, který se pokoušíte aktualizovat. Pokud chcete tento problém vyřešit, vytvořte samostatné přístupový objekt obsahující pouze sloupce, které chcete změnit. Předejte počet přistupujícího objektu do `SetData`.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)