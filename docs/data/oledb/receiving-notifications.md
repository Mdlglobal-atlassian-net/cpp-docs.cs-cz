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
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209775"
---
# <a name="receiving-notifications"></a>Příjem oznámení

OLE DB poskytuje rozhraní pro příjem oznámení, když dojde k událostem. Tyto informace jsou popsány v tématu [OLE DBch oznámení o objektech](/previous-versions/windows/desktop/ms725406(v=vs.85)) v **referenci programátora OLE DB**. Nastavení těchto událostí používá standardní mechanismus připojení COM. Například objekt ATL, který chce načíst události prostřednictvím `IRowsetNotify` implementuje rozhraní `IRowsetNotify` přidáním `IRowsetNotify` do seznamu odvozeného od třídy a jeho zpřístupněním pomocí makra COM_INTERFACE_ENTRY.

`IRowsetNotify` má tři metody, které je možné volat v různých časech. Pokud chcete reagovat jenom na jednu z těchto metod, můžete použít třídu [IRowsetNotifyImpl –](../../data/oledb/irowsetnotifyimpl-class.md) , která vrací E_NOTIMPL pro metody, které vás zajímají.

Při vytváření sady řádků je nutné sdělit poskytovateli, že má vrácený objekt sady řádků podporovat `IConnectionPointContainer`, který je potřeba k nastavení oznámení.

Následující kód ukazuje, jak otevřít sadu řádků z objektu knihovny ATL a použít funkci `AtlAdvise` k nastavení jímky oznámení. `AtlAdvise` vrátí soubor cookie, který se používá při volání `AtlUnadvise`.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

Pak se používá v následujícím kódu:

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
