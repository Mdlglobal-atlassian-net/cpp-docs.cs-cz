---
title: Makra Map (ATL) zpráva | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbfd58491981cdba1b3aa3002736f49a7c09038c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054473"
---
# <a name="message-map-macros-atl"></a>Makra Map zpráv (ATL)

Tato makra definují mapy zpráv a položky.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Označuje začátek toho mapování alternativních zprávy.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Označuje začátek toho výchozí mapování zprávy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Je zřetězen do mapování alternativních zprávy v základní třídě.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Je zřetězen do mapování alternativních zprávu v datovém členu třídy.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Je zřetězen do výchozího mapování zpráv v základní třídě.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Je zřetězen do mapy zpráv v jiné třídě v době běhu.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Je zřetězen do výchozího mapování zprávu v datovém členu třídy.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě kódu oznámení.|
|[COMMAND_HANDLER](#command_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a souvislý rozsah identifikátory ovládacího prvku.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu pro souvislý rozsah identifikátorů ovládacího prvku.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implementuje mapu prázdnou zprávu.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Poskytuje výchozí obslužnou rutinu pro zrcadlené zprávy, které nejsou zpracovány jinak.|
|[END_MSG_MAP](#end_msg_map)|Označuje konec mapy zpráv.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Přeposílá zprávy upozornění do nadřazeného okna.|
|[MESSAGE_HANDLER](#message_handler)|Mapuje na funkci obslužné rutiny zpráv Windows.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapování zpráv Windows souvislý rozsah funkce obslužné rutiny.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje na obslužnou rutinu, na základě kódu oznámení wm_notify – zprávy.|
|[NOTIFY_HANDLER](#notify_handler)|Wm_notify – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a identifikátor ovládacího prvku.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Wm_notify – zprávy se mapuje na obslužnou rutinu, na základě identifikátoru ovládacího prvku.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Wm_notify – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a souvislý rozsah identifikátory ovládacího prvku.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Wm_notify – zprávy se mapuje na obslužnou rutinu pro souvislý rozsah identifikátorů ovládacího prvku.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Odráží zpráv s oznámením zpět do okna, která je odeslána.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje zrcadlené zprávy wm_command – obslužná rutina funkce, na základě kódu oznámení.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje zrcadlené zprávy wm_command – obslužná rutina funkce, na základě kód upozornění a identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje zrcadlené zprávy wm_command – obslužná rutina funkce, na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Zrcadlené wm_command – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a souvislý rozsah identifikátory ovládacího prvku.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje zrcadlené wm_command – zprávy pro obslužnou rutinu pro souvislý rozsah identifikátorů ovládacího prvku.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje zrcadlené wm_notify – zprávy pro obslužnou rutinu, na základě kódu oznámení.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje zrcadlené wm_notify – zprávy pro obslužnou rutinu, na základě kód upozornění a identifikátor ovládacího prvku.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Zrcadlené wm_notify – zprávy se mapuje na obslužnou rutinu, na základě identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Zrcadlené wm_notify – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a souvislý rozsah identifikátory ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje zrcadlené wm_notify – zprávy pro obslužnou rutinu pro souvislý rozsah identifikátorů ovládacího prvku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="alt_msg_map"></a>  ALT_MSG_MAP

Označuje začátek toho mapování alternativních zprávy.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Parametry

*msgMapID*<br/>
[in] Identifikátor mapování zprávy.

### <a name="remarks"></a>Poznámky

ATL – identifikuje každý mapu zpráv podle čísla. Výchozí mapování zpráv (deklarované pomocí – makro BEGIN_MSG_MAP) je identifikován 0. Mapování alternativních zprávy je identifikován *msgMapID*.

Zprávy maps se používají ke zpracování zprávy odeslané do okna. Například [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vám umožní určit identifikátor mapy zpráv v nadřazeného objektu. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) pak používá tuto mapu zpráv ke směrování zpráv obsaženého okna odpovídající obslužné rutiny nebo jiné mapování zprávy. Seznam maker, které deklarace funkcí obslužných rutin najdete v tématu [BEGIN_MSG_MAP](#begin_msg_map).

Vždy začínají s BEGIN_MSG_MAP mapy zpráv. Potom můžete deklarovat následující alternativní zprávy maps.

[END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Všimněte si, že vždy přesně jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje výchozí zprávu mapování a mapování jeden alternativní zprávy, každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Další příklad ukazuje dva alternativní zprávy maps. Výchozí mapování zpráv je prázdný.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="begin_msg_map"></a>  BEGIN_MSG_MAP

Označuje začátek toho výchozí mapování zprávy.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[in] Název třídy obsahující mapování zprávy.

### <a name="remarks"></a>Poznámky

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) používá výchozí mapování zpráv pro zpracování zprávy odeslané do okna. Mapy zpráv směruje zprávy odpovídající obslužné rutiny nebo jiné mapování zprávy.

Následující makra mapování na obslužnou rutinu zprávy. Tato funkce musí být definován v *theClass*.

|– Makro|Popis|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mapuje na funkci obslužné rutiny zpráv Windows.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mapování zpráv Windows souvislý rozsah funkce obslužné rutiny.|
|[COMMAND_HANDLER](#command_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru.|
|[COMMAND_CODE_HANDLER](#command_handler)|Wm_command – zprávy se mapuje na obslužnou rutinu, na základě kódu oznámení.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mapuje souvislý rozsah z wm_command – zprávy pro obslužnou rutinu, na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru.|
|[NOTIFY_HANDLER](#notify_handler)|Wm_notify – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a identifikátor ovládacího prvku.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Wm_notify – zprávy se mapuje na obslužnou rutinu, na základě identifikátoru ovládacího prvku.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mapuje na obslužnou rutinu, na základě kódu oznámení wm_notify – zprávy.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mapuje souvislý rozsah WM_NOTIFY zprávy na obslužnou rutinu, na základě identifikátoru ovládacího prvku.|

Následující makra směrování zpráv do jiné mapování zprávy. Tento proces se nazývá "řetězení."

|– Makro|Popis|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Je zřetězen do výchozího mapování zpráv v základní třídě.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Je zřetězen do výchozího mapování zprávu v datovém členu třídy.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Je zřetězen do mapování alternativních zprávy v základní třídě.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Je zřetězen do mapování alternativních zprávu v datovém členu třídy.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Je zřetězen do výchozího mapování zpráv v jiné třídě v době běhu.|

Následující makra směrování zpráv "projeví" z nadřazeného okna. Například ovládací prvek obvykle odesílá zprávy s oznámením nezašle nadřazenému oknu pro zpracování, ale nadřazeného okna můžete sledovat, zprávy zpět do ovládacího prvku.

|– Makro|Popis|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mapuje zrcadlené zprávy wm_command – obslužná rutina funkce, na základě kód upozornění a identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mapuje zrcadlené zprávy wm_command – obslužná rutina funkce, na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mapuje zrcadlené zprávy wm_command – obslužná rutina funkce, na základě kódu oznámení.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mapuje zrcadlené wm_command – zprávy pro obslužnou rutinu pro souvislý rozsah identifikátorů ovládacího prvku.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Zrcadlené wm_command – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a souvislý rozsah identifikátory ovládacího prvku.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mapuje zrcadlené wm_notify – zprávy pro obslužnou rutinu, na základě kód upozornění a identifikátor ovládacího prvku.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Zrcadlené wm_notify – zprávy se mapuje na obslužnou rutinu, na základě identifikátoru ovládacího prvku.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mapuje zrcadlené wm_notify – zprávy pro obslužnou rutinu, na základě kódu oznámení.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mapuje zrcadlené wm_notify – zprávy pro obslužnou rutinu pro souvislý rozsah identifikátorů ovládacího prvku.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Zrcadlené wm_notify – zprávy se mapuje na obslužnou rutinu, na základě kód upozornění a souvislý rozsah identifikátory ovládacího prvku.|

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Když `CMyExtWindow` objekt přijme zprávu WM_PAINT, zpráva se přesměruje do `CMyExtWindow::OnPaint` pro vlastní zpracování. Pokud `OnPaint` označuje zprávy vyžaduje další zpracování, zpráva se pak přesměrováni na výchozí mapování zpráv v `CMyBaseWindow`.

Kromě výchozí mapování zpráv, můžete definovat mapování alternativních zprávu s [ALT_MSG_MAP](#alt_msg_map). Vždy začínají s BEGIN_MSG_MAP mapy zpráv. Potom můžete deklarovat následující alternativní zprávy maps. Následující příklad ukazuje výchozí zprávu mapování a mapování jeden alternativní zprávy, každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Další příklad ukazuje dva alternativní zprávy maps. Výchozí mapování zpráv je prázdný.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Všimněte si, že vždy přesně jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="chain_msg_map_alt"></a>  CHAIN_MSG_MAP_ALT

Definuje položku v mapování zprávy.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
[in] Název základní třídy, který obsahuje mapování zprávy.

*msgMapID*<br/>
[in] Identifikátor mapování zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_ALT směruje zprávy na mapování alternativních zprávy v základní třídě. Jste vyjádřili tuto mapu alternativní zprávu s [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Ke směrování zpráv do mapy zpráv výchozí základní třídu (deklarované pomocí [BEGIN_MSG_MAP](#begin_msg_map)), použijte CHAIN_MSG_MAP. Příklad najdete v tématu [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
>  Vždy začínají s BEGIN_MSG_MAP mapy zpráv. Pak může deklarovat mapy následující alternativní zpráv s ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

Definuje položku v mapování zprávy.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
[in] Název datového člena, který obsahuje mapování zprávy.

*msgMapID*<br/>
[in] Identifikátor mapování zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_ALT_MEMBER směruje zprávy na mapování alternativních zprávu v datovém členu. Jste vyjádřili tuto mapu alternativní zprávu s [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Ke směrování zpráv do mapy zpráv výchozí datový člen (deklarované pomocí [BEGIN_MSG_MAP](#begin_msg_map)), použijte CHAIN_MSG_MAP_MEMBER. Příklad najdete v tématu [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
>  Vždy začínají s BEGIN_MSG_MAP mapy zpráv. Pak může deklarovat mapy následující alternativní zpráv s ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="chain_msg_map"></a>  CHAIN_MSG_MAP

Definuje položku v mapování zprávy.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Parametry

*theChainClass*<br/>
[in] Název základní třídy, který obsahuje mapování zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP směruje zprávy do mapy zpráv výchozí základní třídu (deklarované pomocí [BEGIN_MSG_MAP](#begin_msg_map)). Ke směrování zpráv do mapování alternativních zprávy základní třídu (deklarované pomocí [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
>  Vždy začínají s BEGIN_MSG_MAP mapy zpráv. Pak může deklarovat mapy následující alternativní zpráv s ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Tento příklad znázorňuje následující:

- Pokud používáte proceduru okna `CMyClass`pro výchozí mapování zpráv a `OnPaint` nemá popisovač zpráva, zpráva se přesměruje do `CMyBaseClass`pro výchozí mapování zpráv pro zpracování.

- Pokud první mapování alternativních zprávy v používá proceduru okna `CMyClass`, všechny zprávy jsou směrované na `CMyBaseClass`pro výchozí mapování zprávy.

- Pokud používáte proceduru okna `CMyClass`uživatele mapovat druhé alternativní zprávy a `OnChar` nemá popisovač zprávu, zpráva se přesměruje do mapy zadaná alternativní zpráva v `CMyBaseClass`. `CMyBaseClass` vyjádřili tuto mapu zpráv s ALT_MSG_MAP(1).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

Definuje položku v mapování zprávy.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Parametry

*dynaChainID*<br/>
[in] Jedinečný identifikátor objektu mapování zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_DYNAMIC směruje zprávy, v době běhu k výchozí mapování zpráv v jiném objektu. Objekt a jeho mapu zpráv jsou přidružené k *dynaChainID*, které jste definovali [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Musíte odvodit třídu z `CDynamicChain` Chcete-li použít CHAIN_MSG_MAP_DYNAMIC. Příklad najdete v tématu [cdynamicchain –](../../atl/reference/cdynamicchain-class.md) Přehled.

> [!NOTE]
>  Vždy začínají mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Pak může deklarovat mapy následující alternativní zpráv s ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

Definuje položku v mapování zprávy.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Parametry

*theChainMember*<br/>
[in] Název datového člena, který obsahuje mapování zprávy.

### <a name="remarks"></a>Poznámky

CHAIN_MSG_MAP_MEMBER směruje zprávy do mapy zpráv výchozí datový člen (deklarované pomocí [BEGIN_MSG_MAP](#begin_msg_map)). Ke směrování zpráv do mapy zpráv alternativní datový člen (deklarované pomocí [ALT_MSG_MAP](#alt_msg_map)), použijte [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
>  Vždy začínají s BEGIN_MSG_MAP mapy zpráv. Pak může deklarovat mapy následující alternativní zpráv s ALT_MSG_MAP. [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Tento příklad znázorňuje následující:

- Pokud používáte proceduru okna `CMyClass`pro výchozí mapování zpráv a `OnPaint` nemá popisovač zpráva, zpráva se přesměruje do `m_obj`pro výchozí mapování zpráv pro zpracování.

- Pokud první mapování alternativních zprávy v používá proceduru okna `CMyClass`, všechny zprávy jsou směrované na `m_obj`pro výchozí mapování zprávy.

- Pokud používáte proceduru okna `CMyClass`uživatele mapovat druhé alternativní zprávy a `OnChar` nemá popisovač zpráva, zpráva se přesměruje do zadané alternativní zprávy mapu `m_obj`. Třída `CMyContainedClass` vyjádřili tuto mapu zpráv s ALT_MSG_MAP(1).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [wm_command –](/windows/desktop/menurc/wm-command) zprávy pouze na základě oznámení kódu.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Parametry

*kód*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="command_handler"></a>  COMMAND_HANDLER

Definuje položku v mapování zprávy.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*kód*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

Mapuje COMMAND_HANDLER [wm_command –](/windows/desktop/menurc/wm-command) zpráva zadaná obslužná rutina funkce, na základě kód upozornění a identifikátor ovládacího prvku. Příklad:

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Všechny funkce uvedené v makru COMMAND_HANDLER musí být definován následujícím způsobem:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Mapování sady zpráv `bHandled` na hodnotu TRUE před `CommandHandler` je volána. Pokud `CommandHandler` plně nezpracovává zprávy, měli nastavit `bHandled` na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.

> [!NOTE]
>  Vždy začínají mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Pak může deklarovat mapy následující alternativní zpráv s [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě COMMAND_HANDLER, můžete použít [MESSAGE_HANDLER](#message_handler) mapovat wm_command – zprávy bez ohledu na identifikátor nebo kódu. V takovém případě `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` bude směrovat všechny wm_command – zprávy pro `OnHandlerFunction`.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [wm_command –](/windows/desktop/menurc/wm-command) zprávy pouze na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru odeslání zprávy.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje [wm_command –](/windows/desktop/menurc/wm-command) zprávy s kódem konkrétní oznámení z celou řadu ovládacích prvků na funkci jedna obslužná rutina.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*kód*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru odeslání zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje [wm_command –](/windows/desktop/menurc/wm-command) zprávy z celou řadu ovládacích prvků na funkci jedna obslužná rutina.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je na základě identifikátoru položku nabídky, ovládací prvek nebo akcelerátoru odeslání zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="declare_empty_msg_map"></a>  DECLARE_EMPTY_MSG_MAP

Deklaruje mapu prázdnou zprávu.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Poznámky

DECLARE_EMPTY_MSG_MAP je makro pohodlí, které volá makra [BEGIN_MSG_MAP](#begin_msg_map) a [END_MSG_MAP](#end_msg_map) vytvořit mapu prázdná zpráva:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>  DEFAULT_REFLECTION_HANDLER

Poskytuje výchozí obslužnou rutinu pro podřízené okno (ovládací prvek), která bude dostávat reflektovaných zpráv; Obslužná rutina předá správně nezpracované zprávy `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="end_msg_map"></a>  END_MSG_MAP

Označuje konec mapy zpráv.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Poznámky

Vždy používat [BEGIN_MSG_MAP](#begin_msg_map) – makro k označení začátku mapy zpráv. Použití [ALT_MSG_MAP](#alt_msg_map) deklarovat následující alternativní zprávy maps.

Všimněte si, že vždy přesně jedna instance BEGIN_MSG_MAP a END_MSG_MAP.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje výchozí zprávu mapování a mapování jeden alternativní zprávy, každá obsahuje jednu funkci obslužné rutiny:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

Další příklad ukazuje dva alternativní zprávy maps. Výchozí mapování zpráv je prázdný.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="forward_notifications"></a>  FORWARD_NOTIFICATIONS

Přeposílá zprávy upozornění do nadřazeného okna.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Poznámky

Zadejte toto makro jako součást mapy zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

Definuje položku v mapování zprávy.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Parametry

*zpráva*<br/>
[in] Zprávy Windows.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

MESSAGE_HANDLER mapuje zadané obslužné rutiny zpráv Windows.

Všechny funkce uvedené v makru MESSAGE_HANDLER musí být definován následujícím způsobem:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Mapování sady zpráv `bHandled` na hodnotu TRUE před `MessageHandler` je volána. Pokud `MessageHandler` plně nezpracovává zprávy, měli nastavit `bHandled` na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.

> [!NOTE]
>  Vždy začínají mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Pak může deklarovat mapy následující alternativní zpráv s [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě MESSAGE_HANDLER, můžete použít [COMMAND_HANDLER](#command_handler) a [NOTIFY_HANDLER](#notify_handler) mapovat [wm_command –](/windows/desktop/menurc/wm-command) a [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy , v uvedeném pořadí.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

Podobně jako [MESSAGE_HANDLER](#message_handler), ale mapování funkce jedna obslužná rutina zprávy rozsah Windows.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Parametry

*msgFirst*<br/>
[in] Označuje začátek toho souvislý rozsah zprávy.

*msgLast*<br/>
[in] Označuje konec souvislý rozsah zprávy.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy pouze na základě oznámení kódu.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Parametry

*CD*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="notify_handler"></a>  NOTIFY_HANDLER

Definuje položku v mapování zprávy.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor ovládacího prvku odeslání zprávy.

*CD*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

Mapuje NOTIFY_HANDLER [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) zpráva zadaná obslužná rutina funkce, na základě kód upozornění a identifikátor ovládacího prvku.

Všechny funkce uvedené v makru NOTIFY_HANDLER musí být definován následujícím způsobem:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Mapování sady zpráv `bHandled` na hodnotu TRUE před `NotifyHandler` je volána. Pokud `NotifyHandler` plně nezpracovává zprávy, měli nastavit `bHandled` na hodnotu FALSE pro označení je zprávu zapotřebí další zpracování.

> [!NOTE]
>  Vždy začínají mapy zpráv s [BEGIN_MSG_MAP](#begin_msg_map). Pak může deklarovat mapy následující alternativní zpráv s [ALT_MSG_MAP](#alt_msg_map). [END_MSG_MAP](#end_msg_map) – makro označuje konec mapování zprávy. Mapování každé zprávy musí mít přesně jednu instanci BEGIN_MSG_MAP a END_MSG_MAP.

Kromě NOTIFY_HANDLER, můžete použít [MESSAGE_HANDLER](#message_handler) mapovat wm_notify – zprávy bez ohledu na identifikátor nebo kódu. V takovém případě `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` bude směrovat všechny wm_notify – zprávy pro `OnHandlerFunction`.

Další informace o používání mapy zpráv v ATL naleznete v tématu [mapy zpráv](../../atl/message-maps-atl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [wm_notify –](https://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy podle pouze identifikátor ovládacího prvku.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor ovládacího prvku odeslání zprávy.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy s kódem konkrétní oznámení z celou řadu ovládacích prvků na funkci jedna obslužná rutina.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*CD*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je na základě identifikátoru odesílání zprávy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) zprávy z celou řadu ovládacích prvků na funkci jedna obslužná rutina.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="remarks"></a>Poznámky

Tento rozsah je na základě identifikátoru odesílání zprávy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflect_notifications"></a>  REFLECT_NOTIFICATIONS

Odráží zpráv s oznámením zpět na podřízené okno (ovládací prvek), který jim poslali.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Poznámky

Zadejte toto makro jako součást mapování nadřazené okno zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

Podobně jako [COMMAND_CODE_HANDLER](#command_code_handler), ale mapuje příkazy projeví z nadřazeného okna.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Parametry

*kód*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

Podobně jako [COMMAND_HANDLER](#command_handler), ale mapuje příkazy projeví z nadřazeného okna.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*kód*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

Podobně jako [COMMAND_ID_HANDLER](#command_id_handler), ale mapuje příkazy projeví z nadřazeného okna.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

Podobně jako [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), ale mapuje příkazy projeví z nadřazeného okna.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*kód*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

Podobně jako [COMMAND_RANGE_HANDLER](#command_range_handler), ale mapuje příkazy projeví z nadřazeného okna.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

Podobně jako [NOTIFY_CODE_HANDLER](#notify_code_handler), ale mapuje oznámení projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Parametry

*CD*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_notify_handler"></a>  REFLECTED_NOTIFY_HANDLER

Podobně jako [NOTIFY_HANDLER](#notify_handler), ale mapuje oznámení projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*CD*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

Podobně jako [NOTIFY_ID_HANDLER](#notify_id_handler), ale mapuje oznámení projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identifikátor položky nabídky, ovládací prvek nebo akcelerátoru.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Podobně jako [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), ale mapuje oznámení projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*CD*<br/>
[in] Kód upozornění.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

Podobně jako [NOTIFY_RANGE_HANDLER](#notify_range_handler), ale mapuje oznámení projeví z nadřazeného okna.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Parametry

*idFirst*<br/>
[in] Označuje začátek toho souvislý rozsah identifikátory ovládacího prvku.

*idLast*<br/>
[in] Označuje konec souvislý rozsah identifikátory ovládacího prvku.

*Func*<br/>
[in] Název funkce obslužná rutina zprávy.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
