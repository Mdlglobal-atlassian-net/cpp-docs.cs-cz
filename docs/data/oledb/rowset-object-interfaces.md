---
title: Rozhraní objektu sady řádků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e8a1a5f5256087a8869426489fe01250b16fc598
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340508"
---
# <a name="rowset-object-interfaces"></a>Rozhraní objektu sady řádků
V následující tabulce jsou uvedeny povinných a volitelných rozhraní určené v objektu sady řádků OLE DB.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)|Povinné|Ano|  
|[IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Povinné|Ano|  
|[IConvertType](https://msdn.microsoft.com/library/ms715926.aspx)|Povinné|Ano|  
|[IRowset](https://msdn.microsoft.com/library/ms720986.aspx)|Povinné|Ano|  
|[IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Povinné|Ano|  
|[IChapteredRowset](https://msdn.microsoft.com/library/ms718180.aspx)|Nepovinné|Ne|  
|[IColumnsInfo2](https://msdn.microsoft.com/library/ms712953.aspx)|Nepovinné|Ne|  
|[IColumnsRowset](https://msdn.microsoft.com/library/ms722657.aspx)|Nepovinné|Ne|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Nepovinné|Ano (pomocí knihovny ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/library/ms709832.aspx)|Nepovinné|Ne|  
|[IGetRow](https://msdn.microsoft.com/library/ms718047.aspx)|Nepovinné|Ne|  
|[IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)|Nepovinné|Ano|  
|[IRowsetChapterMember](https://msdn.microsoft.com/library/ms725430.aspx)|Nepovinné|Ne|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/library/ms709700.aspx)|Nepovinné|Ne|  
|[IRowsetFind](https://msdn.microsoft.com/library/ms724221.aspx)|Nepovinné|Ne|  
|[IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx)|Nepovinné (ale vyžaduje pro poskytovatele úroveň 0)|Ano|  
|[IRowsetIndex](https://msdn.microsoft.com/library/ms719604.aspx)|Nepovinné|Ne|  
|[IRowsetLocate](https://msdn.microsoft.com/library/ms721190.aspx)|Nepovinné|Ano|  
|[IRowsetRefresh](https://msdn.microsoft.com/library/ms714892.aspx)|Nepovinné|Ne|  
|[IRowsetScroll](https://msdn.microsoft.com/library/ms712984.aspx)|Nepovinné|Ne|  
|[IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx)|Nepovinné|Ano|  
|[IRowsetView](https://msdn.microsoft.com/library/ms709755.aspx)|Nepovinné|Ne|  
|[ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Nepovinné|Ano|  
|[IRowsetBookmark](https://msdn.microsoft.com/library/ms714246.aspx)|Nepovinné|Ne|  
  
 Implementuje objekt generované v Průvodci řádků `IAccessor`, `IRowset`, a `IRowsetInfo` prostřednictvím dědičnosti. `IAccessorImpl` Váže oba výstupní sloupce. `IRowset` Rozhraní zpracovává načtené řádky a data. `IRowsetInfo` Rozhraní zpracovává vlastnosti sady řádků.  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)