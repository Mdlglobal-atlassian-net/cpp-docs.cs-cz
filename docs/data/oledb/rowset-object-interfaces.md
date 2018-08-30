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
ms.openlocfilehash: 2050a444ca228554cfbb3b6bba2693c55e53c4a2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217547"
---
# <a name="rowset-object-interfaces"></a>Rozhraní objektu sady řádků
V následující tabulce jsou uvedeny povinných a volitelných rozhraní určené v objektu sady řádků OLE DB.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](/previous-versions/windows/desktop/ms719672\(v=vs.85\))|Povinné|Ano|  
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\))|Povinné|Ano|  
|[IConvertType](/previous-versions/windows/desktop/ms715926\(v=vs.85\))|Povinné|Ano|  
|[IRowset](/previous-versions/windows/desktop/ms720986\(v=vs.85\))|Povinné|Ano|  
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\))|Povinné|Ano|  
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180\(v=vs.85\))|Nepovinné|Ne|  
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953\(v=vs.85\))|Nepovinné|Ne|  
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657\(v=vs.85\))|Nepovinné|Ne|  
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Nepovinné|Ano (pomocí knihovny ATL)|  
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832\(v=vs.85\))|Nepovinné|Ne|  
|[IGetRow](/previous-versions/windows/desktop/ms718047\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\))|Nepovinné|Ano|  
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetFind](/previous-versions/windows/desktop/ms724221\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913\(v=vs.85\))|Nepovinné (ale vyžaduje pro poskytovatele úroveň 0)|Ano|  
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\))|Nepovinné|Ano|  
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984\(v=vs.85\))|Nepovinné|Ne|  
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401\(v=vs.85\))|Nepovinné|Ano|  
|[IRowsetView](/previous-versions/windows/desktop/ms709755\(v=vs.85\))|Nepovinné|Ne|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|Nepovinné|Ano|  
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246\(v=vs.85\))|Nepovinné|Ne|  
  
 Implementuje objekt generované v Průvodci řádků `IAccessor`, `IRowset`, a `IRowsetInfo` prostřednictvím dědičnosti. `IAccessorImpl` Váže oba výstupní sloupce. `IRowset` Rozhraní zpracovává načtené řádky a data. `IRowsetInfo` Rozhraní zpracovává vlastnosti sady řádků.  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)