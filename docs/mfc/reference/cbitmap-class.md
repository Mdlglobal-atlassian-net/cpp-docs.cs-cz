---
title: CBitmap – – třída
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 7161a4cf4484b6cc9e76e6955de558ca6e9121ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418956"
---
# <a name="cbitmap-class"></a>CBitmap – – třída

Zapouzdřuje rastrový obrázek rozhraní Windows Graphics Device Interface (GDI) a poskytuje členské funkce pro manipulaci s bitmapou.

## <a name="syntax"></a>Syntaxe

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBitmap –:: CBitmap –](#cbitmap)|Vytvoří objekt `CBitmap`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBitmap –:: CreateBitmap](#createbitmap)|Inicializuje objekt pomocí rastrového obrázku závislého na zařízení, který má zadanou šířku, výšku a bitový vzor.|
|[CBitmap –:: CreateBitmapIndirect](#createbitmapindirect)|Inicializuje objekt pomocí rastrového obrázku se šířkou, výškou a bitovou vzorem (Pokud je zadaný) ve struktuře `BITMAP`.|
|[CBitmap –:: CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializuje objekt pomocí rastrového obrázku, aby byl kompatibilní se zadaným zařízením.|
|[CBitmap –:: CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializuje objekt pomocí hodící se rastrového obrázku, který je kompatibilní se zadaným zařízením.|
|[CBitmap –:: FromHandle](#fromhandle)|Vrátí ukazatel na objekt `CBitmap`, pokud je předána obslužná rutina `HBITMAP` rastrového obrázku systému Windows.|
|[CBitmap –:: getbitmapa](#getbitmap)|Vyplní strukturu `BITMAP` informacemi o bitmapě.|
|[CBitmap –:: GetBitmapBits](#getbitmapbits)|Zkopíruje bity zadaného rastrového obrázku do zadané vyrovnávací paměti.|
|[CBitmap –:: GetBitmapDimension](#getbitmapdimension)|Vrátí šířku a výšku rastrového obrázku. U výšky a šířky se předpokládá, že byla nastavena dříve pomocí členské funkce [SetBitmapDimension](#setbitmapdimension) .|
|[CBitmap –:: LoadBitmap](#loadbitmap)|Inicializuje objekt načtením pojmenovaného rastrového prostředku ze spustitelného souboru aplikace a připojením rastrového obrázku k objektu.|
|[CBitmap –:: LoadMappedBitmap](#loadmappedbitmap)|Načte rastrový obrázek a mapuje barvy na aktuální systémové barvy.|
|[CBitmap –:: LoadOEMBitmap](#loadoembitmap)|Inicializuje objekt načtením předdefinovaného rastrového obrázku systému Windows a připojením rastrového obrázku k objektu.|
|[CBitmap –:: SetBitmapBits](#setbitmapbits)|Nastaví bity rastrového obrázku na zadané bitové hodnoty.|
|[CBitmap –:: SetBitmapDimension](#setbitmapdimension)|Přiřadí šířku a výšku rastrového obrázku v 0,1 mm jednotek.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CBitmap –:: operator HBITMAP](#operator_hbitmap)|Vrátí popisovač systému Windows připojený k objektu `CBitmap`.|

## <a name="remarks"></a>Poznámky

Chcete-li použít objekt `CBitmap`, Sestavte objekt, připojte k němu popisovač rastrového obrázku s jednou z funkcí členů inicializace a pak zavolejte členské funkce objektu.

Další informace o použití grafických objektů, jako jsou `CBitmap`, naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cbitmap"></a>CBitmap –:: CBitmap –

Vytvoří objekt `CBitmap`.

```
CBitmap();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt musí být inicializován s jednou z funkcí členů inicializace.

##  <a name="createbitmap"></a>CBitmap –:: CreateBitmap

Inicializuje rastrový obrázek závislý na zařízení se zadanou šířkou, výškou a bitovým vzorem.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Určuje šířku rastrového obrázku (v pixelech).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v pixelech).

*nPlanes*<br/>
Určuje počet barevných rovin rastrového obrázku.

*nBitcount*<br/>
Určuje počet barevných bitů na pixel pro zobrazení.

*lpBits*<br/>
Odkazuje na pole bajtů, které obsahuje počáteční bitové hodnoty rastrového obrázku. Pokud má hodnotu NULL, nový rastrový obrázek zůstane Neinicializovaný.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pro barevný rastrový obrázek musí být parametr *nPlanes* nebo *nBitcount* nastavený na hodnotu 1. Pokud jsou oba parametry nastavené na 1, `CreateBitmap` vytvoří monochromatický rastrový obrázek.

I když rastr nemůže být pro zobrazovací zařízení vybraný přímo, dá se vybrat jako aktuální rastrový obrázek pro "kontext paměťového zařízení" pomocí funkce [CDC:: VybratObjekt](../../mfc/reference/cdc-class.md#selectobject) a zkopírování do jakéhokoli kompatibilního kontextu zařízení pomocí funkce [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) .

Až skončíte s objektem `CBitmap` vytvořeným funkcí `CreateBitmap`, nejdřív vyberte rastrový obrázek mimo kontext zařízení a pak odstraňte objekt `CBitmap`.

Další informace najdete v popisu pole `bmBits` ve struktuře `BITMAP`. Struktura [rastrového obrázku](/windows/win32/api/wingdi/ns-wingdi-bitmap) je popsána v rámci členské funkce [CBitmap –:: CreateBitmapIndirect](#createbitmapindirect) .

##  <a name="createbitmapindirect"></a>CBitmap –:: CreateBitmapIndirect

Inicializuje rastrový obrázek, který má šířku, výšku a bitový vzor (Pokud je zadaný) zadaný ve struktuře, na kterou odkazuje *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parametry

*lpBitmap*<br/>
Odkazuje na strukturu [rastrového obrázku](/windows/win32/api/wingdi/ns-wingdi-bitmap) , která obsahuje informace o rastrovém obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

I když rastr nelze vybrat přímo pro zobrazovací zařízení, lze jej vybrat jako aktuální rastrový obrázek pro kontext paměťového zařízení pomocí funkce [CDC:: VybratObjekt](../../mfc/reference/cdc-class.md#selectobject) a zkopírováním do jakéhokoli kompatibilního kontextu zařízení pomocí funkce [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) . (Funkce [CDC::P atblt](../../mfc/reference/cdc-class.md#patblt) může zkopírovat bitmapu pro aktuální štětec přímo do kontextu zobrazení zařízení.)

Pokud byla `BITMAP` struktura, na kterou odkazoval parametr *lpBitmap* , vyplněna pomocí funkce `GetObject`, nejsou bity rastrového obrázku zadány a rastrový obrázek není inicializovaný. Pro inicializaci rastrového obrázku může aplikace použít funkci, jako je například [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) , ke zkopírování bitů z rastrového obrázku určeného prvním parametrem `CGdiObject::GetObject` do rastrového obrázku vytvořeného `CreateBitmapIndirect`.

Až skončíte s objektem `CBitmap` vytvořeným pomocí funkce `CreateBitmapIndirect`, nejdřív vyberte rastrový obrázek mimo kontext zařízení a pak odstraňte objekt `CBitmap`.

##  <a name="createcompatiblebitmap"></a>CBitmap –:: CreateCompatibleBitmap

Inicializuje rastrový obrázek, který je kompatibilní se zařízením určeným *primárním řadičem domény*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Určuje kontext zařízení.

*nWidth*<br/>
Určuje šířku rastrového obrázku (v pixelech).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v pixelech).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rastr má stejný počet barevných rovin nebo stejný formát bitů na pixel jako zadaný kontext zařízení. Dá se vybrat jako aktuální rastrový obrázek pro všechna paměťová zařízení, která jsou kompatibilní s ovladačem, který je určený *primárním řadičem domény*.

Pokud je *primární řadič domény* kontextem paměťového zařízení, má vrácená bitmapa stejný formát jako aktuálně vybraná bitmapa v daném kontextu zařízení. "Kontext zařízení v paměti" je blok paměti, který představuje zobrazovací plochu. Dá se použít k přípravě imagí v paměti před jejich zkopírováním na skutečnou zobrazovací plochu kompatibilního zařízení.

Když se vytvoří kontext paměťového zařízení, GDI pro něj automaticky vybírá černobílý rastrový obrázek.

Vzhledem k tomu, že v kontextu zařízení barevné paměti může být vybrán buď barevný nebo monochromatický rastrový obrázek, formát rastrového obrázku vrácený funkcí `CreateCompatibleBitmap` není vždy stejný; Formát kompatibilního rastrového obrázku pro kontext zařízení, který není v paměti, je ale vždycky ve formátu zařízení.

Až skončíte s objektem `CBitmap` vytvořeným pomocí funkce `CreateCompatibleBitmap`, nejdřív vyberte rastrový obrázek mimo kontext zařízení a pak odstraňte objekt `CBitmap`.

##  <a name="creatediscardablebitmap"></a>CBitmap –:: CreateDiscardableBitmap

Inicializuje rastr pro vypuštění, který je kompatibilní s kontextem zařízení, který identifikuje *primární řadič domény*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Určuje kontext zařízení.

*nWidth*<br/>
Určuje šířku rastrového obrázku (v bitech).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v bitech).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rastr má stejný počet barevných rovin nebo stejný formát bitů na pixel jako zadaný kontext zařízení. Aplikace může tuto bitmapu vybrat jako aktuální rastrový obrázek pro paměťové zařízení, které je kompatibilní s ovladačem, který je určený *primárním řadičem domény*.

Systém Windows může zrušit rastrový obrázek vytvořený touto funkcí pouze v případě, že aplikace nebyla vybrána v kontextu zobrazení. Pokud systém Windows zahodí rastrový obrázek, když není vybrán, a aplikace se později pokusí o jeho výběr, vrátí funkce [CDC:: VybratObjekt](../../mfc/reference/cdc-class.md#selectobject) hodnotu null.

Až skončíte s objektem `CBitmap` vytvořeným pomocí funkce `CreateDiscardableBitmap`, nejdřív vyberte rastrový obrázek mimo kontext zařízení a pak odstraňte objekt `CBitmap`.

##  <a name="fromhandle"></a>CBitmap –:: FromHandle

Vrátí ukazatel na objekt `CBitmap`, pokud je předána obslužná rutina pro rastrový obrázek GDI systému Windows.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Určuje rastrový obrázek GDI systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CBitmap` v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt `CBitmap` již není k popisovači připojen, je vytvořen a připojen dočasný objekt `CBitmap`. Tento dočasný `CBitmap` objekt je platný pouze do okamžiku, kdy aplikace bude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to vyjádřit, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

##  <a name="getbitmap"></a>CBitmap –:: getbitmapa

Načte vlastnosti obrázku připojené bitmapy.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parametry

*pBitMap*<br/>
Ukazatel na [bitmapovou](/windows/win32/api/wingdi/ns-wingdi-bitmap) strukturu, která získá vlastnosti obrázku. Tento parametr nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="getbitmapbits"></a>CBitmap –:: GetBitmapBits

Zkopíruje bitový vzorek připojeného rastrového obrázku do zadané vyrovnávací paměti.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Počet bajtů, které mají být zkopírovány do vyrovnávací paměti.

*lpBits*<br/>
Ukazatel na vyrovnávací paměť, která obdrží rastrový obrázek.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů zkopírovaných do vyrovnávací paměti, pokud byla metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

K určení požadované velikosti vyrovnávací paměti použijte [CBitmap –:: GetBitmap](#getbitmap) .

##  <a name="getbitmapdimension"></a>CBitmap –:: GetBitmapDimension

Vrátí šířku a výšku rastrového obrázku.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka a výška rastrového obrázku měřená v 0,1 mm jednotek. Výška je ve `cy` členu objektu `CSize` a šířka je v `cx`m členu. Pokud Šířka a výška rastrového obrázku nebyly nastaveny pomocí `SetBitmapDimension`, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Předpokládá se, že výška a šířka se předem nastavily pomocí členské funkce [SetBitmapDimension](#setbitmapdimension) .

##  <a name="loadbitmap"></a>CBitmap –:: LoadBitmap

Načte prostředek rastrového obrázku s názvem *lpszResourceName* nebo identifikovaný číslem ID v *nIDResource* ze spustitelného souboru aplikace.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název prostředku rastrového obrázku.

*nIDResource*<br/>
Určuje číslo ID prostředku rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Načtený rastrový obrázek je připojen k objektu `CBitmap`.

Pokud rastr identifikovaný *lpszResourceName* neexistuje nebo pokud není dostatek paměti pro načtení rastrového obrázku, vrátí funkce hodnotu 0.

K odstranění rastrového obrázku načteného funkcí `LoadBitmap` lze použít funkci [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) , nebo destruktor `CBitmap` odstraní objekt.

> [!CAUTION]
>  Před odstraněním objektu se ujistěte, že není vybraný do kontextu zařízení.

Následující rastrové obrázky byly přidány do verzí Windows 3,1 a novějších:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Tyto bitmapy se nenašly v ovladačích zařízení pro Windows verze 3,0 a starší. Úplný seznam rastrových obrázků a zobrazení jejich vzhledu najdete v Windows SDK.

##  <a name="loadmappedbitmap"></a>CBitmap –:: LoadMappedBitmap

Zavolejte tuto členskou funkci pro načtení rastrového obrázku a namapujte barvy na aktuální systémové barvy.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
ID prostředku rastrového obrázku

*nFlags*<br/>
Příznak rastrového obrázku. Může být nula nebo CMB_MASKED.

*lpColorMap*<br/>
Ukazatel na strukturu `COLORMAP`, která obsahuje informace o barvách potřebné k mapování rastrových obrázků. Pokud má tento parametr hodnotu NULL, funkce použije výchozí mapu barev.

*nMapSize*<br/>
Počet map barev, na které odkazuje *lpColorMap*

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `LoadMappedBitmap` mapuje barvy běžně používané v glyfech tlačítek.

Informace o vytvoření mapované bitmapy naleznete v tématu funkce Windows Function [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) a struktura [ColorMap](/windows/win32/api/commctrl/ns-commctrl-colormap) v Windows SDK.

##  <a name="loadoembitmap"></a>CBitmap –:: LoadOEMBitmap

Načte předdefinovaný rastrový obrázek používaný systémem Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
ID předdefinovaného rastrového obrázku Windows Možné hodnoty jsou uvedeny níže v systému WINDOWS. Y

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Názvy rastrových obrázků začínajících OBM_OLD reprezentují bitmapy používané verzemi Windows staršími než 3,0.

Všimněte si, že konstanta OEMRESOURCE musí být definována před zahrnutím oken. H, aby bylo možné použít kteroukoli z **OBM_** konstanty.

##  <a name="operator_hbitmap"></a>CBitmap –:: operator HBITMAP

Tento operátor použijte k získání připojené obslužné rutiny Windows GDI objektu `CBitmap`.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, popisovač objektu GDI systému Windows reprezentovaného objektem `CBitmap`; jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu `HBITMAP`.

Další informace o použití grafických objektů naleznete v tématu [Graphics Objects](/windows/win32/gdi/graphic-objects) in Windows SDK.

##  <a name="setbitmapbits"></a>CBitmap –:: SetBitmapBits

Nastaví bity rastrového obrázku na bitové hodnoty zadané v *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Určuje počet bajtů, na které odkazuje *lpBits*.

*lpBits*<br/>
Odkazuje na pole bajtů obsahující hodnoty v pixelech, které mají být zkopírovány do objektu `CBitmap`. Aby bitmapa mohla správně vykreslit svůj obrázek, hodnoty by měly být formátovány tak, aby odpovídaly hodnotám výška, Šířka a Hloubka barvy, které byly zadány při vytvoření instance CBitmap –. Další informace najdete v tématu [CBitmap –:: CreateBitmap](#createbitmap).

### <a name="return-value"></a>Návratová hodnota

Počet bajtů použitých v nastavení bitů rastrových obrázků; 0, pokud se funkce nezdařila.

##  <a name="setbitmapdimension"></a>CBitmap –:: SetBitmapDimension

Přiřadí šířku a výšku rastrového obrázku v 0,1 mm jednotek.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Určuje šířku rastrového obrázku (v jednotkách 0,1 – milimetr).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v jednotkách 0,1 – milimetr).

### <a name="return-value"></a>Návratová hodnota

Předchozí rozměry rastrového obrázku. Vlastnost Height je v `cy` členské proměnné objektu `CSize` a šířka je v proměnné členu `cx`.

### <a name="remarks"></a>Poznámky

GDI nepoužívá tyto hodnoty s výjimkou, že je vrátí, když aplikace volá členskou funkci [GetBitmapDimension](#getbitmapdimension) .

## <a name="see-also"></a>Viz také

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
