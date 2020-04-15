---
title: CD2DTextLayout – třída
ms.date: 03/27/2019
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
ms.openlocfilehash: 9be4c1134e2f82ceb3af31cbeb1a7d55f4071777
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369028"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout – třída

Obálka pro IDWriteTextLayout.

## <a name="syntax"></a>Syntaxe

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Vytvoří objekt CD2DTextLayout.|
|[CD2DTextLayout::~CD2DTextLayout](#_dtorcd2dtextlayout)|Destruktor. Nazývá se při zničení objektu rozložení textu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRozložení textu::Vytvořit](#create)|Vytvoří cd2DTextLayout. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DTextLayout::Destroy](#destroy)|Zničí objekt CD2DTextLayout. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DRozložení textu::Získat](#get)|Vrátí rozhraní IDWriteTextLayout.|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Zkopíruje název rodiny písem textu na zadanépozici.|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Získá název národního prostředí textu na zadané pozici.|
|[CD2DTextLayout::IsValid CD2DTextLayout::IsValid CD2DTextLayout::IsValid CD2](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DTextLayout::Znovu vytvořit](#recreate)|Znovu vytvoří CD2DTextLayout. (Přepíše [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Nastaví název rodiny písem s neplatným i pro text v zadaném rozsahu textu.|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Nastaví název národního prostředí pro text v zadaném rozsahu textu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextLayout::operátor IDWriteTextLayout*](#operator_idwritetextlayout_star)|Vrátí rozhraní IDWriteTextLayout.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Ukazatel na IDWriteTextLayout.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[Cd2DRozložení textu](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a>CD2DTextLayout::~CD2DTextLayout

Destruktor. Nazývá se při zničení objektu rozložení textu D2D.

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a>CD2DTextLayout::CD2DTextLayout

Vytvoří objekt CD2DTextLayout.

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
Ukazatel na cíl vykreslení.

*strText*<br/>
CString objekt, který obsahuje řetězec vytvořit nový objekt CD2DTextLayout z.

*Textformat*<br/>
CString objekt, který obsahuje formát použít řetězec.

*sizeMax*<br/>
Velikost pole rozložení.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a>CD2DRozložení textu::Vytvořit

Vytvoří cd2DTextLayout.

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a>CD2DTextLayout::Destroy

Zničí objekt CD2DTextLayout.

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a>CD2DRozložení textu::Získat

Vrátí rozhraní IDWriteTextLayout.

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextLayout nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextLayout::GetFontFamilyName

Zkopíruje název rodiny písem textu na zadanépozici.

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parametry

*currentPosition*<br/>
Pozice textu zkoumat.

*textRozsah*<br/>
Rozsah textu, který má stejné formátování jako text na pozici určené currentPosition. To znamená, že běh má přesné formátování jako zadanou pozici, včetně, ale bez omezení na název rodiny písma.

### <a name="return-value"></a>Návratová hodnota

CString objekt, který obsahuje aktuální název rodiny písma.

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a>CD2DTextLayout::GetLocaleName

Získá název národního prostředí textu na zadané pozici.

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>Parametry

*currentPosition*<br/>
Umístění textu ke kontrole.

*textRozsah*<br/>
Rozsah textu, který má stejné formátování jako text na pozici určené currentPosition. To znamená, že spuštění má přesné formátování jako zadanou pozici, včetně, ale bez omezení na název národního prostředí.

### <a name="return-value"></a>Návratová hodnota

CString objekt, který obsahuje aktuální název národního prostředí.

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a>CD2DTextLayout::IsValid CD2DTextLayout::IsValid CD2DTextLayout::IsValid CD2

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a>CD2DTextLayout::m_pTextLayout

Ukazatel na IDWriteTextLayout.

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a>CD2DTextLayout::operátor IDWriteTextLayout*

Vrátí rozhraní IDWriteTextLayout.

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteTextLayout nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a>CD2DTextLayout::Znovu vytvořit

Znovu vytvoří CD2DTextLayout.

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a>CD2DTextLayout::SetFontFamilyName

Nastaví název rodiny písem s neplatným i pro text v zadaném rozsahu textu.

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parametry

*pwzFontFamilyName*<br/>
Název rodiny písem, který se vztahuje na celý textový řetězec v rozsahu určeném textrange

*textRozsah*<br/>
Rozsah textu, na který se tato změna vztahuje

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a>CD2DTextLayout::SetLocaleName

Nastaví název národního prostředí pro text v zadaném rozsahu textu.

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>Parametry

*pwzLocaleName*<br/>
Řetězec názvů národního prostředí ukončeného hodnotou null

*textRozsah*<br/>
Rozsah textu, na který se tato změna vztahuje

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu NEPRAVDA.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
