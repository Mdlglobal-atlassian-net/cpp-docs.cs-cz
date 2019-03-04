---
title: Globální funkce mapy modelu COM.
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: 75d081674fa4b63e66f1296834d3de305665ab9a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271616"
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

*iid*<br/>
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

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)<br/>
[Makra map COM](../../atl/reference/com-map-macros.md)
