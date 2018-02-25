---
title: "Rozhraní objektu sady řádků | Microsoft Docs"
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
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 211fb5bbd0a950eff5f954d1c23b3dc993badb0d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="rowset-object-interfaces"></a>Rozhraní objektu sady řádků
V následující tabulce jsou povinné a nepovinné rozhraní definované v objektu sady řádků OLE DB.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)|Povinné|Ano|  
|[IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)|Povinné|Ano|  
|[IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx)|Povinné|Ano|  
|[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)|Povinné|Ano|  
|[IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)|Povinné|Ano|  
|[IChapteredRowset](https://msdn.microsoft.com/en-us/library/ms718180.aspx)|Nepovinné|Ne|  
|[IColumnsInfo2](https://msdn.microsoft.com/en-us/library/ms712953.aspx)|Nepovinné|Ne|  
|[IColumnsRowset](https://msdn.microsoft.com/en-us/library/ms722657.aspx)|Nepovinné|Ne|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Nepovinné|Ano (prostřednictvím ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/en-us/library/ms709832.aspx)|Nepovinné|Ne|  
|[IGetRow](https://msdn.microsoft.com/en-us/library/ms718047.aspx)|Nepovinné|Ne|  
|[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)|Nepovinné|Ano|  
|[IRowsetChapterMember](https://msdn.microsoft.com/en-us/library/ms725430.aspx)|Nepovinné|Ne|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/en-us/library/ms709700.aspx)|Nepovinné|Ne|  
|[IRowsetFind](https://msdn.microsoft.com/en-us/library/ms724221.aspx)|Nepovinné|Ne|  
|[IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx)|Nepovinné (ale požadované pro zprostředkovatele úrovně 0)|Ano|  
|[IRowsetIndex](https://msdn.microsoft.com/en-us/library/ms719604.aspx)|Nepovinné|Ne|  
|[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)|Nepovinné|Ano|  
|[IRowsetRefresh](https://msdn.microsoft.com/en-us/library/ms714892.aspx)|Nepovinné|Ne|  
|[IRowsetScroll](https://msdn.microsoft.com/en-us/library/ms712984.aspx)|Nepovinné|Ne|  
|[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)|Nepovinné|Ano|  
|[IRowsetView](https://msdn.microsoft.com/en-us/library/ms709755.aspx)|Nepovinné|Ne|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Nepovinné|Ano|  
|[IRowsetBookmark](https://msdn.microsoft.com/en-us/library/ms714246.aspx)|Nepovinné|Ne|  
  
 Implementuje objekt generované v Průvodci řádků `IAccessor`, `IRowset`, a `IRowsetInfo` prostřednictvím dědičnosti. `IAccessorImpl` Váže oba výstupní sloupce. `IRowset` Rozhraní zpracovává načtené řádky a data. `IRowsetInfo` Rozhraní zpracovává vlastnosti řádků.  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)