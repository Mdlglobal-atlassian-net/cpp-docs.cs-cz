---
title: Globální funkce bodu připojení
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 0313e93ee82bb96f3bfe08e45f70ccfee30dbee6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864396"
---
# <a name="connection-point-global-functions"></a>Globální funkce bodu připojení

Tyto funkce poskytují podporu pro body připojení a mapy jímky.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.|
|[AtlUnadvise](#atlunadvise)|Ukončí připojení navázané prostřednictvím `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Radí nebo nedoporučuje položky v mapě jímky událostí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="atladvise"></a>AtlAdvise

Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
pro Ukazatel na `IUnknown` objektu, se kterým chce klient připojit.

*pUnk*<br/>
pro Ukazatel na `IUnknown`klienta.

*identifikátor*<br/>
pro Identifikátor GUID bodu připojení Obvykle je to stejné jako odchozí rozhraní spravované bodem připojení.

*PDW*<br/>
mimo Ukazatel na soubor cookie, který jedinečně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Jímka implementuje odchozí rozhraní podporované bodem připojení. Klient pomocí souboru cookie *PDW* Odebere připojení jeho předáním do [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>AtlUnadvise

Ukončí připojení navázané pomocí [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
pro Ukazatel na `IUnknown` objektu, se kterým je klient připojen.

*identifikátor*<br/>
pro Identifikátor GUID bodu připojení Obvykle je to stejné jako odchozí rozhraní spravované bodem připojení.

*DW*<br/>
pro Soubor cookie, který jedinečně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Voláním této funkce vytvoříte nebo zrušíte avízo o všech položkách v mapě událostí jímky objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parametry

*Bodů*<br/>
pro Ukazatel na objekt obsahující mapu jímky.

*bAdvise*<br/>
pro TRUE, pokud se mají vyhodnotit všechny záznamy jímky; FALSE, pokud mají být všechny záznamy jímky nedoporučeníné.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)<br/>
[Makra bodů připojení](../../atl/reference/connection-point-macros.md)
