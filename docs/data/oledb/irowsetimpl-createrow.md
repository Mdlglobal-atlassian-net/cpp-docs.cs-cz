---
title: IRowsetImpl::CreateRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs:
- C++
helpviewer_keywords:
- CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4403388146b79eec4435374793b2517dd46ff188
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
Pomocná metoda volá [GetNextRows –](../../data/oledb/irowsetimpl-getnextrows.md) přidělit nový **HROW**.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT CreateRow(DBROWOFFSET lRowsOffset,  
  DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows);  
```  
  
#### <a name="parameters"></a>Parametry  
 *lRowsOffset*  
 Pozice kurzoru řádku vytváří.  
  
 *cRowsObtained*  
 Odkaz byl předán zpět určující počet řádků vytvořit uživateli.  
  
 *rgRows*  
 Pole **HROW**s vrácen volajícímu s popisovačů nově vytvořený řádků.  
  
## <a name="remarks"></a>Poznámky  
 Pokud existuje řádek, tato metoda volá [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a vrátí. Jinak přiděluje novou instanci třídy proměnná RowClass šablony a přidává ji k [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)