---
title: CRowsetImpl::NameFromDBID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs:
- C++
helpviewer_keywords:
- NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 54ee345d4bf97c6f77398e62d1cb31614868a568
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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