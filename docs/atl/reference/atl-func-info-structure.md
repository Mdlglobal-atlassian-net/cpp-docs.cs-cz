---
title: _Atl_func_info – struktura
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: f6cf32bab86d741f3b0750c150c7bbc647b27ddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248690"
---
# <a name="atlfuncinfo-structure"></a>_Atl_func_info – struktura

Obsahuje informace o typu používané k popisu metody nebo vlastnosti na dispinterface.

## <a name="syntax"></a>Syntaxe

```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>Členové

`cc`<br/>
Konvence volání. Při použití této struktury s [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md) třídy, musí být tento člen CC_STDCALL. `CC_CDECL` je jedinou možností, které jsou podporovány v aplikaci pro Windows CE `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Jakákoli jiná hodnota není podporován tedy nedefinované chování.

`vtReturn`<br/>
Typ varianty funkce vrátí hodnotu.

`nParams`<br/>
Počet parametrů funkce.

`pVarTypes`<br/>
Pole variantních typů parametrů funkce.

## <a name="remarks"></a>Poznámky

ATL interně, používá tato struktura pro uložení informace získané z knihovny typů. Možná budete muset tato struktura manipulovat přímo, pokud zadáte informace o typu pro obslužnou rutinu události, které jsou součástí [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md) třídy a [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) – makro.

## <a name="example"></a>Příklad

Zadaný metodu odesílajícího rozhraní definované v IDL:

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

můžete nadefinovat `_ATL_FUNC_INFO` struktury:

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>Požadavky

Záhlaví: atlcom

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
