---
title: Cbrush – třída
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: f2a2e385a9f210b3644d7fade00b72c4befa47ef
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778868"
---
# <a name="cbrush-class"></a>Cbrush – třída

Zapouzdřuje štětec rozhraní GDI systému Windows grafiky zařízení.

## <a name="syntax"></a>Syntaxe

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Vytvoří `CBrush` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicializuje štětce styl, barvu a vzoru určenému v [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury.|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicializuje štětcem pomocí vzoru určené bitmap nezávislých na zařízení (DIB).|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicializuje se zadanému vzoru šrafované a barvou štětce.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicializuje štětcem pomocí vzoru určené rastrový obrázek.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicializuje zadaný plnou barvou štětce.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Vytvoří štětec, který je výchozí barva systému.|
|[CBrush::FromHandle](#fromhandle)|Vrací ukazatel na `CBrush` objektu, když je zadaný popisovač Windows `HBRUSH` objektu.|
|[CBrush::GetLogBrush](#getlogbrush)|Získá [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CBrush::operator HBRUSH](#operator_hbrush)|Vrátí popisovač Windows připojené k `CBrush` objektu.|

## <a name="remarks"></a>Poznámky

Použití `CBrush` objektu, sestavit `CBrush` objektu a předejte jej do libovolné `CDC` členskou funkci, která vyžaduje štětce.

Štětce může být plná, zasílána nebo vzorované.

Další informace o `CBrush`, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cbrush"></a>  CBrush::CBrush

Vytvoří `CBrush` objektu.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Určuje barvu popředí štětce jako barva RGB. Pokud je zasílána štětec, tento parametr určuje barvu šrafování.

*nIndex*<br/>
Určuje styl šrafování štětce. To může být jedna z následujících hodnot:

- HS_BDIAGONAL Šrafování dolů (zleva doprava) na 45 stupňů

- HS_CROSS vodorovné a svislé mřížkovaný

- HS_DIAGCROSS šrafování na 45 stupňů

- Nahoru HS_FDIAGONAL šrafování (zleva doprava) na 45 stupňů

- Vodorovné HS_HORIZONTAL šrafování

- Svislé HS_VERTICAL šrafování

*pBitmap*<br/>
Odkazuje `CBitmap` objekt, který určuje, které jsou vykreslovány štětec rastrový obrázek.

### <a name="remarks"></a>Poznámky

`CBrush` má čtyři přetížené konstruktory. Konstruktor bez argumentů vytvoří neinicializované `CBrush` objekt, který musí být inicializován před jeho použitím.

Pokud použijete konstruktor bez argumentů, musí inicializovat výsledný `CBrush` objekt s [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), nebo [CreateDIBPatternBrush](#createdibpatternbrush). Pokud použijete jeden z konstruktorů, které přebírá argumenty, pak žádné další inicializace je nezbytné. Konstruktory s argumenty může vyvolat výjimku, pokud nedojde k chybám, když bude vždy úspěšné konstruktor bez argumentů.

Konstruktor s jedním [COLORREF](/windows/desktop/gdi/colorref) parametru sestaví štětec určenou barvou. Barva určuje hodnota RGB a může být zkonstruovaný pomocí RGB – makro v systému WINDOWS. H.

Konstruktor se dvěma parametry vytvoří štětce šrafování. *NIndex* parametr určuje index šrafované vzor. *CrColor* parametr určuje barvu.

Konstruktor `CBitmap` parametru sestaví vzorkem štětce. Tento parametr identifikuje rastrový obrázek. Rastrový obrázek se předpokládá, že byly vytvořeny pomocí [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), nebo [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimální velikost rastrového obrázku použije vzorek výplně je 8 x 8 pixelů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect

Inicializuje stopy s styl, barvu a vzoru určenému v [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury.

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parametry

*lpLogBrush*<br/>
Odkazuje [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) strukturu, která obsahuje informace o stopy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Štětec je následně vybrat jako aktuální štětec pro jakýkoli kontext zařízení.

Štětce vytvořené pomocí (1 roviny, 1 bitů na pixel) monochromatický rastrový obrázek je vykreslen aktuální barvy textu a pozadí. Aktuální barvou textu bude vykreslen pixelů reprezentována bit nastaven na hodnotu 0. Aktuální barvou pozadí bude vykreslen pixelů reprezentována bit nastaven na hodnotu 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

Inicializuje štětce se vzorem určené bitmap nezávislých na zařízení (DIB).

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>Parametry

*hPackedDIB*<br/>
Určuje objekt globální paměť obsahující komprimovat komprimovaný objekt bitmap nezávislých na zařízení (DIB).

*Npoužití*<br/>
Určuje, zda `bmiColors[]` pole [bitmapinfo –](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo) struktury dat (část z "komprimace DIB") obsahují explicitní hodnoty RGB nebo indexů do aktuálně realizované logickou paletu. Parametr musí být jedna z následujících hodnot:

- DIB_PAL_COLORS tabulku barvy se skládá z pole indexů 16 bitů.

- Tabulky barev DIB_RGB_COLORS obsahuje literálové hodnoty RGB.

*lpPackedDIB*<br/>
Odkazuje na sbalené DIB skládající se z `BITMAPINFO` struktura bezprostředně následovat pole bajtů definování pixelů rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Štětec je následně vybrat pro jakýkoli kontext zařízení, který podporuje rastrové operace.

Dvě verze se liší v tak, jak zpracovat DIB:

- V první verze, chcete-li získat popisovač DIB zavoláte Windows `GlobalAlloc` funkce a přidělení bloku paměti globální paměť vyplnit sbalené DIB.

- V druhém verzi, není nutné volat `GlobalAlloc` přidělení paměti pro komprimovaný DIB.

Sbalené DIB se skládá z `BITMAPINFO` datová struktura bezprostředně následovat pole bajtů, který definuje pixelů rastrového obrázku. Použít jako vzorky výplně rastrových obrázků musí být 8 x 8 pixelů. Pokud rastrového obrázku je větší, vytvoří Windows vzorek výplně pomocí pouze bity odpovídající řádky prvních 8 a 8 sloupce v levém horním rohu rastrového obrázku v pixelech.

Když aplikace vybere dvě barvy štětce vzor DIB kontextu monochromatického zařízení, Windows bude ignorovat barvy definované v DIB a namísto toho se zobrazí vzorek štětec pomocí aktuální barvy textu a pozadí kontextu zařízení. Pixely namapované na první barvou DIB (na posunu 0 v tabulce barev DIB) se zobrazí pomocí barvu textu. Pixely namapované na druhý sloupec (na posunu 1 v tabulce barev) se zobrazí barvou pozadí.

Informace o používání následujících funkcí Windows najdete v tématu Windows SDK:

- [CreateDIBPatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrush) (Tato funkce slouží pouze pro kompatibilitu s aplikace napsané pro verzích Windows starších než 3.0; použijte `CreateDIBPatternBrushPt` funkce.)

- [CreateDIBPatternBrushPt](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Tato funkce by měla sloužit pro aplikace založené na Win32.)

- [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

Inicializuje se zadanému vzoru šrafované a barvou štětce.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje styl šrafování štětce. To může být jedna z následujících hodnot:

- HS_BDIAGONAL Šrafování dolů (zleva doprava) na 45 stupňů

- HS_CROSS vodorovné a svislé mřížkovaný

- HS_DIAGCROSS šrafování na 45 stupňů

- Nahoru HS_FDIAGONAL šrafování (zleva doprava) na 45 stupňů

- Vodorovné HS_HORIZONTAL šrafování

- Svislé HS_VERTICAL šrafování

*crColor*<br/>
Určuje barvu popředí štětce jako barva RGB (barva šrafování). Zobrazit [COLORREF](/windows/desktop/gdi/colorref) v sadě Windows SDK pro další informace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Štětec je následně vybrat jako aktuální štětec pro jakýkoli kontext zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

Inicializuje štětcem pomocí vzoru určené rastrový obrázek.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Identifikuje rastrový obrázek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Štětec je následně vybrat pro jakýkoli kontext zařízení, který podporuje rastrové operace. Rastrový obrázek identifikovaný *pBitmap* je obvykle inicializována pomocí [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [cbitmap –:: Loadbitmap –](../../mfc/reference/cbitmap-class.md#loadbitmap), nebo [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) funkce.

Použít jako vzorky výplně rastrových obrázků musí být 8 x 8 pixelů. Pokud rastrového obrázku je větší, Windows použije pouze bity odpovídající prvních 8 řádků a sloupců v levém horním rohu rastrového obrázku v pixelech.

Štětce vzor je možné odstranit bez ovlivnění přidružený rastrový obrázek. To znamená, že rastrového obrázku je možné vytvořit libovolný počet vzorkem štětce.

Štětce vytvořené pomocí monochromatický rastrový obrázek (1 barevné roviny 1 bitů na pixel) je vykreslen aktuální barvy textu a pozadí. Obrazových bodů reprezentované bit nastaven na hodnotu 0 jsou vykreslovány pomocí aktuální barvu textu. Obrazové body reprezentované bit nastaven na hodnotu 1, jsou vykreslovány aktuální barvou pozadí.

Informace o používání [CreatePatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createpatternbrush), Windows fungovat, naleznete v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush

Inicializuje zadaný plnou barvou štětce.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
A [COLORREF](/windows/desktop/gdi/colorref) struktura, která určuje barvu štětce. Barva určuje hodnota RGB a může být zkonstruovaný pomocí RGB – makro v systému WINDOWS. H.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Štětec je následně vybrat jako aktuální štětec pro jakýkoli kontext zařízení.

Když aplikace dokončí štětce vytvořené využitím `CreateSolidBrush`, ji by měl vybrat štětce mimo kontext zařízení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CBrush::CBrush](#cbrush).

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

Inicializuje Barva štětce.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index barev. Tato hodnota odpovídá barva použitá k vykreslení jeden z elementů 21 okna. Zobrazit [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) v sadě Windows SDK pro seznam hodnot.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Štětec je následně vybrat jako aktuální štětec pro jakýkoli kontext zařízení.

Když aplikace dokončí štětce vytvořené využitím `CreateSysColorBrush`, ji by měl vybrat štětce mimo kontext zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>  CBrush::FromHandle

Vrací ukazatel na `CBrush` objektu, když je zadaný popisovač Windows [HBRUSH](#operator_hbrush) objektu.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parametry

*hBrush*<br/>
POPISOVAČ Windows GDI štětce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CBrush` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud `CBrush` objekt už není připojen ke zpracování, dočasný `CBrush` objekt se vytvoří a připojí. Tento dočasný `CBrush` objektu je platná pouze až do příštího aplikace má čas nečinnosti v jeho smyčkou událostí. V tuto chvíli se odstraní všechny dočasné grafických objektů. Jinými slovy dočasný objekt platí pouze při zpracování zprávy jedno okno.

Další informace o použití grafických objektů najdete v tématu [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CBrush::CBrush](#cbrush).

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

Voláním této členské funkce k načtení `LOGBRUSH` struktury.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parametry

*pLogBrush*<br/>
Odkazuje [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) strukturu, která obsahuje informace o stopy.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, a *pLogBrush* je platný ukazatel, vrácená hodnota je počet bajtů uložených do vyrovnávací paměti.

Pokud je funkce úspěšná, a *pLogBrush* má hodnotu NULL, vrácená hodnota je počet bajtů vyžadovaných k uložení informace o funkci by ukládání do vyrovnávací paměti.

Pokud funkce selže, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

`LOGBRUSH` Struktury definuje styl, barvu a vzorkem štětce.

Například volání `GetLogBrush` tak, aby odpovídaly konkrétní barvu nebo vzorek rastrového obrázku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>  CBrush::operator HBRUSH

Tento operátor se získat popisovač Windows GDI připojené `CBrush` objektu.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud úspěchu popisovač objektů Windows GDI reprezentována `CBrush` objektu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, která podporuje přímému použití objektu HBRUSH.

Další informace o použití grafických objektů najdete v tématu [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Cgdiobject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Cbitmap – třída](../../mfc/reference/cbitmap-class.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)
