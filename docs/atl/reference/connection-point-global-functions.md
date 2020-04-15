---
title: Globální funkce spojovacího bodu
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331531"
---
# <a name="connection-point-global-functions"></a>Globální funkce spojovacího bodu

Tyto funkce poskytují podporu pro spojovací body a mapy jímky.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.|
|[AtlUnadvise](#atlunadvise)|Ukončí připojení navázáno prostřednictvím `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Radí nebo unadvises položky v mapě jímky událostí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>AtlAdvise

Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
[v] Ukazatel na `IUnknown` objekt, se kterým se chce klient připojit.

*Punk*<br/>
[v] Ukazatel na klienta `IUnknown`.

*Iid*<br/>
[v] Identifikátor GUID spojovacího bodu. Obvykle je to stejné jako odchozí rozhraní spravované bodem připojení.

*Pdw*<br/>
[out] Ukazatel na soubor cookie, který jednoznačně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Jímka implementuje odchozí rozhraní podporované bodem připojení. Klient používá *pdw* cookie k odstranění připojení předáním [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUnadvise

Ukončí připojení navázáno prostřednictvím [AtlAdvise](#atladvise).

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
[v] Ukazatel na `IUnknown` objekt, ke kterému je klient připojen.

*Iid*<br/>
[v] Identifikátor GUID spojovacího bodu. Obvykle je to stejné jako odchozí rozhraní spravované bodem připojení.

*Dw*<br/>
[v] Soubor cookie, který jednoznačně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Voláním této funkce vytvoříte nebo zrušíte avízo o všech položkách v mapě událostí jímky objektu.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[v] Ukazatel na objekt obsahující mapu jímky.

*bPoradit*<br/>
[v] PRAVDA, pokud mají být doporučeny všechny položky jímky; FALSE, pokud všechny položky jímky mají být nedoporučeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)<br/>
[Makra spojovacího bodu](../../atl/reference/connection-point-macros.md)
