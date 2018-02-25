---
title: "Převod dat nepodporovaných zprostředkovatelem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2fd46e57397eba0e8e732bba586df384951a86dc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem
Pokud příjemce požádá o datový typ, který není podporována zprostředkovatelem, šablony zprostředkovatele technologie OLE DB kód `IRowsetImpl::GetData` Msdadc.dll k převedení datového typu.  
  
 Pokud implementujete rozhraní jako `IRowsetChange` který vyžaduje převod dat, můžete zavolat DLL knihovnu Msdaenum.dll k provést převod. Použití `GetData`, definované v Atldb.h jako příklad.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)