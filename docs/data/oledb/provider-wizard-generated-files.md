---
title: Poskytovatel souborů vytvořených průvodcem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: ac23f06bf1ae697ecd627d493aa5902219488138
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106005"
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem
Průvodce zprostředkovatele OLE DB ATL generuje následující soubory. V následujících tématech použijte krátký název "MyProvider", ale přesné názvy souborů závisí na možnost, kterou zvolili při vytváření zprostředkovatele.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|MyProviderRS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapu sloupců poskytovatele.|  
|MyProviderDS.h|Implementuje objekt zdroje dat. Tento soubor záhlaví obsahuje mapu vlastností pro vlastnosti zdroje dat.|  
|MyProviderRS.h|Implementuje objekty příkazu a sady řádků. Tento soubor záhlaví obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|  
|MyProviderSess.h|Implementuje objekt relace. Tento soubor záhlaví obsahuje mapu vlastností pro vlastnosti relace.|  
|MyProvider.rgs|Obsahuje registrované objekty generované průvodcem zprostředkovatele OLE DB.|  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)