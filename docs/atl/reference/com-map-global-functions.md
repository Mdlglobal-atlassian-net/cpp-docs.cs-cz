---
title: Globální funkce mapy modelu COM. | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9185a71cc77cadb1ad7cdf577654730819147d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113133"
---
# <a name="com-map-global-functions"></a>Globální funkce mapy modelu COM.

Tyto funkce poskytuje podporu pro mapy modelu COM. `IUnknown` implementace.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje se do `IUnknown` neagregovaná objektu.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje kód efektivní pro porovnání rozhraní proti `IUnknown`.|  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface

Načte ukazatel na požadované rozhraní.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pThis*<br/>
[in] Ukazatel na objekt, který obsahuje mapování modelu COM rozhraní vystavena `QueryInterface`.

*pEntries*<br/>
[in] Pole `_ATL_INTMAP_ENTRY` struktury, které přistupují k mapě dostupné rozhraní.

*identifikátor IID*<br/>
[in] Identifikátor GUID se požadované rozhraní.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní zadané v *iid*, nebo hodnota NULL, pokud se nenajde rozhraní.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

`AtlInternalQueryInterface` zpracovává pouze v tabulce mapy modelu COM rozhraní. Pokud objekt je agregován, `AtlInternalQueryInterface` není delegovat na vnější neznámá. Rozhraní můžete zadat do tabulky mapování modelu COM s makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) nebo jeden z jeho variant.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown

Tato funkce se volá pro speciální případ testování hodnoty `IUnknown`.

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parametry

*rguid1*<br/>
[in] Identifikátor GUID, který má být porovnán s `IID_IUnknown`.

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)<br/>
[Makra map COM](../../atl/reference/com-map-macros.md)
