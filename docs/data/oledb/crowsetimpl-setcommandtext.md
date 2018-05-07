---
title: CRowsetImpl::SetCommandText | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- SetCommandText method
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f6d3f811b60efdbd71f4919da05c3d7b6dd50bd2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetimplsetcommandtext"></a>CRowsetImpl::SetCommandText
Ověří a ukládá **DBID**s v dva řetězce ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTableID`  
 [v] Ukazatel **DBID** představující ID tabulky.  
  
 `pIndexID`  
 [v] Ukazatel **DBID** představující ID indexu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 **SetCommentText** metoda je volána metodou `CreateRowset`, statického převést na šablonu metodu `IOpenRowsetImpl`.  
  
 Tato metoda deleguje svou práci voláním [ValidateCommandID –](../../data/oledb/crowsetimpl-validatecommandid.md) a [getcommandfromid –](../../data/oledb/crowsetimpl-getcommandfromid.md) prostřednictvím upcasted ukazatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CRowsetImpl – třída](../../data/oledb/crowsetimpl-class.md)