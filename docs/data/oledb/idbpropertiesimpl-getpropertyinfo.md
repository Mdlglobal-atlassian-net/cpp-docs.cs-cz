---
title: IDBPropertiesImpl::GetPropertyInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
dev_langs: C++
helpviewer_keywords: GetPropertyInfo method
ms.assetid: 170e9640-5010-4e0d-8a54-f50b23af08ad
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4891ba281000f58dd06a2c6e8bf38731da593005
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="idbpropertiesimplgetpropertyinfo"></a>IDBPropertiesImpl::GetPropertyInfo
Vrátí informace o vlastnosti zdroje dat nepodporuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD(GetPropertyInfo)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IDBProperties::GetPropertyInfo](https://msdn.microsoft.com/en-us/library/ms718175.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
 Některé parametry odpovídají *referenční příručka programátora technologie OLE DB* parametry odlišné názvy, které jsou popsány v **IDBProperties::GetPropertyInfo**:  
  
|Parametry šablony technologie OLE DB|*Referenční příručka programátora technologie OLE DB* parametry|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
  
## <a name="remarks"></a>Poznámky  
 Používá [IDBInitializeImpl::m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) implementovat tuto funkci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBPropertiesImpl – třída](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)