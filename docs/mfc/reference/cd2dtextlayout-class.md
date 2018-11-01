---
title: Cd2dtextlayout – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
ms.openlocfilehash: 378c96622144a4acac27785cef844f0c1d21b98b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630942"
---
# <a name="cd2dtextlayout-class"></a>Cd2dtextlayout – třída

Obálka pro IDWriteTextLayout.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Vytvoří objekt cd2dtextlayout –.|
|[Cd2dtextlayout –:: ~ cd2dtextlayout –](#cd2dtextlayout__~cd2dtextlayout)|Destruktor. Volá se, když se likviduje rozložení objektu D2D text.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|Vytvoří cd2dtextlayout –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Odstraní objekt cd2dtextlayout –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DTextLayout::Get](#get)|Vrátí IDWriteTextLayout rozhraní|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Zkopíruje název rodiny písem textu na zadané pozici.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Získá název národního prostředí text na konkrétní pozici.|
|[CD2DTextLayout::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::ReCreate](#recreate)|Znovu vytvoří cd2dtextlayout –. (Přepíše [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nastaví název typu zakončený hodnotou null písma pro text rozsahu zadaným textem|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Nastaví název národního prostředí pro text rozsahu zadaným textem|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DTextLayout::Operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Vrátí IDWriteTextLayout rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Ukazatel IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource –](../../mfc/reference/cd2dresource-class.md)

[Cd2dtextlayout –](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dtextlayout"></a>  Cd2dtextlayout –:: ~ cd2dtextlayout –

Destruktor. Volá se, když se likviduje rozložení objektu D2D text.

```
virtual ~CD2DTextLayout();
```

##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout

Vytvoří objekt cd2dtextlayout –.

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*strText*<br/>
CString – objekt, který obsahuje řetězec, který má-li vytvořit nový objekt cd2dtextlayout – z.

*textFormat*<br/>
CString – objekt, který obsahuje formát, který se použije na řetězec.

*sizeMax*<br/>
Velikost pole rozložení.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="create"></a>  CD2DTextLayout::Create

Vytvoří cd2dtextlayout –.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DTextLayout::Destroy

Odstraní objekt cd2dtextlayout –.

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextLayout::Get

Vrátí IDWriteTextLayout rozhraní

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextLayout nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName

Zkopíruje název rodiny písem textu na zadané pozici.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parametry

*currentPosition*<br/>
Umístění textu k prozkoumání.

*TextRange*<br/>
Rozsah textu, který má stejný formát jako text na pozici určené currentPosition. To znamená, že nemá přesné formátování jako pozice zadána, včetně, ale nikoli výhradně název rodiny písem.

### <a name="return-value"></a>Návratová hodnota

CString – objekt, který obsahuje aktuální název rodiny písem.

##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName

Získá název národního prostředí text na konkrétní pozici.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parametry

*currentPosition*<br/>
Umístění textu ke kontrole.

*TextRange*<br/>
Rozsah textu, který má stejný formát jako text na pozici určené currentPosition. To znamená, že nemá přesné formátování jako pozice zadána, včetně, ale nikoli výhradně na název národního prostředí.

### <a name="return-value"></a>Návratová hodnota

CString – objekt, který obsahuje název aktuální národní prostředí.

##  <a name="isvalid"></a>  CD2DTextLayout::IsValid

Kontrola platnosti prostředků

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout

Ukazatel IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::Operator IDWriteTextLayout *

Vrátí IDWriteTextLayout rozhraní

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextLayout nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="recreate"></a>  CD2DTextLayout::ReCreate

Znovu vytvoří cd2dtextlayout –.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName

Nastaví název typu zakončený hodnotou null písma pro text rozsahu zadaným textem

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parametry

*pwzFontFamilyName*<br/>
Název rodiny písem, které platí pro celého textového řetězce v rozsahu určeném textRange

*TextRange*<br/>
Rozsah textu, do které tato změna se vztahuje

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrací FALSE

##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName

Nastaví název národního prostředí pro text rozsahu zadaným textem

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parametry

*pwzLocaleName*<br/>
Řetězec názvu národního prostředí zakončený hodnotou null

*TextRange*<br/>
Rozsah textu, do které tato změna se vztahuje

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu TRUE. V opačném případě vrací FALSE

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
