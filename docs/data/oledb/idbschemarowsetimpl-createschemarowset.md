---
title: IDBSchemaRowsetImpl::CreateSchemaRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateSchemaRowset method
ms.assetid: ad3e3e4d-45b9-461c-b7b8-3af6843631b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 90a942fc92faf3066669b46fd825ad2eae393f43
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103993"
---
# <a name="idbschemarowsetimplcreateschemarowset"></a>IDBSchemaRowsetImpl::CreateSchemaRowset
Implementuje funkce tvůrce objektu COM pro daný objekt zadaný parametrem šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pUnkOuter`  
 [v] Vnější [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) při agregování, jinak **NULL**.  
  
 `cRestrictions`  
 [v] Počet omezení platných pro sadu řádků schématu.  
  
 `rgRestrictions`  
 [v] Pole `cRestrictions` **VARIANT**s má být použita pro sadu řádků.  
  
 `riid`  
 [v] Rozhraní [QueryInterface](../../atl/queryinterface.md) pro na výstup **IUnknown**.  
  
 `cPropertySets`  
 [v] Nastaví počet vlastnost nastavit.  
  
 `rgPropertySets`  
 [v] Pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury, které určují vlastnosti Probíhá nastavení.  
  
 `ppRowset`  
 [out] Odchozích **IUnknown** požadoval `riid`. To **IUnknown** je rozhraní objektu sady řádků schématu.  
  
 `pSchemaRowset`  
 [out] Ukazatel na instanci třídy sady řádků schématu. Obvykle se tento parametr se nepoužívá, ale můžete použít, pokud další práci na sadě řádků schématu je třeba provést před blokováním na objekt COM. Životnost `pSchemaRowset` je svázaná s `ppRowset`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce implementuje obecný tvůrce pro všechny typy sad řádků schématu. Uživatel obvykle není volání této funkce. Je volána metodou implementace mapy schématu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)