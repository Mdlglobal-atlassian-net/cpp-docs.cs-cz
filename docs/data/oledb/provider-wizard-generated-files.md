---
title: Poskytovatel souborů vytvořených průvodcem | Dokumentace Microsoftu
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
ms.openlocfilehash: 26e20e0417e2253158930a8d3d055171fe767001
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108401"
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem

Průvodce zprostředkovatelem ATL OLE DB generuje následující soubory. V následujících tématech použijte krátký název "MyProvider", ale názvy souborů záviset na volbě provedené při vytváření poskytovatele.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|MyProviderRS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapování sloupců zprostředkovatele.|  
|MyProviderDS.h|Implementuje objekt zdroje dat. Tento soubor hlavičky obsahuje vlastnosti zdroje dat na mapě vlastnost.|  
|MyProviderRS.h|Implementuje objekty příkazu a sady řádků. Tento soubor hlavičky obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|  
|MyProviderSess.h|Implementuje objekt relace. Tento soubor hlavičky obsahuje mapování vlastnosti pro vlastnosti relace.|  
|MyProvider.rgs|Obsahuje objekty registrované generované průvodcem zprostředkovatele OLE DB.|  
  
## <a name="see-also"></a>Viz také  

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)