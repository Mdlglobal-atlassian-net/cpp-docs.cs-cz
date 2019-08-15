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
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501287"
---
# <a name="rowset-object-interfaces"></a>Rozhraní objektu sady řádků

Následující tabulka ukazuje povinná a volitelná rozhraní definovaná OLE DB pro objekt sady řádků.

|Rozhraní|Povinné?|Implementováno pomocí šablon OLE DB?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|Povinné|Ano|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Povinné|Ano|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|Povinné|Ano|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|Povinné|Ano|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Povinné|Ano|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|volitelná,|Ne|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|volitelná,|Ne|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|volitelná,|Ne|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|volitelná,|Ano (přes ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|volitelná,|Ne|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|volitelná,|Ne|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|volitelná,|Ano|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|volitelná,|Ne|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|volitelná,|Ne|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|volitelná,|Ne|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|Volitelné (ale vyžaduje se pro poskytovatele úrovně 0)|Ano|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|volitelná,|Ne|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|volitelná,|Ano|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|volitelná,|Ne|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|volitelná,|Ne|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|volitelná,|Ano|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|volitelná,|Ne|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|volitelná,|Ano|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|volitelná,|Ne|

Průvodcem generovaný objekt sady řádků implementuje `IAccessor`, `IRowset`a `IRowsetInfo` prostřednictvím dědičnosti. `IAccessorImpl` Vytvoří vazby obou výstupních sloupců. Obslužné `IRowset` rutiny rozhraní načítají řádky a data. `IRowsetInfo` Rozhraní zpracovává vlastnosti sady řádků.

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
