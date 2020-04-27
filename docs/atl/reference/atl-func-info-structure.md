---
title: Struktura _ATL_FUNC_INFO
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: b1c740cf1a1ed344dbceb028bd1f39a87fc09363
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168589"
---
# <a name="_atl_func_info-structure"></a>Struktura _ATL_FUNC_INFO

Obsahuje informace o typu používané k popisu metody nebo vlastnosti pro odesílající rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>Členové

`cc`<br/>
Konvence volání. Při použití této struktury s třídou [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) musí být tento člen CC_STDCALL. `CC_CDECL`je jediná možnost podporovaná v systém Windows CE pro `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Jakákoli jiná hodnota je Nepodporovaná, takže její chování není definované.

`vtReturn`<br/>
Typ variant návratové hodnoty funkce.

`nParams`<br/>
Počet parametrů funkce.

`pVarTypes`<br/>
Pole typů variant parametrů funkce.

## <a name="remarks"></a>Poznámky

Interně ATL používá tuto strukturu pro uchovávání informací získaných z knihovny typů. Je možné, že budete chtít manipulovat s touto strukturou přímo, pokud zadáte informace o typu pro obslužnou rutinu události, která se používá pro třídu [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) a makro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) .

## <a name="example"></a>Příklad

Předaná metoda odesílajícího rozhraní definovaná v IDL:

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

měli byste definovat `_ATL_FUNC_INFO` strukturu:

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>Požadavky

Záhlaví: atlcom. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
