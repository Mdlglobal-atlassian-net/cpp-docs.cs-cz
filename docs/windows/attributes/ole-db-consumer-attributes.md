---
title: Atributy příjemce OLE DB (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
ms.openlocfilehash: 67f58d6dd32360248c6437f66fa7042871bc4ea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214678"
---
# <a name="ole-db-consumer-attributes"></a>Atributy příjemce technologie OLE DB
Atributy příjemce OLE DB vloží kód založený na [šablonách spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)a vytvoří pracovní OLE DB příjemce, který provádí úkoly, jako je například otevírání tabulek, spouštění příkazů a přístup k datům.

|Atribut|Popis|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Vytvoří vazby sloupců v sadě řádků a vytvoří jejich vazby k odpovídajícím mapám přistupujícímu objektu.|
|[db_column](db-column.md)|Váže zadaný sloupec na sadu řádků.|
|[db_command](db-command.md)|Spustí příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadanou členskou proměnnou ke vstupnímu nebo výstupnímu parametru.|
|[db_source](db-source.md)|Vytvoří a zapouzdří připojení prostřednictvím poskytovatele ke zdroji dat.|
|[db_table](db-table.md)|Otevře tabulku OLE DB.|

## <a name="see-also"></a>Viz také

[Atributy podle skupin](attributes-by-group.md)
