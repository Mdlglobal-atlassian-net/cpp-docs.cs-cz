---
title: CRowsetImpl::NameFromDBID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs:
- C++
helpviewer_keywords:
- NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 451c5d0474cbd5d72e650648ebd99eb9f2277a66
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplnamefromdbid"></a>CRowsetImpl::NameFromDBID
Extrahuje řetězec z **DBID** a zkopíruje je do `bstr` předaná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pDBID*  
 [v] Ukazatel **DBID** ze kterého budou extrahovány řetězec.  
  
 `bstr`  
 [v] A [CComBSTR](../../atl/reference/ccombstr-class.md) odkaz na umístěte kopii **DBID** řetězec.  
  
 `bIndex`  
 [v] **true** Pokud index **DBID**; **false** Pokud tabulku **DBID**.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`. Podle toho, jestli **DBID** tabulky nebo indexu (odlišené `bIndex`), metoda bude buď vrátit **DB_E_NOINDEX** nebo **DB_E_NOTABLE**.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána `CRowsetImpl` implementace [ValidateCommandID –](../../data/oledb/crowsetimpl-validatecommandid.md) a [getcommandfromid –](../../data/oledb/crowsetimpl-getcommandfromid.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CRowsetImpl – třída](../../data/oledb/crowsetimpl-class.md)