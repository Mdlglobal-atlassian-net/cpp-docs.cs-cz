---
title: IDBSchemaRowsetImpl::GetRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5164bcd56c61868649af6185c8b84ebf20098b18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
Vrací sadu řádků schématu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD (GetRowset)(  
   IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset   
);  
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
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)