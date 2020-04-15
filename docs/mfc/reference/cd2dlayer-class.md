---
title: Třída CD2DLayer
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: aa6fb313bfcc2983f167936e5ad4f78be1e17a44
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369205"
---
# <a name="cd2dlayer-class"></a>Třída CD2DLayer

Obálka pro ID2D1Layer.

## <a name="syntax"></a>Syntaxe

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Vytvoří objekt CD2DLayer.|
|[CD2DLayer::~CD2DLayer](#_dtorcd2dlayer)|Destruktor. Nazývá se při zničení objektu vrstvy D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLayer::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DLayer::Vytvořit](#create)|Vytvoří vrstvu CD2D. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Zničí objekt CD2DLayer. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DLayer::Získat](#get)|Vrátí rozhraní ID2D1Layer.|
|[CD2DLayer::GetSize](#getsize)|Vrátí velikost cíle vykreslení v pixelech nezávislých na zařízení.|
|[CD2DLayer::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLayer::operátor ID2D1Layer*](#operator_id2d1layer_star)|Vrátí rozhraní ID2D1Layer.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Uloží ukazatel na objekt ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>CD2DLayer::~CD2DLayer

Destruktor. Nazývá se při zničení objektu vrstvy D2D.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer::Připojit

Připojí k objektu existující rozhraní prostředků.

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer::CD2DLayer

Vytvoří objekt CD2DLayer.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer::Vytvořit

Vytvoří vrstvu CD2D.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer::Destroy

Zničí objekt CD2DLayer.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer::Získat

Vrátí rozhraní ID2D1Layer.

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Layer nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer::GetSize

Vrátí velikost cíle vykreslení v pixelech nezávislých na zařízení.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost cíle vykreslení v pixelech nezávislých na zařízení

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>CD2DLayer::IsValid

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer::m_pLayer

Uloží ukazatel na objekt ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer::operátor ID2D1Layer*

Vrátí rozhraní ID2D1Layer.

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Layer nebo NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
