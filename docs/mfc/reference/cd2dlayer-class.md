---
title: Cd2dlayer – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d381ecaa2ac894ce7f393685e67909fea013cde
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400117"
---
# <a name="cd2dlayer-class"></a>Cd2dlayer – třída

Obálka pro ID2D1Layer.

## <a name="syntax"></a>Syntaxe

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Vytvoří objekt cd2dlayer –.|
|[Cd2dlayer –:: ~ cd2dlayer –](#_dtorcd2dlayer)|Destruktor. Volá se, když se likviduje vrstvy objektu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DLayer::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DLayer::Create](#create)|Vytvoří cd2dlayer –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Odstraní objekt cd2dlayer –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DLayer::Get](#get)|Vrátí ID2D1Layer rozhraní|
|[CD2DLayer::GetSize](#getsize)|Vrátí velikost cíle vykreslování v pixelech nezávislých na zařízení|
|[CD2DLayer::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DLayer::Operator ID2D1Layer *](#operator_id2d1layer_star)|Vrátí ID2D1Layer rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Uchovává ukazatel na objekt ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource –](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dlayer"></a>  Cd2dlayer –:: ~ cd2dlayer –

Destruktor. Volá se, když se likviduje vrstvy objektu D2D.

```
virtual ~CD2DLayer();
```

##  <a name="attach"></a>  CD2DLayer::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer

Vytvoří objekt cd2dlayer –.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DLayer::Create

Vytvoří cd2dlayer –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DLayer::Destroy

Odstraní objekt cd2dlayer –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLayer::detach

Odpojí prostředků rozhraní z objektu

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DLayer::Get

Vrátí ID2D1Layer rozhraní

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Layer nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getsize"></a>  CD2DLayer::GetSize

Vrátí velikost cíle vykreslování v pixelech nezávislých na zařízení

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost cíle vykreslování v pixelech nezávislých na zařízení

##  <a name="isvalid"></a>  CD2DLayer::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_player"></a>  CD2DLayer::m_pLayer

Uchovává ukazatel na objekt ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::Operator ID2D1Layer *

Vrátí ID2D1Layer rozhraní

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Layer nebo hodnota NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
