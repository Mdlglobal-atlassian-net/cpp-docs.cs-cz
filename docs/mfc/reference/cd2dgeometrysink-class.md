---
title: Třída CD2DGeometrySink
ms.date: 11/04/2016
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
ms.openlocfilehash: cb51c7b11f75debece61105bf20a201b6eab80a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369243"
---
# <a name="cd2dgeometrysink-class"></a>Třída CD2DGeometrySink

Obálka pro ID2D1GeometrySink.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometrySink;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Vytvoří objekt CD2DGeometrySink z objektu CD2DPathGeometry.|
|[CD2DGeometrySink::~CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destruktor. Nazývá se při zničení objektu jímky geometrie D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Přidá do geometrie cesty jeden oblouk.|
|[CD2DGeometrySink::AddBezier](#addbezier)|Vytvoří kubickou Bezierovu křivku mezi aktuálním a zadaným koncovým bodem.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Vytvoří posloupnost kubických Bezierových křivek a přidá je do jímky geometrie.|
|[CD2DGeometrySink::AddLine](#addline)|Vytvoří segment čáry mezi aktuálním a zadaným koncovým bodem a přidá ho do jímky geometrie.|
|[CD2DGeometrySink::AddLines](#addlines)|Vytvoří posloupnost čar pomocí určených bodů a přidá je do jímky geometrie.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Vytvoří kvadratickou Bezierovu křivku mezi aktuálním a zadaným koncovým bodem.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Přidá posloupnost kvadratické Segmenty Bezier jako pole v jednom volání.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Spustí nový obrázek v zadaném bodě.|
|[CD2DGeometrySink::Zavřít](#close)|Zavře jímka geometrie.|
|[CD2DGeometrySink::EndFigure](#endfigure)|Ukončí aktuální obrázek; volitelně jej zavře.|
|[CD2DGeometrySink::Získat](#get)|Vrátí rozhraní ID2D1GeometrySink.|
|[CD2DGeometrySink::IsValid](#isvalid)|Zkontroluje platnost jímky geometrie.|
|[CD2DGeometrySink::Režim SetFillMode](#setfillmode)|Určuje metodu použitou k určení bodů, které jsou uvnitř geometrie popsané tímto jímkou geometrie a které body jsou mimo.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Určuje volby tahu a spojení, které mají být použity na nové segmenty přidané do jímky geometrie.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometrySink::operátor ID2D1GeometrySink*](#operator_id2d1geometrysink_star)|Vrátí rozhraní ID2D1GeometrySink.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Ukazatel na ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CD2DGeometrySink`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink::~CD2DGeometrySink

Destruktor. Nazývá se při zničení objektu jímky geometrie D2D.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2DGeometrySink::AddArc

Přidá do geometrie cesty jeden oblouk.

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parametry

*Oblouk*<br/>
Segment oblouku, který chcete přidat k pojivu

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2DGeometrySink::AddBezier

Vytvoří kubickou Bezierovu křivku mezi aktuálním a zadaným koncovým bodem.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Bezierovy*<br/>
Struktura, která popisuje řídicí body a koncový bod Bezierovy křivky, kterou chcete přidat.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2DGeometrySink::AddBeziers

Vytvoří posloupnost kubických Bezierových křivek a přidá je do jímky geometrie.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Beziers*<br/>
Pole Bezierových segmentů, které popisuje Bezierovy křivky, které chcete vytvořit. Křivka je nakreslena z aktuálního bodu dřezu geometrie (koncový bod posledního nakresleného segmentu nebo umístění určeného beginfigure) do koncového bodu prvního Bezierova segmentu v poli. pokud pole obsahuje další Bezierovy segmenty, každý následující Bezierův segment použije koncový bod předchozího Bezierova segmentu jako počáteční bod.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2DGeometrySink::AddLine

Vytvoří segment čáry mezi aktuálním a zadaným koncovým bodem a přidá ho do jímky geometrie.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Koncový bod čáry k nakreslení.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2DGeometrySink::AddLines

Vytvoří posloupnost čar pomocí určených bodů a přidá je do jímky geometrie.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parametry

*Body*<br/>
Pole jednoho nebo více bodů, které popisují čáry kreslit. Čára je nakreslena z aktuálního bodu jímky geometrie (koncový bod posledního nakresleného segmentu nebo umístění určeného beginfigure) k prvnímu bodu v poli. Pokud pole obsahuje další body, čára je nakreslena z prvního bodu do druhého bodu v poli, z druhého bodu do třetího bodu a tak dále. Pole posloupnosti koncových bodů čar, které chcete nakreslit.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier

Vytvoří kvadratickou Bezierovu křivku mezi aktuálním a zadaným koncovým bodem.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parametry

*Bezierovy*<br/>
Struktura, která popisuje řídicí bod a koncový bod kvadratické Bezierovy křivky, kterou chcete přidat.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers

Přidá posloupnost kvadratické Segmenty Bezier jako pole v jednom volání.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parametry

*Beziers*<br/>
Pole posloupnosti kvadratické Bezierovy segmenty.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2DGeometrySink::BeginFigure

Spustí nový obrázek v zadaném bodě.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parametry

*startpoint*<br/>
Bod, ve kterém začít novou postavu.

*obrázekZačít*<br/>
Zda má být nová postava dutá nebo vyplněná.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink

Vytvoří objekt CD2DGeometrySink z objektu CD2DPathGeometry.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parametry

*Pathgeometry*<br/>
Existující objekt CD2DPathGeometry.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2DGeometrySink::Zavřít

Zavře jímka geometrie.

```
BOOL Close();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak FALSE.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2DGeometrySink::EndFigure

Ukončí aktuální obrázek; volitelně jej zavře.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parametry

*figureEnd*<br/>
Hodnota, která označuje, zda je aktuální údaj uzavřen. Pokud je obrázek uzavřen, je nakreslena čára mezi aktuálním bodem a počátečním bodem určeným beginfigure.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2DGeometrySink::Získat

Vrátí rozhraní ID2D1GeometrySink.

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1GeometrySink nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2DGeometrySink::IsValid

Zkontroluje platnost jímky geometrie.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je jímka geometrie platná; jinak FALSE.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2DGeometrySink::m_pSink

Ukazatel na ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operátor ID2D1GeometrySink*

Vrátí rozhraní ID2D1GeometrySink.

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1GeometrySink nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2DGeometrySink::Režim SetFillMode

Určuje metodu použitou k určení bodů, které jsou uvnitř geometrie popsané tímto jímkou geometrie a které body jsou mimo.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parametry

*fillMode*<br/>
Metoda použitá k určení, zda je daný bod součástí geometrie.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags

Určuje volby tahu a spojení, které mají být použity na nové segmenty přidané do jímky geometrie.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parametry

*vertexFlags*<br/>
Volby tahu a spojení, které mají být použity na nové segmenty přidané do jímky geometrie.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
