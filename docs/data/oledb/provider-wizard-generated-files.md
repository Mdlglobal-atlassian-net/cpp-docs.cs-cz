---
title: Poskytovatel souborů vytvořených průvodcem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 40422ac7894523a28a2135b7f5005eb1f11d36c8
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216367"
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem

**Průvodce zprostředkovatelem ATL OLE DB** generuje následující soubory. V následujících tématech použijte krátký název *vlastní*, ale názvy souborů závisí na volby provedené při vytváření zprostředkovatele.

|Název souboru|Popis|
|---------------|-----------------|
|*Vlastní*RS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapování sloupců zprostředkovatele.|
|*Vlastní*DS.h|Implementuje objekt zdroje dat. Tento soubor hlavičky obsahuje vlastnosti zdroje dat na mapě vlastnost.|
|*Vlastní*RS.h|Implementuje objekty příkazu a sady řádků. Tento soubor hlavičky obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|
|*Vlastní*Sess.h|Implementuje objekt relace. Tento soubor hlavičky obsahuje mapování vlastnosti pro vlastnosti relace.|
|*Vlastní*.rgs|Obsahuje objekty registrované generovaných **Průvodce zprostředkovatelem technologie OLE DB**.|

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
