---
title: IRowsetImpl::CreateRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs: C++
helpviewer_keywords: CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f90a5de73b5eea37eea192a4886fe29d1d8b435b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
Pomocná metoda volá [GetNextRows –](../../data/oledb/irowsetimpl-getnextrows.md) přidělit nový **HROW**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *lRowsOffset*  
 Pozice kurzoru řádku vytváří.  
  
 *získaná hodnota cRowsObtained*  
 Odkaz byl předán zpět určující počet řádků vytvořit uživateli.  
  
 *rgRows*  
 Pole **HROW**s vrácen volajícímu s popisovačů nově vytvořený řádků.  
  
## <a name="remarks"></a>Poznámky  
 Pokud existuje řádek, tato metoda volá [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a vrátí. Jinak přiděluje novou instanci třídy proměnná RowClass šablony a přidává ji k [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)