---
title: Globální funkce bodů připojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f68c22ff88ac92357dabfef8076c160271a76378
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756487"
---
# <a name="connection-point-global-functions"></a>Globální funkce bodů připojení

Tyto funkce poskytuje podporu pro spojovací body a jímky mapy.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.|
|[AtlUnadvise](#atlunadvise)|Ukončí připojení navázané prostřednictvím `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Vás informuje o tom nebo unadvises položky v mapě událostí jímky.|  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="atladvise"></a>  AtlAdvise

Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*  
[in] Ukazatel `IUnknown` objektu chce připojit pomocí klienta.

*pUnk*  
[in] Ukazatel na straně klienta `IUnknown`.

*identifikátor IID*  
[in] Identifikátor GUID je spojovací bod. Obvykle je to stejné jako odchozí rozhraní spravuje spojovací bod.

*pdw*  
[out] Ukazatel na soubor cookie, který jednoznačně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Jímka implementuje rozhraní odchozí podporovány bodem připojení. Klient použije *pdw* souboru cookie odebrat připojení tím, že ji předáte [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

Ukončí připojení navázané prostřednictvím [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*  
[in] Ukazatel `IUnknown` objektu, který je klient připojen s.

*identifikátor IID*  
[in] Identifikátor GUID je spojovací bod. Obvykle je to stejné jako odchozí rozhraní spravuje spojovací bod.

*datový sklad*  
[in] Soubor cookie, který jednoznačně identifikuje připojení.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

Voláním této funkce vytvoříte nebo zrušíte avízo o všech položkách v mapě událostí jímky objektu.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parametry

*PT*  
[in] Ukazatel na objekt obsahující mapování jímky.

*bAdvise*  
[in] Hodnota TRUE, pokud mají všechny položky jímky doporučujeme; FALSE, pokud mají být unadvised všechny položky jímky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)   
[Makra bodů připojení](../../atl/reference/connection-point-macros.md)
