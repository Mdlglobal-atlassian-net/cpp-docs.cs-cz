---
title: CBrush – třída
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
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352481"
---
# <a name="cbrush-class"></a>CBrush – třída

Zapouzdřuje štětec rozhraní grafického zařízení (Windows) (GDI).

## <a name="syntax"></a>Syntaxe

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Vytvoří `CBrush` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicializuje stopu se stylem, barvou a vzorkem určeným ve struktuře [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicializuje stopu se vzorkem určeným bitmapou (DIB) nezávislou na zařízení.|
|[CBrush::Vytvořit hatchbrush](#createhatchbrush)|Inicializuje stopu se zadaným šrafovaným vzorkem a barvou.|
|[CBrush::Vytvořit stopu](#createpatternbrush)|Inicializuje stopu se vzorkem určeným bitmapou.|
|[CBrush::Vytvořitstopný užitkový](#createsolidbrush)|Inicializuje stopu se zadanou plnou barvou.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Vytvoří stopu, která je výchozí systémovou barvou.|
|[CBrush::FromHandle](#fromhandle)|Vrátí ukazatel na `CBrush` objekt, když daný `HBRUSH` popisovač objektu systému Windows.|
|[CBrush::GetLogBrush](#getlogbrush)|Získá [strukturu LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CBrush::operátor HBRUSH](#operator_hbrush)|Vrátí popisovač systému `CBrush` Windows připojený k objektu.|

## <a name="remarks"></a>Poznámky

Chcete-li `CBrush` použít objekt, vytvořte `CBrush` objekt `CDC` a předajte jej libovolné členské funkci, která vyžaduje stopu.

Stopy mohou být plné, šrafované nebo vzorované.

Další informace `CBrush`naleznete v tématu [Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CGdi](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush

Vytvoří `CBrush` objekt.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Určuje barvu popředí stopy jako barvu RGB. Pokud je šrafovaný šrafovaný, tento parametr určuje barvu šrafování.

*nIndex*<br/>
Určuje styl šrafování stopy. Může to být některá z následujících hodnot:

- HS_BDIAGONAL Poklop směrem dolů (zleva doprava) při 45 stupních

- HS_CROSS Vodorovný a svislý šrafování

- HS_DIAGCROSS Crosshatch při 45 stupních

- HS_FDIAGONAL Nahoru poklop (zleva doprava) při 45 stupních

- HS_HORIZONTAL Vodorovný poklop

- HS_VERTICAL Svislý poklop

*pBitmap*<br/>
Odkazuje na `CBitmap` objekt, který určuje bitmapu, se kterou štětec maluje.

### <a name="remarks"></a>Poznámky

`CBrush`má čtyři přetížené konstruktory. Konstruktor bez argumentů vytvoří neinicializovaný `CBrush` objekt, který musí být před použitím inicializován.

Pokud používáte konstruktor bez argumentů, musíte inicializovat `CBrush` výsledný objekt pomocí [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreateBrushBrush](#createpatternbrush)nebo [CreateDIBPatternBrush](#createdibpatternbrush). Pokud použijete jeden z konstruktorů, který přebírá argumenty, není nutné žádné další inicializace. Konstruktory s argumenty může vyvolat výjimku, pokud dojde k chybám, zatímco konstruktor bez argumentů bude vždy úspěšné.

Konstruktor s jedním parametrem [COLORREF](/windows/win32/gdi/colorref) vytvoří plnou stopu se zadanou barvou. Barva určuje hodnotu RGB a může být vytvořena pomocí makra RGB v systému WINDOWS. H.

Konstruktor se dvěma parametry vytvoří šrafovací stopu. Parametr *nIndex* určuje index šrafovaného vzoru. Parametr *crColor* určuje barvu.

Konstruktor s `CBitmap` parametrem vytvoří vzorovou stopu. Parametr identifikuje bitmapu. Předpokládá se, že bitmapa byla vytvořena pomocí [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)nebo [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimální velikost bitmapy, která má být použita ve vzorku výplně, je 8 x 8 pixelů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect

Inicializuje stopu se stylem, barvou a vzorkem určeným ve struktuře [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush)

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parametry

*lpLogBrush*<br/>
Odkazuje na [strukturu LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush) která obsahuje informace o stopě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Stopu lze následně vybrat jako aktuální stopu pro libovolný kontext zařízení.

Stopa vytvořená pomocí monochromatické (1 rovina, 1 bit na pixel) bitmapa je nakreslena pomocí aktuálního textu a barev pozadí. Obrazové body reprezentované bitem nastaveným na 0 budou nakresleny s aktuální barvou textu. Obrazové body reprezentované bitem nastaveným na 1 budou nakresleny s aktuální barvou pozadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush

Inicializuje stopu se vzorkem určeným bitmapou (DIB) nezávislou na zařízení.

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
Identifikuje objekt globální paměti obsahující zabalenou bitmapu (DIB) nezávislou na zařízení.

*nPoužití*<br/>
Určuje, `bmiColors[]` zda pole datové struktury [BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (část "baleného DIB") obsahují explicitní hodnoty nebo indexy RGB do aktuálně realizované logické palety. Parametr musí být jedna z následujících hodnot:

- DIB_PAL_COLORS Tabulka barev se skládá z pole 16bitových indexů.

- DIB_RGB_COLORS Tabulka barev obsahuje literálové hodnoty RGB.

*lpPackedDIB*<br/>
Odkazuje na zabalený DIB `BITMAPINFO` skládající se ze struktury, za kterou bezprostředně následuje pole bajtů definujících obrazové body bitmapy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Stopu lze následně vybrat pro libovolný kontext zařízení, který podporuje rastrové operace.

Tyto dvě verze se liší ve způsobu, jakým zpracováváte DIB:

- V první verzi získat popisovač DIB zavoláte `GlobalAlloc` funkci systému Windows přidělit blok globální paměti a potom vyplnit paměť s zabalený DIB.

- Ve druhé verzi není nutné volat `GlobalAlloc` k přidělení paměti pro zabalené DIB.

Zabalený DIB se `BITMAPINFO` skládá z datové struktury bezprostředně následované pole bajtů, která definuje obrazové body bitmapy. Rastry použité jako vzorky výplně by měly být 8 x 8 pixelů. Pokud je bitmapa větší, systém Windows vytvoří vzorek výplně pouze pomocí bitů odpovídajících prvním 8 řádkům a 8 sloupcům obrazových bodů v levém horním rohu bitmapy.

Když aplikace vybere dvoubarevný štětec DIB do kontextu monochromatického zařízení, systém Windows ignoruje barvy zadané v dib a místo toho zobrazí stopu se vzorkem pomocí aktuálního textu a barvy pozadí kontextu zařízení. Obrazové body mapované na první barvu (při posunu 0 v tabulce barev DIB) dib jsou zobrazeny pomocí barvy textu. Obrazové body mapované na druhou barvu (při posunu 1 v tabulce barev) se zobrazí pomocí barvy pozadí.

Informace o použití následujících funkcí systému Windows naleznete v části Sada Windows SDK:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Tato funkce je k dispozici pouze pro kompatibilitu s aplikacemi napsanými pro verze systému Windows starší než 3.0; použijte `CreateDIBPatternBrushPt` funkci.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Tato funkce by měla být použita pro aplikace založené na win32.)

- [GlobálníAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::Vytvořit hatchbrush

Inicializuje stopu se zadaným šrafovaným vzorkem a barvou.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje styl šrafování stopy. Může to být některá z následujících hodnot:

- HS_BDIAGONAL Poklop směrem dolů (zleva doprava) při 45 stupních

- HS_CROSS Vodorovný a svislý šrafování

- HS_DIAGCROSS Crosshatch při 45 stupních

- HS_FDIAGONAL Nahoru poklop (zleva doprava) při 45 stupních

- HS_HORIZONTAL Vodorovný poklop

- HS_VERTICAL Svislý poklop

*crColor*<br/>
Určuje barvu popředí stopy jako barvu RGB (barvu šraf). Další informace naleznete v části [COLORREF](/windows/win32/gdi/colorref) v kani s sadou Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Stopu lze následně vybrat jako aktuální stopu pro libovolný kontext zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::Vytvořit stopu

Inicializuje stopu se vzorkem určeným bitmapou.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Identifikuje bitmapu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Stopu lze následně vybrat pro libovolný kontext zařízení, který podporuje rastrové operace. Bitmapa identifikovaná *pBitmap* je obvykle inicializována pomocí funkce [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)nebo [CBitmap::CreateCompatibleBitmap.](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)

Rastry použité jako vzorky výplně by měly být 8 x 8 pixelů. Pokud je bitmapa větší, systém Windows použije pouze bity odpovídající prvním 8 řádkům a sloupce obrazových bodů v levém horním rohu bitmapy.

Stopa se vzorkem může být odstraněna bez ovlivnění přidružené bitmapy. To znamená, že bitmapu lze použít k vytvoření libovolného počtu stop se vzorkem.

Stopa vytvořená pomocí monochromatické bitmapy (1 barevná rovina, 1 bit na pixel) je nakreslena pomocí aktuálníbarvy textu a pozadí. Obrazové body reprezentované bitem nastaveným na 0 jsou nakresleny s aktuální barvou textu. Obrazové body reprezentované bitem nastaveným na 1 jsou kresleny s aktuální barvou pozadí.

Informace o použití funkce [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)naleznete v části Sada Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::Vytvořitstopný užitkový

Inicializuje stopu se zadanou plnou barvou.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
[Colorref](/windows/win32/gdi/colorref) struktura, která určuje barvu stopy. Barva určuje hodnotu RGB a může být vytvořena pomocí makra RGB v systému WINDOWS. H.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Stopu lze následně vybrat jako aktuální stopu pro libovolný kontext zařízení.

Po dokončení aplikace pomocí stopy `CreateSolidBrush`vytvořené aplikace by měla vybrat stopu z kontextu zařízení.

### <a name="example"></a>Příklad

  Viz příklad pro [CBrush::CBrush](#cbrush).

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush

Inicializuje barvu stopy.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index barev. Tato hodnota odpovídá barvě použité k malování jednoho z 21 prvků okna. Seznam hodnot najdete v tématu [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Stopu lze následně vybrat jako aktuální stopu pro libovolný kontext zařízení.

Po dokončení aplikace pomocí stopy `CreateSysColorBrush`vytvořené aplikace by měla vybrat stopu z kontextu zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::FromHandle

Vrátí ukazatel na `CBrush` objekt, když daný popisovač windows [HBRUSH](#operator_hbrush) objektu.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parametry

*hŠtětec*<br/>
Zpracovat štětec GDI systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CBrush` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CBrush` objekt ještě není připojen k popisovač, dočasný `CBrush` objekt je vytvořen a připojen. Tento `CBrush` dočasný objekt je platný pouze do příště aplikace má nečinnosti čas ve smyčce událostí. V tomto okamžiku jsou odstraněny všechny dočasné grafické objekty. Jinými slovy dočasný objekt je platný pouze při zpracování jedné zprávy okna.

Další informace o používání grafických objektů naleznete v [tématu Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CBrush::CBrush](#cbrush).

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush

Volání této členské funkce `LOGBRUSH` načíst strukturu.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parametry

*pLogBrush*<br/>
Odkazuje na [strukturu LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush) která obsahuje informace o stopě.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná a *pLogBrush* je platný ukazatel, vrácená hodnota je počet bajtů uložených do vyrovnávací paměti.

Pokud je funkce úspěšná a *pLogBrush* je NULL, vrácená hodnota je počet bajtů potřebných k uložení informací, které by funkce uklápěla do vyrovnávací paměti.

Pokud funkce selže, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Struktura `LOGBRUSH` definuje styl, barvu a vzorek stopy.

Volání například `GetLogBrush` odpovídá určité barvě nebo vzorku bitmapy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::operátor HBRUSH

Pomocí tohoto operátoru získáte připojený popisovač GDI systému Windows objektu. `CBrush`

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu GDI systému Windows reprezentovaný objektem; `CBrush` jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití HBRUSH objektu.

Další informace o používání grafických objektů naleznete v [tématu Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Viz také

[Vzorek mfc PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBitmap – třída](../../mfc/reference/cbitmap-class.md)<br/>
[Třída CDC](../../mfc/reference/cdc-class.md)
