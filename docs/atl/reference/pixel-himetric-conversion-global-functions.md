---
title: Globální funkce pro převod pixelů na HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276832"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globální funkce pro převod pixelů/HIMETRIC

Tyto funkce poskytují podporu pro převod do a z pixelů a jednotkách HIMETRIC.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Převede jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) na pixelech.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Převede pixelů na jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

Převede velikost objektu v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) na velikost v pixelech na obrazovkovém zařízení.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parametry

*lpSizeInHiMetric*<br/>
[in] Ukazatel na velikost objektu v jednotkách HIMETRIC.

*lpSizeInPix*<br/>
[out] Ukazatel na kterém má být vrácena velikost objektu v pixelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

Převede velikost objektu v pixelech na obrazovkovém zařízení na velikost v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parametry

*lpSizeInPix*<br/>
[in] Ukazatel objekt velikost v pixelech.

*lpSizeInHiMetric*<br/>
[out] Ukazatel na to, kde je velikost objektu v jednotkách HIMETRIC má být vrácen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)
