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
ms.openlocfilehash: 24da0ab4b3ab27cdb9a70c0f9cc05e3ca86e117d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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