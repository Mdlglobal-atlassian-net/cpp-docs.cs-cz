---
title: Odkazování na vlastnost ve zprostředkovateli | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b250e29acc964e1fb1273d02a3b1ea93c087e5c4
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082738"
---
# <a name="referencing-a-property-in-your-provider"></a>Odkazování na vlastnost ve zprostředkovateli

Najdete skupinu vlastností a vlastnost ID pro požadovanou vlastnost. Další informace najdete v tématu [vlastnosti technologie OLE DB](/previous-versions/windows/desktop/ms722734) v *OLE DB referenční informace pro programátory*.  
  
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
CAgentRowset<CMyProviderCommand>* pRowset = (CAgentRowset<CMyProviderCommand>*) pThis;  
  
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