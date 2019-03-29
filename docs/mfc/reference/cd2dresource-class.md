---
title: Cd2dresource – třída
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: e2cc6be7119a2df193aa2af415a9c8d4054f537c
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564772"
---
# <a name="cd2dresource-class"></a>Cd2dresource – třída

Abstraktní třída, která poskytuje rozhraní pro vytváření a správu D2D prostředky, jako jsou štětce, vrstvy a texty.

## <a name="syntax"></a>Syntaxe

```
class CD2DResource : public CObject;
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|Vytvoří objekt cd2dresource –.|
|[CD2DResource::~CD2DResource](#_dtorcd2dresource)|Destruktor. Volá se, když se likviduje prostředků objektu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CD2DResource::Create](#create)|Vytvoří cd2dresource –.|
|[CD2DResource::Destroy](#destroy)|Odstraní objekt cd2dresource –.|
|[CD2DResource::IsValid](#isvalid)|Kontrola platnosti prostředků|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Kontrola automaticky zničit příznak.|
|[CD2DResource::ReCreate](#recreate)|Znovu vytvoří cd2dresource –.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Zničení prostředků vlastníkem (crendertarget –)|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Ukazatel na hodnotu parent crendertarget –)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dresource"></a>  Cd2dresource –:: ~ cd2dresource –

Destruktor. Volá se, když se likviduje prostředků objektu D2D.

```
virtual ~CD2DResource();
```

##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource

Vytvoří objekt cd2dresource –.

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DResource::Create

Vytvoří cd2dresource –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DResource::Destroy

Odstraní objekt cd2dresource –.

```
virtual void Destroy() = 0;
```

##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy

Kontrola automaticky zničit příznak.

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud vlastník; bude objekt zničen. v opačném případě FALSE.

##  <a name="isvalid"></a>  CD2DResource::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy

Zničení prostředků vlastníkem (crendertarget –)

```
BOOL m_bIsAutoDestroy;
```

##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget

Ukazatel na hodnotu parent crendertarget –)

```
CRenderTarget* m_pParentTarget;
```

##  <a name="recreate"></a>  CD2DResource::ReCreate

Znovu vytvoří cd2dresource –.

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
