---
title: CSimpleRow – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68f1983eaad36494892c9a18dcb2dbebe2da1f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="csimplerow-class"></a>CSimpleRow – třída
Poskytuje výchozí implementaci pro popisovač řádku, který je používán [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CSimpleRow  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrow –](../../data/oledb/csimplerow-addrefrow.md)|Přidá počet odkazů na popisovač existující řádek.|  
|[Porovnání](../../data/oledb/csimplerow-compare.md)|Porovná dva řádky, které chcete zobrazit, pokud odkazují na stejnou instanci řádek.|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|Konstruktor|  
|[Releaserow –](../../data/oledb/csimplerow-releaserow.md)|Uvolní řádků.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_dwRef](../../data/oledb/csimplerow-m-dwref.md)|Počet odkazů na popisovač existující řádek.|  
|[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)|Index pro sadu řádků představující kurzor.|  
  
## <a name="remarks"></a>Poznámky  
 Popisovač řádku je logicky jedinečný kód pro řádek, výsledek. `IRowsetImpl` Vytvoří novou `CSimpleRow` pro každý řádek požadované v [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` můžete nahradit vlastní implementaci popisovač řádku, jako je argumentem výchozí šablonu pro `IRowsetImpl`. Jediným požadavkem k nahrazení Tato třída je tak, aby měl náhradní třídě poskytují konstruktor, který přijímá jeden parametr typu **DLOUHO**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)