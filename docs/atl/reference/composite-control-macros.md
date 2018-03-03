---
title: "Makra složeného ovládacího prvku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b609801a1716e47b208644be02d4746abf8c288a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="composite-control-macros"></a>Makra složeného ovládacího prvku
Tyto makra definovat mapy jímek událostí a položek.  
  
|||  
|-|-|  
|[BEGIN_SINK_MAP](#begin_sink_map)|Označuje začátek mapy jímek událostí složeného ovládacího prvku.|  
|[END_SINK_MAP](#end_sink_map)|Označuje konec mapy jímek událostí složeného ovládacího prvku.|  
|[SINK_ENTRY](#sink_entry)|Položka k mapy jímek událostí.|  
|[SINK_ENTRY_EX](#sink_entry_ex)|Položka k mapy jímek událostí s dalším parametrem.| 
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobně jako u SINK_ENTRY_EX s tím rozdílem, že trvá ukazatel na iid.|  
|[SINK_ENTRY_INFO](#sink_entry_info)|Položka k mapa jímky událostí s ručně zadaný typ informace pro použití s [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|  
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobně jako u SINK_ENTRY_INFO s tím rozdílem, že trvá ukazatel na iid.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  

##  <a name="begin_sink_map"></a>BEGIN_SINK_MAP  
 Deklaruje začátku mapy jímek událostí složeného ovládacího prvku.  
  
```
BEGIN_SINK_MAP(_class)
```  
  
### <a name="parameters"></a>Parametry  
 `_class`  
 [v] Určuje ovládacího prvku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Poznámky  
 Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  
##  <a name="end_sink_map"></a>END_SINK_MAP  
 Deklaruje konec mapy jímek událostí složeného ovládacího prvku.  
  
```
END_SINK_MAP()
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Poznámky  
 Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  
##  <a name="sink_entry"></a>SINK_ENTRY  
 Deklaruje obslužné rutiny ( `fn`) pro zadanou událost ( `dispid`), ovládacího prvku identifikovaný `id`.  
  
```
SINK_ENTRY( id, dispid, fn )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikuje ovládacího prvku.  
  
 `dispid`  
 [v] Identifikuje zadané události.  
  
 `fn`  
 [v] Název obslužné rutiny událostí. Musíte použít tuto funkci **_stdcall** konvence volání a mít odpovídající stylu dispinterface podpis.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]  
  
### <a name="remarks"></a>Poznámky  
 Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  
##  <a name="sink_entry_ex"></a>SINK_ENTRY_EX a SINK_ENTRY_EX_P
 Deklaruje obslužné rutiny ( `fn`) pro zadanou událost ( `dispid`), rozhraní dispatch ( *iid)*, pro ovládací prvek identifikovaný `id`.  
  
```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikuje ovládacího prvku.  
  
 `iid`  
 [v] Určuje rozhraní pro odesílání.  

 `piid`  
 [v] Ukazatel rozhraní odesílání.  
  
 `dispid`  
 [v] Identifikuje zadané události.  
  
 `fn`  
 [v] Název obslužné rutiny událostí. Musíte použít tuto funkci **_stdcall** konvence volání a mít odpovídající stylu dispinterface podpis.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]  
  
### <a name="remarks"></a>Poznámky  
 Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  
##  <a name="sink_entry_info"></a>SINK_ENTRY_INFO a SINK_ENTRY_INFO_P  
 Použití `SINK_ENTRY_INFO` makro v rámci mapování jímky událostí poskytnout informace, které [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) události trasy k příslušné obslužné rutiny.  
  
```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Celé číslo bez znaménka identifikace zdroj události. Tato hodnota musí odpovídat `nID` šablony parametr použitý v související [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) základní třídy.  
  
 `iid`  
 [v] Identifikátory IID, který identifikuje rozhraní odesílání.  

 `piid`  
 [v] Ukazatel na IID, který identifikuje rozhraní odesílání.
  
 `dispid`  
 [v] DISPID identifikace zadané události.  
  
 `fn`  
 [v] Název obslužné rutiny událostí. Musíte použít tuto funkci **_stdcall** konvence volání a mít odpovídající stylu dispinterface podpis.  
  
 `info`  
 [v] Zadejte informace o funkci obslužná rutina události. Tento typ informace jsou poskytovány ve formě ukazatel na `_ATL_FUNC_INFO` struktura. `CC_CDECL`je jedinou možností v systém Windows CE pro podporované `CALLCONV` pole z `_ATL_FUNC_INFO` struktura. Žádné jiné hodnoty nejsou proto není definovaná své chování.  
  
### <a name="remarks"></a>Poznámky  
 První čtyři makro parametry jsou stejné jako u [SINK_ENTRY_EX](#sink_entry_ex) makro. Konečný parametr obsahuje typ informace o události. Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  

## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [Globální funkce složených ovládacích prvků](../../atl/reference/composite-control-global-functions.md)
