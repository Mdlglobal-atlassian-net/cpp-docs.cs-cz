---
title: IRowsetUpdateImpl::IsUpdateAllowed | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d39c726e4131b17d1dbdd76418e6da7985e4404
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105345"
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
Potlačí tuto metodu ke kontrole pro zabezpečení, integritu, a tak dále před aktualizací.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Stav*  
 [v] Stav čekající operace na řádky.  
  
 *hRowUpdate*  
 [v] Obslužná rutina pro řádky, které chce uživatel aktualizovat.  
  
 *pRowStatus*  
 [out] Stav vrátil uživateli.  
  
## <a name="remarks"></a>Poznámky  
 Pokud zjistíte, že se mají povolit aktualizaci, vrátí `S_OK`; v opačném případě vrátí **E_FAIL**. Pokud povolíte aktualizaci, musíte také nastavit **DBROWSTATUS** v [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) příslušné [řádek stavu](https://msdn.microsoft.com/en-us/library/ms722752.aspx).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md)