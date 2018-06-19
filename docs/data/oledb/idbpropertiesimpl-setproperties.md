---
title: IDBPropertiesImpl::SetProperties | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- SetProperties method
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5067173da531bb8a4f437666ccfc9c9c61bb47f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106476"
---
# <a name="idbpropertiesimplsetproperties"></a>IDBPropertiesImpl::SetProperties
Nastaví vlastnosti ve zdroji dat a inicializační vlastnosti skupiny, pro objekty zdroje dat, nebo skupině vlastností inicializace pro výčty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je inicializovat zprostředkovatele, tato metoda nastaví hodnoty vlastností v **DBPROPSET_DATASOURCE**, **DBPROPSET_DATASOURCEINFO**, **DBPROPSET_DBINIT** vlastnost skupiny pro objekt zdroje dat. Pokud není inicializována zprostředkovatele, nastaví **DBPROPSET_DBINIT** vlastností pouze skupiny.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBPropertiesImpl – třída](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)