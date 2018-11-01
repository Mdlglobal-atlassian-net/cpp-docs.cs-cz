---
title: Rozhraní objektu sady řádků
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: 739c7d94e5df2d5edddc00bd3ae2703e07435c23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641009"
---
# <a name="rowset-object-interfaces"></a>Rozhraní objektu sady řádků

V následující tabulce jsou uvedeny povinných a volitelných rozhraní určené v objektu sady řádků OLE DB.

|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672)|Povinné|Ano|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541)|Povinné|Ano|
|[IConvertType](/previous-versions/windows/desktop/ms715926)|Povinné|Ano|
|[IRowset](/previous-versions/windows/desktop/ms720986)|Povinné|Ano|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541)|Povinné|Ano|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180)|volitelná,|Ne|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953)|volitelná,|Ne|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657)|volitelná,|Ne|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|volitelná,|Ano (pomocí knihovny ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832)|volitelná,|Ne|
|[IGetRow](/previous-versions/windows/desktop/ms718047)|volitelná,|Ne|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790)|volitelná,|Ano|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430)|volitelná,|Ne|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700)|volitelná,|Ne|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221)|volitelná,|Ne|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913)|Nepovinné (ale vyžaduje pro poskytovatele úroveň 0)|Ano|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604)|volitelná,|Ne|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190)|volitelná,|Ano|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892)|volitelná,|Ne|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984)|volitelná,|Ne|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401)|volitelná,|Ano|
|[IRowsetView](/previous-versions/windows/desktop/ms709755)|volitelná,|Ne|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|volitelná,|Ano|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246)|volitelná,|Ne|

Implementuje objekt generované v Průvodci řádků `IAccessor`, `IRowset`, a `IRowsetInfo` prostřednictvím dědičnosti. `IAccessorImpl` Váže oba výstupní sloupce. `IRowset` Rozhraní zpracovává načtené řádky a data. `IRowsetInfo` Rozhraní zpracovává vlastnosti sady řádků.

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
