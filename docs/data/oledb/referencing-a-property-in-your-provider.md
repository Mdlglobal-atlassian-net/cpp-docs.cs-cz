---
title: "Odkazování na vlastnost ve zprostředkovateli | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ccd06ab229f5bf6643145c03d8396d48c45a303
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
propset.AddProperty(DBPROP_UPDATABILITY,  
DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
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
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)