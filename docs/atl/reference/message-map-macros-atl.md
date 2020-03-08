---
title: Makra map zpráv (ATL)
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
ms.openlocfilehash: 42fdc7a3f09568b641229e897a2a493994a7ba8a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862960"
---
# <a name="message-map-macros-atl"></a>Makra map zpráv (ATL)

Tato makra definují mapování a položky zpráv.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Označuje začátek alternativního mapování zpráv.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Označuje začátek výchozího mapování zprávy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Řetězí k alternativní mapě zpráv v základní třídě.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Řetězí k alternativní mapě zpráv v datovém členu třídy.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Řetězí k výchozímu mapování zpráv v základní třídě.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Řetězení k mapě zpráv v jiné třídě v době běhu.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Vytvoří řetěz k výchozímu mapování zpráv v datovém členu třídy.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení.|
|[COMMAND_HANDLER](#command_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky, ovládacího prvku nebo akcelerátoru nabídky.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacích prvků.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacích prvků.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje prázdnou mapu zpráv.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Poskytuje výchozí obslužnou rutinu pro zrcadlené zprávy, které nejsou zpracovávány jinak.|
|[END_MSG_MAP](#end_msg_map)|Označí konec mapy zprávy.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Přepošle oznamovací zprávy do nadřazeného okna.|
|[MESSAGE_HANDLER](#message_handler)|Namapuje zprávu Windows na funkci obslužné rutiny.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje souvislý rozsah zpráv systému Windows ke funkci obslužné rutiny.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacích prvků.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odmítne oznamovací zprávy zpět do okna, které je odeslalo.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacích prvků.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="alt_msg_map"></a>ALT_MSG_MAP

Označuje začátek alternativního mapování zpráv.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parametry

*msgMapID*<br/>
pro Identifikátor mapy zpráv

### <a name="remarks"></a>Poznámky

ATL identifikuje každou mapu zpráv podle čísla. Výchozí mapa zprávy (deklarovaná pomocí makra BEGIN_MSG_MAP) je identifikována 0. Alternativní mapa zpráv je identifikována nástrojem *msgMapID*.

Mapy zpráv se používají ke zpracování zpráv odesílaných do okna. Například [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) umožňuje zadat identifikátor mapy zprávy v objektu, který ho obsahuje. [CContainedWindow:: WindowProc](ccontainedwindowt-class.md#windowproc) potom použije tuto mapu zpráv k nasměrování zpráv obsažených oken buď na příslušnou funkci obslužné rutiny, nebo na jinou mapu zpráv. Seznam maker, která deklaruje funkce obslužné rutiny, naleznete v tématu [BEGIN_MSG_MAP](#begin_msg_map).

Vždy zahajte mapu zpráv pomocí BEGIN_MSG_MAP. Následně můžete deklarovat následné alternativní mapy zpráv.

[END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Všimněte si, že existuje vždy pouze jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje výchozí mapu zprávy a jednu alternativní mapu zpráv, z nichž každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Další příklad ukazuje dva alternativní mapy zpráv. Výchozí mapa zpráv je prázdná.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP

Označuje začátek výchozího mapování zprávy.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
pro Název třídy obsahující mapu zprávy

### <a name="remarks"></a>Poznámky

[CWindowImpl:: WindowProc](cwindowimpl-class.md#windowproc) používá výchozí mapu zpráv pro zpracování zpráv odesílaných do okna. Mapa zpráv směruje zprávy buď na příslušnou funkci obslužné rutiny, nebo na jinou mapu zpráv.

Následující makra mapují zprávu na funkci obslužné rutiny. Tato funkce musí být definovaná v *theclass*.

|– Makro|Popis|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Namapuje zprávu Windows na funkci obslužné rutiny.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapuje souvislý rozsah zpráv systému Windows ke funkci obslužné rutiny.|
|[COMMAND_HANDLER](#command_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky, ovládacího prvku nebo akcelerátoru nabídky.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mapuje zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje souvislý rozsah WM_COMMAND zpráv na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[NOTIFY_HANDLER](#notify_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje souvislý rozsah WM_NOTIFY zpráv na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|

Následující makra směrují zprávy na jinou mapu zpráv. Tento proces se nazývá řetězení.

|– Makro|Popis|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Řetězí k výchozímu mapování zpráv v základní třídě.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Vytvoří řetěz k výchozímu mapování zpráv v datovém členu třídy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Řetězí k alternativní mapě zpráv v základní třídě.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Řetězí k alternativní mapě zpráv v datovém členu třídy.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Řetězí k výchozímu mapování zpráv v jiné třídě v době běhu.|

Následující makra nasměrují "zrcadlené" zprávy z nadřazeného okna. Například ovládací prvek obvykle odesílá zprávy oznámení do svého nadřazeného okna pro zpracování, ale nadřazené okno může odrážet zprávu zpět do ovládacího prvku.

|– Makro|Popis|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mapuje zrcadlenou zprávu WM_COMMAND na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě souvislého rozsahu identifikátorů ovládacích prvků.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mapuje zrcadlenou zprávu WM_NOTIFY na funkci obslužné rutiny na základě kódu oznámení a souvislého rozsahu identifikátorů ovládacích prvků.|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Když objekt `CMyExtWindow` obdrží zprávu WM_PAINT, bude zpráva směrována na `CMyExtWindow::OnPaint` pro skutečné zpracování. Pokud `OnPaint` označuje, že zpráva vyžaduje další zpracování, bude zpráva přesměrována na výchozí mapu zprávy v `CMyBaseWindow`.

Kromě výchozího mapování zpráv můžete definovat alternativní mapu zpráv pomocí [ALT_MSG_MAP](#alt_msg_map). Vždy zahajte mapu zpráv pomocí BEGIN_MSG_MAP. Následně můžete deklarovat následné alternativní mapy zpráv. Následující příklad ukazuje výchozí mapu zprávy a jednu alternativní mapu zpráv, z nichž každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Další příklad ukazuje dva alternativní mapy zpráv. Výchozí mapa zpráv je prázdná.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Všimněte si, že existuje vždy pouze jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
pro Název základní třídy obsahující mapu zprávy.

*msgMapID*<br/>
pro Identifikátor mapy zpráv

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_ALT směruje zprávy na alternativní mapu zpráv v základní třídě. Tuto alternativní mapu zpráv musíte deklarovat pomocí [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Chcete-li směrovat zprávy do výchozího mapování zpráv základní třídy (deklarováno s [BEGIN_MSG_MAP](#begin_msg_map)), použijte CHAIN_MSG_MAP. Příklad naleznete v tématu [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí BEGIN_MSG_MAP. Pak můžete pomocí ALT_MSG_MAP deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
pro Název datového členu, který obsahuje mapu zprávy.

*msgMapID*<br/>
pro Identifikátor mapy zpráv

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_ALT_MEMBER směruje zprávy na alternativní mapu zpráv v datovém členu. Tuto alternativní mapu zpráv musíte deklarovat pomocí [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Chcete-li směrovat zprávy na výchozí mapu zpráv datového člena (deklarovaný s [BEGIN_MSG_MAP](#begin_msg_map)), použijte CHAIN_MSG_MAP_MEMBER. Příklad naleznete v tématu [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí BEGIN_MSG_MAP. Pak můžete pomocí ALT_MSG_MAP deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
pro Název základní třídy obsahující mapu zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP směruje zprávy na výchozí mapu zprávy základní třídy (deklarovaný s [BEGIN_MSG_MAP](#begin_msg_map)). Chcete-li směrovat zprávy na alternativní mapu zpráv základní třídy (deklarována s [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí BEGIN_MSG_MAP. Pak můžete pomocí ALT_MSG_MAP deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Tento příklad ilustruje následující:

- Pokud procedura okna používá výchozí mapu zpráv `CMyClass`a `OnPaint` nezpracovává zprávu, zpráva se přesměruje na výchozí mapu zpráv `CMyBaseClass`pro zpracování.

- Pokud se v `CMyClass`procedura používá první alternativní mapa zpráv v, všechny zprávy se přesměrují na výchozí mapu zpráv `CMyBaseClass`.

- Pokud procedura okna používá druhé alternativní mapování zpráv `CMyClass`a `OnChar` nezpracovává zprávu, zpráva se přesměruje na zadané alternativní mapování zpráv v `CMyBaseClass`. `CMyBaseClass` musí mít tuto mapu zpráv deklarovanou ALT_MSG_MAP (1).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parametry

*dynaChainID*<br/>
pro Jedinečný identifikátor pro mapu zpráv objektu.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_DYNAMIC směruje zprávy v době běhu do výchozí mapy zpráv v jiném objektu. Objekt a jeho mapa zpráv jsou přidruženy k *dynaChainID*, které definujete prostřednictvím [CDynamicChain:: SetChainEntry](cdynamicchain-class.md#setchainentry). Třídu musíte odvodit z `CDynamicChain`, aby bylo možné použít CHAIN_MSG_MAP_DYNAMIC. Příklad najdete v přehledu [CDynamicChain](../../atl/reference/cdynamicchain-class.md) .

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí [BEGIN_MSG_MAP](#begin_msg_map). Pak můžete pomocí ALT_MSG_MAP deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Definuje položku v mapě zpráv.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
pro Název datového členu, který obsahuje mapu zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_MEMBER směruje zprávy na výchozí mapu zpráv datového člena (deklarovaný s [BEGIN_MSG_MAP](#begin_msg_map)). Chcete-li směrovat zprávy na alternativní mapu zpráv datového člena (deklarovaný s [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí BEGIN_MSG_MAP. Pak můžete pomocí ALT_MSG_MAP deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Tento příklad ilustruje následující:

- Pokud procedura okna používá výchozí mapu zpráv `CMyClass`a `OnPaint` nezpracovává zprávu, zpráva se přesměruje na výchozí mapu zpráv `m_obj`pro zpracování.

- Pokud se v `CMyClass`procedura používá první alternativní mapa zpráv v, všechny zprávy se přesměrují na výchozí mapu zpráv `m_obj`.

- Pokud procedura okna používá druhé alternativní mapování zpráv `CMyClass`a `OnChar` nezpracovává zprávu, zpráva se přesměruje na určenou alternativní mapu zpráv `m_obj`. `CMyContainedClass` třídy musí mít tuto mapu zpráv deklarovanou ALT_MSG_MAP (1).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) na základě kódu oznámení.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parametry

*znakovou*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="command_handler"></a>COMMAND_HANDLER

Definuje položku v mapě zpráv.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru

*znakovou*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

COMMAND_HANDLER mapuje zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) na zadanou funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku. Příklad:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Všechny funkce zadané v makru COMMAND_HANDLER musí být definovány takto:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Mapa zpráv `bHandled` nastavena na hodnotu TRUE před voláním `CommandHandler`. Pokud `CommandHandler` zprávu zcela nezpracovává, měla by být nastavena `bHandled` na hodnotu FALSE, aby označovala, že zpráva potřebuje další zpracování.

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí [BEGIN_MSG_MAP](#begin_msg_map). Pak můžete pomocí [ALT_MSG_MAP](#alt_msg_map)deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě COMMAND_HANDLER můžete použít [MESSAGE_HANDLER](#message_handler) k namapování WM_COMMAND zprávy bez ohledu na identifikátor nebo kód. V takovém případě bude `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` směrovat všechny WM_COMMAND zprávy na `OnHandlerFunction`.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="command_id_handler"></a>COMMAND_ID_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje zprávu [WM_COMMAND](/windows/win32/menurc/wm-command) na základě identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru, který posílá zprávu

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje [WM_COMMAND](/windows/win32/menurc/wm-command) zprávy s určitým kódem oznámení z rozsahu ovládacích prvků na jedinou funkci obslužné rutiny.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*znakovou*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru, který posílá zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [WM_COMMAND](/windows/win32/menurc/wm-command) zprávy z rozsahu ovládacích prvků na jedinou funkci obslužné rutiny.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru položky nabídky, ovládacího prvku nebo akcelerátoru, který posílá zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Deklaruje prázdnou mapu zprávy.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Poznámky

DECLARE_EMPTY_MSG_MAP je praktické makro, které volá makra [BEGIN_MSG_MAP](#begin_msg_map) a [END_MSG_MAP](#end_msg_map) k vytvoření prázdné mapy zpráv:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Poskytuje výchozí obslužnou rutinu pro podřízené okno (ovládací prvek), které obdrží odrážetelné zprávy. Obslužná rutina bude správně předávat neošetřené zprávy `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="end_msg_map"></a>END_MSG_MAP

Označí konec mapy zprávy.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Poznámky

Vždy použijte [BEGIN_MSG_MAP](#begin_msg_map) makro k označení začátku mapy zprávy. Použijte [ALT_MSG_MAP](#alt_msg_map) k deklaraci dalších alternativních map zpráv.

Všimněte si, že existuje vždy pouze jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje výchozí mapu zprávy a jednu alternativní mapu zpráv, z nichž každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Další příklad ukazuje dva alternativní mapy zpráv. Výchozí mapa zpráv je prázdná.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Přepošle oznamovací zprávy do nadřazeného okna.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Poznámky

Zadejte toto makro jako součást mapy zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="message_handler"></a>MESSAGE_HANDLER

Definuje položku v mapě zpráv.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parametry

*MSG*<br/>
pro Zpráva Windows

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

MESSAGE_HANDLER mapuje zprávu systému Windows k zadané funkci obslužné rutiny.

Všechny funkce zadané v makru MESSAGE_HANDLER musí být definovány takto:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Mapa zpráv `bHandled` nastavena na hodnotu TRUE před voláním `MessageHandler`. Pokud `MessageHandler` zprávu zcela nezpracovává, měla by být nastavena `bHandled` na hodnotu FALSE, aby označovala, že zpráva potřebuje další zpracování.

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí [BEGIN_MSG_MAP](#begin_msg_map). Pak můžete pomocí [ALT_MSG_MAP](#alt_msg_map)deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě MESSAGE_HANDLER můžete použít [COMMAND_HANDLER](#command_handler) a [NOTIFY_HANDLER](#notify_handler) k mapování [WM_COMMAND](/windows/win32/menurc/wm-command) a [WM_NOTIFYch](/windows/win32/controls/wm-notify) zpráv v uvedeném pořadí.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Podobně jako [MESSAGE_HANDLER](#message_handler), ale mapuje řadu zpráv Windows na jednu funkci obslužné rutiny.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parametry

*msgFirst*<br/>
pro Označuje začátek souvislého rozsahu zpráv.

*msgLast*<br/>
pro Označuje konec souvislého rozsahu zpráv.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje zprávu [WM_NOTIFY](/windows/win32/controls/wm-notify) na základě kódu oznámení.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parametry

*CD*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="notify_handler"></a>NOTIFY_HANDLER

Definuje položku v mapě zpráv.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor ovládacího prvku, který odesílá zprávu

*CD*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

NOTIFY_HANDLER mapuje zprávu [WM_NOTIFY](/windows/win32/controls/wm-notify) na zadanou funkci obslužné rutiny na základě kódu oznámení a identifikátoru ovládacího prvku.

Všechny funkce zadané v makru NOTIFY_HANDLER musí být definovány takto:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Mapa zpráv `bHandled` nastavena na hodnotu TRUE před voláním `NotifyHandler`. Pokud `NotifyHandler` zprávu zcela nezpracovává, měla by být nastavena `bHandled` na hodnotu FALSE, aby označovala, že zpráva potřebuje další zpracování.

> [!NOTE]
>  Vždy zahajte mapu zpráv pomocí [BEGIN_MSG_MAP](#begin_msg_map). Pak můžete pomocí [ALT_MSG_MAP](#alt_msg_map)deklarovat následné alternativní mapy zpráv. [END_MSG_MAP](#end_msg_map) makro označí konec mapy zprávy. Každá mapa zpráv musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě NOTIFY_HANDLER můžete použít [MESSAGE_HANDLER](#message_handler) k namapování WM_NOTIFY zprávy bez ohledu na identifikátor nebo kód. V takovém případě bude `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` směrovat všechny WM_NOTIFY zprávy na `OnHandlerFunction`.

Další informace o použití map zpráv v knihovně ATL najdete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje zprávu [WM_NOTIFY](/windows/win32/controls/wm-notify) na základě identifikátoru ovládacího prvku.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor ovládacího prvku, který odesílá zprávu

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávy s určitým kódem oznámení z rozsahu ovládacích prvků na jedinou funkci obslužné rutiny.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*CD*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru ovládacího prvku odesílajícího zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](/windows/win32/controls/wm-notify) zprávy z rozsahu ovládacích prvků na jedinou funkci obslužné rutiny.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="remarks"></a>Poznámky

Tento rozsah je založen na identifikátoru ovládacího prvku odesílajícího zprávu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Odráží oznamovací zprávy zpátky do podřízeného okna (ovládacího prvku), které je odeslalo.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Poznámky

Zadejte toto makro jako součást mapy zpráv nadřazeného okna.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Podobně jako [COMMAND_CODE_HANDLER](#command_code_handler), ale mapy příkazů, které se projeví v nadřazeném okně.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parametry

*znakovou*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapy příkazů, které se projeví v nadřazeném okně.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru

*znakovou*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Podobně jako [COMMAND_ID_HANDLER](#command_id_handler), ale mapy příkazů, které se projeví v nadřazeném okně.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Podobně jako [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapy příkazů, které se projeví v nadřazeném okně.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*znakovou*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapy příkazů, které se projeví v nadřazeném okně.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Podobně jako u [NOTIFY_CODE_HANDLER](#notify_code_handler), ale oznámení o mapách se projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parametry

*CD*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Podobně jako u [NOTIFY_HANDLER](#notify_handler), ale oznámení o mapách se projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru

*CD*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Podobně jako u [NOTIFY_ID_HANDLER](#notify_id_handler), ale oznámení o mapách se projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikátor položky nabídky, ovládacího prvku nebo akcelerátoru

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Podobně jako u [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale oznámení o mapách se projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*CD*<br/>
pro Kód oznámení.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Podobně jako u [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale oznámení o mapách se projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
pro Označuje začátek souvislého rozsahu identifikátorů ovládacích prvků.

*idLast*<br/>
pro Označuje konec souvislého rozsahu identifikátorů ovládacích prvků.

*func*<br/>
pro Název funkce obslužné rutiny zpráv.

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)
