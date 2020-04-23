---
title: Třída CD2DBrushProperties
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: 2db720fd09c62f8b86baecea9229d946f3892333
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754181"
---
# <a name="cd2dbrushproperties-class"></a>Třída CD2DBrushProperties

Obálka pro `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[VLASTNOSTI CD2DBrushProperties::VLASTNOSTI CD2DBrushProperties](#cd2dbrushproperties)|Přetíženo. Vytvoří `CD2D_BRUSH_PROPERTIES` strukturu|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicializuje objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>VLASTNOSTI CD2DBrushProperties::VLASTNOSTI CD2DBrushProperties

Vytvoří CD2D_BRUSH_PROPERTIES strukturu

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>Parametry

*_opacity*<br/>
Základní krytí stopy. Výchozí hodnota je 1,0.

*_transform*<br/>
Transformace, která se má aplikovat na stopu

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrushProperties::CommonInit

Inicializuje objekt.

```cpp
void CommonInit();
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
