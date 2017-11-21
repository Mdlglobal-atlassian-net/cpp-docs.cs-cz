---
title: Modul snap-In objekt makra | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
dev_langs: C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b70a8e3d644389bcfb21b276c5a3bcfad84891a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="snap-in-object-macros"></a>Modul snap-In objekt makra
Tyto makra poskytuje podporu pro rozšíření modulu snap-in.  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Označuje začátek mapování třídy dat rozšiřující modul snap-in pro objekt, který modul Snap-In.|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Označuje začátek mapy nástrojů pro objekt, který modul Snap-In.|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Označuje konec mapování třídy dat rozšiřující modul snap-in pro objekt, který modul Snap-In.|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Označuje konec mapy nástrojů pro objekt, který modul Snap-In.|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Vytvoří člena dat pro datové třídy rozšíření modulu snap-in.|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Zadá třídu rozšiřující modul snap-in data do mapování třídy dat rozšiřující modul snap-in objektu modulu Snap-In.|  
|[SNAPINMENUID](#snapinmenuid)|Deklaruje ID v místní nabídce použité objektem modul Snap-In.|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Do panelu nástrojů mapy objektu modulu Snap-In vstupuje do panelu nástrojů.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 Označuje začátek mapování třídy dat rozšiřující modul snap-in.  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 [v] Název třídy dat rozšiřující modul snap-in.  
  
### <a name="remarks"></a>Poznámky  
 Spuštění mapy rozšiřující modul snap-in s `BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP` makro, přidejte položky pro všechny vaše rozšiřující modul snap-in datových typů s [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makro a dokončete mapa s [END_ EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makro.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP  
 Deklaruje začátku mapy ID nástrojů pro objekt, modul Snap-In.  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>Parametry  
 `_class`  
 [v] Určuje třídu objektu modulu Snap-In.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP  
 Označuje konec mapování třídy dat rozšiřující modul snap-in.  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>Poznámky  
 Spuštění mapy rozšiřující modul snap-in s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makro, přidejte položky pro všechny vaše rozšíření modulu snap-in datových typů s [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makro, a dokončit mapa s `END_EXTENSION_SNAPIN_NODEINFO_MAP` makro.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).  
  
##  <a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP  
 Deklaruje konec mapy ID nástrojů pro objekt, modul Snap-In.  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>Parametry  
 `_class`  
 [v] Určuje třídu objektu modulu Snap-In.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).  
  
##  <a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS  
 Přidá datový člen třídy dat rozšiřující modul snap-in pro **ISnapInItemImpl**-odvozené třídy.  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>Parametry  
 `dataClass`  
 [v] Třída dat rozšíření modulu snap-in.  
  
### <a name="remarks"></a>Poznámky  
 Tato třída musí být zadán také do mapování třídy dat rozšiřující modul snap-in. Spustit mapování třídy rozšiřující modul snap-in dat s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makro, přidejte položky pro všechny vaše rozšiřující modul snap-in datových typů s [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)makro a dokončete mapa s [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makro.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY  
 Přidá třídu data rozšiřující modul snap-in k mapování tříd dat rozšiřující modul snap-in.  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>Parametry  
 `dataClass`  
 [v] Třída dat rozšíření modulu snap-in.  
  
### <a name="remarks"></a>Poznámky  
 Spustit mapování třídy rozšiřující modul snap-in dat s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makro, přidejte položky pro všechny vaše rozšiřující modul snap-in datových typů s `EXTENSION_SNAPIN_NODEINFO_ENTRY` makro a dokončete mapa s [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makro.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).  
  
##  <a name="snapinmenuid"></a>SNAPINMENUID  
 Pomocí této makro deklarovat prostředků nabídky kontextu objektu modulu Snap-In.  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikuje v místní nabídce objektu modulu Snap-In.  
  
##  <a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY  
 Pomocí této makro zadat ID panelu nástrojů do mapování ID objektu modulu Snap-In panelu nástrojů.  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikuje ovládací prvek panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) makro označuje začátek mapy ID nástrojů; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) makro označí end.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
