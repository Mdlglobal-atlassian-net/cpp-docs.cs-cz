---
title: CDataSource::GetProperties | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
dev_langs: C++
helpviewer_keywords: GetProperties method
ms.assetid: ffaecc17-9fe7-449e-94d6-43d31ad06cfc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b8460aaabf94562e686f87ff15a072702dd2ecb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourcegetproperties"></a>CDataSource::GetProperties
Vrátí informace o vlastnosti požadované pro objekt zdroje dat připojené.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetProperties(   
   ULONG ulPropIDSets,   
   const DBPROPIDSET* pPropIDSet,   
   ULONG* pulPropertySets,   
   DBPROPSET** ppPropsets    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) v *referenční příručka programátora prostředí OLE DB* ve Windows SDK.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Jedinou vlastností, použijte [GetProperty](../../data/oledb/cdatasource-getproperty.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataSource – třída](../../data/oledb/cdatasource-class.md)