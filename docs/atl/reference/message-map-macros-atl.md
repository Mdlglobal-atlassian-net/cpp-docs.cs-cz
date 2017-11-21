---
title: "Zpráva makra mapy (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
dev_langs: C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e4abb41c756baecc5578bbc7db94d65768cae70a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="message-map-macros-atl"></a>Makra Map zpráv (ATL)
Tyto makra definovat mapy zpráv a položky.  
  
|||  
|-|-|  
|[ALT_MSG_MAP](#alt_msg_map)|Označuje začátek mapy alternativní zprávy.|  
|[BEGIN_MSG_MAP](#begin_msg_map)|Označuje začátek výchozí mapování zpráv.|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Řetězy zprávu alternativní mapovat v základní třídě.|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Řetězy zprávu alternativní mapovat v datový člen třídy.|  
|[CHAIN_MSG_MAP](#chain_msg_map)|Zřetězen do výchozí mapování zpráv v základní třídě.|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Zřetězen do mapy zpráv v jiné třídy v době běhu.|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Zřetězen do výchozí mapování zpráv v datový člen třídy.|  
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[COMMAND_HANDLER](#command_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor položky nabídky, řízení nebo akcelerátoru.|  
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě identifikátoru položky nabídky, řízení nebo akcelerátoru.|  
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a souvislý rozsah identifikátorů ovládacího prvku.|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě souvislý rozsahu identifikátorů ovládacího prvku.|  
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje mapování prázdná zpráva.|  
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Poskytuje výchozí obslužnou rutinu pro zrcadlené zprávy, které jinak nejsou zpracovány.|  
|[END_MSG_MAP](#end_msg_map)|Označuje konec mapy zpráv.|  
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Předává zprávy s oznámením do nadřazeného okna.|  
|[MESSAGE_HANDLER](#message_handler)|Zprávy Windows se mapuje na obslužnou rutinu.|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapy zpráv souvislý rozsah Windows funkce obslužné rutiny.|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[NOTIFY_HANDLER](#notify_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor ovládacího prvku.|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|  
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a souvislý rozsah identifikátorů ovládacího prvku.|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě souvislý rozsahu identifikátorů ovládacího prvku.|  
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odráží zpráv s oznámením zpět do okna, které jim poslali.|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor položky nabídky, řízení nebo akcelerátoru.|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě identifikátoru položky nabídky, řízení nebo akcelerátoru.|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a souvislý rozsah identifikátorů ovládacího prvku.|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě souvislý rozsahu identifikátorů ovládacího prvku.|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor ovládacího prvku.|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a souvislý rozsah identifikátorů ovládacího prvku.|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě souvislý rozsahu identifikátorů ovládacího prvku.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="alt_msg_map"></a>ALT_MSG_MAP  
 Označuje začátek mapy alternativní zprávy.  
  
```
ALT_MSG_MAP(msgMapID)
```  
  
### <a name="parameters"></a>Parametry  
 `msgMapID`  
 [v] Identifikátor mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 ATL identifikuje každého mapy zpráv podle čísla. Výchozí mapování zpráv (deklarovat s `BEGIN_MSG_MAP` makro) je identifikována 0. Mapování alternativní zpráv je určený podle `msgMapID`.  
  
 Mapy zpráv se používá ke zpracování zprávy odeslané do časového období. Například [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vám umožní určit identifikátor mapy zpráv v obsahující objektu. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) pak používá tuto zprávu mapu směrovat zprávy obsažené oken na příslušnou obslužnou rutinu funkce nebo na jinou mapy zpráv. Seznam makra, které deklarace funkcí obslužných rutin najdete v tématu [BEGIN_MSG_MAP](#begin_msg_map).  
  
 Vždy začít mapy zpráv s `BEGIN_MSG_MAP`. Potom můžete deklarovat mapy následné alternativní zpráv.  
  
 [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Všimněte si, že vždy přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje mapy zpráv výchozí a alternativní jednu zprávu mapy, každá obsahuje jednu funkci obslužné rutiny:  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 Další příklad ukazuje dva mapy alternativní zpráv. Mapy zpráv výchozí je prázdný.  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP  
 Označuje začátek výchozí mapování zpráv.  
  
```
BEGIN_MSG_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [v] Název třídy obsahující mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 [CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) ke zpracování zprávy odeslané do okna používá výchozí mapování zpráv. Mapy zpráv směrovat zprávy na příslušnou obslužnou rutinu funkce nebo na jinou mapy zpráv.  

  
 Následující makra zprávu mapování na obslužnou rutinu. Tato funkce musí být definován v `theClass`.  
  
|– Makro|Popis|  
|-----------|-----------------|  
|[MESSAGE_HANDLER](#message_handler)|Zprávy Windows se mapuje na obslužnou rutinu.|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapy zpráv souvislý rozsah Windows funkce obslužné rutiny.|  
|[COMMAND_HANDLER](#command_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor položky nabídky, řízení nebo akcelerátoru.|  
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě identifikátoru položky nabídky, řízení nebo akcelerátoru.|  
|[COMMAND_CODE_HANDLER](#command_handler)|Mapy **wm_command –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje souvislý rozsah **wm_command –** zpráv, které mají funkci obslužné rutiny na základě identifikátoru položky nabídky, řízení nebo akcelerátoru.|  
|[NOTIFY_HANDLER](#notify_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor ovládacího prvku.|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapy **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje souvislý rozsah **wm_notify –** zpráv, které mají funkci obslužné rutiny na základě řízení identifikátoru.|  
  
 Následující makra přímé zpráv na jiné mapy zpráv. Tento proces se nazývá "řetězení."  
  
|– Makro|Popis|  
|-----------|-----------------|  
|[CHAIN_MSG_MAP](#chain_msg_map)|Zřetězen do výchozí mapování zpráv v základní třídě.|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Zřetězen do výchozí mapování zpráv v datový člen třídy.|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Řetězy zprávu alternativní mapovat v základní třídě.|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Řetězy zprávu alternativní mapovat v datový člen třídy.|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Zřetězen do výchozí mapování zpráv v jiné třídy v době běhu.|  
  
 Následující makra přímé "Zobrazit" zprávy z nadřazeného okna. Například ovládacího prvku obvykle posílá zpráv s oznámením do jeho nadřazeného okna pro zpracování, ale nadřazeného okna můžete podle zprávy zpět do ovládacího prvku.  
  
|– Makro|Popis|  
|-----------|-----------------|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor položky nabídky, řízení nebo akcelerátoru.|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě identifikátoru položky nabídky, řízení nebo akcelerátoru.|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě souvislý rozsahu identifikátorů ovládacího prvku.|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Se mapuje reflektované **wm_command –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a souvislý rozsah identifikátorů ovládacího prvku.|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a identifikátor ovládacího prvku.|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kódu oznámení.|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě souvislý rozsahu identifikátorů ovládacího prvku.|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Se mapuje reflektované **wm_notify –** zpráva, která má funkci obslužné rutiny na základě kód oznámení a souvislý rozsah identifikátorů ovládacího prvku.|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]  
  
 Když `CMyExtWindow` přijímá objekt `WM_PAINT` zprávu, zpráva se přesměruje na `CMyExtWindow::OnPaint` pro vlastní zpracování. Pokud `OnPaint` určuje zpráva vyžaduje další zpracování, zpráva se pak přesměrováni na výchozí mapování zpráv v `CMyBaseWindow`.  
  
 Kromě výchozí mapování zpráv, můžete definovat mapování alternativní zprávu s [ALT_MSG_MAP](#alt_msg_map). Vždy začít mapy zpráv s `BEGIN_MSG_MAP`. Potom můžete deklarovat mapy následné alternativní zpráv. Následující příklad ukazuje mapy zpráv výchozí a alternativní jednu zprávu mapy, každá obsahuje jednu funkci obslužné rutiny:  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 Další příklad ukazuje dva mapy alternativní zpráv. Mapy zpráv výchozí je prázdný.  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
 [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Všimněte si, že vždy přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT  
 Definuje položku mapy zpráv.  
  
```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainClass`  
 [v] Název základní třídy obsahující mapy zpráv.  
  
 `msgMapID`  
 [v] Identifikátor mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `CHAIN_MSG_MAP_ALT`směrovat zprávy na mapě služby alternativní zpráva v základní třídě. Je nutné deklarované Tato mapa alternativní zprávu s [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Směrovat zprávy a pokuste se mapy zpráv výchozí základní třídu (deklarovat s [BEGIN_MSG_MAP](#begin_msg_map)), použijte `CHAIN_MSG_MAP`. Příklad, naleznete v části [CHAIN_MSG_MAP](#chain_msg_map).  
  
> [!NOTE]
>  Vždy začít mapy zpráv s `BEGIN_MSG_MAP`. Potom můžete deklarovat mapy následné alternativní zpráv s `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER  
 Definuje položku mapy zpráv.  
  
```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainMember`  
 [v] Název člena dat obsahující mapy zpráv.  
  
 `msgMapID`  
 [v] Identifikátor mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `CHAIN_MSG_MAP_ALT_MEMBER`směrovat zprávy na mapě služby alternativní zpráva v člena. Je nutné deklarované Tato mapa alternativní zprávu s [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Směrovat zprávy a pokuste se mapy zpráv výchozí datový člen (deklarovat s [BEGIN_MSG_MAP](#begin_msg_map)), použijte `CHAIN_MSG_MAP_MEMBER`. Příklad, naleznete v části [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).  
  
> [!NOTE]
>  Vždy začít mapy zpráv s `BEGIN_MSG_MAP`. Potom můžete deklarovat mapy následné alternativní zpráv s `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP  
 Definuje položku mapy zpráv.  
  
```
CHAIN_MSG_MAP(theChainClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainClass`  
 [v] Název základní třídy obsahující mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `CHAIN_MSG_MAP`přesměruje zprávy a pokuste se mapy zpráv výchozí základní třídu (deklarovat s [BEGIN_MSG_MAP](#begin_msg_map)). Směrovat zprávy a pokuste se mapa alternativní zpráv základní třídu (deklarovat s [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).  
  
> [!NOTE]
>  Vždy začít mapy zpráv s `BEGIN_MSG_MAP`. Potom můžete deklarovat mapy následné alternativní zpráv s `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]  
  
 Tento příklad ukazuje následující:  
  
-   Pokud je pomocí procedury okna `CMyClass`na výchozí mapy zpráv a `OnPaint` nemá popisovač zprávu, zpráva se přesměruje `CMyBaseClass`na výchozí mapy zpráv pro zpracování.  
  
-   Pokud okno postup používá první mapa alternativní zpráv v `CMyClass`, všechny zprávy jsou přesměrovány `CMyBaseClass`na výchozí mapy zpráv.  
  
-   Pokud je pomocí procedury okna `CMyClass`je druhá zpráva alternativní mapování a `OnChar` nemá popisovač zprávu, zpráva se přesměruje zadaná alternativní zpráva mapy ve `CMyBaseClass`. `CMyBaseClass`je nutné deklarované této mapy zpráv s `ALT_MSG_MAP(1)`.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC  
 Definuje položku mapy zpráv.  
  
```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```  
  
### <a name="parameters"></a>Parametry  
 *dynaChainID*  
 [v] Jedinečný identifikátor objektu mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `CHAIN_MSG_MAP_DYNAMIC`Určí, že zprávy, v době běhu k výchozí mapování zpráv v jiném objektu. Přidružený objekt a jeho mapy zpráv *dynaChainID*, které definujete prostřednictvím [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Musí být odvozeny třídě z `CDynamicChain` Chcete-li použít `CHAIN_MSG_MAP_DYNAMIC`. Příklad, naleznete v části [CDynamicChain](../../atl/reference/cdynamicchain-class.md) Přehled.  

  
> [!NOTE]
>  Vždy začít mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat mapy následné alternativní zpráv s `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER  
 Definuje položku mapy zpráv.  
  
```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```  
  
### <a name="parameters"></a>Parametry  
 `theChainMember`  
 [v] Název člena dat obsahující mapy zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `CHAIN_MSG_MAP_MEMBER`přesměruje zprávy a pokuste se mapy zpráv výchozí datový člen (deklarovat s [BEGIN_MSG_MAP](#begin_msg_map)). Směrovat zprávy a pokuste se mapy zpráv alternativní datový člen (deklarovat s [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).  
  
> [!NOTE]
>  Vždy začít mapy zpráv s `BEGIN_MSG_MAP`. Potom můžete deklarovat mapy následné alternativní zpráv s `ALT_MSG_MAP`. [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]  
  
 Tento příklad ukazuje následující:  
  
-   Pokud je pomocí procedury okna `CMyClass`na výchozí mapy zpráv a `OnPaint` nemá popisovač zprávu, zpráva se přesměruje `m_obj`na výchozí mapy zpráv pro zpracování.  
  
-   Pokud okno postup používá první mapa alternativní zpráv v `CMyClass`, všechny zprávy jsou přesměrovány `m_obj`na výchozí mapy zpráv.  
  
-   Pokud je pomocí procedury okna `CMyClass`je druhá zpráva alternativní mapování a `OnChar` nemá popisovač zprávu, zpráva se přesměruje zadaná alternativní zpráva mapu `m_obj`. Třída `CMyContainedClass` musí mít deklarován této mapy zpráv s `ALT_MSG_MAP(1)`.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="command_code_handler"></a>COMMAND_CODE_HANDLER  
 Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy pouze na základě oznámení kódu.  
  
```
COMMAND_CODE_HANDLER(code, func)
```  
  
### <a name="parameters"></a>Parametry  
 `code`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="command_handler"></a>COMMAND_HANDLER  
 Definuje položku mapy zpráv.  
  
```
COMMAND_HANDLER(id, code, func)
```    
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor položky nabídky, řízení nebo akcelerátoru.  
  
 `code`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `COMMAND_HANDLER`se mapuje [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zpráva funkce zadaná obslužná rutina, na základě kód oznámení a identifikátor ovládacího prvku. Příklad:  
  
 [!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]  
  
 Všechny funkce, zadaný v `COMMAND_HANDLER` makro musí být definován následujícím způsobem:  
  
 `LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`  
  
 Nastaví mapy zpráv `bHandled` k **TRUE** před `CommandHandler` je volána. Pokud `CommandHandler` plně nezpracovává zprávy, je potřeba nastavit `bHandled` k **FALSE** k označení zprávy potřebuje další zpracování.  
  
> [!NOTE]
>  Vždy začít mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat mapy následné alternativní zpráv s [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Kromě `COMMAND_HANDLER`, můžete použít [MESSAGE_HANDLER](#message_handler) mapovat **wm_command –** zpráv bez ohledu na identifikátor nebo kódu. V takovém případě `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` budou směrovat všechny **wm_command –** zprávy pro `OnHandlerFunction`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="command_id_handler"></a>COMMAND_ID_HANDLER  
 Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy pouze na základě identifikátoru položky nabídky, řízení nebo akcelerátoru.  
  
```
COMMAND_ID_HANDLER(id, func)
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor položky nabídky, řízení nebo odesílání zprávy akcelerátoru.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER  
 Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy s kódem konkrétní oznámení z rozsahu ovládacích prvků k jedné obslužné rutiny funkce.  
  
```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```    
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `code`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 Tento rozsah je založena na identifikátor položky nabídky, řízení nebo odesílání zprávy akcelerátoru.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="command_range_handler"></a>COMMAND_RANGE_HANDLER  
 Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy z rozsahu ovládacích prvků k jedné obslužné rutiny funkce.  
  
```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```    
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 Tento rozsah je založena na identifikátor položky nabídky, řízení nebo odesílání zprávy akcelerátoru.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP  
 Deklaruje mapování prázdná zpráva.  
  
```
DECLARE_EMPTY_MSG_MAP()
```  
  
### <a name="remarks"></a>Poznámky  
 `DECLARE_EMPTY_MSG_MAP`je užitečný makro, který volá makra [BEGIN_MSG_MAP](#begin_msg_map) a [END_MSG_MAP](#end_msg_map) k vytvoření mapy prázdná zpráva:  
  
 [!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]  
  
##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER  
 Poskytuje výchozí obslužnou rutinu pro podřízeného okna (řízení), která bude přijímat reflektovaných zpráv; Obslužná rutina správně předá neošetřené zprávy a pokuste se `DefWindowProc`.  
  
```
DEFAULT_REFLECTION_HANDLER()
```  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="end_msg_map"></a>END_MSG_MAP  
 Označuje konec mapy zpráv.  
  
```
END_MSG_MAP()
```  
  
### <a name="remarks"></a>Poznámky  
 Vždy nutné použít [BEGIN_MSG_MAP](#begin_msg_map) makro k označení začátku mapy zpráv. Použití [ALT_MSG_MAP](#alt_msg_map) deklarovat mapy následné alternativní zpráv.  
  
 Všimněte si, že vždy přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje mapy zpráv výchozí a alternativní jednu zprávu mapy, každá obsahuje jednu funkci obslužné rutiny:  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 Další příklad ukazuje dva mapy alternativní zpráv. Mapy zpráv výchozí je prázdný.  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS  
 Předává zprávy s oznámením do nadřazeného okna.  
  
```
FORWARD_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>Poznámky  
 Zadejte tento makro jako součást vaší mapy zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="message_handler"></a>MESSAGE_HANDLER  
 Definuje položku mapy zpráv.  
  
```
MESSAGE_HANDLER( msg, func )
```  
  
### <a name="parameters"></a>Parametry  
 `msg`  
 [v] Zpráva systému Windows.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `MESSAGE_HANDLER`zprávy Windows se mapuje na funkci zadaná obslužná rutina.  
  
 Všechny funkce, zadaný v `MESSAGE_HANDLER` makro musí být definován následujícím způsobem:  
  
 `LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`  
  
 Nastaví mapy zpráv `bHandled` k **TRUE** před `MessageHandler` je volána. Pokud `MessageHandler` plně nezpracovává zprávy, je potřeba nastavit `bHandled` k **FALSE** k označení zprávy potřebuje další zpracování.  
  
> [!NOTE]
>  Vždy začít mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat mapy následné alternativní zpráv s [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Kromě `MESSAGE_HANDLER`, můžete použít [COMMAND_HANDLER](#command_handler) a [NOTIFY_HANDLER](#notify_handler) mapovat [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) a [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy v uvedeném pořadí.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER  
 Podobně jako [MESSAGE_HANDLER](#message_handler), ale mapy rozsah Windows zprávy k jedné obslužné rutiny funkce.  
  
```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 *msgFirst*  
 [v] Označuje začátek souvislý rozsah zprávy.  
  
 *msgLast*  
 [v] Označuje konec souvislý rozsah zprávy.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER  
 Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy pouze na základě oznámení kódu.  
  
```
NOTIFY_CODE_HANDLER(cd, func)
```  
  
### <a name="parameters"></a>Parametry  
 `cd`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="notify_handler"></a>NOTIFY_HANDLER  
 Definuje položku mapy zpráv.  
  
```
NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor ovládacího prvku odesílání zprávy.  
  
 `cd`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 `NOTIFY_HANDLER`se mapuje [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zpráva funkce zadaná obslužná rutina, na základě kód oznámení a identifikátor ovládacího prvku.  
  
 Všechny funkce, zadaný v `NOTIFY_HANDLER` makro musí být definován následujícím způsobem:  
  
 `LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`  
  
 Nastaví mapy zpráv `bHandled` k **TRUE** před `NotifyHandler` je volána. Pokud `NotifyHandler` plně nezpracovává zprávy, je potřeba nastavit `bHandled` k **FALSE** k označení zprávy potřebuje další zpracování.  
  
> [!NOTE]
>  Vždy začít mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat mapy následné alternativní zpráv s [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) makro označuje konec mapy zpráv. Každý mapy zpráv musí mít přesně jednu instanci `BEGIN_MSG_MAP` a `END_MSG_MAP`.  
  
 Kromě `NOTIFY_HANDLER`, můžete použít [MESSAGE_HANDLER](#message_handler) mapovat **wm_notify –** zpráv bez ohledu na identifikátor nebo kódu. V takovém případě `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` budou směrovat všechny **wm_notify –** zprávy pro `OnHandlerFunction`.  
  
 Další informace o používání mapy zpráv v ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="notify_id_handler"></a>NOTIFY_ID_HANDLER  
 Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy pouze na základě řízení identifikátoru.  
  
```
NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor ovládacího prvku odesílání zprávy.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER  
 Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy s kódem konkrétní oznámení z rozsahu ovládacích prvků k jedné obslužné rutiny funkce.  
  
```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `cd`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 Tento rozsah je založena na identifikátor ovládacího prvku odesílání zprávy.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER  
 Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy z rozsahu ovládacích prvků k jedné obslužné rutiny funkce.  
  
```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="remarks"></a>Poznámky  
 Tento rozsah je založena na identifikátor ovládacího prvku odesílání zprávy.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS  
 Odráží zpráv s oznámením zpět do okna podřízené (řízení), který jim poslali.  
  
```
REFLECT_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>Poznámky  
 Zadejte tento makro jako součást nadřazeného okna mapa zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER  
 Podobně jako [COMMAND_CODE_HANDLER](#command_code_handler), ale mapuje příkazy projeví z nadřazeného okna.  
  
```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```  
  
### <a name="parameters"></a>Parametry  
 `code`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
   
##  <a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER  
 Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje příkazy projeví z nadřazeného okna.  
  
```
REFLECTED_COMMAND_HANDLER( id, code, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor položky nabídky, řízení nebo akcelerátoru.  
  
 `code`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER  
 Podobně jako [COMMAND_ID_HANDLER](#command_id_handler), ale mapuje příkazy projeví z nadřazeného okna.  
  
```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor položky nabídky, řízení nebo akcelerátoru.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER  
 Podobně jako [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapuje příkazy projeví z nadřazeného okna.  
  
```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `code`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER  
 Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje příkazy projeví z nadřazeného okna.  
  
```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER  
 Podobně jako [NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapuje oznámení projeví z nadřazeného okna.  
  
```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `cd`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER  
 Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje oznámení projeví z nadřazeného okna.  
  
```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor položky nabídky, řízení nebo akcelerátoru.  
  
 `cd`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER  
 Podobně jako [NOTIFY_ID_HANDLER](#notify_id_handler), ale mapuje oznámení projeví z nadřazeného okna.  
  
```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor položky nabídky, řízení nebo akcelerátoru.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

##  <a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER  
 Podobně jako [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapuje oznámení projeví z nadřazeného okna.  
  
```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```    
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `cd`  
 [v] Kód oznámení.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h   
  
##  <a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER  
 Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje oznámení projeví z nadřazeného okna.  
  
```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>Parametry  
 `idFirst`  
 [v] Označuje začátek souvislý rozsah identifikátorů ovládacího prvku.  
  
 `idLast`  
 [v] Označuje konec souvislý rozsah identifikátorů ovládacího prvku.  
  
 `func`  
 [v] Název funkce obslužné rutiny zpráv.  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
