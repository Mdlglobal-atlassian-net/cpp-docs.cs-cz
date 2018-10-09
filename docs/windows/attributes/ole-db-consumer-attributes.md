---
title: Atributy příjemce technologie OLE DB (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], database
- attributes [C++/CLI], data access
- databases [C++], attributes
- OLE DB consumers [C++], attributes
- database attributes [C++/CLI]
- attributes [C++/CLI], OLE DB consumer
ms.assetid: 017b591f-8f9a-42b4-84d5-cc42a21ab0cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35051c565a18ba61de53813ce57be147140cc468
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789547"
---
# <a name="ole-db-consumer-attributes"></a>Atributy příjemce technologie OLE DB
Atributy příjemce technologie OLE DB vložit kód, na základě [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-reference.md), chcete-li vytvořit pracovní technologie OLE DB příjemce, který provádí úlohy, jako je otevření tabulek, provádění příkazů a přístup k datům.
  
|Atribut|Popis|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Vytvoří vazbu sloupců v sadě řádků a sváže s odpovídající přístupového objektu map.|
|[db_column](db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](db-command.md)|Provede příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr.|
|[db_source](db-source.md)|Vytvoří a zapouzdřuje připojení prostřednictvím poskytovatele ke zdroji dat.|
|[db_table](db-table.md)|Otevře se tabulku OLE DB.|
  
## <a name="see-also"></a>Viz také

[Atributy podle skupin](attributes-by-group.md)