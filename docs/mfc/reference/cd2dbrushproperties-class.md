---
title: Cd2dbrushproperties – třída
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
ms.openlocfilehash: 5ca791af658ee719b2e6d6ea78f82e23a66edc98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253722"
---
# <a name="cd2dbrushproperties-class"></a>Cd2dbrushproperties – třída

Obálka pro `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Syntaxe

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Přetíženo. Vytvoří `CD2D_BRUSH_PROPERTIES` struktura|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicializuje objekt|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2dbrushproperties"></a>  CD2DBrushProperties::CD2DBrushProperties

Vytvoří strukturu CD2D_BRUSH_PROPERTIES

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>Parametry

*_opacity*<br/>
Základní neprůhlednost štětce. Výchozí hodnota je 1.0.

*_transform*<br/>
Transformace vyrovnat štětec

##  <a name="commoninit"></a>  CD2DBrushProperties::CommonInit

Inicializuje objekt

```
void CommonInit();
```

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
