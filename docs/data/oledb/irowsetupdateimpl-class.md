---
title: "IRowsetUpdateImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs: C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe93031417b8fc7717be13007b0fcfc5d08a2c40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl – třída
Implementace šablony technologie OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  
class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass  
>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída odvozená z `IRowsetUpdateImpl`.  
  
 `Storage`  
 Záznamu uživatele.  
  
 `UpdateArray`  
 Pole obsahující data uložená v mezipaměti pro aktualizaci sady řádků.  
  
 `RowClass`  
 Jednotky úložiště pro **HROW**.  
  
 `MapClass`  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)  
  
|||  
|-|-|  
|[SetData –](../../data/oledb/irowsetupdateimpl-setdata.md)|Nastaví hodnoty dat v jedné nebo více sloupců.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Metody rozhraní (používá se s IRowsetUpdate)  
  
|||  
|-|-|  
|[Getoriginaldata –](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|Získá data naposledy přenášeny do nebo získat ze zdroje dat, ignoruje změny čekající na zpracování.|  
|[Getpendingrows –](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|Vrátí seznam hodnot řádků s čekajícími změnami.|  
|[GetRowStatus –](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|Vrátí stav zadané řádky.|  
|[Vrácení zpět](../../data/oledb/irowsetupdateimpl-undo.md)|Zruší všechny změny na řádek od posledního načtení nebo aktualizace.|  
|[Aktualizace](../../data/oledb/irowsetupdateimpl-update.md)|Přenáší všechny změny na řádek od posledního načtení nebo aktualizace.|  
  
### <a name="implementation-methods-callback"></a>Implementace metody (zpětného volání)  
  
|||  
|-|-|  
|[IsUpdateAllowed –](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|Používá k ověření zabezpečení, integritu, a tak dále před povolením aktualizace.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|Obsahuje původní data pro odložené operaci.|  
  
## <a name="remarks"></a>Poznámky  
 Doporučujeme nejprve číst a pochopit v dokumentaci k [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx), protože všechno popsané existuje platí i zde. Doporučujeme přečíst kapitoly 6 *referenční příručka programátora technologie OLE DB* na nastavení data.  
  
 `IRowsetUpdateImpl`implementuje OLE DB `IRowsetUpdate` rozhraní, která umožňuje příjemci sdělovat změny provedené s `IRowsetChange` do zdroje dat a vrátit zpět změny před samotným přenosem.  
  
> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si přečetli následující dokumentace před pokusem o implementovat poskytovatele:  
  
-   [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Kapitoly 6 *referenční příručka programátora prostředí OLE DB*  
  
-   Informace v tématu Jak `RUpdateRowset` třída se používá v ukázce UpdatePV  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)