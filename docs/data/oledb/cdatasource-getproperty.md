---
title: CDataSource::GetProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
dev_langs:
- C++
helpviewer_keywords:
- GetProperty method
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afe21f6f41491a4f62eda09e2df43aa470417e20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090484"
---
# <a name="cdatasourcegetproperty"></a>CDataSource::GetProperty
Vrátí hodnotu zadané vlastnosti pro objekt zdroje dat připojené.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetProperty(const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [v] Identifikace je vlastnost nastavena, pro které chcete vrátit vlastnost na identifikátor GUID.  
  
 `propid`  
 [v] Vlastnost ID pro vlastnost vrátit.  
  
 *pVariant*  
 [out] Ukazatel na varianta kde **GetProperty** vrátí hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat více vlastností, použijte [GetProperties](../../data/oledb/cdatasource-getproperties.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataSource – třída](../../data/oledb/cdatasource-class.md)