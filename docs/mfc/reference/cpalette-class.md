---
title: CPalette – třída
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 83cd125fa7ab64aa39c606bc048022400d158e72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374761"
---
# <a name="cpalette-class"></a>CPalette – třída

Zapouzdřuje paletu barev systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Vytvoří `CPalette` objekt bez připojené palety Systému Windows. Před použitím je `CPalette` nutné objekt inicializovat jednou z funkcí inicializačního člena.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Nahradí položky v logické paletě identifikované objektem. `CPalette` Aplikace nemusí aktualizovat svou klientskou oblast, protože systém Windows okamžitě mapuje nové položky do systémové palety.|
|[CPalette::Vytvořitpolotónpaleta](#createhalftonepalette)|Vytvoří polotónovou paletu pro kontext zařízení a `CPalette` připojí ji k objektu.|
|[CPalette::CreatePalette](#createpalette)|Vytvoří paletu barev systému Windows `CPalette` a připojí ji k objektu.|
|[CPalette::FromHandle](#fromhandle)|Vrátí ukazatel na `CPalette` objekt, když je daný popisovač objektu palety systému Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Načte počet položek palety v logické paletě.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Vrátí index položky v logické paletě, která nejvíce odpovídá hodnotě barvy.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Načte rozsah položek palety v logické paletě.|
|[CPalette::Změna velikostiPaleta](#resizepalette)|Změní velikost logické palety určené `CPalette` objektem na zadaný počet položek.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Nastaví hodnoty barev A označí RGB v rozsahu položek v logické paletě.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CPalette::operátor HPALETTE](#operator_hpalette)|Vrátí hodnotu HPALETTE `CPalette`připojenou k rozhraní .|

## <a name="remarks"></a>Poznámky

Paleta poskytuje rozhraní mezi aplikací a barevným výstupním zařízením (například zobrazovacím zařízením). Rozhraní umožňuje aplikaci plně využít barevné schopnosti výstupního zařízení, aniž by vážně zasahovaly do barev zobrazených jinými aplikacemi. Systém Windows používá k určení použitých barev logickou paletu aplikace (seznam potřebných barev) a systémovou paletu (která definuje dostupné barvy).

Objekt `CPalette` poskytuje členské funkce pro manipulaci s paletou, na kterou objekt odkazuje. Vytvořte `CPalette` objekt a použijte jeho členské funkce k vytvoření skutečné palety, objektu rozhraní grafického zařízení (GDI) a k manipulaci s jeho položkami a dalšími vlastnostmi.

Další informace o `CPalette`použití naleznete v [tématu Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CGdi](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette::AnimatePalette

Nahradí položky v logické paletě `CPalette` připojené k objektu.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Určuje první položku v paletě, která má být animována.

*nPoložky výčtu*<br/>
Určuje počet položek v paletě, které mají být animovány.

*lpPaletteBarvy*<br/>
Odkazuje na prvního člena pole [struktur PALETTEENTRY,](/previous-versions/dd162769\(v=vs.85\)) který nahradí položky palety identifikované *položkami nStartIndex* a *nNumEntries*.

### <a name="remarks"></a>Poznámky

Pokud aplikace `AnimatePalette`volá , nemusí aktualizovat svou klientskou oblast, protože systém Windows okamžitě mapuje nové položky do systémové palety.

Funkce `AnimatePalette` změní pouze položky s příznakem `palPaletteEntry` PC_RESERVED nastaveným v odpovídajícím členu `CPalette` struktury [LOGPALETTE,](/windows/win32/api/wingdi/ns-wingdi-logpalette) který je připojen k objektu. Další informace o této struktuře naleznete v tématu LOGPALETTE v ksouboru Windows SDK.

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette::CPalette

Vytvoří `CPalette` objekt.

```
CPalette();
```

### <a name="remarks"></a>Poznámky

Objekt nemá žádnou připojenou `CreatePalette` paletu, dokud ji nezavoláte.

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::Vytvořitpolotónpaleta

Vytvoří polotónovou paletu pro kontext zařízení.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Identifikuje kontext zařízení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace by měla vytvořit polotónovou paletu, pokud je režim roztahování kontextu zařízení nastaven na HALFTONE. Paleta logických polotónů vrácená členovou funkcí [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) by pak měla být vybrána a realizována do kontextu zařízení před voláním funkce [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) nebo [StretchDIBits.](/windows/win32/api/wingdi/nf-wingdi-stretchdibits)

Další informace o souboru Windows `CreateHalftonePalette` `StretchDIBits`SDK naleznete v souboru Windows SDK.

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::CreatePalette

Inicializuje `CPalette` objekt vytvořením logické palety barev systému `CPalette` Windows a jejím připojením k objektu.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Odkazuje na strukturu [LOGPALETTE,](/windows/win32/api/wingdi/ns-wingdi-logpalette) která obsahuje informace o barvách v logické paletě.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace o `LOGPALETTE` struktuře naleznete v části Sada Windows SDK.

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>CPalette::FromHandle

Vrátí ukazatel na `CPalette` objekt, když je daný popisovač objektu palety systému Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parametry

*hPaleta*<br/>
Úchyt palety barev Windows GDI.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPalette` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CPalette` objekt ještě není připojen k paletě `CPalette` systému Windows, je vytvořen a připojen dočasný objekt. Tento `CPalette` dočasný objekt je platný pouze do příště aplikace má nečinnosti čas ve smyčce událostí, kdy jsou odstraněny všechny dočasné grafické objekty. Jinými slovy dočasný objekt je platný pouze při zpracování jedné zprávy okna.

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette::GetEntryCount

Volání této členské funkce načíst počet položek v dané logické palety.

```
int GetEntryCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v logické paletě.

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex

Vrátí index položky v logické paletě, který nejvíce odpovídá zadané hodnotě barvy.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Určuje barvu, která má být spárována.

### <a name="return-value"></a>Návratová hodnota

Index položky v logické paletě. Položka obsahuje barvu, která nejvíce odpovídá zadané barvě.

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette::GetPaletteEntries

Načte rozsah položek palety v logické paletě.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Určuje první položku v logické paletě, která má být načtena.

*nPoložky výčtu*<br/>
Určuje počet položek v logické paletě, které mají být načteny.

*lpPaletteBarvy*<br/>
Odkazuje na pole [palety](/previous-versions/dd162769\(v=vs.85\)) dat struktury přijímat položky palety. Pole musí obsahovat alespoň tolik datových struktur, kolik je určeno *nNumEntries*.

### <a name="return-value"></a>Návratová hodnota

Počet položek načtených z logické palety; 0, pokud se funkce nezdařila.

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::operátor HPALETTE

Pomocí tohoto operátoru získáte připojený popisovač GDI systému Windows objektu. `CPalette`

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu GDI systému Windows reprezentovaný objektem; `CPalette` jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HPALETTE.

Další informace o používání grafických objektů naleznete v článku [Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette::Změna velikostiPaleta

Změní velikost logické palety připojené `CPalette` k objektu na počet položek určených *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parametry

*nPoložky výčtu*<br/>
Určuje počet položek v paletě po jeho změněné velikosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla velikost palety úspěšně měkcí; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud aplikace `ResizePalette` volá ke zmenšení velikosti palety, položky zbývající v paletě velikosti se nezmění. Pokud aplikace `ResizePalette` volá pro zvětšení palety, další položky palety jsou nastaveny na černou (červené, zelené a modré hodnoty jsou všechny 0) a příznaky pro všechny další položky jsou nastaveny na 0.

Další informace o rozhraní `ResizePalette`API systému Windows naleznete v tématu [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) v sadě Windows SDK.

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::SetPaletteEntries

Nastaví hodnoty barev A označí RGB v rozsahu položek v logické paletě.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Určuje první položku v logické paletě, která má být nastavena.

*nPoložky výčtu*<br/>
Určuje počet položek v logické paletě, která má být nastavena.

*lpPaletteBarvy*<br/>
Odkazuje na pole [palety](/previous-versions/dd162769\(v=vs.85\)) dat struktury přijímat položky palety. Pole musí obsahovat alespoň tolik datových struktur, kolik je určeno *nNumEntries*.

### <a name="return-value"></a>Návratová hodnota

Počet položek nastavených v logické paletě; 0, pokud se funkce nezdařila.

### <a name="remarks"></a>Poznámky

Pokud je logická paleta vybrána do `SetPaletteEntries`kontextu zařízení při volání aplikace , změny se projeví, dokud aplikace nezavolá [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Další informace naleznete v tématu [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
