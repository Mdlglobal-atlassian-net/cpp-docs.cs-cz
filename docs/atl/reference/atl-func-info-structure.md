---
title: _Atl_func_info – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 392e9dc2997dc7f4f0f36b1d7d38cd8ecdc691bb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759529"
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

`cc`  
Konvence volání. Při použití této struktury s [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md) třídy, musí být tento člen CC_STDCALL. `CC_CDECL` je jedinou možností, které jsou podporovány v aplikaci pro Windows CE `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Jakákoli jiná hodnota není podporován tedy nedefinované chování.

`vtReturn`  
Typ varianty funkce vrátí hodnotu.

`nParams`  
Počet parametrů funkce.

`pVarTypes`  
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

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)  
[Idispeventsimpleimpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)   
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)

