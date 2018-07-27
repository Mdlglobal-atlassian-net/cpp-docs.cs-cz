---
title: Irowsetidentityimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cbafe7f43d8a6c7acfaccb52fd22b595bdd0ec4
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322095"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl – třída
Implementuje rozhraní OLE DB [IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx) rozhraní, které umožňují testování pro řádek identitu.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Třída odvozená z `IRowsetIdentityImpl`.  
  
 *RowClass*  
 Jednotka pro ukládání `HROW`.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Issamerow –](#issamerow)|Porovná dvě popisovačů řádků zjistěte odkazují na stejný řádek.|  
  
## <a name="issamerow"></a> IRowsetIdentityImpl::IsSameRow
Porovná dvě popisovačů řádků zjistěte odkazují na stejný řádek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/library/ms719629.aspx) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete porovnat popisovačů řádků, tato metoda přetypování `HROW` popisovače `RowClass` členy a volání `memcmp` na ukazatelů.  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
