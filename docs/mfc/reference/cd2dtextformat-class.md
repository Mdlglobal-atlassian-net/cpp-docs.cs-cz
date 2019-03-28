---
title: CD2DTextFormat Class
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: fa2f3b663cb5258c64ec0405abacf2e4eedeb987
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565318"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat Class

Obálka pro IDWriteTextFormat.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Vytvoří objekt cd2dtextformat –.|
|[CD2DTextFormat::~CD2DTextFormat](#_dtorcd2dtextformat)|Destruktor. Volá se, když se likviduje objektu D2D textového formátu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CD2DTextFormat::Create](#create)|Vytvoří cd2dtextformat –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormat::Destroy](#destroy)|Odstraní objekt cd2dtextformat –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextFormat::Get](#get)|Vrátí IDWriteTextFormat rozhraní|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Získá kopii objektu název rodiny písem.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Získá kopii objektu název národního prostředí.|
|[CD2DTextFormat::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::ReCreate](#recreate)|Znovu vytvoří cd2dtextformat –. (Přepíše [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DTextFormat::operator IDWriteTextFormat*](#operator_idwritetextformat_star)|Vrátí IDWriteTextFormat rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Ukazatel IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dtextformat"></a>  CD2DTextFormat::~CD2DTextFormat

Destruktor. Volá se, když se likviduje objektu D2D textového formátu.

```
virtual ~CD2DTextFormat();
```

##  <a name="cd2dtextformat"></a>  CD2DTextFormat::CD2DTextFormat

Vytvoří objekt cd2dtextformat –.

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*strFontFamilyName*<br/>
CString – objekt, který obsahuje název rodiny písem.

*fontSize*<br/>
Logická velikost písma v jednotkách vyhrazené IP adresy ("pixelech nezávislých na zařízení"). DIPequals 1/96 palce.

*fontWeight*<br/>
Hodnota, která určuje tloušťku písma pro objekt textu.

*fontStyle*<br/>
Hodnota, která určuje styl písma textu objektu.

*fontStretch*<br/>
Hodnota, která určuje stretch písmo pro text objektu.

*strFontLocale*<br/>
CString – objekt, který obsahuje název národního prostředí.

*pFontCollection*<br/>
Ukazatel na objekt kolekce písma. V případě, že toto je NULL, označuje kolekce písem systémové.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DTextFormat::Create

Vytvoří cd2dtextformat –.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DTextFormat::Destroy

Odstraní objekt cd2dtextformat –.

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextFormat::Get

Vrátí IDWriteTextFormat rozhraní

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextFormat nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getfontfamilyname"></a>  CD2DTextFormat::GetFontFamilyName

Získá kopii objektu název rodiny písem.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Návratová hodnota

CString – objekt, který obsahuje aktuální název rodiny písem.

##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName

Získá kopii objektu název národního prostředí.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Návratová hodnota

CString – objekt, který obsahuje název aktuální národní prostředí.

##  <a name="isvalid"></a>  CD2DTextFormat::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat

Ukazatel IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::Operator IDWriteTextFormat *

Vrátí IDWriteTextFormat rozhraní

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextFormat nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="recreate"></a>  CD2DTextFormat::ReCreate

Znovu vytvoří cd2dtextformat –.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
