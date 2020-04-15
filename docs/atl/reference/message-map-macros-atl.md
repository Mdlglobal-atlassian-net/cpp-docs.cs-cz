---
title: Makra mapy zpráv (ATL)
ms.date: 11/04/2016
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
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326220"
---
# <a name="message-map-macros-atl"></a>Makra mapy zpráv (ATL)

Tato makra definují mapy zpráv a položky.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Označuje začátek mapy alternativnízprávy.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Označuje začátek výchozí mapy zpráv.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Řetězy na alternativní mapy zpráv v základní třídě.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Řetězy na alternativní zprávy mapování v datovém členu třídy.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Řetězy na výchozí mapu zpráv v základní třídě.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Řetězy na mapu zpráv v jiné třídě za běhu.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Řetězy na výchozí mapování zpráv v datovém členu třídy.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení.|
|[COMMAND_HANDLER](#command_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacího prvku.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacího prvku.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje mapu prázdných zpráv.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Poskytuje výchozí obslužnou rutinu pro odražené zprávy, které nejsou zpracovány jinak.|
|[END_MSG_MAP](#end_msg_map)|Označuje konec mapy zpráv.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Předá oznámení do nadřazeného okna.|
|[MESSAGE_HANDLER](#message_handler)|Mapuje zprávu systému Windows na funkci obslužné rutiny.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje souvislý rozsah zpráv systému Windows na funkci obslužné rutiny.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje WM_NOTIFY zprávu na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacího prvku.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odráží oznámení zpět do okna, které je odeslalo.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odražené WM_COMMAND zprávy na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odražené WM_COMMAND zprávy na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odražené WM_COMMAND zprávy na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odražené WM_COMMAND zprávu na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odražené WM_COMMAND zprávu na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odražené WM_NOTIFY zprávy na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odražené WM_NOTIFY zprávu na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odražené WM_NOTIFY zprávu na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odražené WM_NOTIFY zprávu na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odražené WM_NOTIFY zprávy na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacího prvku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

Označuje začátek mapy alternativnízprávy.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parametry

*msgMapID*<br/>
[v] Identifikátor mapy zprávy.

### <a name="remarks"></a>Poznámky

Atl identifikuje každou mapu zpráv podle čísla. Výchozí mapa zpráv (deklarovaná s BEGIN_MSG_MAP makro) je označena hodnotou 0. Alternativní mapa zpráv je *identifikována msgMapID*.

Mapy zpráv se používají ke zpracování zpráv odeslaných do okna. [Například CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) umožňuje zadat identifikátor mapy zprávy v obsahující objekt. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) pak používá tuto mapu zprávy k přesměrování zprávy obsažené okno buď na příslušnou funkci obslužné rutiny nebo na jiné mapování zpráv. Seznam maker, která deklarují funkce obslužné rutiny, naleznete [v tématu BEGIN_MSG_MAP](#begin_msg_map).

Vždy začínat mapu zpráv s BEGIN_MSG_MAP. Potom můžete deklarovat následné mapy alternativní zprávy.

Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Všimněte si, že je vždy přesně jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje výchozí mapu zpráv a jednu alternativní mapu zpráv, z nichž každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Následující příklad ukazuje dvě alternativní mapy zpráv. Výchozí mapa zpráv je prázdná.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

Označuje začátek výchozí mapy zpráv.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[v] Název třídy obsahující mapu zpráv.

### <a name="remarks"></a>Poznámky

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) používá výchozí mapu zpráv ke zpracování zpráv odeslaných do okna. Mapa zpráv směruje zprávy buď na příslušnou funkci obslužné rutiny nebo na jinou mapu zpráv.

Následující makra mapují zprávu na funkci obslužné rutiny. Tato funkce musí být *definována*v class .

|Makro|Popis|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mapuje zprávu systému Windows na funkci obslužné rutiny.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje souvislý rozsah zpráv systému Windows na funkci obslužné rutiny.|
|[COMMAND_HANDLER](#command_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje souvislý rozsah WM_COMMAND zpráv na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje WM_NOTIFY zprávu na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje souvislý rozsah WM_NOTIFY zpráv na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|

Následující makra směrují zprávy na jiné mapování zpráv. Tento proces se nazývá "řetězení".

|Makro|Popis|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Řetězy na výchozí mapu zpráv v základní třídě.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Řetězy na výchozí mapování zpráv v datovém členu třídy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Řetězy na alternativní mapy zpráv v základní třídě.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Řetězy na alternativní zprávy mapování v datovém členu třídy.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Řetězy na výchozí mapu zpráv v jiné třídě za běhu.|

Následující makra přímé "odražené" zprávy z nadřazeného okna. Například ovládací prvek obvykle odešle oznámení do nadřazeného okna pro zpracování, ale nadřazené okno může odrážet zprávu zpět do ovládacího prvku.

|Makro|Popis|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje odražené WM_COMMAND zprávy na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje odražené WM_COMMAND zprávy na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje odražené WM_COMMAND zprávy na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje odražené WM_COMMAND zprávu na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje odražené WM_COMMAND zprávu na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje odražené WM_NOTIFY zprávu na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje odražené WM_NOTIFY zprávu na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje odražené WM_NOTIFY zprávy na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje odražené WM_NOTIFY zprávy na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje odražené WM_NOTIFY zprávu na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacího prvku.|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Když `CMyExtWindow` objekt obdrží zprávu WM_PAINT, zpráva je `CMyExtWindow::OnPaint` směrována na skutečné zpracování. Pokud `OnPaint` označuje, že zpráva vyžaduje další zpracování, bude zpráva `CMyBaseWindow`přesměrována na výchozí mapu zpráv v .

Kromě výchozího mapování zpráv můžete definovat alternativní mapu zpráv s [ALT_MSG_MAP](#alt_msg_map). Vždy začínat mapu zpráv s BEGIN_MSG_MAP. Potom můžete deklarovat následné mapy alternativní zprávy. Následující příklad ukazuje výchozí mapu zpráv a jednu alternativní mapu zpráv, z nichž každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Následující příklad ukazuje dvě alternativní mapy zpráv. Výchozí mapa zpráv je prázdná.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Všimněte si, že je vždy přesně jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
[v] Název základní třídy obsahující mapu zpráv.

*msgMapID*<br/>
[v] Identifikátor mapy zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_ALT směruje zprávy na alternativní mapu zpráv v základní třídě. Musíte deklarovat tuto mapu alternativní zprávy s [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Chcete-li směrovat zprávy na výchozí mapu zpráv základní třídy (deklarované s [BEGIN_MSG_MAP](#begin_msg_map)), použijte CHAIN_MSG_MAP. Příklad naleznete v [tématu CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Vždy začínat mapu zpráv s BEGIN_MSG_MAP. Potom můžete deklarovat následné mapy alternativních zpráv s ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parametry

*člen řetězce*<br/>
[v] Název datového člena obsahujícího mapu zpráv.

*msgMapID*<br/>
[v] Identifikátor mapy zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_ALT_MEMBER směruje zprávy na alternativní mapu zpráv v datovém prvku. Musíte deklarovat tuto mapu alternativní zprávy s [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Chcete-li směrovat zprávy na výchozí mapu zpráv datového člena (deklarované s [BEGIN_MSG_MAP](#begin_msg_map)), použijte CHAIN_MSG_MAP_MEMBER. Viz například [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Vždy začínat mapu zpráv s BEGIN_MSG_MAP. Potom můžete deklarovat následné mapy alternativních zpráv s ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
[v] Název základní třídy obsahující mapu zpráv.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP směruje zprávy na výchozí mapu zpráv základní třídy (deklarované s [BEGIN_MSG_MAP).](#begin_msg_map) Chcete-li směrovat zprávy na alternativní mapu zpráv základní třídy (deklarované s [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
> Vždy začínat mapu zpráv s BEGIN_MSG_MAP. Potom můžete deklarovat následné mapy alternativních zpráv s ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Tento příklad ilustruje následující:

- Pokud procedura okna `CMyClass`používá výchozí mapu `OnPaint` zpráv společnosti a nezpracovává zprávu, je zpráva přesměrována na `CMyBaseClass`výchozí mapu zpráv společnosti pro zpracování.

- Pokud procedura okna používá první alternativní `CMyClass`mapu zpráv v `CMyBaseClass`aplikace , jsou všechny zprávy směrovány na výchozí mapu zpráv společnosti .

- Pokud procedura okna `CMyClass`používá druhou alternativní `OnChar` mapu zpráv aplikace a nezpracovává zprávu, je zpráva `CMyBaseClass`přesměrována na zadanou mapu alternativních zpráv v . `CMyBaseClass`musí deklarovat tuto mapu zpráv s ALT_MSG_MAP(1).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parametry

*dynaChainID*<br/>
[v] Jedinečný identifikátor mapy zpráv objektu.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_DYNAMIC přesměruje zprávy za běhu na výchozí mapu zpráv v jiném objektu. Objekt a jeho mapa zpráv jsou přidruženy k *dynaChainID*, který definujete pomocí [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Chcete-li použít `CDynamicChain` CHAIN_MSG_MAP_DYNAMIC, musíte třídu odvodit. Například viz přehled [CDynamicChain.](../../atl/reference/cdynamicchain-class.md)

> [!NOTE]
> Vždy začínat mapu zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat následné mapy alternativních zpráv s ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parametry

*člen řetězce*<br/>
[v] Název datového člena obsahujícího mapu zpráv.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_MEMBER směruje zprávy na výchozí mapu zpráv datového člena (deklarované s [BEGIN_MSG_MAP).](#begin_msg_map) Chcete-li směrovat zprávy na alternativní mapu zpráv datového člena (deklarované s [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
> Vždy začínat mapu zpráv s BEGIN_MSG_MAP. Potom můžete deklarovat následné mapy alternativních zpráv s ALT_MSG_MAP. Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Tento příklad ilustruje následující:

- Pokud procedura okna `CMyClass`používá výchozí mapu `OnPaint` zpráv společnosti a nezpracovává zprávu, je zpráva přesměrována na `m_obj`výchozí mapu zpráv společnosti pro zpracování.

- Pokud procedura okna používá první alternativní `CMyClass`mapu zpráv v `m_obj`aplikace , jsou všechny zprávy směrovány na výchozí mapu zpráv společnosti .

- Pokud procedura okna `CMyClass`používá druhou alternativní `OnChar` mapu zpráv společnosti a nezpracovává zprávu, je zpráva `m_obj`přesměrována na zadanou mapu alternativních zpráv aplikace . Třída `CMyContainedClass` musí deklarovat tuto mapu zpráv s ALT_MSG_MAP(1).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](/windows/win32/menurc/wm-command) zprávu pouze na základě kódu oznámení.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parametry

*Kód*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

Definuje položku v mapě zpráv.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru.

*Kód*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

COMMAND_HANDLER mapuje [WM_COMMAND](/windows/win32/menurc/wm-command) zprávu na zadanou funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku. Příklad:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Každá funkce určená v COMMAND_HANDLER makro musí být definována takto:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Mapa zpráv `bHandled` se nastaví na TRUE před `CommandHandler` je volána. Pokud `CommandHandler` není plně zpracovat zprávu, `bHandled` by měla být nastavena na HODNOTU NEPRAVDA označuje zprávu potřebuje další zpracování.

> [!NOTE]
> Vždy začínat mapu zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat následné mapy alternativních zpráv s [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě COMMAND_HANDLER můžete pomocí [MESSAGE_HANDLER](#message_handler) mapovat WM_COMMAND zprávu bez ohledu na identifikátor nebo kód. V takovém `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` případě bude všechny `OnHandlerFunction`WM_COMMAND zprávy nasměrovat na .

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [zprávu WM_COMMAND](/windows/win32/menurc/wm-command) pouze na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru odesílajícího zprávu.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje [WM_COMMAND](/windows/win32/menurc/wm-command) zprávy s konkrétním kódem oznámení z rozsahu ovládacích prvků na jednu funkci obslužné rutiny.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*Kód*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru odesílajícího zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](/windows/win32/menurc/wm-command) zprávy z rozsahu ovládacích prvků na jednu funkci obslužné rutiny.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru odesílajícího zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Deklaruje mapu prázdných zpráv.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Poznámky

DECLARE_EMPTY_MSG_MAP je pohodlné makro, které volá makra [BEGIN_MSG_MAP](#begin_msg_map) a [END_MSG_MAP](#end_msg_map) k vytvoření prázdné mapy zpráv:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Poskytuje výchozí obslužnou rutinu pro podřízené okno (ovládací prvek), který obdrží odražené zprávy; obslužná rutina `DefWindowProc`bude správně předávat neošetřené zprávy společnosti .

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

Označuje konec mapy zpráv.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Poznámky

Vždy použijte [BEGIN_MSG_MAP](#begin_msg_map) makro k označení začátku mapy zpráv. Pomocí [ALT_MSG_MAP](#alt_msg_map) deklarujte následné mapy alternativních zpráv.

Všimněte si, že je vždy přesně jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje výchozí mapu zpráv a jednu alternativní mapu zpráv, z nichž každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Následující příklad ukazuje dvě alternativní mapy zpráv. Výchozí mapa zpráv je prázdná.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Předá oznámení do nadřazeného okna.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Poznámky

Toto makro zadejte jako součást mapy zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

Definuje položku v mapě zpráv.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parametry

*msg*<br/>
[v] Zpráva systému Windows.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

MESSAGE_HANDLER mapuje zprávu systému Windows na zadanou funkci obslužné rutiny.

Každá funkce zadaná v MESSAGE_HANDLER makro musí být definována takto:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Mapa zpráv `bHandled` se nastaví na TRUE před `MessageHandler` je volána. Pokud `MessageHandler` není plně zpracovat zprávu, `bHandled` by měla být nastavena na HODNOTU NEPRAVDA označuje zprávu potřebuje další zpracování.

> [!NOTE]
> Vždy začínat mapu zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat následné mapy alternativních zpráv s [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě MESSAGE_HANDLER můžete pomocí [COMMAND_HANDLER](#command_handler) a [NOTIFY_HANDLER](#notify_handler) mapovat [WM_COMMAND](/windows/win32/menurc/wm-command) a [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávy.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Podobně jako [MESSAGE_HANDLER](#message_handler), ale mapuje rozsah zpráv systému Windows na jednu funkci obslužné rutiny.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parametry

*msgPrvní*<br/>
[v] Označuje začátek souvislého rozsahu zpráv.

*msgLast*<br/>
[v] Označuje konec souvislého rozsahu zpráv.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávu pouze na základě kódu oznámení.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parametry

*Cd*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

Definuje položku v mapě zpráv.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor ovládacího prvku odesílajícího zprávu.

*Cd*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

NOTIFY_HANDLER mapuje [zprávu WM_NOTIFY](/windows/win32/controls/wm-notify) na zadanou funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.

Každá funkce určená v NOTIFY_HANDLER makro musí být definována takto:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Mapa zpráv `bHandled` se nastaví na TRUE před `NotifyHandler` je volána. Pokud `NotifyHandler` není plně zpracovat zprávu, `bHandled` by měla být nastavena na HODNOTU NEPRAVDA označuje zprávu potřebuje další zpracování.

> [!NOTE]
> Vždy začínat mapu zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Potom můžete deklarovat následné mapy alternativních zpráv s [ALT_MSG_MAP](#alt_msg_map). Makro [END_MSG_MAP](#end_msg_map) označuje konec mapy zpráv. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě NOTIFY_HANDLER můžete pomocí [MESSAGE_HANDLER](#message_handler) mapovat WM_NOTIFY zprávu bez ohledu na identifikátor nebo kód. V takovém `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` případě bude směřovat všechny WM_NOTIFY zprávy na `OnHandlerFunction`.

Další informace o používání map zpráv v atl naleznete v [tématu Mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávu pouze na základě identifikátoru ovládacího prvku.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor ovládacího prvku odesílajícího zprávu.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávy s konkrétním kódem oznámení z rozsahu ovládacích prvků na jednu funkci obslužné rutiny.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*Cd*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru ovládacího prvku odesílajícího zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávy z rozsahu ovládacích prvků na jednu funkci obslužné rutiny.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru ovládacího prvku odesílajícího zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Odráží oznámení zpět do podřízeného okna (ovládacího prvku), který je odeslal.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Poznámky

Zadejte toto makro jako součást mapy zpráv nadřazeného okna.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Podobně jako [COMMAND_CODE_HANDLER](#command_code_handler), ale mapy příkazy odráží od nadřazeného okna.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parametry

*Kód*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapy příkazy odráží od nadřazeného okna.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru.

*Kód*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Podobně jako [COMMAND_ID_HANDLER](#command_id_handler), ale mapuje příkazy odražené z nadřazeného okna.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Podobně jako [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapuje příkazy odražené z nadřazeného okna.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*Kód*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapy příkazy odráží od nadřazeného okna.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Podobně jako [NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapy oznámení odráží od nadřazeného okna.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parametry

*Cd*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapy oznámení odráží od nadřazeného okna.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru.

*Cd*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Podobně jako [NOTIFY_ID_HANDLER](#notify_id_handler), ale mapy oznámení odráží od nadřazeného okna.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Podobně jako [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapy oznámení odráží od nadřazeného okna.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*Cd*<br/>
[v] Kód oznámení.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapy oznámení odráží od nadřazeného okna.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idPrvní*<br/>
[v] Označuje začátek souvislého rozsahu identifikátorů ovládacího prvku.

*idPoslední*<br/>
[v] Označuje konec souvislého rozsahu identifikátorů ovládacího prvku.

*func*<br/>
[v] Název funkce obslužné rutiny zprávy.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
