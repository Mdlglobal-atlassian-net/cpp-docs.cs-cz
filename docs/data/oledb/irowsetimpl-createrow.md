---
title: IRowsetImpl::CreateRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
ms.openlocfilehash: fd378ed599795911a86fb4bc10625721c76f417b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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