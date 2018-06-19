---
title: Odkazování na vlastnost ve zprostředkovateli | Microsoft Docs
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
ms.openlocfilehash: 36965ac33fc0a563951c0c0dfdce60d9d0e4f55b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106541"
---
# <a name="referencing-a-property-in-your-provider"></a>Odkazování na vlastnost ve zprostředkovateli
Pro vlastnost, kterou chcete najít skupinu vlastností a vlastnost ID. Další informace najdete v tématu [vlastnosti technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 V následujícím příkladu se předpokládá, že se pokoušíte získat vlastnost ze sady řádků. Kód pro pomocí relace nebo příkazu je podobný, ale používá jiné rozhraní.  
  
 Vytvoření [CDBPropSet](../../data/oledb/cdbpropset-class.md) pomocí skupiny vlastností jako parametr pro konstruktor. Příklad:  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 Volání [AddProperty –](../../data/oledb/cdbpropset-addproperty.md), předáním ji ID vlastnosti a hodnotu, má-li být přiřazeno k vlastnosti. Typ hodnoty závisí na vlastnost, kterou používáte.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IRowsetChange, true);  

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 Použití `IRowset` pro volání rozhraní **GetProperties**. Předejte sadu jako parametr vlastností. Toto je poslední kód:  
  
```  
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