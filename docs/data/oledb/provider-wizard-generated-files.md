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
ms.openlocfilehash: f22c5e21d1f648a8235207713391306b24e0a6cf
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807287"
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem

Průvodce zprostředkovatelem ATL OLE DB generuje následující soubory. V následujících tématech použijte krátký název *vlastní*, ale názvy souborů závisí na volby provedené při vytváření zprostředkovatele.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|*Vlastní*RS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapování sloupců zprostředkovatele.|  
|*Vlastní*DS.h|Implementuje objekt zdroje dat. Tento soubor hlavičky obsahuje vlastnosti zdroje dat na mapě vlastnost.|  
|*Vlastní*RS.h|Implementuje objekty příkazu a sady řádků. Tento soubor hlavičky obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|  
|*Vlastní*Sess.h|Implementuje objekt relace. Tento soubor hlavičky obsahuje mapování vlastnosti pro vlastnosti relace.|  
|*Vlastní*.rgs|Obsahuje objekty registrované generované průvodcem zprostředkovatele OLE DB.|  
  
## <a name="see-also"></a>Viz také  

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)