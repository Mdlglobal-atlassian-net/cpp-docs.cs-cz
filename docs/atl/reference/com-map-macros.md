---
title: Makra mapy COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326606"
---
# <a name="com-map-macros"></a>Makra mapy COM

Tato makra definují mapy rozhraní COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Označuje začátek položek mapy rozhraní COM.|
|[END_COM_MAP](#end_com_map)|Označuje konec položek mapy rozhraní COM.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

Mapa COM je mechanismus, který zpřístupňuje rozhraní `QueryInterface`na objekt u klienta prostřednictvím .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název objektu třídy, na který vystavujete rozhraní.

### <a name="remarks"></a>Poznámky

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) vrací pouze ukazatele pro rozhraní v mapě COM. Spusťte mapu rozhraní s BEGIN_COM_MAP makra, přidejte položky pro každé z vašich rozhraní s [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) makra nebo některou z jeho variant a dokončete mapu [END_COM_MAP](#end_com_map) makry.

### <a name="example"></a>Příklad

Ze vzorku ATL [BEEPER:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

Ukončí definici mapy rozhraní COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globální funkce mapy COM](../../atl/reference/com-map-global-functions.md)
