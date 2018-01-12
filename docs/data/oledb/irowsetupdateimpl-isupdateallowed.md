---
title: IRowsetUpdateImpl::IsUpdateAllowed | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs: C++
helpviewer_keywords: IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 312d0488afc73d38ebd1ceb8a3f4334468607ed9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
Potlačí tuto metodu ke kontrole pro zabezpečení, integritu, a tak dále před aktualizací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT IsUpdateAllowed(  
   DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */  
);  
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