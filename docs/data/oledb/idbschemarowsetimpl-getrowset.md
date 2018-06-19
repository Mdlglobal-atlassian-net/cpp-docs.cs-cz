---
title: IDBSchemaRowsetImpl::GetRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ec479809bf95d4a88338401013b7f5980b703d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103746"
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
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)