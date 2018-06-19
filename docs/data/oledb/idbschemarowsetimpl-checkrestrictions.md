---
title: IDBSchemaRowsetImpl::CheckRestrictions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
dev_langs:
- C++
helpviewer_keywords:
- CheckRestrictions method
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c951c892a2e6d875fb1085b1d3208d43938347c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106424"
---
# <a name="idbschemarowsetimplcheckrestrictions"></a>IDBSchemaRowsetImpl::CheckRestrictions
Ověří platnost omezení proti sada řádků schématu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rguidSchema`  
 [v] Odkaz na identifikátor GUID sady řádků schématu požadovaný (například `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [v] Počet omezení, které příjemce předaná pro sadu řádků schématu.  
  
 `rgRestrictions`  
 [v] Pole s délkou *cRestrictions* omezení hodnot nastavení. Další informace najdete v části Popis `rgRestrictions` parametr v [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
## <a name="remarks"></a>Poznámky  
 Použití `CheckRestrictions` Zkontrolujte platnost omezení proti sada řádků schématu. Zkontroluje, omezení pro `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, a **DBSCHEMA_PROVIDER_TYPES** sad řádků schématu. Pojmenujte ji k určení, zda příjemce volat na **IDBSchemaRowset::GetRowset** je správný. Pokud chcete podporovat schéma sad řádků než výše uvedené, měli byste vytvořit vlastní funkce k provedení této úlohy.  
  
 `CheckRestrictions` Určuje, pokud je volání příjemce [GetRowset –](../../data/oledb/idbschemarowsetimpl-getrowset.md) s správné omezení a omezení správný typ (například `VT_BSTR` řetězce) podporující zprostředkovatele. Také určuje, pokud jsou podporovány správný počet omezení. Ve výchozím nastavení `CheckRestrictions` požádá poskytovatele, prostřednictvím [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) volání, která omezení podporuje v dané sadě řádků. Pak porovná omezení od příjemce s těmi, které zprostředkovatel a buď úspěšná nebo neúspěšná.  
  
 Další informace o sad řádků schématu najdete v tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)