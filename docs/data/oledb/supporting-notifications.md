---
title: Podpora oznámení
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: d29f84a0a5b33d55c0a04a4c758050cf9746f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209541"
---
# <a name="supporting-notifications"></a>Podpora oznámení

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementace rozhraní bodu připojení na poskytovateli a příjemci

Pro implementaci oznámení musí třída poskytovatele dědit z [IRowsetNotifyCP –](../../data/oledb/irowsetnotifycp-class.md) a [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` implementuje web poskytovatele pro rozhraní připojovacího bodu rozhraní [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)). `IRowsetNotifyCP` implementuje všesměrové funkce pro poradenství naslouchací procesy v bodu připojení `IID_IRowsetNotify` změny obsahu sady řádků.

Také je nutné implementovat a zaregistrovat `IRowsetNotify` na příjemce (označované také jako jímka) pomocí [IRowsetNotifyImpl –](../../data/oledb/irowsetnotifyimpl-class.md) , aby příjemce mohl zpracovávat oznámení. Informace o implementaci rozhraní bodu připojení na příjemce najdete v tématu [přijímání oznámení](../../data/oledb/receiving-notifications.md).

Třída musí mít také mapu, která definuje položku bodu připojení, například:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Přidání rozhraní IRowsetNotify

Chcete-li přidat `IRowsetNotify`, je nutné přidat `IConnectionPointContainerImpl<rowset-name>` a `IRowsetNotifyCP<rowset-name>` do svého řetězu dědičnosti.

Zde je například řetězec dědičnosti pro `RUpdateRowset` v [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> Vzorový kód se může lišit od toho, co je uvedeno zde. měli byste se považovat za vzorový kód jako aktuálnější verzi.

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)

class RUpdateRowset :
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,
      public IConnectionPointContainerImpl<RUpdateRowset>,
      public IRowsetNotifyCP<RUpdateRowset>
```

### <a name="setting-com-map-entries"></a>Nastavení položek map COM

Také je nutné přidat následující do mapy modelu COM v sadě řádků:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Tato makra umožňují všem uživatelům volat `QueryInterface` pro váš kontejner přípojných bodů (základ `IRowsetNotify`) k vyhledání požadovaného rozhraní na vašem poskytovateli. Příklad použití bodů připojení najdete v tématu Ukázka a kurz pro ATL.

### <a name="setting-connection-point-map-entries"></a>Nastavení položek mapy bodu připojení

Také je nutné přidat mapu spojovacího bodu. Měl by vypadat nějak takto:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Tato mapa spojovacího bodu umožňuje komponentě vyhledat `IRowsetNotify` rozhraní, které se ve vašem poskytovateli najde.

### <a name="setting-properties"></a>Vlastnosti nastavení

Do poskytovatele také musíte přidat následující vlastnosti. Stačí přidat vlastnosti založené na rozhraních, která podporujete.

|Vlastnost|Přidat, Pokud podporujete|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|Vždy|
|DBPROP_NOTIFICATIONGRANULARITY|Vždy|
|DBPROP_NOTIFICATIONPHASES|Vždy|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|Vždy|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|Vždy|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

Většina implementace oznámení je již vložena v šablonách poskytovatele OLE DB. Pokud nepřidáte `IRowsetNotifyCP` do svého řetězu dědičnosti, kompilátor odebere veškerý tento kód z datového proudu kompilace, takže velikost vašeho kódu bude menší.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)
