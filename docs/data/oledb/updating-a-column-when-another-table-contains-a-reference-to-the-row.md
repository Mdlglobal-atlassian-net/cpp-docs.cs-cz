---
title: Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 46de5f54a3ec6525f779a6b55a700429a2a84fef
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039212"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek

Někteří poskytovatelé dokáže detekovat sloupce, které při změně řádku, ale nikoli mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud neexistuje odkaz na řádek, který se pokoušíte aktualizovat. Pokud chcete tento problém vyřešit, vytvořte samostatné přístupový objekt obsahující pouze sloupce, které chcete změnit. Předejte počet přistupujícího objektu do `SetData`.

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)