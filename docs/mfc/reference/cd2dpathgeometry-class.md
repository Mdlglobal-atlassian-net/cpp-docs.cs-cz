---
title: CD2DPathGeometry – třída
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
ms.openlocfilehash: 59ef82151983720b654502ccf3ca647e55366268
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369173"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry – třída

Obálka pro ID2D1PathGeometry.

## <a name="syntax"></a>Syntaxe

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Vytvoří objekt CD2DPathGeometry.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DPathGeometry::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DPathGeometry::Vytvořit](#create)|Vytvoří CD2DPathGeometry. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPathGeometry::Destroy](#destroy)|Zničí objekt CD2DPathGeometry. (Přepíše [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPathGeometry::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Načte počet ponožek v geometrii cesty.|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Načte počet segmentů v geometrii cesty.|
|[CD2DPathGeometry::Otevřít](#open)|Načte jímka geometrie, která se používá k naplnění geometrie cesty postavami a segmenty.|
|[CD2DPathGeometry::Stream](#stream)|Zkopíruje obsah geometrie cesty do zadaného ID2D1GeometrySink.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Ukazatel na ID2D1PathGeometry.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPathGeometry::Připojit

Připojí k objektu existující rozhraní prostředků.

```
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry

Vytvoří objekt CD2DPathGeometry.

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPathGeometry::Vytvořit

Vytvoří CD2DPathGeometry.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPathGeometry::Destroy

Zničí objekt CD2DPathGeometry.

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPathGeometry::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount

Načte počet ponožek v geometrii cesty.

```
int GetFigureCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet číslic v geometrii cesty.

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount

Načte počet segmentů v geometrii cesty.

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet segmentů v geometrii cesty.

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry

Ukazatel na ID2D1PathGeometry.

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPathGeometry::Otevřít

Načte jímka geometrie, která se používá k naplnění geometrie cesty postavami a segmenty.

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ID2D1GeometrySink, který se používá k naplnění geometrie cesty s čísly a segmenty.

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPathGeometry::Stream

Zkopíruje obsah geometrie cesty do zadaného ID2D1GeometrySink.

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>Parametry

*geometrySink*<br/>
Jímka, do kterého jsou zkopírovány obsah geometrie cesty. Změna tohoto jímky nezmění obsah této geometrie cesty.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
