---
title: Makra COM Map
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: e3358ff9f3f2aa5f3dde81c5eb218278178822ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563875"
---
# <a name="com-map-macros"></a>Makra COM Map

Tato makra definují mapy rozhraní modelu COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Označuje začátek položek mapování rozhraní modelu COM.|
|[END_COM_MAP](#end_com_map)|Označuje konec položky map rozhraní COM.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="begin_com_map"></a>  BEGIN_COM_MAP

Mapy modelu COM je mechanismus, který poskytuje rozhraní pro objekt do klienta prostřednictvím `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název objektu třídy, které jsou vystaveny rozhraní na.

### <a name="remarks"></a>Poznámky

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) pouze v objektu map COM vrací ukazatele pro rozhraní. Mapy rozhraní začínat – makro BEGIN_COM_MAP, přidejte položky pro každý z vašich rozhraní s [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) – makro nebo jeden z jeho variant a dokončete mapy s [END_COM_MAP](#end_com_map) makra.

### <a name="example"></a>Příklad

Z knihovny ATL [BEEPER](../../visual-cpp-samples.md) vzorku:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

Ukončí definici mapy rozhraní modelu COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globální funkce mapy modelu COM](../../atl/reference/com-map-global-functions.md)
