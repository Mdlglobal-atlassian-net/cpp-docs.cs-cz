---
title: Odkazování na vlastnost ve zprostředkovateli
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: d70a1901c457d9fbdbe8712d84999e256a54d0c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209763"
---
# <a name="referencing-a-property-in-your-provider"></a>Odkazování na vlastnost ve zprostředkovateli

Vyhledejte skupinu vlastností a ID vlastnosti požadované vlastnosti. Další informace najdete v tématu [OLE DB vlastnosti](/previous-versions/windows/desktop/ms722734(v=vs.85)) v **referenci programátora OLE DB**.

Následující příklad předpokládá, že se pokoušíte získat vlastnost ze sady řádků. Kód pro použití relace nebo příkazu je podobný, ale používá jiné rozhraní.

Vytvořte objekt [CDBPropSet](../../data/oledb/cdbpropset-class.md) pomocí skupiny vlastností jako parametru konstruktoru. Příklad:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Zavolejte [AddProperty](../../data/oledb/cdbpropset-addproperty.md)a předejte jí ID vlastnosti a hodnotu, která má být přiřazena vlastnosti. Typ hodnoty závisí na vlastnosti, kterou používáte.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

K volání `GetProperties`použijte rozhraní `IRowset`. Předat sadu vlastností jako parametr. Zde je konečný kód:

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

DBPROPIDSET set;
set.AddPropertyID(DBPROP_BOOKMARKS);

DBPROPSET* pPropSet = NULL;
ULONG ulPropSet = 0;

HRESULT hr;

if (spRowsetProps)
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

if (pPropSet)
{
   CComVariant var = pPropSet->rgProperties[0].vValue;
   CoTaskMemFree(pPropSet->rgProperties);
   CoTaskMemFree(pPropSet);

   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
   {
      ...  // Use property here
   }
}
```

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
