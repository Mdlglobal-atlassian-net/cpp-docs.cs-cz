---
title: IDBSchemaRowsetImpl::SetRestrictions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
dev_langs:
- C++
helpviewer_keywords:
- SetRestrictions method
ms.assetid: 707d5065-b853-4d38-9b67-3066b4d3b279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b6effd432b033941d404c4935cdbad5a2336ac8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105852"
---
# <a name="idbschemarowsetimplsetrestrictions"></a>IDBSchemaRowsetImpl::SetRestrictions
Určuje, která omezení podpory pro sadu řádků schématu konkrétní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
void SetRestrictions(ULONG cRestrictions,  
  GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRestrictions`  
 [v] Počet omezení v `rgRestrictions` pole a počet identifikátory GUID v `rguidSchema` pole.  
  
 `rguidSchema`  
 [v] Pole identifikátory GUID sady řádků schématu, pro které chcete načíst omezení. Každý element pole obsahuje identifikátor GUID sady řádků jedno schéma (například `DBSCHEMA_TABLES`).  
  
 `rgRestrictions`  
 [v] Pole s délkou `cRestrictions` omezení hodnot nastavení. Každý prvek odpovídá omezení pro sadu řádků schématu se identifikovanou pomocí identifikátoru GUID. Pokud sada řádků schématu není podporována zprostředkovatelem, element nastavená na hodnotu nula. Jinak **ULONG** hodnota obsahuje bitová maska, která představuje omezení podporované na tomto sada řádků schématu. Další informace, na kterém omezení odpovídají konkrétní sadě řádků schématu, naleznete v tabulce GUID sad řádků schématu v [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* v systému Windows SDK.  
  
## <a name="remarks"></a>Poznámky  
 **IDBSchemaRowset** objektu volání `SetRestrictions` k určení, která omezení podpory pro sadu řádků schématu konkrétní (je volána metodou [GetSchemas –](../../data/oledb/idbschemarowsetimpl-getschemas.md) prostřednictvím upcasted ukazatele). Omezení umožňují spotřebitelům načítat pouze odpovídající řádky (třeba najít všechny sloupce v tabulce "MyTable"). Omezení jsou volitelné a v případě, ve které žádný není podporována (výchozí), vždycky vrátí se všechna data.  
  
 Nastaví výchozí implementace této metody `rgRestrictions` pole elementů na hodnotu 0. Přepište výchozí nastavení v třídě relace nastavit omezení jiné než výchozí.  
  
 Informace o implementaci Podpora sad řádků schématu naleznete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).  
  
 Příklad poskytovatele, který podporuje sady řádků schématu, naleznete v části [UpdatePV](../../visual-cpp-samples.md) ukázka.  
  
 Další informace o sad řádků schématu najdete v tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md)   
 [UpdatePV](../../visual-cpp-samples.md)