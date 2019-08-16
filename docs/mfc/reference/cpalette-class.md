---
title: CPalette – – třída
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
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503001"
---
# <a name="cpalette-class"></a>CPalette – – třída

Zapouzdřuje paletu barev systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPalette –:: CPalette –](#cpalette)|`CPalette` Vytvoří objekt bez připojené palety Windows. Je nutné inicializovat `CPalette` objekt jednou z funkcí členů inicializace předtím, než je možné jej použít.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPalette –:: AnimatePalette](#animatepalette)|Nahradí položky v logické paletě identifikované `CPalette` objektem. Aplikace nemusí aktualizovat její klientskou oblast, protože Windows mapuje nové položky do systémové palety hned.|
|[CPalette –:: CreateHalftonePalette](#createhalftonepalette)|Vytvoří paletu polotónů pro kontext zařízení a připojí ho k `CPalette` objektu.|
|[CPalette –:: CreatePalette](#createpalette)|Vytvoří barevnou paletu Windows a připojí ji k `CPalette` objektu.|
|[CPalette –:: FromHandle](#fromhandle)|Vrací ukazatel na `CPalette` objekt, pokud je předána popisovač objektu palety systému Windows.|
|[CPalette::GetEntryCount](#getentrycount)|Načte počet položek palety v logické paletě.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Vrátí index záznamu v logické paletě, který nejlépe odpovídá hodnotě barvy.|
|[CPalette –:: GetPaletteEntries](#getpaletteentries)|Načte rozsah položek palety v logické paletě.|
|[CPalette –:: ResizePalette](#resizepalette)|Změní velikost logické palety určené `CPalette` objektem na zadaný počet položek.|
|[CPalette –:: SetPaletteEntries](#setpaletteentries)|Nastaví hodnoty barev RGB a příznaky v rozsahu položek v logické paletě.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CPalette –:: operator HPALETTE](#operator_hpalette)|Vrátí HPALETTE připojené k `CPalette`.|

## <a name="remarks"></a>Poznámky

Paleta poskytuje rozhraní mezi aplikací a barevným výstupním zařízením (například zobrazovací zařízení). Rozhraní umožňuje aplikaci plně využít možnosti barev výstupního zařízení bez závažného rušivého vlivu na barvy zobrazené jinými aplikacemi. Systém Windows používá logickou paletu aplikace (seznam potřebných barev) a systémovou paletu (která definuje dostupné barvy) k určení použitých barev.

`CPalette` Objekt poskytuje členské funkce pro manipulaci s paletou, na kterou je odkazováno pomocí objektu. Sestavte `CPalette` objekt a pomocí jeho členských funkcí vytvořte vlastní paletu, objekt rozhraní GDI (Graphics Device Interface) a manipulaci s jeho položkami a dalšími vlastnostmi.

Další informace o použití `CPalette`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="animatepalette"></a>CPalette –:: AnimatePalette

Nahradí položky v logické paletě připojené k `CPalette` objektu.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Určuje první položku v paletě, která se má animovat.

*nNumEntries*<br/>
Určuje počet položek v paletě, které mají být animovány.

*lpPaletteColors*<br/>
Odkazuje na prvního člena pole struktur [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) , aby nahradil položky palety identifikované *nStartIndex* a *nNumEntries*.

### <a name="remarks"></a>Poznámky

Při volání `AnimatePalette`aplikace není nutné aktualizovat její klientskou oblast, protože systém Windows provede okamžité mapování nových položek do systémové palety.

Funkce bude měnit pouze položky s příznakem PC_RESERVED nastaveným v odpovídajícím `palPaletteEntry` členu struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , která je připojena k `CPalette` objektu. `AnimatePalette` Další informace o této struktuře naleznete v tématu LOGPALETTE v Windows SDK.

##  <a name="cpalette"></a>CPalette –:: CPalette –

`CPalette` Vytvoří objekt.

```
CPalette();
```

### <a name="remarks"></a>Poznámky

Objekt nemá připojenou paletu, dokud nebudete volat `CreatePalette` , aby se připojila jedna.

##  <a name="createhalftonepalette"></a>CPalette –:: CreateHalftonePalette

Vytvoří paletu polotónů pro kontext zařízení.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Identifikuje kontext zařízení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace by měla vytvořit polotónovou paletu, když je režim roztažení kontextu zařízení nastaven na polotón. Paleta logického polotónu vrácená členskou funkcí [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) by měla být vybrána a realizována do kontextu zařízení před voláním funkce [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) nebo [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) .

Další informace o `CreateHalftonePalette` a `StretchDIBits`najdete v Windows SDK.

##  <a name="createpalette"></a>CPalette –:: CreatePalette

Inicializuje objekt vytvořením logické palety barev systému Windows a jeho připojením `CPalette` k objektu. `CPalette`

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parametry

*lpLogPalette*<br/>
Odkazuje na strukturu [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , která obsahuje informace o barvách v logické paletě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace o `LOGPALETTE` struktuře najdete v Windows SDK.

##  <a name="fromhandle"></a>CPalette –:: FromHandle

Vrací ukazatel na `CPalette` objekt, pokud je předána popisovač objektu palety systému Windows.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parametry

*hPalette*<br/>
Popisovač palety barev Windows GDI.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPalette` objekt v případě úspěchu; jinak null.

### <a name="remarks"></a>Poznámky

Pokud objekt již není připojen k paletě systému Windows, je vytvořen a `CPalette` připojen dočasný objekt. `CPalette` Tento dočasný `CPalette` objekt je platný pouze do příštího okamžiku, kdy aplikace nebude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Jinými slovy, dočasný objekt je platný pouze během zpracování jedné zprávy okna.

##  <a name="getentrycount"></a>CPalette –:: GetEntryCount

Zavolejte tuto členskou funkci pro načtení počtu položek v dané logické paletě.

```
int GetEntryCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v logické paletě.

##  <a name="getnearestpaletteindex"></a>CPalette –:: GetNearestPaletteIndex

Vrátí index záznamu v logické paletě, který nejlépe odpovídá zadané hodnotě barvy.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Určuje barvu, která má být shodná.

### <a name="return-value"></a>Návratová hodnota

Index položky v logické paletě. Položka obsahuje barvu, která téměř odpovídá zadané barvě.

##  <a name="getpaletteentries"></a>CPalette –:: GetPaletteEntries

Načte rozsah položek palety v logické paletě.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Určuje první položku v logické paletě, která se má načíst.

*nNumEntries*<br/>
Určuje počet položek v logické paletě, která se má načíst.

*lpPaletteColors*<br/>
Odkazuje na pole [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) datových struktur pro příjem položek palety. Pole musí obsahovat alespoň tolik datových struktur, jak Určuje *nNumEntries*.

### <a name="return-value"></a>Návratová hodnota

Počet položek načtených z logické palety; 0, pokud se funkce nezdařila.

##  <a name="operator_hpalette"></a>CPalette –:: operator HPALETTE

Tento operátor použijte k získání připojené obslužné rutiny `CPalette` Windows GDI objektu.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, popisovač objektu GDI systému Windows reprezentovaný `CPalette` objektem; v opačném případě hodnota null.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HPALETTE.

Další informace o použití grafických objektů naleznete v článku [grafické objekty](/windows/win32/gdi/graphic-objects) v Windows SDK.

##  <a name="resizepalette"></a>CPalette –:: ResizePalette

Změní velikost logické palety připojené k `CPalette` objektu na počet položek určených parametrem *nNumEntries*.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parametry

*nNumEntries*<br/>
Určuje počet položek v paletě po změně velikosti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se úspěšně změnila velikost palety; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud aplikace zavolá `ResizePalette` ke zmenšení velikosti palety, položky zbývající v paletě se změněnou velikostí se nezmění. Pokud aplikace volá `ResizePalette` zvětšení palety, jsou další položky palety nastaveny na černou (hodnoty červené, zelené a modré jsou všechny 0) a příznaky všech dalších položek jsou nastaveny na hodnotu 0.

Další informace o rozhraní API `ResizePalette`systému Windows naleznete v tématu [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) v Windows SDK.

##  <a name="setpaletteentries"></a>CPalette –:: SetPaletteEntries

Nastaví hodnoty barev RGB a příznaky v rozsahu položek v logické paletě.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parametry

*nStartIndex*<br/>
Určuje první položku v logické paletě, která se má nastavit.

*nNumEntries*<br/>
Určuje počet položek v logické paletě, která se má nastavit.

*lpPaletteColors*<br/>
Odkazuje na pole [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) datových struktur pro příjem položek palety. Pole musí obsahovat alespoň tolik datových struktur, jak Určuje *nNumEntries*.

### <a name="return-value"></a>Návratová hodnota

Počet položek nastavených v logické paletě; 0, pokud se funkce nezdařila.

### <a name="remarks"></a>Poznámky

Pokud je logická paleta vybrána v kontextu zařízení při volání `SetPaletteEntries`aplikace, změny se projeví až poté, co aplikace volá metodu [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).

Další informace najdete v tématu [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) v Windows SDK.

## <a name="see-also"></a>Viz také:

[DIBLOOK Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPalette –:: GetPaletteEntries](#getpaletteentries)<br/>
[CPalette –:: SetPaletteEntries](#setpaletteentries)
