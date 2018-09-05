---
title: Globální funkce pro převod pixelů na HIMETRIC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 086310efe565e060645320db30526b03d57a68af
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752407"
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

*lpSizeInHiMetric*  
[in] Ukazatel na velikost objektu v jednotkách HIMETRIC.

*lpSizeInPix*  
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

*lpSizeInPix*  
[in] Ukazatel objekt velikost v pixelech.

*lpSizeInHiMetric*  
[out] Ukazatel na to, kde je velikost objektu v jednotkách HIMETRIC má být vrácen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h  

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)
