---
title: Makra spojovacího bodu
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: cb8d6f696980ef91d7b43c960dc50289ea8500a6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417731"
---
# <a name="connection-point-macros"></a>Makra spojovacího bodu

Tato makra definují mapy a položky spojovacího bodu.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Označí začátek položek mapy bodu připojení.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Vloží body připojení do mapy.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobně jako CONNECTION_POINT_ENTRY, ale přebírá ukazatel na identifikátor IID.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Označuje konec položek mapy spojovacího bodu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Označí začátek položek mapy bodu připojení.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy, která obsahuje body připojení.

### <a name="remarks"></a>Poznámky

Spusťte mapu spojovacího bodu pomocí makra BEGIN_CONNECTION_POINT_MAP, přidejte položky pro každý z vašich bodů připojení pomocí makra [CONNECTION_POINT_ENTRY](#connection_point_entry) a dokončete mapu pomocí makra [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Další informace o bodech připojení v knihovně ATL naleznete v článku [body připojení](../../atl/atl-connection-points.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY a CONNECTION_POINT_ENTRY_P

Zadá bod připojení pro zadané rozhraní do mapy spojovacího bodu tak, aby byl k němu možné přihlédnout.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*identifikátor*<br/>
pro Identifikátor GUID přidávaného rozhraní do mapy spojovacího bodu.

*piid*<br/>
pro Ukazatel na identifikátor GUID rozhraní, které se ADDE.

### <a name="remarks"></a>Poznámky

Položky spojovacího bodu v mapě používá [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Třída obsahující mapu spojovacího bodu musí dědit z `IConnectionPointContainerImpl`.

Spusťte mapu spojovacího bodu pomocí makra [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , přidejte položky pro každý z vašich bodů připojení pomocí makra CONNECTION_POINT_ENTRY a dokončete mapu pomocí makra [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Další informace o bodech připojení v knihovně ATL naleznete v článku [body připojení](../../atl/atl-connection-points.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Označuje konec položek mapy spojovacího bodu.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Poznámky

Spusťte mapu spojovacího bodu pomocí makra [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , přidejte položky pro každý z vašich bodů připojení pomocí makra [CONNECTION_POINT_ENTRY](#connection_point_entry) a dokončete mapu pomocí makra END_CONNECTION_POINT_MAP.

Další informace o bodech připojení v knihovně ATL naleznete v článku [body připojení](../../atl/atl-connection-points.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)<br/>
[Globální funkce bodů připojení](../../atl/reference/connection-point-global-functions.md)
