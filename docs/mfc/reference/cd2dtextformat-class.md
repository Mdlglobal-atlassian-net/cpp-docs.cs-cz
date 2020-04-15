---
title: Třída cd2DTextFormat
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
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369036"
---
# <a name="cd2dtextformat-class"></a>Třída cd2DTextFormat

Obálka pro IDWriteTextFormat.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextFormat::CD2DTextový formát](#cd2dtextformat)|Vytvoří objekt CD2DTextFormat.|
|[CD2DTextFormat::~CD2DTextFormat](#_dtorcd2dtextformat)|Destruktor. Nazývá se při zničení objektu formátu textu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextFormat::Vytvořit](#create)|Vytvoří formát CD2DTextFormat. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextFormát::Destroy](#destroy)|Zničí objekt CD2DTextFormat. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextový formát::Získat](#get)|Vrátí rozhraní IDWriteTextFormat.|
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Získá kopii názvu rodiny písma.|
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Získá kopii názvu národního prostředí.|
|[CD2DTextFormat::isValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextFormat::Znovu vytvořit](#recreate)|Znovu vytvoří formát CD2DTextFormat. (Přepíše [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextFormat::operátor IDWriteTextFormat*](#operator_idwritetextformat_star)|Vrátí rozhraní IDWriteTextFormat.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Ukazatel na formát IDWriteTextFormat.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[Formát CD2DText](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat::~CD2DTextFormat

Destruktor. Nazývá se při zničení objektu formátu textu D2D.

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextový formát

Vytvoří objekt CD2DTextFormat.

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
Ukazatel na cíl vykreslení.

*strFontFamilyName*<br/>
CString objekt, který obsahuje název rodiny písem.

*Fontsize*<br/>
Logická velikost písma v jednotkách DIP ("pixel nezávislý na zařízení"). DIProvná 1/96 palce.

*Fontweight*<br/>
Hodnota, která označuje tloušťku písma pro textový objekt.

*Fontstyle*<br/>
Hodnota, která označuje styl písma pro textový objekt.

*Fontstretch*<br/>
Hodnota, která označuje roztažení písma pro textový objekt.

*strFontLocale*<br/>
CString objekt, který obsahuje název národního prostředí.

*kolekce pFontCollection*<br/>
Ukazatel na objekt kolekce písma. Pokud je hodnota NULL, označuje kolekci systémových písem.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Vytvořit

Vytvoří formát CD2DTextFormat.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormát::Destroy

Zničí objekt CD2DTextFormat.

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2DTextový formát::Získat

Vrátí rozhraní IDWriteTextFormat.

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextFormat nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName

Získá kopii názvu rodiny písma.

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>Návratová hodnota

CString objekt, který obsahuje aktuální název rodiny písma.

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName

Získá kopii názvu národního prostředí.

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>Návratová hodnota

CString objekt, který obsahuje aktuální název národního prostředí.

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::isValid

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat

Ukazatel na formát IDWriteTextFormat.

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::operátor IDWriteTextFormat*

Vrátí rozhraní IDWriteTextFormat.

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextFormat nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::Znovu vytvořit

Znovu vytvoří formát CD2DTextFormat.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
