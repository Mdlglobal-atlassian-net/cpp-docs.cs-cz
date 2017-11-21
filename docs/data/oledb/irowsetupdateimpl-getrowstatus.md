---
title: IRowsetUpdateImpl::GetRowStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
dev_langs: C++
helpviewer_keywords: GetRowStatus method
ms.assetid: ce57e8be-5891-44d9-b3c5-59ffd3913678
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e5955c3340666acf1fee8ede93af62a6e7baf1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimplgetrowstatus"></a>IRowsetUpdateImpl::GetRowStatus
Vrátí stav zadané řádky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD ( GetRowStatus )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hReserved`  
 [v] Odpovídá `hChapter` parametr v [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx).  
  
 Dalších parametrů, najdete v části [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md)