---
title: Makra Map vlastnost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dfd99fa59fc5e1d97011ac3dba4d16dd222c35b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="property-map-macros"></a>Makra mapy vlastností
Tyto makra definovat mapování vlastností a položek.  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|Označuje začátek ATL mapa vlastností.|  
|[PROP_DATA_ENTRY](#prop_data_entry)|Určuje rozsah, nebo dimenze ovládacího prvku ActiveX.|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|Popis, vlastnost DISPID a vlastnost stránky vlastností CLSID zadá do mapa vlastností.|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Zadá popis vlastnosti, vlastnost DISPID, stránka vlastností CLSID, a `IDispatch` IID do mapa vlastností.|  
|[PROP_PAGE](#prop_page)|Stránky vlastností CLSID vstoupí do mapa vlastností.|  
|[END_PROP_MAP](#end_prop_map)|Označuje konec ATL mapa vlastností.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
   
##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 Označuje začátek mapa vlastností objektu.  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [v] Určuje třídu obsahující mapa vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Mapa vlastností ukládá popisů vlastnosti hodnoty dispID vlastnost, stránka vlastností CLSID, a `IDispatch` identifikátory IID. Třídy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), a [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)k načtení a nastavení tyto informace použít mapa vlastností.  
  
 Při vytváření objektu pomocí Průvodce projektem ATL, Průvodce vytvoří prázdnou vlastností mapy zadáním `BEGIN_PROP_MAP` následuje [END_PROP_MAP](#end_prop_map).  
  
 `BEGIN_PROP_MAP`není uložit mimo rozsah (to znamená, dimenze) mapa vlastností, protože objekt, který používá mapa vlastností nemusí mít uživatelské rozhraní, neměl by mít žádné míry. Pokud se objekt ovládacího prvku ActiveX s uživatelským rozhraním, má rozsah. V takovém případě musíte zadat [PROP_DATA_ENTRY](#prop_data_entry) v mapu vlastností a zadejte rozsah.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 Určuje rozsah, nebo dimenze ovládacího prvku ActiveX.  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>Parametry  
 `szDesc`  
 [v] Popis vlastnosti.  
  
 `member`  
 [v] Datový člen obsahující rozsah; například `m_sizeExtent`.  
  
 *VT*  
 [v] Určuje typ VARIANT vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro způsobí, že zadaná data člena natrvalo.  
  
 Když vytvoříte ovládací prvek ActiveX, Průvodce vloží tento makro za makra mapy vlastnost [BEGIN_PROP_MAP](#begin_prop_map) a před makra mapy vlastnost [END_PROP_MAP](#end_prop_map).  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu v rozsahu objektu ( `m_sizeExtent`) je jako trvalý.  
  
 [!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 Pomocí této makro zadejte popis, vlastnost DISPID a vlastnost stránky vlastností CLSID do mapa vlastností objektu.  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>Parametry  
 `szDesc`  
 [v] Popis vlastnosti.  
  
 `dispid`  
 [v] Vlastnosti DISPID.  
  
 `clsid`  
 [v] CLSID stránce přidružené vlastnosti. Použít speciální hodnotu `CLSID_NULL` pro vlastnost, která nemá stránku přidružené vlastnosti.  
  
 `vt`  
 [v] Typ vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
 `PROP_ENTRY` Makro byl nezabezpečené a zastaralé. Byla nahrazena `PROP_ENTRY_TYPE`.  
  
 [BEGIN_PROP_MAP](#begin_prop_map) makro označuje začátek mapa vlastností; [END_PROP_MAP](#end_prop_map) makro označí end.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_PROP_MAP](#begin_prop_map).  
  
##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
 Podobně jako [PROP_ENTRY_TYPE](#prop_entry_type), ale můžete určit konkrétní IID, pokud objekt podporuje více duální rozhraní.  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>Parametry  
 `szDesc`  
 [v] Popis vlastnosti.  
  
 `dispid`  
 [v] Vlastnosti DISPID.  
  
 `clsid`  
 [v] CLSID stránce přidružené vlastnosti. Použít speciální hodnotu `CLSID_NULL` pro vlastnost, která nemá stránku přidružené vlastnosti.  
  
 `iidDispatch`  
 [v] Identifikátory IID rozhraní duální definování vlastnost.  
  
 `vt`  
 [v] Typ vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
 `PROP_ENTRY_EX` Makro byl nezabezpečené a zastaralé. Byla nahrazena `PROP_ENTRY_TYPE_EX`.  
  
 [BEGIN_PROP_MAP](#begin_prop_map) makro označuje začátek mapa vlastností; [END_PROP_MAP](#end_prop_map) makro označí end.  
  
### <a name="example"></a>Příklad  
 Následující příklad skupiny položky pro `IMyDual1` následuje záznam pro `IMyDual2`. Seskupení duální rozhraní umožní zvýšení výkonu.  
  
 [!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="prop_page"></a>PROP_PAGE  
 Pomocí této makro zadat stránky vlastností CLSID do mapa vlastností objektu.  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] CLSID stránky vlastností.  
  
### <a name="remarks"></a>Poznámky  
 `PROP_PAGE`je podobná [PROP_ENTRY_TYPE](#prop_entry_type), ale nevyžaduje vlastnost Popis nebo DISPID.  
  
> [!NOTE]
>  Pokud jste již zadali CLSID s `PROP_ENTRY_TYPE` nebo [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), není potřeba provést další položku s `PROP_PAGE`.  
  
 [BEGIN_PROP_MAP](#begin_prop_map) makro označuje začátek mapa vlastností; [END_PROP_MAP](#end_prop_map) makro označí end.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="end_prop_map"></a>END_PROP_MAP  
 Označuje konec mapa vlastností objektu.  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>Poznámky  
 Při vytváření objektu pomocí Průvodce projektem ATL, Průvodce vytvoří prázdnou vlastností mapy zadáním [BEGIN_PROP_MAP](#begin_prop_map) následuje `END_PROP_MAP`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_PROP_MAP](#begin_prop_map).  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
