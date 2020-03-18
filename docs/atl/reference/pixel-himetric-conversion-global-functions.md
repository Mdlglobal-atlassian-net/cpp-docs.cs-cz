---
title: Globální funkce převodu pixelů – HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417570"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globální funkce převodu pixel/HIMETRIC

Tyto funkce poskytují podporu pro převod na a z pixelů a HIMETRIC jednotek.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Převede jednotky HIMETRIC (každá jednotka je 0,01 mm) na pixely.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Převede pixely na jednotky HIMETRIC (každá jednotka je 0,01 mm).|

##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Převede velikost objektu v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) na velikost v pixelech na obrazovkovém zařízení.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parametry

*lpSizeInHiMetric*<br/>
pro Ukazatel na velikost objektu v jednotkách HIMETRIC

*lpSizeInPix*<br/>
mimo Ukazatel na místo, kde má být vrácena velikost objektu v pixelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Převede velikost objektu v pixelech na obrazovkovém zařízení na velikost v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parametry

*lpSizeInPix*<br/>
pro Ukazatel na velikost objektu v pixelech.

*lpSizeInHiMetric*<br/>
mimo Ukazatel na místo, kde má být vrácena velikost objektu v jednotkách HIMETRIC

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
