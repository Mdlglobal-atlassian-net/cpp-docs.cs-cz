---
title: CDataSource::GetProperty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
dev_langs: C++
helpviewer_keywords: GetProperty method
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96b7437bd96592044b4eab33df3e4912bd677591
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdatasourcegetproperty"></a>CDataSource::GetProperty
Vrátí hodnotu zadané vlastnosti pro objekt zdroje dat připojené.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetProperty(   
   const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant    
) const throw( );  
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