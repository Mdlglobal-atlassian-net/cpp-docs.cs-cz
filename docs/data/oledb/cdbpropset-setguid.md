---
title: CDBPropSet::SetGUID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- SetGUID method
- AddProperty method
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 140bc76968780efff826ccc42343f27b2cd2eae6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropsetsetguid"></a>CDBPropSet::SetGUID
Nastaví **guidPropertySet** pole **DBPROPSET** struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
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