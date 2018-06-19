---
title: IRowsetImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetImpl class
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ca6d35eeea1dbfae4f2a5bb1b2ee93553e53519
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108435"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl – třída
Představuje implementaci objektu `IRowset` rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*>>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IRowsetImpl`.  
  
 `RowsetInterface`  
 Třída odvozená z `IRowsetImpl`.  
  
 `RowClass`  
 Jednotky úložiště pro **HROW**.  
  
 `MapClass`  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md)|Přidá počet odkazů na popisovač existující řádek.|  
|[Createrow –](../../data/oledb/irowsetimpl-createrow.md)|Voláno rozhraním [GetNextRows –](../../data/oledb/irowsetimpl-getnextrows.md) přidělit nový **HROW**. Není volána přímo uživatelem.|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|Načte data z dané sadě řádků kopii řádku.|  
|[GetDBStatus –](../../data/oledb/irowsetimpl-getdbstatus.md)|Vrátí stav pro zadané pole.|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|Načte řádky postupně, nezapomeňte předchozí pozici.|  
|[IRowsetImpl –](../../data/oledb/irowsetimpl-class.md)|Konstruktor Není volána přímo uživatelem.|  
|[Refrows –](../../data/oledb/irowsetimpl-refrows.md)|Voláno rozhraním [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a [releaserows –](../../data/oledb/irowsetimpl-releaserows.md). Není volána přímo uživatelem.|  
|[Releaserows –](../../data/oledb/irowsetimpl-releaserows.md)|Uvolní řádků.|  
|[Volání metody RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|Přemístí následující načtenou pozici na výchozí pozici; To znamená vytvořit pozici při první sadu řádků.|  
|[SetDBStatus –](../../data/oledb/irowsetimpl-setdbstatus.md)|Nastaví příznaky stavu pro zadané pole.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|Určuje, zda zprostředkovatel podporuje zpětné načítání.|  
|[m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|Určuje, zda zprostředkovatele zpětné může mít jeho scroll kurzoru.|  
|[m_bReset](../../data/oledb/irowsetimpl-m-breset.md)|Určuje, jestli má zprostředkovatel resetovat jeho pozice kurzoru. Tato akce nemá zvláštní význam při posouvání zpětné nebo načítání zpětné v [GetNextRows –](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|Index pro sadu řádků, představující kurzor.|  
|[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|Seznam popisovačů řádků.|  
  
## <a name="remarks"></a>Poznámky  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) je rozhraní pro základní sady řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)