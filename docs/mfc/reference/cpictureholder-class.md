---
title: CPictureHolder Class
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
ms.openlocfilehash: 5386240114550826e4bf557b63310a91590afb55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284213"
---
# <a name="cpictureholder-class"></a>CPictureHolder Class

Implementuje vlastnost obrázku, který umožňuje uživateli zobrazit obrázek v ovládacím prvku.

## <a name="syntax"></a>Syntaxe

```
class CPictureHolder
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Vytvoří `CPictureHolder` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Vytvoří prázdnou `CPictureHolder` objektu.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Vytvoří `CPictureHolder` objekt z bitmapy.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Vytvoří `CPictureHolder` objekt z ikony.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Vytvoří `CPictureHolder` objekt z metasouboru.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Načte řetězec zobrazený v prohlížeči vlastností ovládacího prvku kontejneru.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Vrátí `CPictureHolder` objektu `IDispatch` rozhraní.|
|[CPictureHolder::GetType](#gettype)|Určuje, zda `CPictureHolder` je objekt rastrový obrázek, metasoubor nebo ikonu.|
|[CPictureHolder::Render](#render)|Vykreslí obrázek.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Nastaví `CPictureHolder` objektu `IDispatch` rozhraní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Ukazatel na objekt obrázku.|

## <a name="remarks"></a>Poznámky

`CPictureHolder` nemá základní třídu.

Pomocí uložených vlastností obrázků vývojář může určit rastrový obrázek, ikona nebo metasoubor pro zobrazení.

Informace o vytvoření vlastnosti vlastního obrázku, najdete v článku [knihovny MFC – ovládací prvky ActiveX: Použití obrázků v ovládacím prvku ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CPictureHolder`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

##  <a name="cpictureholder"></a>  CPictureHolder::CPictureHolder

Vytvoří `CPictureHolder` objektu.

```
CPictureHolder();
```

##  <a name="createempty"></a>  CPictureHolder::CreateEmpty

Vytvoří prázdnou `CPictureHolder` objektu a připojí ji k `IPicture` rozhraní.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.

##  <a name="createfrombitmap"></a>  CPictureHolder::CreateFromBitmap

Rastrový obrázek používá k inicializaci objektu na obrázku `CPictureHolder`.

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

*idResource*<br/>
ID prostředku prostředku rastrového obrázku.

*pBitmap*<br/>
Ukazatel [cbitmap –](../../mfc/reference/cbitmap-class.md) objektu.

*pPal*<br/>
Ukazatel [cpalette –](../../mfc/reference/cpalette-class.md) objektu.

*bTransferOwnership*<br/>
Označuje, zda objekt obrázek bude trvat vlastnictví objektů rastrového obrázku a palety.

*hbm*<br/>
Zpracování do bitmapy, ze kterého `CPictureHolder` je vytvořen objekt.

*hpal*<br/>
Popisovač na paletě používané k vykreslování rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bTransferOwnership* má hodnotu TRUE, volající by neměly používat rastrový obrázek nebo vrátí objekt palety nijak po tomto volání. Pokud *bTransferOwnership* má hodnotu FALSE, volající zodpovídá za to, že rastrového obrázku a paleta objektů jsou dál platné po dobu životnosti objektu obrázku.

##  <a name="createfromicon"></a>  CPictureHolder::CreateFromIcon

Používá ikony k inicializaci objektu na obrázku `CPictureHolder`.

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*idResource*<br/>
ID prostředku prostředku rastrového obrázku.

*hIcon*<br/>
Zpracování na ikonu, ze kterého `CPictureHolder` je vytvořen objekt.

*bTransferOwnership*<br/>
Označuje, zda objekt obrázek bude převzít vlastnictví objektu ikona.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bTransferOwnership* má hodnotu TRUE, volající by neměl ikona objektu užívat žádným způsobem po tomto volání vrátí. Pokud *bTransferOwnership* má hodnotu FALSE, volající zodpovídá za to, že zůstane ikona objektu platný po dobu životnosti objektu obrázku.

##  <a name="createfrommetafile"></a>  CPictureHolder::CreateFromMetafile

Používá metasoubor k inicializaci objektu na obrázku `CPictureHolder`.

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parametry

*hmf*<br/>
Zpracování na metasoubor použitý k vytvoření `CPictureHolder` objektu.

*xExt*<br/>
X rozsahu obrázku.

*yExt*<br/>
Y rozsahu obrázku.

*bTransferOwnership*<br/>
Určuje, zda objekt obrázek bude převzít vlastnictví objektu metasouboru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt je úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bTransferOwnership* má hodnotu TRUE, volající by neměl objekt metasoubor užívat žádným způsobem po tomto volání vrátí. Pokud *bTransferOwnership* má hodnotu FALSE, volající zodpovídá za to, že objekt metasoubor zůstane platný po dobu životnosti objektu obrázku.

##  <a name="getdisplaystring"></a>  CPictureHolder::GetDisplayString

Načte řetězec, který se zobrazí v prohlížeči vlastností kontejneru.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odkaz [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který je pro uložení řetězce zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud řetězec je úspěšně načíst. jinak 0.

##  <a name="getpicturedispatch"></a>  CPictureHolder::GetPictureDispatch

Tato funkce vrací ukazatel `CPictureHolder` objektu `IPictureDisp` rozhraní.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CPictureHolder` objektu `IPictureDisp` rozhraní.

### <a name="remarks"></a>Poznámky

Volající musí volat `Release` na tento ukazatel po jeho dokončení.

##  <a name="gettype"></a>  CPictureHolder::GetType

Označuje, zda je na obrázku rastrový obrázek, metafile nebo ikonu.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota určující typ obrázku. Možné hodnoty a jejich význam jsou následující:

|Hodnota|Význam|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder` objekt je unititialized.|
|PICTYPE_NONE|`CPictureHolder` objekt je prázdný.|
|PICTYPE_BITMAP|Obrázek je rastrový obrázek.|
|PICTYPE_METAFILE|Obrázek je metasouboru.|
|PICTYPE_ICON|Obrázek je ikona.|

##  <a name="m_ppict"></a>  CPictureHolder::m_pPict

Ukazatel `CPictureHolder` objektu `IPicture` rozhraní.

```
LPPICTURE m_pPict;
```

##  <a name="render"></a>  CPictureHolder::Render

Vykreslí obrázek v obdélníku odkazuje *rcRender*.

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontextu zobrazení, ve kterém má být vykreslen na obrázku.

*rcRender*<br/>
Obdélník, ve kterém má být vykreslen na obrázku.

*rcWBounds*<br/>
Obdélník představující ohraničující obdélník objekt vykreslování obrázku. Pro ovládací prvek, je tento obdélník *rcBounds* byl předán parametr přepsání [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

##  <a name="setpicturedispatch"></a>  CPictureHolder::SetPictureDispatch

Připojuje `CPictureHolder` do objektu `IPictureDisp` rozhraní.

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
Ukazatel na novou `IPictureDisp` rozhraní.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder – třída](../../mfc/reference/cfontholder-class.md)
