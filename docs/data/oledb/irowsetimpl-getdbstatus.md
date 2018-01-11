---
title: IRowsetImpl::GetDBStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
dev_langs: C++
helpviewer_keywords: GetDBStatus method
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dff50d7ef201e8479ad06f6096549268b2dfe31d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimplgetdbstatus"></a>IRowsetImpl::GetDBStatus
Vrátí `DBSTATUS` příznaky stavu pro zadané pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      virtual DBSTATUS GetDBStatus(  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`currentRow`  
 Na aktuálním řádku.  
  
 [v]`columnNames`  
 Sloupec, pro které je požadováno stavu.  
  
## <a name="return-value"></a>Návratová hodnota  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) příznaky pro sloupec.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)