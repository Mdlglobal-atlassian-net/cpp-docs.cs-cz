---
title: IRowsetImpl::CreateRow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eae3fbdce1db5760d4ee5ca75e007c01e98b7bed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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