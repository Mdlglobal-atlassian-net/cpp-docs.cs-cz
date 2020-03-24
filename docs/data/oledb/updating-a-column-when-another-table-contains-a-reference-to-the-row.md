---
title: Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 95cddfd5f030c7bd8d1220cf040de4bc5a883226
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209479"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek

Někteří poskytovatelé můžou zjistit, které sloupce se v řádku změní, ale mnoho poskytovatelů nedokáže. V důsledku toho může aktualizace sloupce způsobit chybu, pokud existuje odkaz na řádek, který se pokoušíte aktualizovat. Chcete-li tento problém vyřešit, vytvořte samostatný přistupující objekt, který uchovává pouze sloupce, které chcete změnit. Předejte počet přistupujících objektů do `SetData`.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
