---
title: CBitmap – třída
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
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352746"
---
# <a name="cbitmap-class"></a>CBitmap – třída

Zapouzdřuje bitmapu rozhraní grafického zařízení systému Windows (GDI) a poskytuje členské funkce pro manipulaci s bitmapou.

## <a name="syntax"></a>Syntaxe

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Vytvoří `CBitmap` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmap::Vytvořit bitmapu](#createbitmap)|Inicializuje objekt bitmapou paměti závislé na zařízení, která má zadanou šířku, výšku a bitový vzorek.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicializuje objekt bitmapou s šířkou, výškou a bitovým vzorkem `BITMAP` (pokud je zadán) daným ve struktuře.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializuje objekt bitmapou tak, aby byl kompatibilní se zadaným zařízením.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializuje objekt pomocí zahoditelné bitmapy, která je kompatibilní se zadaným zařízením.|
|[CBitmap::FromHandle](#fromhandle)|Vrátí ukazatel na `CBitmap` objekt, když daný `HBITMAP` popisovač bitmapy systému Windows.|
|[CBitmap::GetBitmap](#getbitmap)|Vyplní `BITMAP` strukturu informacemi o rastrové mapě.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Zkopíruje bity zadanébitové mapy do zadané vyrovnávací paměti.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Vrátí šířku a výšku bitmapy. Předpokládá se, že výška a šířka byly dříve nastaveny členovou funkcí [SetBitmapDimension.](#setbitmapdimension)|
|[CBitmap::LoadBitmap](#loadbitmap)|Inicializuje objekt načtením pojmenovanébitmapové prostředku ze spustitelného souboru aplikace a připojením bitmapy k objektu.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Načte bitmapu a mapuje barvy na aktuální systémové barvy.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicializuje objekt načtením předdefinované bitmapy systému Windows a připojením bitmapy k objektu.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Nastaví bitové bitmapy na zadané bitové hodnoty.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Přiřadí rastrový obrázek v jednotkách 0,1 milimetru šířku a výšku.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CBitmap::operátor HBITMAP](#operator_hbitmap)|Vrátí popisovač systému `CBitmap` Windows připojený k objektu.|

## <a name="remarks"></a>Poznámky

Chcete-li `CBitmap` použít objekt, vytvořte objekt, připojte k němu popisovač rastrového mapu pomocí jedné z členských funkcí inicializace a pak volejte členské funkce objektu.

Další informace o používání `CBitmap`grafických objektů například [v tématu Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CGdi](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>CBitmap::CBitmap

Vytvoří `CBitmap` objekt.

```
CBitmap();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt musí být inicializován jednou z inicializačních členských funkcí.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>CBitmap::Vytvořit bitmapu

Inicializuje bitmapu paměti závislé na zařízení, která má zadanou šířku, výšku a bitový vzorek.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
Určuje šířku (v obrazových bodech) bitmapy.

*nVýška*<br/>
Určuje výšku (v obrazových bodech) bitmapy.

*nLetadla*<br/>
Určuje počet barevných rovin rastrového obrázku.

*nPočet bitů*<br/>
Určuje počet barevných bitů na obrazový bod zobrazení.

*lpBity*<br/>
Odkazuje na pole bajtů, které obsahuje počáteční bitové bitové hodnoty. Pokud je null, nový bitmap je ponechána bez inicializována.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

U barevné bitmapy by měl být parametr *nPlanes* nebo *nBitcount* nastaven na hodnotu 1. Pokud jsou oba tyto parametry `CreateBitmap` nastaveny na hodnotu 1, vytvoří monochromatický rastrový obrázek.

Přestože bitmapu nelze přímo vybrat pro zobrazovací zařízení, lze ji vybrat jako aktuální bitmapu pro "kontext paměťového zařízení" pomocí [cdc::SelectObject](../../mfc/reference/cdc-class.md#selectobject) a zkopírovat do libovolného kontextu kompatibilního zařízení pomocí funkce [CDC::BitBlt.](../../mfc/reference/cdc-class.md#bitblt)

Po dokončení s `CBitmap` objektem `CreateBitmap` vytvořeným funkcí nejprve vyberte bitmapu z `CBitmap` kontextu zařízení a odstraňte objekt.

Další informace naleznete v popisu `bmBits` pole `BITMAP` ve struktuře. Struktura [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) je popsána v rámci členské funkce [CBitmap::CreateBitmapIndirect.](#createbitmapindirect)

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect

Inicializuje bitmapu, která má šířku, výšku a bitový vzorek (pokud je zadán) daný ve struktuře, na kterou poukazuje *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parametry

*lpBitmap*<br/>
Odkazuje na strukturu [BITMAP,](/windows/win32/api/wingdi/ns-wingdi-bitmap) která obsahuje informace o bitmapě.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Přestože bitmapu nelze přímo vybrat pro zobrazovací zařízení, lze ji vybrat jako aktuální bitmapu pro kontext paměťového zařízení pomocí [cdc::SelectObject](../../mfc/reference/cdc-class.md#selectobject) a zkopírovat do libovolného kontextu kompatibilního zařízení pomocí funkce [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [CDC::StretchBlt.](../../mfc/reference/cdc-class.md#stretchblt) (Funkce [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) může zkopírovat bitmapu pro aktuální stopu přímo do kontextu zobrazovacího zařízení.)

Pokud `BITMAP` byla struktura, na kterou odkazovává parametr `GetObject` *lpBitmap* byla vyplněna pomocí funkce, nejsou určeny bitové bitmapy a bitmapa je neinicializována. Chcete-li inicializovat bitmapu, aplikace může použít funkci, jako je [NAPŘÍKLAD CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) ke kopírování bitů z bitmapy identifikované prvním parametrem `CGdiObject::GetObject` bitmapy vytvořené `CreateBitmapIndirect`aplikací .

Po dokončení s `CBitmap` objektem `CreateBitmapIndirect` vytvořeným pomocí funkce nejprve vyberte bitmapu `CBitmap` z kontextu zařízení a odstraňte objekt.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap

Inicializuje bitmapu, která je kompatibilní se zařízením určeným *programem pDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Určuje kontext zařízení.

*nŠířka*<br/>
Určuje šířku (v obrazových bodech) bitmapy.

*nVýška*<br/>
Určuje výšku (v obrazových bodech) bitmapy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Bitmapa má stejný počet barevných rovin nebo stejný formát bitů na pixel jako zadaný kontext zařízení. Lze jej vybrat jako aktuální bitmapu pro libovolné paměťové zařízení, které je kompatibilní s nástrojem *pDC*.

Pokud *je pDC* kontext paměťového zařízení, vrácená bitmapa má stejný formát jako aktuálně vybraná bitmapa v tomto kontextu zařízení. "Kontext paměťového zařízení" je blok paměti, který představuje povrch zobrazení. Lze jej použít k přípravě obrázků v paměti před jejich zkopírováním na skutečný povrch displeje kompatibilního zařízení.

Když je vytvořen kontext paměťového zařízení, GDI automaticky vybere monochromatický stock rastrový obrázek pro něj.

Vzhledem k tomu, že kontext zařízení s barevnou pamětí může mít vybranou barevnou nebo monochromatickou bitmapu, formát rastrového obrázku vráceného `CreateCompatibleBitmap` funkcí není vždy stejný; formát kompatibilní bitmapy pro kontext zařízení bez paměti je však vždy ve formátu zařízení.

Po dokončení s `CBitmap` objektem `CreateCompatibleBitmap` vytvořeným pomocí funkce nejprve vyberte bitmapu `CBitmap` z kontextu zařízení a odstraňte objekt.

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap

Inicializuje zahoditelný bitmapu, která je kompatibilní s kontextem zařízení identifikovaným *primárním řadičem domény*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Určuje kontext zařízení.

*nŠířka*<br/>
Určuje šířku (v bitech) bitmapy.

*nVýška*<br/>
Určuje výšku (v bitech) bitmapy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Bitmapa má stejný počet barevných rovin nebo stejný formát bitů na pixel jako zadaný kontext zařízení. Aplikace může vybrat tuto bitmapu jako aktuální bitmapu pro paměťové zařízení, které je kompatibilní s bitkou určenou *programem pDC*.

Systém Windows může zahodit bitmapu vytvořenou touto funkcí pouze v případě, že ji aplikace nevybrala do kontextu zobrazení. Pokud systém Windows zahodí bitmapu, pokud není vybrána a aplikace se ji později pokusí vybrat, vrátí funkce [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) hodnotu NULL.

Po dokončení s `CBitmap` objektem `CreateDiscardableBitmap` vytvořeným pomocí funkce nejprve vyberte bitmapu `CBitmap` z kontextu zařízení a odstraňte objekt.

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap::FromHandle

Vrátí ukazatel na `CBitmap` objekt, když daný popisovač bitmapy GDI systému Windows.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Určuje bitmapu GDI systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CBitmap` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CBitmap` objekt ještě není připojen k popisovač, dočasný `CBitmap` objekt je vytvořen a připojen. Tento `CBitmap` dočasný objekt je platný pouze do příště aplikace má nečinnosti čas ve smyčce událostí, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to říct, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>CBitmap::GetBitmap

Načte vlastnosti obrazu pro připojenou bitmapu.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parametry

*pBitMap*<br/>
Ukazatel na strukturu [BITMAP,](/windows/win32/api/wingdi/ns-wingdi-bitmap) která obdrží vlastnosti obrazu. Tento parametr nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>CBitmap::GetBitmapBits

Zkopíruje bitový vzorek připojené bitmapy do zadané vyrovnávací paměti.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Počet bajtů, které mají být zkopírovány do vyrovnávací paměti.

*lpBity*<br/>
Ukazatel na vyrovnávací paměť, která obdrží bitmapu.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů zkopírovaných do vyrovnávací paměti, pokud byla metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Použijte [CBitmap::GetBitmap](#getbitmap) k určení požadované velikosti vyrovnávací paměti.

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension

Vrátí šířku a výšku bitmapy.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka a výška bitmapy měřená v jednotkách 0,1 milimetru. Výška je `cy` v člen `CSize` objektu a šířka `cx` je v členu. Pokud šířka a výška bitmapy `SetBitmapDimension`nebyly nastaveny pomocí , vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Předpokládá se, že výška a šířka byly nastaveny dříve pomocí členské funkce [SetBitmapDimension.](#setbitmapdimension)

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>CBitmap::LoadBitmap

Načte bitmapový prostředek pojmenovaný *lpszResourceName* nebo identifikovaný číslem ID v *nIDResource* ze spustitelného souboru aplikace.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název bitmapového prostředku.

*nIDZdroj*<br/>
Určuje číslo ID prostředku bitmapového prostředku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Načtená bitmapa je připojena k objektu. `CBitmap`

Pokud bitmapa identifikovaná *lpszResourceName* neexistuje nebo pokud není dostatek paměti pro načtení bitmapy, funkce vrátí 0.

Funkci [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) můžete použít k odstranění bitmapy `LoadBitmap` načtené `CBitmap` funkcí, nebo destruktor odstraní objekt za vás.

> [!CAUTION]
> Před odstraněním objektu se ujistěte, že není vybrán do kontextu zařízení.

Do verzí systému Windows 3.1 a novějších byly přidány následující bitmapy:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Tyto bitmapy nejsou nalezeny v ovladačích zařízení pro windows verze 3.0 a starší. Úplný seznam bitmap a zobrazení jejich vzhledu naleznete v části Sada Windows SDK.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap

Volání této členské funkce načíst bitmapu a mapovat barvy na aktuální systémové barvy.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
ID bitmapového prostředku.

*nPříznaky*<br/>
Příznak pro rastrový obrázek. Může být nula nebo CMB_MASKED.

*lpColorMap*<br/>
Ukazatel na `COLORMAP` strukturu, která obsahuje informace o barvách potřebné k mapování bitmap. Pokud je tento parametr NULL, funkce použije výchozí barevnou mapu.

*nVelikost mapy*<br/>
Počet barevných map, na které poukazuje *lpColorMap*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím `LoadMappedBitmap` nastavení mapuje barvy běžně používané v glyfech tlačítek.

Informace o vytvoření mapované rastrové mapy naleznete v tématu Funkce systému Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) a struktura [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) v sadě Windows SDK.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap

Načte předdefinovanou bitmapu používanou systémem Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
Číslo ID předdefinované bitmapy systému Windows. Možné hodnoty jsou uvedeny níže z windows. H:

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

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Názvy bitmap začínající OBM_OLD představují bitmapy používané verzemi systému Windows před verzí 3.0.

Všimněte si, že konstantní OEMRESOURCE musí být definovány před zahrnutím systému WINDOWS. H, aby bylo možné použít některou z **OBM_** konstant.

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap::operátor HBITMAP

Pomocí tohoto operátoru získáte připojený popisovač GDI systému Windows objektu. `CBitmap`

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu GDI systému Windows reprezentovaný objektem; `CBitmap` jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, `HBITMAP` který podporuje přímé použití objektu.

Další informace o používání grafických objektů naleznete v [tématu Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>CBitmap::SetBitmapBits

Nastaví bity bitmapy na bitové hodnoty dané *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Určuje počet bajtů, na které je odkaz *lpBits*.

*lpBity*<br/>
Odkazuje na pole BYTE, které obsahuje hodnoty obrazových bodů, které mají být zkopírovány do objektu. `CBitmap` Aby bitmapa mohla správně vykreslit svůj obraz, měly by být hodnoty formátovány tak, aby odpovídaly hodnotám výšky, šířky a hloubky barev, které byly zadány při vytvoření instance CBitmap. Další informace naleznete v tématu [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Návratová hodnota

Počet bajtů použitých při nastavování bitmapových bitů; 0, pokud funkce selže.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension

Přiřadí rastrový obrázek v jednotkách 0,1 milimetru šířku a výšku.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
Určuje šířku bitmapy (v jednotkách 0,1 milimetru).

*nVýška*<br/>
Určuje výšku bitmapy (v jednotkách 0,1 milimetru).

### <a name="return-value"></a>Návratová hodnota

Předchozí bitmapové dimenze. Výška je `cy` v členské `CSize` proměnné objektu a `cx` šířka je v proměnné člena.

### <a name="remarks"></a>Poznámky

GDI nepoužívá tyto hodnoty s výjimkou k jejich vrácení, když aplikace volá členská funkce [GetBitmapDimension.](#getbitmapdimension)

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
