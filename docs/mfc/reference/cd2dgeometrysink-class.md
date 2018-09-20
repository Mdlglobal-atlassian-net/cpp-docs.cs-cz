---
title: Cd2dgeometrysink – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b97bccbf9615c90292976839f841e4b2ffe6af9d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383804"
---
# <a name="cd2dgeometrysink-class"></a>Cd2dgeometrysink – třída

Obálka pro ID2D1GeometrySink.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometrySink;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Vytvoří objekt cd2dgeometrysink – z cd2dpathgeometry – objektu.|
|[Cd2dgeometrysink –:: ~ cd2dgeometrysink –](#_dtorcd2dgeometrysink)|Destruktor. Volá se, když se likviduje objektu D2D geometrie jímky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Přidá jeden oblouk geometrické cesty|
|[CD2DGeometrySink::AddBezier](#addbezier)|Vytvoří kubické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Vytvoří posloupnost kubické Bézierovy křivky a přidá je do jímky geometry.|
|[CD2DGeometrySink::AddLine](#addline)|Vytvoří úsek čáry mezi aktuálním bodem a zadaným koncový bod a přidá jej do jímky geometry.|
|[CD2DGeometrySink::AddLines](#addlines)|Vytvoří posloupnost řádky pomocí zadané body a přidá je do jímky geometry.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Vytvoří kvadratické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Přidá pořadí kvadratické Bézierovy křivky segmentů jako pole v jednom volání.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Spustí nový obrázek na zadaný bod.|
|[CD2DGeometrySink::Close](#close)|Zavře jímky geometrie|
|[CD2DGeometrySink::EndFigure](#endfigure)|Ukončí aktuální obrázek; Volitelně můžete zavře.|
|[CD2DGeometrySink::Get](#get)|Vrátí ID2D1GeometrySink rozhraní|
|[CD2DGeometrySink::IsValid](#isvalid)|Zkontroluje platnost jímky geometrie|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Určuje metodu sloužící k určení, které body jsou uvnitř geometrie popsal tuto jímku geometrie a které jsou body mimo.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Určuje možnosti stroke a zapojte se má použít u nových segmentů přidán do jímky geometry.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DGeometrySink::Operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Vrátí ID2D1GeometrySink rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Ukazatel ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CD2DGeometrySink`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dgeometrysink"></a>  Cd2dgeometrysink –:: ~ cd2dgeometrysink –

Destruktor. Volá se, když se likviduje objektu D2D geometrie jímky.

```
virtual ~CD2DGeometrySink();
```

##  <a name="addarc"></a>  CD2DGeometrySink::AddArc

Přidá jeden oblouk geometrické cesty

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parametry

*Oblouk*<br/>
Segment oblouk přidat obrázek

##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier

Vytvoří kubické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Bézierovy křivky*<br/>
Struktura, která popisuje kontrolních bodů a koncový bod Bézierovy křivky na Přidat.

##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers

Vytvoří posloupnost kubické Bézierovy křivky a přidá je do jímky geometry.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Bézierovy křivky*<br/>
Pole Bézierovy segmentů, které popisuje Bézierových křivek na vytvořit. Křivky pochází z aktuálního místa jímky Geometrie (koncový bod poslední segment vykreslit nebo umístění, které určuje BeginFigure) pro koncový bod první segment Bézierovy křivky v poli. Pokud pole obsahuje další segmenty Bézierovy, každý další segment Bézierovu používá koncový bod předchozího segmentu Bézierovu jako počáteční bod.

##  <a name="addline"></a>  CD2DGeometrySink::AddLine

Vytvoří úsek čáry mezi aktuálním bodem a zadaným koncový bod a přidá jej do jímky geometry.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Koncový bod čáry.

##  <a name="addlines"></a>  CD2DGeometrySink::AddLines

Vytvoří posloupnost řádky pomocí zadané body a přidá je do jímky geometry.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parametry

*body*<br/>
Pole jednoho nebo více bodů, které popisují řádky, které chcete kreslit. Linie vychází ze jímky geometrie aktuálního místa (koncový bod poslední segment vykreslit nebo umístění, které určuje BeginFigure) k první bod v poli. Pokud pole obsahuje další body, linie vychází z prvního bodu na druhý bod v poli, z druhé bodu třetí bodu, a tak dále. Pole sekvence koncové body čáry pro kreslení.

##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier

Vytvoří kvadratické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Bézierovy křivky*<br/>
Struktura, která popisuje řídicí bod a koncový bod kvadratické Bézierovy křivky na Přidat.

##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers

Přidá pořadí kvadratické Bézierovy křivky segmentů jako pole v jednom volání.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Bézierovy křivky*<br/>
Pole sekvence kvadratické Bézierovy křivky segmenty.

##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure

Spustí nový obrázek na zadaný bod.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parametry

*startPoint*<br/>
Bod, na kterém má být nový obrázek.

*figureBegin*<br/>
Určuje, zda nový obrázek musí být prázdný nebo vyplněné.

##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink

Vytvoří objekt cd2dgeometrysink – z cd2dpathgeometry – objektu.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parametry

*pathGeometry*<br/>
Existující objekt cd2dpathgeometry –.

##  <a name="close"></a>  CD2DGeometrySink::Close

Zavře jímky geometrie

```
BOOL Close();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. v opačném případě FALSE.

##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure

Ukončí aktuální obrázek; Volitelně můžete zavře.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parametry

*figureEnd*<br/>
Hodnota, která určuje, zda je aktuální figure uzavřený. Pokud na obrázku je zavřená, linie vychází mezi aktuálním bodem a počáteční bod určené BeginFigure.

##  <a name="get"></a>  CD2DGeometrySink::Get

Vrátí ID2D1GeometrySink rozhraní

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1GeometrySink nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid

Zkontroluje platnost jímky geometrie

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud geometrie jímkou je platná. v opačném případě FALSE.

##  <a name="m_psink"></a>  CD2DGeometrySink::m_pSink

Ukazatel ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

##  <a name="operator_id2d1geometrysink_star"></a>  CD2DGeometrySink::Operator ID2D1GeometrySink *

Vrátí ID2D1GeometrySink rozhraní

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1GeometrySink nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode

Určuje metodu sloužící k určení, které body jsou uvnitř geometrie popsal tuto jímku geometrie a které jsou body mimo.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parametry

*fillMode*<br/>
Metoda používá k určení, zda daný bod je součástí geometrii.

##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags

Určuje možnosti stroke a zapojte se má použít u nových segmentů přidán do jímky geometry.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parametry

*vertexFlags*<br/>
Možnosti stroke a zapojte se má použít u nových segmentů, které jsou přidány do jímky geometrie.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
