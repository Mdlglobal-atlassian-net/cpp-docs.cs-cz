---
title: "CCommand – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
dev_langs: C++
helpviewer_keywords: CCommand class
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 82fb0dc84253fc5984f2ac9e52b96a27fb47e770
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccommand-class"></a>CCommand – třída
Poskytuje metody k nastavení a spuštění příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   class TAccessor = CNoAccessor,  
   template < typename T > class TRowset = CRowset,  
   class TMultiple = CNoMultipleResults   
>  
class CCommand :   
   public CAccessorRowset <  
      TAccessor,   
      TRowset   
   >,  
   public CCommandBase,  
   public TMultiple  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Typ třídy přístupového objektu (například `CDynamicParameterAccessor`, `CDynamicStringAccessor`, nebo `CEnumeratorAccessor`), chcete, aby příkaz použil. Výchozí hodnota je `CNoAccessor`, která určuje, že třída není podporovala parametry nebo výstupní sloupce.  
  
 `TRowset`  
 Typ třídy sady řádků (například `CArrayRowset` nebo `CNoRowset`), chcete, aby příkaz použil. Výchozí hodnota je `CRowset`.  
  
 `TMultiple`  
 Chcete-li použít příkaz OLE DB, který může vrátit více výsledků, zadejte [CMultipleResults](../../data/oledb/cmultipleresults-class.md). Jinak použijte [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Podrobnosti najdete v tématu [IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx).  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zavřete](../../data/oledb/ccommand-close.md)|Zavře aktuální příkaz.|  
|[GetNextResult –](../../data/oledb/ccommand-getnextresult.md)|Načte další výsledek při použití více výsledků sad.|  
|[Otevřete](../../data/oledb/ccommand-open.md)|Spustí a volitelně váže příkaz.|  
  
### <a name="inherited-methods"></a>Zděděné metody  
  
|||  
|-|-|  
|[Vytvoření](../../data/oledb/ccommand-create.md)|Vytvoří nový příkaz pro zadaná relace a poté nastaví text příkazu.|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|Vytvoří nový příkaz.|  
|[Getparameterinfo –](../../data/oledb/ccommand-getparameterinfo.md)|Získá seznam parametrů příkazu, jejich názvy a jejich typy.|  
|[Příprava](../../data/oledb/ccommand-prepare.md)|Ověří a optimalizuje aktuální příkaz.|  
|[ReleaseCommand –](../../data/oledb/ccommand-releasecommand.md)|Uvolní přistupujícího objektu parametr, v případě potřeby pak uvolní příkaz.|  
|[SetParameterInfo –](../../data/oledb/ccommand-setparameterinfo.md)|Určuje typ nativní každý parametr příkazu.|  
|[Unprepare –](../../data/oledb/ccommand-unprepare.md)|Zruší aktuální plán spuštění příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto třídu používejte, když potřebujete provést operaci na základě parametrů nebo spuštění příkazu. Pokud potřebujete jenom otevřete jednoduché sady řádků, použijte [CTable](../../data/oledb/ctable-class.md) místo.  
  
 Přistupující objekt třídy, kterou používáte určuje způsob vazby parametrů a data.  
  
 Poznámka: nelze použít uložené procedury pomocí zprostředkovatele OLE DB pro Jet vzhledem k tomu, že zprostředkovatel nepodporuje uložené procedury (v řetězcích dotazů jsou povoleny pouze konstanty).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)