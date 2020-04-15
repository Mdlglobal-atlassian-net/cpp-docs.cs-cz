---
title: Třída CD2DGeometry
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 2631005fcedfb8d5db69667e22c375f585b4f044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369249"
---
# <a name="cd2dgeometry-class"></a>Třída CD2DGeometry

Obálka pro ID2D1Geometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Vytvoří objekt CD2DGeometry.|
|[CD2DGeometry::~CD2DGeometry](#_dtorcd2dgeometry)|Destruktor. Nazývá se při zničení objektu geometrie D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometry::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Zkombinuje tuto geometrii se zadanou geometrií a uloží výsledek do id2D1SimplifiedGeometrySink.|
|[CD2DGeometry::PorovnatSGeometry](#comparewithgeometry)|Popisuje průsečík mezi touto geometrií a zadanou geometrií. Porovnání se provádí pomocí zadané tolerance sloučení.|
|[CD2DGeometry::ComputeArea](#computearea)|Vypočítá oblast geometrie poté, co byla transformována zadanou maticí a sloučí se pomocí zadané tolerance.|
|[CD2DGeometry::ComputeLength](#computelength)|Vypočítá délku geometrie, jako by každý segment byl rozbalen do čáry.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Vypočítá bod a vektor tečny v zadané vzdálenosti podél geometrie poté, co byly transformovány zadanou maticí a srovnány se sazí pomocí zadané tolerance.|
|[CD2DGeometry::Destroy](#destroy)|Zničí objekt CD2DGeometry. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometry::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Označuje, zda by plocha vyplněná geometrií obsahovala zadaný bod vzhledem k zadané toleranci sloučení.|
|[CD2DGeometry::Získat](#get)|Vrátí rozhraní ID2D1Geometry.|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Získá hranice geometrie poté, co byla rozšířena o zadanou šířku tahu a styl a transformována zadanou maticí.|
|[CD2DGeometry::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Osnova](#outline)|Vypočítá obrys geometrie a zapíše výsledek do ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Zjednodušit](#simplify)|Vytvoří zjednodušenou verzi geometrie, která obsahuje pouze čáry a (volitelně) kubické Bezierovy křivky a zapíše výsledek do ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Určuje, zda tah geometrie obsahuje zadaný bod vzhledem k zadané tloušťce tahu, stylu a transformaci.|
|[CD2DGeometry::Tessellate](#tessellate)|Vytvoří sadu trojúhelníků ve směru hodinových ručiček, které pokrývají geometrii poté, co byla transformována pomocí zadané matice a sloučí se pomocí zadané tolerance.|
|[CD2DGeometry::Rozšířit](#widen)|Rozšíří geometrii o zadaný tah a zapíše výsledek do ID2D1SimplifiedGeometrySink poté, co byl transformován zadanou maticí a sloučí se pomocí zadané tolerance.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometry::operátor ID2D1Geometry*](#operator_id2d1geometry_star)|Vrátí rozhraní ID2D1Geometry.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Ukazatel na ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2DGeometry::~CD2DGeometry

Destruktor. Nazývá se při zničení objektu geometrie D2D.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2DGeometry::Připojit

Připojí k objektu existující rozhraní prostředků.

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry

Vytvoří objekt CD2DGeometry.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry

Zkombinuje tuto geometrii se zadanou geometrií a uloží výsledek do id2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*inputGeometry*<br/>
Geometrie kombinovat s touto instancí.

*combineMode*<br/>
Typ operace kombinovat provést.

*inputGeometryTransform*<br/>
Transformace použít inputGeometry před kombinací.

*geometrySink*<br/>
Výsledek operace kombinovat.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrií. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2DGeometry::PorovnatSGeometry

Popisuje průsečík mezi touto geometrií a zadanou geometrií. Porovnání se provádí pomocí zadané tolerance sloučení.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*inputGeometry*<br/>
Geometrie k testování.

*inputGeometryTransform*<br/>
Transformace použít inputGeometry.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrií. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2DGeometry::ComputeArea

Vypočítá oblast geometrie poté, co byla transformována zadanou maticí a sloučí se pomocí zadané tolerance.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformace, která se má použít pro tuto geometrii před výpočtem její oblasti.

*Oblasti*<br/>
Když se tato metoda vrátí, obsahuje ukazatel na oblast transformované, naložené verze této geometrie. Pro tento parametr je nutné přidělit úložiště.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2DGeometry::ComputeLength

Vypočítá délku geometrie, jako by každý segment byl rozbalen do čáry.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformace, která se má použít na geometrii před výpočtem její délky.

*Délka*<br/>
Když tato metoda vrátí, obsahuje ukazatel na délku geometrie. U uzavřených geometrií zahrnuje délka implicitní uzavírací segment. Pro tento parametr je nutné přidělit úložiště.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength

Vypočítá bod a vektor tečny v zadané vzdálenosti podél geometrie poté, co byly transformovány zadanou maticí a srovnány se sazí pomocí zadané tolerance.

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*Délka*<br/>
Vzdálenost podél geometrie bodu a tečna k nalezení. Pokud je tato vzdálenost menší než 0, tato metoda vypočítá první bod v geometrii. Pokud je tato vzdálenost větší než délka geometrie, tato metoda vypočítá poslední bod v geometrii.

*worldTransform*<br/>
Transformace, která se má použít na geometrii před výpočtem zadaného bodu a tečny.

*Bod*<br/>
Umístění v zadané vzdálenosti podél geometrie. Pokud je geometrie prázdná, tento bod obsahuje NaN jako hodnoty x a y.

*unitTangentVector*<br/>
Když se tato metoda vrátí, obsahuje ukazatel na tečný vektor v zadané vzdálenosti podél geometrie. Pokud je geometrie prázdná, tento vektor obsahuje NaN jako hodnoty x a y. Pro tento parametr je nutné přidělit úložiště.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2DGeometry::Destroy

Zničí objekt CD2DGeometry.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2DGeometry::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint

Označuje, zda by plocha vyplněná geometrií obsahovala zadaný bod vzhledem k zadané toleranci sloučení.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Bod k testování.

*worldTransform*<br/>
Transformace použít na geometrii před testováním kontejnmentu.

*Obsahuje*<br/>
Když tato metoda vrátí, obsahuje bool hodnotu, která je PRAVDA, pokud oblast vyplněná geometrií obsahuje bod; jinak NEPRAVDA. Pro tento parametr je nutné přidělit úložiště.

*sloučení tolerance*<br/>
Číselná přesnost, s jakou se počítá přesná geometrická cesta a průsečík cesty. Body, u kterých fill chybí menší než tolerance, jsou stále považovány za uvnitř. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2DGeometry::Získat

Vrátí rozhraní ID2D1Geometry.

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Geometry nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
*Hranice*

### <a name="return-value"></a>Návratová hodnota

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds

Získá hranice geometrie poté, co byla rozšířena o zadanou šířku tahu a styl a transformována zadanou maticí.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*strokeWidth*<br/>
Částka, o kterou chcete rozšířit geometrii vytažením jejího obrysu.

*strokeStyle*<br/>
Styl tahu, který rozšiřuje geometrii.

*worldTransform*<br/>
Transformace, která se použije na geometrii po transformaci geometrie a po vytažení geometrie.

*Hranice*<br/>
Když tato metoda vrátí, obsahuje hranice rozšířené geometrie. Pro tento parametr je nutné přidělit úložiště.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrií. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2DGeometry::IsValid

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry

Ukazatel na ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2DGeometry::operátor ID2D1Geometry*

Vrátí rozhraní ID2D1Geometry.

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Geometry nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2DGeometry::Osnova

Vypočítá obrys geometrie a zapíše výsledek do ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformace, která se má použít na obrys geometrie.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, ke kterému je připojen geometrie transformované osnovy.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2DGeometry::Zjednodušit

Vytvoří zjednodušenou verzi geometrie, která obsahuje pouze čáry a (volitelně) kubické Bezierovy křivky a zapíše výsledek do ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*možnost zjednodušení*<br/>
Hodnota, která určuje, zda má zjednodušená geometrie obsahovat křivky.

*worldTransform*<br/>
Transformace, která se má použít pro zjednodušenou geometrii.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, ke kterému je připojena zjednodušená geometrie.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint

Určuje, zda tah geometrie obsahuje zadaný bod vzhledem k zadané tloušťce tahu, stylu a transformaci.

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Bod k testování kontejnmentu.

*strokeWidth*<br/>
Tloušťka tahu, který chcete použít.

*strokeStyle*<br/>
Styl tahu, který chcete použít.

*worldTransform*<br/>
Transformace, která se má aplikovat na vytahovku geometrie.

*Obsahuje*<br/>
Když tato metoda vrátí, obsahuje logickou hodnotu nastavenou na HODNOTU PRAVDA, pokud tah geometrie obsahuje zadaný bod; jinak NEPRAVDA. Pro tento parametr je nutné přidělit úložiště.

*sloučení tolerance*<br/>
Číselná přesnost, s jakou se počítá přesná geometrická cesta a průsečík cesty. Body, které postrádají tah o méně než tolerance, jsou stále považovány za uvnitř. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2DGeometry::Tessellate

Vytvoří sadu trojúhelníků ve směru hodinových ručiček, které pokrývají geometrii poté, co byla transformována pomocí zadané matice a sloučí se pomocí zadané tolerance.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformace, která se má použít pro tuto geometrii nebo NULL.

*tessellationSink*<br/>
ID2D1TessellationSink, ke kterému je připojen mozaikové.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2DGeometry::Rozšířit

Rozšíří geometrii o zadaný tah a zapíše výsledek do ID2D1SimplifiedGeometrySink poté, co byl transformován zadanou maticí a sloučí se pomocí zadané tolerance.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*strokeWidth*<br/>
Částka, o kterou chcete rozšířit geometrii.

*strokeStyle*<br/>
Styl tahu, který se má použít na geometrii nebo NULL.

*worldTransform*<br/>
Transformace, která se použije na geometrii po jeho rozšíření.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, ke kterému je připojena rozšířená geometrie.

*sloučení tolerance*<br/>
Maximální hranice vzdálenosti mezi body v polygonové aproximaci geometrie. Menší hodnoty vytvářejí přesnější výsledky, ale způsobují pomalejší provádění.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
