---
title: "CSimpleRow – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
dev_langs: C++
helpviewer_keywords: CSimpleRow class
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8c7f1ca1823970dec3f9a8c1ceb0198bc8a71b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csimplerow-class"></a>CSimpleRow – třída
Poskytuje výchozí implementaci pro popisovač řádku, který je používán [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Popisovač řádku je logicky jedinečný kód pro řádek, výsledek. `IRowsetImpl`Vytvoří novou `CSimpleRow` pro každý řádek požadované v [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow`můžete nahradit vlastní implementaci popisovač řádku, jako je argumentem výchozí šablonu pro `IRowsetImpl`. Jediným požadavkem k nahrazení Tato třída je tak, aby měl náhradní třídě poskytují konstruktor, který přijímá jeden parametr typu **DLOUHO**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)