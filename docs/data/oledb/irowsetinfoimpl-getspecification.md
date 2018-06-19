---
title: IRowsetInfoImpl::GetSpecification | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
dev_langs:
- C++
helpviewer_keywords:
- GetSpecification method
ms.assetid: 8e14289d-9cca-4df7-a9e0-f4ef03c61e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9d46b2adcbe6d1e3c49699bf8ecfceff0ec8dfd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103416"
---
# <a name="irowsetinfoimplgetspecification"></a>IRowsetInfoImpl::GetSpecification
Vrátí ukazatele rozhraní v objektu (příkaz nebo relace), který vytvořen této sady řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetInfo::GetSpecification](https://msdn.microsoft.com/en-us/library/ms716746.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této metody se [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) se načíst vlastnosti z objektu zdroje dat.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetInfoImpl – třída](../../data/oledb/irowsetinfoimpl-class.md)   
 [IRowsetInfoImpl::GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)   
 [IRowsetInfoImpl::GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)