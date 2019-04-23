---
title: Odkazování na vlastnost ve zprostředkovateli
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: c3e620cd760aa04df7d7d2209ef009a606675276
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028452"
---
# <a name="referencing-a-property-in-your-provider"></a>Odkazování na vlastnost ve zprostředkovateli

Najdete skupinu vlastností a vlastnost ID pro požadovanou vlastnost. Další informace najdete v tématu [vlastnosti technologie OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) v **OLE DB referenční informace pro programátory**.

V následujícím příkladu se předpokládá, že se pokoušíte získat vlastnosti ze sady řádků. Kód pro použití relace nebo příkazu je podobné, ale používá jiné rozhraní.

Vytvoření [CDBPropSet](../../data/oledb/cdbpropset-class.md) pomocí vlastnosti skupiny jako parametr do konstruktoru. Příklad:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Volání [AddProperty](../../data/oledb/cdbpropset-addproperty.md), předejte ID vlastnosti a hodnotu pro přiřazení k vlastnosti. Typ hodnoty závisí na vlastnost, kterou používáte.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Použití `IRowset` rozhraní volat `GetProperties`. Předejte vlastnost nastavit jako parametr. Tady je konečný kód:

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

## <a name="see-also"></a>Viz také:

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)