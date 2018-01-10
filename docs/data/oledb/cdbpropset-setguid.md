---
title: CDBPropSet::SetGUID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs: C++
helpviewer_keywords:
- SetGUID method
- AddProperty method
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0fed876cabd9a197d022a35829174bcc7e43e97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropsetsetguid"></a>CDBPropSet::SetGUID
Nastaví **guidPropertySet** pole **DBPROPSET** struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [v] Identifikátor GUID slouží k nastavení **guidPropertySet** pole z [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury.  
  
## <a name="remarks"></a>Poznámky  
 V tomto poli může být nastavena [konstruktor](../../data/oledb/cdbpropset-cdbpropset.md) také.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDBPropSet – třída](../../data/oledb/cdbpropset-class.md)