---
title: Makra spojovacího bodu
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331500"
---
# <a name="connection-point-macros"></a>Makra spojovacího bodu

Tato makra definují mapy spojovacích bodů a položky.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Označuje začátek položek mapy spojovacího bodu.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Zadá spojovací body do mapy.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobné CONNECTION_POINT_ENTRY ale má ukazatel na iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Označuje konec položek mapy spojovacího bodu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Označuje začátek položek mapy spojovacího bodu.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy obsahující spojovací body.

### <a name="remarks"></a>Poznámky

Začněte mapu připojovacích bodů pomocí BEGIN_CONNECTION_POINT_MAP makru, přidejte položky pro každý z připojovacích bodů pomocí [CONNECTION_POINT_ENTRY](#connection_point_entry) makru a dokončete mapu [END_CONNECTION_POINT_MAP](#end_connection_point_map) makra.

Další informace o přípojcích v atl naleznete v článku [Spojovací body](../../atl/atl-connection-points.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY a CONNECTION_POINT_ENTRY_P

Zadá spojovací bod pro zadané rozhraní do mapy spojovacího bodu, aby k němu bylo možné získat přístup.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID rozhraní přidaného do mapy spojovacího bodu.

*piid*<br/>
[v] Ukazatel na identifikátor GUID rozhraní, které je přidáváno.

### <a name="remarks"></a>Poznámky

Položky spojovacího bodu v mapě používá [iConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Třída obsahující mapu spojovacího bodu `IConnectionPointContainerImpl`musí dědit z .

Začněte mapu připojovacích bodů [pomocí BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makru, přidejte položky pro každý z připojovacích bodů pomocí CONNECTION_POINT_ENTRY makru a dokončete mapu [END_CONNECTION_POINT_MAP](#end_connection_point_map) makra.

Další informace o přípojcích v atl naleznete v článku [Spojovací body](../../atl/atl-connection-points.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Označuje konec položek mapy spojovacího bodu.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Poznámky

Začněte mapu spojovacího bodu pomocí [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makru, přidejte položky pro každý z připojovacích bodů pomocí [CONNECTION_POINT_ENTRY](#connection_point_entry) makru a dokončete mapu END_CONNECTION_POINT_MAP makra.

Další informace o přípojcích v atl naleznete v článku [Spojovací body](../../atl/atl-connection-points.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globální funkce spojovacího bodu](../../atl/reference/connection-point-global-functions.md)
