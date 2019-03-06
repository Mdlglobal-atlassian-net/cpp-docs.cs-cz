---
title: Příjem oznámení
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 67f7eb5f77dc68b57f04ab4d016680255cb1ae86
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416017"
---
# <a name="receiving-notifications"></a>Příjem oznámení

OLE DB poskytuje rozhraní pro příjem oznámení, když dojde k událostem. Tyto možnosti jsou popsány v [oznámení objektu OLE DB](/previous-versions/windows/desktop/ms725406(v=vs.85)) v **OLE DB referenční informace pro programátory**. Nastavení těchto událostí používá standardní mechanismus bodu připojení COM. Například objekt knihovny ATL, který chce, aby se k načtení událostí prostřednictvím `IRowsetNotify` implementuje `IRowsetNotify` rozhraní přidáním `IRowsetNotify` do seznamu odvozené třídy, která bude vystavená prostřednictvím COM_INTERFACE_ENTRY makra.

`IRowsetNotify` má tři metody, které mohou být volány v různých časech. Pokud chcete reagovat na pouze jednu z těchto metod, můžete použít [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) třídu, která vrátí E_NOTIMPL pro metody nemusí.

Když vytvoříte sadu řádků, je zapotřebí sdělit zprostředkovatele, který má objektu sady řádků vrácených pro podporu `IConnectionPointContainer`, který je nutný k nastavení oznámení.

Následující kód ukazuje, jak otevřít v sadě řádků z objektu knihovny ATL a použít `AtlAdvise` funkce k nastavení jímky oznámení. `AtlAdvise` vrátí soubor cookie, který se používá při volání `AtlUnadvise`.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

Použije v následujícím kódu:

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)