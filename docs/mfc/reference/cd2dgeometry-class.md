---
title: Cd2dgeometry – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50ec35fd568031e7e30ee7412fcf078be1088906
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397088"
---
# <a name="cd2dgeometry-class"></a>Cd2dgeometry – třída

Obálka pro ID2D1Geometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Vytvoří objekt cd2dgeometry –.|
|[Cd2dgeometry –:: ~ cd2dgeometry –](#_dtorcd2dgeometry)|Destruktor. Volá se, když se likviduje geometrie objektu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Kombinuje tento geometrie pomocí zadaná geometrie a uloží výsledek v ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Popisuje průnik mezi tato geometrie a zadaná geometrie. Porovnání je provedeno pomocí zadaného sloučení proti chybám.|
|[CD2DGeometry::ComputeArea](#computearea)|Vypočítá oblasti geometrii byla určená matrix transformovat a sloučí pomocí zadanou toleranci.|
|[CD2DGeometry::ComputeLength](#computelength)|Vypočítá délku geometrie, jako by byl každý segment rozbaleno do řádku.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Vypočítá vektoru bodu a tangens v zadané vzdálenosti podél geometrii byla určená matrix transformovat a sloučí pomocí zadanou toleranci.|
|[CD2DGeometry::Destroy](#destroy)|Odstraní objekt cd2dgeometry –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometry::detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Označuje, zda oblasti sestavil geometrii bude obsahovat zadaný bodu zadanou toleranci sloučení.|
|[CD2DGeometry::Get](#get)|Vrátí ID2D1Geometry rozhraní|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Získá hranice geometrii poté, co byl rozšířit tak, že šířka tahu zadané a styl a transformovat určená matrix.|
|[CD2DGeometry::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Outline](#outline)|Vypočítá osnovy geometrie a zapíše výsledek do ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Simplify](#simplify)|Vytvoří zjednodušenou verzi geometrii, která obsahuje pouze řádky a (volitelně) kubické Bézierovy křivky a zapíše výsledek do ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Určuje, zda geometrie stroke obsahuje zadaný bod vzhledem k zadané tloušťka čáry, styl a transformace.|
|[CD2DGeometry::Tessellate](#tessellate)|Vytvoří sadu po směru hodinových ručiček vinutým trojúhelníků, které zahrnují geometrii po byly transformovány, pomocí zadané matice a sloučí pomocí zadanou toleranci.|
|[CD2DGeometry::widen](#widen)|Rozšiřuje geometrie pomocí zadaného tahů a zapíše výsledek do ID2D1SimplifiedGeometrySink byla určená matrix transformovat a sloučí pomocí zadanou toleranci.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DGeometry::Operator ID2D1Geometry *](#operator_id2d1geometry_star)|Vrátí ID2D1Geometry rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Ukazatel ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource –](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dgeometry"></a>  Cd2dgeometry –:: ~ cd2dgeometry –

Destruktor. Volá se, když se likviduje geometrie objektu D2D.

```
virtual ~CD2DGeometry();
```

##  <a name="attach"></a>  CD2DGeometry::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry

Vytvoří objekt cd2dgeometry –.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry

Kombinuje tento geometrie pomocí zadaná geometrie a uloží výsledek v ID2D1SimplifiedGeometrySink.

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
Geometrie zkombinovat s touto instancí.

*combineMode*<br/>
Typ operace sloučení se má provést.

*inputGeometryTransform*<br/>
Transformací, která se má použít pro inputGeometry před kombinace.

*geometrySink*<br/>
Výsledek operace sloučení.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrie. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry

Popisuje průnik mezi tato geometrie a zadaná geometrie. Porovnání je provedeno pomocí zadaného sloučení proti chybám.

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
Transformací, která se má použít pro inputGeometry.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrie. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="computearea"></a>  CD2DGeometry::ComputeArea

Vypočítá oblasti geometrii byla určená matrix transformovat a sloučí pomocí zadanou toleranci.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformací, která se má použít pro tento geometrie před jeho oblasti computingu.

*Oblast*<br/>
Po návratu metody obsahuje ukazatel na oblast transformovaná plochá verzi této geometry. Pro tento parametr, musíte přidělit úložiště.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="computelength"></a>  CD2DGeometry::ComputeLength

Vypočítá délku geometrie, jako by byl každý segment rozbaleno do řádku.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformací, která se má použít pro geometrii před výpočtem jeho délky.

*Délka*<br/>
Po návratu metody obsahuje ukazatel na délku geometrii. Pro uzavřené geometrie délka zahrnuje segmentu implicitní pravou. Pro tento parametr, musíte přidělit úložiště.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength

Vypočítá vektoru bodu a tangens v zadané vzdálenosti podél geometrii byla určená matrix transformovat a sloučí pomocí zadanou toleranci.

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
Vzdálenost podél geometrie bodu a tangens najít. Pokud tato vzdálenost je méně pak 0, tato metoda vypočítá prvním bodem geometrii. Pokud tato vzdálenost je větší než délka geometrii, tato metoda vypočítá posledního bodu v geometrii.

*worldTransform*<br/>
Transformací, která se má použít pro geometrii před výpočtem Zadaný bod a tangens.

*Bod*<br/>
Umístění v zadané vzdálenosti podél geometrii. Pokud geometrii je prázdný, obsahuje tento bod NaN jako jeho x a y hodnoty.

*unitTangentVector*<br/>
Po návratu metody obsahuje ukazatel na tečný vektoru v zadané vzdálenosti podél geometrii. Pokud geometrii je prázdný, tato vektor obsahuje NaN jako jeho x a y hodnoty. Pro tento parametr, musíte přidělit úložiště.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="destroy"></a>  CD2DGeometry::Destroy

Odstraní objekt cd2dgeometry –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DGeometry::detach

Odpojí prostředků rozhraní z objektu

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint

Označuje, zda oblasti sestavil geometrii bude obsahovat zadaný bodu zadanou toleranci sloučení.

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
Transformací, která se má použít pro geometrii před testování pro členství ve skupině.

*Obsahuje*<br/>
Po návratu tato metoda obsahuje hodnotu typu bool, která je hodnota TRUE, pokud oblasti sestavil geometrii obsahuje bod; v opačném případě hodnota FALSE. Pro tento parametr, musíte přidělit úložiště.

*flatteningTolerance*<br/>
Číselná přesnost, pomocí kterého přesné geometrické cesty a cesty průnik se počítá. Chybí výplně o méně než tolerance body jsou stále považovány za uvnitř. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="get"></a>  CD2DGeometry::Get

Vrátí ID2D1Geometry rozhraní

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Geometry nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getbounds"></a>  CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
*Hranice*

### <a name="return-value"></a>Návratová hodnota

##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds

Získá hranice geometrii poté, co byl rozšířit tak, že šířka tahu zadané a styl a transformovat určená matrix.

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
Rozsah, pomocí které se má rozšířit geometrii podle vytažení obrysu.

*strokeStyle*<br/>
Styl, který rozšiřuje geometrii stroke.

*worldTransform*<br/>
Transformaci, kterou chcete použít pro geometrii po transformaci geometrie a poté, co byl vytažený geometrii.

*Hranice*<br/>
Po návratu metody obsahuje hranice rozšířil geometry. Pro tento parametr, musíte přidělit úložiště.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrie. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="isvalid"></a>  CD2DGeometry::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry

Ukazatel ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::Operator ID2D1Geometry *

Vrátí ID2D1Geometry rozhraní

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Geometry nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="outline"></a>  CD2DGeometry::Outline

Vypočítá osnovy geometrie a zapíše výsledek do ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformací, která se má použít pro geometrie obrysu.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, ke kterému je připojen geometrie transformovaný osnovy.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="simplify"></a>  CD2DGeometry::Simplify

Vytvoří zjednodušenou verzi geometrii, která obsahuje pouze řádky a (volitelně) kubické Bézierovy křivky a zapíše výsledek do ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*simplificationOption*<br/>
Hodnota, která určuje, jestli zjednodušené geometrie by měl obsahovat křivky.

*worldTransform*<br/>
Transformací, která se má použít pro zjednodušené geometry.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, ke kterému je připojen zjednodušené geometry.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint

Určuje, zda geometrie stroke obsahuje zadaný bod vzhledem k zadané tloušťka čáry, styl a transformace.

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
Bod tak, aby test pro členství ve skupině.

*strokeWidth*<br/>
Tloušťka tahu použít.

*strokeStyle*<br/>
Styl stroke použít.

*worldTransform*<br/>
Transformací, která se má použít pro vytažené geometry.

*Obsahuje*<br/>
Po návratu tato metoda obsahuje hodnotu typu boolean nastavena na hodnotu TRUE, pokud geometrie stroke obsahuje zadaný bod; v opačném případě hodnota FALSE. Pro tento parametr, musíte přidělit úložiště.

*flatteningTolerance*<br/>
Číselná přesnost, pomocí kterého přesné geometrické cesty a cesty průnik se počítá. O méně než tolerance chybějících tahu bodů jsou stále považovány za uvnitř. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="tessellate"></a>  CD2DGeometry::Tessellate

Vytvoří sadu po směru hodinových ručiček vinutým trojúhelníků, které zahrnují geometrii po byly transformovány, pomocí zadané matice a sloučí pomocí zadanou toleranci.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parametry

*worldTransform*<br/>
Transformací, která se má použít pro tento geometrie, nebo hodnota NULL.

*tessellationSink*<br/>
ID2D1TessellationSink, ke kterému teselace sestavy se připojí.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

##  <a name="widen"></a>  CD2DGeometry::widen

Rozšiřuje geometrie pomocí zadaného tahů a zapíše výsledek do ID2D1SimplifiedGeometrySink byla určená matrix transformovat a sloučí pomocí zadanou toleranci.

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
Rozsah, pomocí které se má rozšířit geometrii.

*strokeStyle*<br/>
Styl stroke vyrovnat geometrie, nebo hodnota NULL.

*worldTransform*<br/>
Transformací, která se má použít pro geometrii po jeho rozšíření.

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink, ke kterému se rozšířil geometrie připojí.

*flatteningTolerance*<br/>
Maximální rozsah vzdálenosti mezi body v mnohoúhelníkové aproximace geometrii. Nižší hodnoty přesnější výsledky však způsobit pomalejší spuštění.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
