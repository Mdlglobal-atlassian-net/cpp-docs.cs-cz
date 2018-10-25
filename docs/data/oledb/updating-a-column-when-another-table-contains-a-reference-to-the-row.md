---
title: Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 7998897c80e392326213324804c1809656e051f3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071820"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizace sloupce, pokud jiná tabulka obsahuje odkaz na řádek

Někteří poskytovatelé dokáže detekovat sloupce, které při změně řádku, ale nikoli mnoho poskytovatelů. V důsledku toho aktualizace sloupce, může mít za následek chybu, pokud neexistuje odkaz na řádek, který se pokoušíte aktualizovat. Pokud chcete tento problém vyřešit, vytvořte samostatné přístupový objekt obsahující pouze sloupce, které chcete změnit. Předejte počet přistupujícího objektu do `SetData`.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)