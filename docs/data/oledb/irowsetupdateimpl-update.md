---
title: IRowsetUpdateImpl::Update | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs: C++
helpviewer_keywords: Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef3b93f85139ae0499d7e6679f39c8c885dbf4b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
Přenáší všechny změny na řádek od posledního načtení nebo aktualizace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD ( Update )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus   
);  
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