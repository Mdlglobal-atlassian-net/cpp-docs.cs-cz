---
title: Makra map COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417850"
---
# <a name="com-map-macros"></a>Makra map COM

Tato makra definují mapy rozhraní modelu COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Označuje začátek položek mapování rozhraní modelu COM.|
|[END_COM_MAP](#end_com_map)|Označuje konec položek mapování rozhraní modelu COM.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="begin_com_map"></a>BEGIN_COM_MAP

Mapa modelu COM je mechanismus, který zpřístupňuje rozhraní objektu klientovi prostřednictvím `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název objektu třídy, na kterém zveřejňujete rozhraní.

### <a name="remarks"></a>Poznámky

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) vrátí ukazatele pro rozhraní v mapě com. Spusťte mapu rozhraní pomocí makra BEGIN_COM_MAP, přidejte položky pro každé z vašich rozhraní pomocí makra [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jednu z jeho variant a dokončete mapu pomocí makra [END_COM_MAP](#end_com_map) .

### <a name="example"></a>Příklad

Z ukázky pro [pípnutí](../../overview/visual-cpp-samples.md) v knihovně ATL:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>END_COM_MAP

Ukončí definici mapy rozhraní modelu COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)<br/>
[Globální funkce mapy modelu COM](../../atl/reference/com-map-global-functions.md)
