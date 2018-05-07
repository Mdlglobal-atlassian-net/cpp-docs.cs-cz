---
title: Převod dat nepodporovaných zprostředkovatelem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0be19345ff6c425cfbc020f2096ca82680586d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="converting-data-not-supported-by-the-provider"></a>Převod dat nepodporovaných zprostředkovatelem
Pokud příjemce požádá o datový typ, který není podporována zprostředkovatelem, šablony zprostředkovatele technologie OLE DB kód `IRowsetImpl::GetData` Msdadc.dll k převedení datového typu.  
  
 Pokud implementujete rozhraní jako `IRowsetChange` který vyžaduje převod dat, můžete zavolat DLL knihovnu Msdaenum.dll k provést převod. Použití `GetData`, definované v Atldb.h jako příklad.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)