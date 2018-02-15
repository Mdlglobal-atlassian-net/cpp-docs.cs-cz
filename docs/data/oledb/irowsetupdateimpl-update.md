---
title: IRowsetUpdateImpl::Update | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 98d0fde6c4fddf43cf353018ca7fcafea82a6f6e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
Přenáší všechny změny na řádek od posledního načtení nebo aktualizace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hReserved`  
 [v] Odpovídá `hChapter` parametr v [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx).  
  
 Dalších parametrů, najdete v části [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Změny, které se přenáší voláním [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Příjemce musí volat [CRowset::Update](../../data/oledb/crowset-update.md) změny se projeví. Nastavit *prgRowstatus* na odpovídající hodnotu jak je popsáno v [stavy řádků](https://msdn.microsoft.com/en-us/library/ms722752.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md)