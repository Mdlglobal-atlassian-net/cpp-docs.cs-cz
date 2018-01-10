---
title: "Poskytovatel souborů vytvořených průvodcem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 27fb95e5dc1c417d3dfb03217463a8ef683f3710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem
Průvodce zprostředkovatele OLE DB ATL generuje následující soubory. V následujících tématech použijte krátký název "MyProvider", ale přesné názvy souborů závisí na možnost, kterou zvolili při vytváření zprostředkovatele.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|MyProviderRS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapu sloupců poskytovatele.|  
|MyProviderDS.h|Implementuje objekt zdroje dat. Tento soubor záhlaví obsahuje mapu vlastností pro vlastnosti zdroje dat.|  
|Souboru MyProviderRS.h|Implementuje objekty příkazu a sady řádků. Tento soubor záhlaví obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|  
|MyProviderSess.h|Implementuje objekt relace. Tento soubor záhlaví obsahuje mapu vlastností pro vlastnosti relace.|  
|MyProvider.rgs|Obsahuje registrované objekty generované průvodcem zprostředkovatele OLE DB.|  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)