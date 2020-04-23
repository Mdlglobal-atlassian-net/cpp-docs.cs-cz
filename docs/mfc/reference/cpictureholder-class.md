---
title: CPictureHolder – třída
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: edb93b05c1187d2c78f4c1120ee76282167c9b49
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753596"
---
# <a name="cpictureholder-class"></a>CPictureHolder – třída

Implementuje Picture vlastnost, která umožňuje uživateli zobrazit obrázek v ovládacím prvku.

## <a name="syntax"></a>Syntaxe

```
class CPictureHolder
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Vytvoří `CPictureHolder` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Vytvoří prázdný `CPictureHolder` objekt.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Vytvoří `CPictureHolder` objekt z bitmapy.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Vytvoří `CPictureHolder` objekt z ikony.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Vytvoří `CPictureHolder` objekt z metasouboru.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazený v prohlížeči vlastností kontejneru ovládacího prvku.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Vrátí `CPictureHolder` rozhraní objektu. `IDispatch`|
|[CPictureHolder::GetType](#gettype)|Určuje, `CPictureHolder` zda je objekt bitmapou, metasouborem nebo ikonou.|
|[CPictureHolder::Vykreslení](#render)|Vykreslí obrázek.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Nastaví `CPictureHolder` rozhraní `IDispatch` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Ukazatel na objekt obrázku.|

## <a name="remarks"></a>Poznámky

`CPictureHolder`nemá základní třídu.

Pomocí vlastnosti Stock Picture může vývojář zadat bitmapu, ikonu nebo metasoubor pro zobrazení.

Informace o vytváření vlastních vlastností obrázku naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Použití obrázků v ovládacím prvku ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CPictureHolder`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPictureHolder::CPictureHolder

Vytvoří `CPictureHolder` objekt.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPictureHolder::CreateEmpty

Vytvoří prázdný `CPictureHolder` objekt a připojí `IPicture` jej k rozhraní.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt úspěšně vytvořen; jinak 0.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap

Používá bitmapu k inicializaci objektu obrázku `CPictureHolder`v rozhraní .

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*idZdroj*<br/>
ID prostředku bitmapového prostředku.

*pBitmap*<br/>
Ukazatel na objekt [CBitmap.](../../mfc/reference/cbitmap-class.md)

*pPal*<br/>
Ukazatel na [cpalette](../../mfc/reference/cpalette-class.md) objekt.

*bVlastnictví převodu*<br/>
Označuje, zda objekt obrázku převezme vlastnictví bitmapových a paletových objektů.

*Hbm*<br/>
Zpracovat bitmapu, ze `CPictureHolder` které je objekt vytvořen.

*hpal*<br/>
Zpracovat paletu použitou pro vykreslení bitmapy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bTransferOwnership* je TRUE, volající by neměl používat bitmapový objekt nebo objekt palety žádným způsobem po vrácení tohoto volání. Pokud *bTransferOwnership* je FALSE, volající je zodpovědný za zajištění, že bitmapa a paleta objekty zůstávají platné po dobu životnosti objektu obrázku.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPictureHolder::CreateFromIcon

Používá ikonu k inicializaci objektu obrázku v aplikaci `CPictureHolder`.

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*idZdroj*<br/>
ID prostředku bitmapového prostředku.

*hIkona*<br/>
Zpracovat na ikonu, `CPictureHolder` ze které je objekt vytvořen.

*bVlastnictví převodu*<br/>
Označuje, zda objekt obrázku převezme vlastnictví objektu ikony.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bTransferOwnership* je TRUE, volající by neměl používat objekt ikony v žádném případě po vrácení tohoto volání. Pokud *bTransferOwnership* je FALSE, volající je zodpovědný za zajištění, že objekt ikony zůstane platný po dobu životnosti objektu obrázku.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile

Používá metasoubor k inicializaci objektu obrázku v . `CPictureHolder`

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*hmf*<br/>
Zpracovat metasoubor použitý k `CPictureHolder` vytvoření objektu.

*xExt*<br/>
X rozsah obrazu.

*yExt*<br/>
Rozsah y obrázku.

*bVlastnictví převodu*<br/>
Označuje, zda objekt obrázku převezme vlastnictví objektu metasouboru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bTransferOwnership* je TRUE, volající by neměl používat objekt metasouboru v žádném případě po vrácení tohoto volání. Pokud *bTransferOwnership* je FALSE, volající je zodpovědný za zajištění, že objekt metasouboru zůstane platný po dobu životnosti objektu obrázku.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPictureHolder::GetDisplayString

Načte řetězec, který se zobrazí v prohlížeči vlastností kontejneru.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odkaz na [CString,](../../atl-mfc-shared/reference/cstringt-class.md) který je držet řetězec zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je řetězec úspěšně načten; jinak 0.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch

Tato funkce vrátí ukazatel `CPictureHolder` na `IPictureDisp` rozhraní objektu.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPictureHolder` `IPictureDisp` rozhraní objektu.

### <a name="remarks"></a>Poznámky

Volající musí `Release` volat na tento ukazatel po dokončení s ním.

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPictureHolder::GetType

Označuje, zda je obrázek bitmapovým, metasouborem nebo ikonou.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota označující typ obrázku. Možné hodnoty a jejich význam jsou následující:

|Hodnota|Význam|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`objekt je unititialized.|
|PICTYPE_NONE|`CPictureHolder`objekt je prázdný.|
|PICTYPE_BITMAP|Obrázek je rastrový obrázek.|
|PICTYPE_METAFILE|Obrázek je metasoubor.|
|PICTYPE_ICON|Obrázek je ikona.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPictureHolder::m_pPict

Ukazatel na `CPictureHolder` `IPicture` rozhraní objektu.

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPictureHolder::Vykreslení

Vykreslí obrázek v obdélníku odkazuje *rcRender*.

```cpp
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zobrazení, ve kterém má být obrázek vykreslen.

*rcRender*<br/>
Obdélník, ve kterém má být obrázek vykreslen.

*rcWBounds*<br/>
Obdélník představující ohraničující obdélník objektu vykreslující obrázek. Pro ovládací prvek je tento obdélník parametr *emituje* přepsání [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch

Připojí objekt `CPictureHolder` k `IPictureDisp` rozhraní.

```cpp
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na `IPictureDisp` nové rozhraní.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder – třída](../../mfc/reference/cfontholder-class.md)
