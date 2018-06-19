---
title: IRowsetImpl::GetDBStatus | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- GetDBStatus method
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ebebbc2d1392e4f3c863ce366e8d19cfad3b7162
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106528"
---
# <a name="irowsetimplgetdbstatus"></a>IRowsetImpl::GetDBStatus
Vrátí `DBSTATUS` příznaky stavu pro zadané pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual DBSTATUS GetDBStatus(RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `currentRow`  
 Na aktuálním řádku.  
  
 [v] `columnNames`  
 Sloupec, pro které je požadováno stavu.  
  
## <a name="return-value"></a>Návratová hodnota  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) příznaky pro sloupec.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)