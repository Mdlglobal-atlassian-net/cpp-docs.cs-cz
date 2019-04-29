---
title: Cd2dpathgeometry – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 8657421e67239cdeb782cffbbd42e0c50f6c0e96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396350"
---
# <a name="cd2dpathgeometry-class"></a>Cd2dpathgeometry – třída

Obálka pro ID2D1PathGeometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Vytvoří objekt cd2dpathgeometry –.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DPathGeometry::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DPathGeometry::Create](#create)|Vytvoří cd2dpathgeometry –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Odstraní objekt cd2dpathgeometry –. (Přepíše [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::Detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Získá počet číslic v geometrické cesty.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Získá počet segmentů v cestě geometrii.|
|[CD2DPathGeometry::Open](#open)|Načte jímka geometrii, která se používá k naplnění geometrie cestu s obrázky a segmentů.|
|[CD2DPathGeometry::Stream](#stream)|Zkopíruje obsah geometrické cesty k zadané ID2D1GeometrySink.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Ukazatel ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[Cd2dgeometry –](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="attach"></a>  CD2DPathGeometry::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dpathgeometry"></a>  CD2DPathGeometry::CD2DPathGeometry

Vytvoří objekt cd2dpathgeometry –.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DPathGeometry::Create

Vytvoří cd2dpathgeometry –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DPathGeometry::Destroy

Odstraní objekt cd2dpathgeometry –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DPathGeometry::Detach

Odpojí prostředků rozhraní z objektu

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="getfigurecount"></a>  CD2DPathGeometry::GetFigureCount

Získá počet číslic v geometrické cesty.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet číslic v geometrické cesty.

##  <a name="getsegmentcount"></a>  CD2DPathGeometry::GetSegmentCount

Získá počet segmentů v cestě geometrii.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet segmentů v cestě geometrii.

##  <a name="m_ppathgeometry"></a>  CD2DPathGeometry::m_pPathGeometry

Ukazatel ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

##  <a name="open"></a>  CD2DPathGeometry::Open

Načte jímka geometrii, která se používá k naplnění geometrie cestu s obrázky a segmentů.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ID2D1GeometrySink, který se používá k naplnění geometrie cestu s obrázky a segmentů.

##  <a name="stream"></a>  CD2DPathGeometry::Stream

Zkopíruje obsah geometrické cesty k zadané ID2D1GeometrySink.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Parametry

*geometrySink*<br/>
Jímky, ke které se zkopírují geometrie Cesta obsahu. Úprava této jímky nezmění obsah geometrie této cesty.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
