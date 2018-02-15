---
title: IDBSchemaRowsetImpl::GetRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
dev_langs:
- C++
helpviewer_keywords:
- GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb3e1460b4eee2de030397e05d527c219acb2bb9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
Vrací sadu řádků schématu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pUnkOuter`  
 [v] Vnější **IUnknown** při totožný; jinak hodnota **NULL**.  
  
 `rguidSchema`  
 [v] Odkaz na identifikátor GUID sady řádků schématu požadovaný (například `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [v] Počet omezení, která má být použita pro sadu řádků.  
  
 `rgRestrictions`  
 [v] Pole `cRestrictions` **VARIANT**s, která představují omezení.  
  
 `riid`  
 [v] Identifikátory IID k vyžádání sady řádků schématu nově vytvořený.  
  
 `cPropertySets`  
 [v] Nastaví počet vlastnost nastavit.  
  
 `rgPropertySets`  
 [vstup/výstup] Pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury nastavit pro sadu řádků schématu nově vytvořený.  
  
 `ppRowset`  
 [out] Ukazatel na požadované rozhraní na sadu řádků schématu nově vytvořený.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje, aby uživatel má schéma mapování ve třídě relace. Pomocí informací o schématu mapy, `GetRowset` vytvoří objekt dané sadě řádků, pokud `rguidSchema` parametr je jednu z položek mapování identifikátory GUID. V tématu [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) popis položku mapování.  
  
 V tématu [IDBSchemaRowset::GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBSchemaRowsetImpl Class](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)