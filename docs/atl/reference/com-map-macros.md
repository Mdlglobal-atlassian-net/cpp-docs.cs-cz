---
title: Makra COM Map | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 057652eaf1f188cfd61dcfa4a0d433a43ef8c56c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068889"
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
