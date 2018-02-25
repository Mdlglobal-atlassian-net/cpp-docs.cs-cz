---
title: "IAccessorImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAccessorImpl
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fe9f4905b1c98641d184ab6e67c25405754f8872
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl – třída
Představuje implementaci objektu [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, 
          class BindType = ATLBINDINGS,
          class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třídě objektu sady řádků nebo příkaz.  
  
 `BindType`  
 Jednotky úložiště pro informace o vazbě. Výchozí hodnota je **ATLBINDINGS** struktury (viz atldb.h).  
  
 `BindingVector`  
 Jednotky úložiště pro informace o sloupci. Výchozí hodnota je [CAtlMap](../../atl/reference/catlmap-class.md) kde je klíčovým prvkem **HACCESSOR** hodnota a hodnota elementu je ukazatel na `BindType` struktury.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|Konstruktor|  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Addrefaccessor –](../../data/oledb/iaccessorimpl-addrefaccessor.md)|Přidá počet odkazů do existující přistupujícího objektu.|  
|[CreateAccessor –](../../data/oledb/iaccessorimpl-createaccessor.md)|Vytvoří přistupující objekt ze sady vazby.|  
|[Getbindings –](../../data/oledb/iaccessorimpl-getbindings.md)|Vrátí vazby přistupující objekt.|  
|[Releaseaccessor –](../../data/oledb/iaccessorimpl-releaseaccessor.md)|Uvolní přistupující objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Toto je povinná na příkazy a sady řádků. OLE DB vyžaduje poskytovatelům implementovat **HACCESSOR**, což je značka na pole [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) struktury. **HACCESSOR**s poskytované `IAccessorImpl` jsou adresy `BindType` struktury. Ve výchozím nastavení `BindType` je definován jako **ATLBINDINGS** v `IAccessorImpl`na definice šablony. `BindType` poskytuje mechanismus používaný `IAccessorImpl` sledovat počet elementů v jeho **DBBINDING** pole a také odkaz počet a přistupujícího objektu příznaky.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)