---
title: Globální funkce mapy COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326699"
---
# <a name="com-map-global-functions"></a>Globální funkce mapy COM

Tyto funkce poskytují podporu `IUnknown` pro implementace mapy COM.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Delegáti `IUnknown` neagregované objektu.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje efektivní kód pro porovnání `IUnknown`rozhraní proti .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface

Načte ukazatel na požadované rozhraní.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pToto*<br/>
[v] Ukazatel na objekt, který obsahuje mapu COM `QueryInterface`rozhraní vystavených .

*pPoložky*<br/>
[v] Pole `_ATL_INTMAP_ENTRY` struktur, které přístup k mapě dostupných rozhraní.

*Iid*<br/>
[v] Identifikátor GUID požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel na ukazatel rozhraní zadaný v *iid*nebo NULL, pokud rozhraní nebylo nalezeno.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

`AtlInternalQueryInterface`zpracovává pouze rozhraní v tabulce mapy COM. Pokud je objekt agregován, `AtlInternalQueryInterface` nedeleguje na vnější neznámé. Rozhraní můžete zadat do tabulky mapy COM pomocí [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) maker nebo jedné z jeho variant.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>InlineIsEqualIUnknown

Volání této funkce, pro zvláštní `IUnknown`případ testování pro .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parametry

*rguid1*<br/>
[v] Identifikátor GUID pro `IID_IUnknown`porovnání s .

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)<br/>
[Makra mapy COM](../../atl/reference/com-map-macros.md)
