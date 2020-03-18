---
title: CBrush – – třída
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
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420538"
---
# <a name="cbrush-class"></a>CBrush – – třída

Zapouzdřuje štětec rozhraní grafického zařízení (GDI) systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBrush –:: CBrush –](#cbrush)|Vytvoří objekt `CBrush`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBrush –:: CreateBrushIndirect](#createbrushindirect)|Inicializuje štětce se stylem, barvou a vzorkem zadaným ve struktuře [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) .|
|[CBrush –:: CreateDIBPatternBrush](#createdibpatternbrush)|Inicializuje štětec pomocí vzoru určeného rastrového obrázku (DIB) nezávislém na zařízení.|
|[CBrush –:: CreateHatchBrush](#createhatchbrush)|Inicializuje štětec se zadaným vyšrafovaném vzorem a barvou.|
|[CBrush –:: CreatePatternBrush](#createpatternbrush)|Inicializuje štětec pomocí vzoru určeného rastrovým obrázkem.|
|[CBrush –:: CreateSolidBrush](#createsolidbrush)|Inicializuje štětec se zadanou plnou barvou.|
|[CBrush –:: CreateSysColorBrush](#createsyscolorbrush)|Vytvoří štětec, který je výchozí systémovou barvou.|
|[CBrush –:: FromHandle](#fromhandle)|Vrací ukazatel na objekt `CBrush`, pokud je předána obslužná rutina objektu Windows `HBRUSH`.|
|[CBrush –:: GetLogBrush](#getlogbrush)|Načte strukturu [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) .|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CBrush –:: operator HBRUSH](#operator_hbrush)|Vrátí popisovač systému Windows připojený k objektu `CBrush`.|

## <a name="remarks"></a>Poznámky

Chcete-li použít objekt `CBrush`, Sestavte objekt `CBrush` a předejte ho do jakékoli `CDC` členské funkce, která vyžaduje štětec.

Štětce můžou být plné, šrafované nebo vzorované.

Další informace o `CBrush`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cbrush"></a>CBrush –:: CBrush –

Vytvoří objekt `CBrush`.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Určuje barvu popředí štětce jako barvu RGB. Pokud je štětec Vyšrafované, tento parametr určuje barvu šrafování.

*nIndex*<br/>
Určuje styl šrafování štětce. Může to být jedna z následujících hodnot:

- HS_BDIAGONAL šikmý šrafování (zleva doprava) na 45 stupňů

- HS_CROSS vodorovné a svislé křížové šrafování

- HS_DIAGCROSS křížové šrafování na 45 stupňů

- HS_FDIAGONAL šikmé šrafování (zleva doprava) na 45 stupňů

- HS_HORIZONTAL vodorovný šrafování

- HS_VERTICAL Vertikální šrafování

*pBitmap*<br/>
Odkazuje na objekt `CBitmap`, který určuje rastrový obrázek, pomocí kterého maluje štětce.

### <a name="remarks"></a>Poznámky

`CBrush` má čtyři přetížené konstruktory. Konstruktor bez argumentů vytvoří Neinicializovaný objekt `CBrush`, který musí být inicializován předtím, než bude možné ho použít.

Použijete-li konstruktor bez argumentů, je nutné inicializovat výsledný objekt `CBrush` pomocí [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)nebo [CreateDIBPatternBrush](#createdibpatternbrush). Použijete-li jeden z konstruktorů, které přebírají argumenty, není nutné provádět žádnou další inicializaci. Konstruktory s argumenty mohou vyvolat výjimku, pokud dojde k chybám, ale konstruktor bez argumentů bude vždy úspěšný.

Konstruktor s jedním parametrem [COLORREF](/windows/win32/gdi/colorref) vytvoří plný štětec se zadanou barvou. Barva Určuje hodnotu RGB a může být vytvořena pomocí makra RGB v systému WINDOWS. Y.

Konstruktor se dvěma parametry vytvoří šrafované štětce. Parametr *nIndex* určuje index šrafovaného vzoru. Parametr *crColor* Určuje barvu.

Konstruktor s parametrem `CBitmap` sestaví vzorované štětce. Parametr identifikuje rastrový obrázek. Předpokládá se, že je bitmapa vytvořená pomocí [CBitmap –:: CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap –:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap –:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)nebo [CBitmap –:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimální velikost rastrového obrázku, který má být použit ve vzorku výplně, je 8 pixelů o 8 pixelů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>CBrush –:: CreateBrushIndirect

Inicializuje štětec se stylem, barvou a vzorkem zadaným ve struktuře [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) .

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parametry

*lpLogBrush*<br/>
Odkazuje na strukturu [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) , která obsahuje informace o štětci.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Štětec se následně dá vybrat jako aktuální štětec pro jakékoli kontexty zařízení.

Obrázek vytvořený pomocí černobílého rastrového obrázku (1 rovina, 1 bitů na pixel) se vykreslí pomocí aktuální barvy textu a pozadí. Pixely reprezentované bitovou sadou nastavenou na hodnotu 0 budou vykresleny pomocí aktuální barvy textu. Pixely reprezentované bitovou sadou nastavenou na hodnotu 1 budou vykresleny pomocí aktuální barvy pozadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>CBrush –:: CreateDIBPatternBrush

Inicializuje štětec se vzorkem určeným rastrovým obrázkem, který je nezávislý na zařízení (DIB).

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
Identifikuje objekt globální paměti obsahující zabalené rastrové obrázky nezávislé na zařízení (DIB).

*nUsage*<br/>
Určuje, zda `bmiColors[]` pole struktury dat [BITMAPINFO –](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (část "zkomprimovaného formátu DIB") obsahují explicitní hodnoty RGB nebo indexy do aktuálně realizované logické palety. Parametr musí být jedna z následujících hodnot:

- DIB_PAL_COLORS tabulka barev se skládá z pole 16bitových indexů.

- DIB_RGB_COLORS tabulka barev obsahuje literálové hodnoty RGB.

*lpPackedDIB*<br/>
Odkazuje na zabalený DIB sestávající z `BITMAPINFO` struktury ihned následovaný polem bajtů definujícím pixely rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Štětec se následně dá vybrat pro libovolný kontext zařízení, který podporuje rastrové operace.

Tyto dvě verze se liší ve způsobu zpracování formátu DIB:

- V první verzi, chcete-li získat popisovač na DIB, zavoláte funkci Windows `GlobalAlloc` a přidělíte tak blok globální paměti a pak vyplníte paměť sbaleným DIB.

- Ve druhé verzi není nutné volat `GlobalAlloc` pro přidělení paměti pro zkomprimovaný DIB.

Zabalený DIB se skládá z `BITMAPINFO` struktury dat ihned po poli bajtů, které definuje pixely rastrového obrázku. Rastrové obrázky používané jako vzory výplní by měly být 8 pixelů o 8 pixelů. Pokud je rastrový obrázek větší, vytvoří systém Windows vzorek výplně s použitím pouze bitů odpovídajících prvních 8 řádků a 8 sloupců pixelů v levém horním rohu rastrového obrázku.

Když aplikace vybere vzorek štětce se dvěma barvami DIB do kontextu monochromatického zařízení, systém Windows ignoruje barvy zadané ve formátu DIB a místo toho zobrazí štětec vzorů s použitím aktuální barvy textu a pozadí kontextu zařízení. Pixely namapované na první barvu (na posunutí 0 v tabulce barev DIB) se zobrazí pomocí barvy textu. Pixely namapované na druhou barvu (na posunu 1 v tabulce barev) se zobrazují pomocí barvy pozadí.

Informace o použití následujících funkcí systému Windows naleznete v Windows SDK:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Tato funkce je k dispozici pouze pro kompatibilitu s aplikacemi napsanými pro verze systému Windows starší než 3,0; použijte funkci `CreateDIBPatternBrushPt`.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Tato funkce by měla být použita pro aplikace založené na Win32.)

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>CBrush –:: CreateHatchBrush

Inicializuje štětec se zadaným vyšrafovaném vzorem a barvou.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje styl šrafování štětce. Může to být jedna z následujících hodnot:

- HS_BDIAGONAL šikmý šrafování (zleva doprava) na 45 stupňů

- HS_CROSS vodorovné a svislé křížové šrafování

- HS_DIAGCROSS křížové šrafování na 45 stupňů

- HS_FDIAGONAL šikmé šrafování (zleva doprava) na 45 stupňů

- HS_HORIZONTAL vodorovný šrafování

- HS_VERTICAL Vertikální šrafování

*crColor*<br/>
Určuje barvu popředí štětce jako barvu RGB (barvy šrafování). Další informace najdete v tématu [COLORREF](/windows/win32/gdi/colorref) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Štětec se následně dá vybrat jako aktuální štětec pro jakékoli kontexty zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>CBrush –:: CreatePatternBrush

Inicializuje štětec pomocí vzoru určeného rastrovým obrázkem.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Identifikuje rastrový obrázek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Štětec se následně dá vybrat pro libovolný kontext zařízení, který podporuje rastrové operace. Rastr identifikovaný *pBitmap* je obvykle inicializován pomocí [CBitmap –:: CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap –:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap –:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)nebo [CBitmap –:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) Function.

Rastrové obrázky používané jako vzory výplní by měly být 8 pixelů o 8 pixelů. Pokud je rastrový obrázek větší, systém Windows použije v levém horním rohu rastrového obrázku pouze bity odpovídající prvních 8 řádků a sloupců pixelů.

Štětec vzorku lze odstranit, aniž by to ovlivnilo přidružený rastrový obrázek. To znamená, že rastr lze použít k vytvoření libovolného počtu štětců vzorů.

Štětec vytvořený pomocí monochromatického rastrového obrázku (1 barevná rovina, 1 bitů na pixel) se vykreslí pomocí aktuální barvy textu a pozadí. Pixely reprezentované bitovou sadou nastavenou na hodnotu 0 jsou vykresleny pomocí aktuální barvy textu. Pixely reprezentované bitovou sadou nastavenou na hodnotu 1 jsou vykresleny pomocí aktuální barvy pozadí.

Informace o použití funkce [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)naleznete v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>CBrush –:: CreateSolidBrush

Inicializuje štětec se zadanou plnou barvou.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parametry

*crColor*<br/>
Struktura [COLORREF](/windows/win32/gdi/colorref) , která určuje barvu štětce. Barva Určuje hodnotu RGB a může být vytvořena pomocí makra RGB v systému WINDOWS. Y.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Štětec se následně dá vybrat jako aktuální štětec pro jakékoli kontexty zařízení.

Když se aplikace dokončí pomocí štětce vytvořeného pomocí `CreateSolidBrush`, měl by vybrat stopu z kontextu zařízení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CBrush –:: CBrush –](#cbrush).

##  <a name="createsyscolorbrush"></a>CBrush –:: CreateSysColorBrush

Inicializuje barvu štětce.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index barvy. Tato hodnota odpovídá barvě použité k vykreslení jednoho z 21 prvků okna. Seznam hodnot naleznete v tématu [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Štětec se následně dá vybrat jako aktuální štětec pro jakékoli kontexty zařízení.

Když se aplikace dokončí pomocí štětce vytvořeného pomocí `CreateSysColorBrush`, měl by vybrat stopu z kontextu zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>CBrush –:: FromHandle

Vrací ukazatel na objekt `CBrush`, pokud je předána obslužná rutina objektu [HBRUSH](#operator_hbrush) Windows.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parametry

*hBrush*<br/>
ZPRACOVÁNÍ štětce s Windows GDI.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CBrush` v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt `CBrush` již není k popisovači připojen, je vytvořen a připojen dočasný objekt `CBrush`. Tento dočasný `CBrush` objekt je platný pouze do okamžiku, kdy aplikace nebude mít čas nečinnosti ve smyčce události. V tuto chvíli se odstraní všechny dočasné grafické objekty. Jinými slovy, dočasný objekt je platný pouze během zpracování jedné zprávy okna.

Další informace o použití grafických objektů naleznete v tématu [Graphics Objects](/windows/win32/gdi/graphic-objects) in Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CBrush –:: CBrush –](#cbrush).

##  <a name="getlogbrush"></a>CBrush –:: GetLogBrush

Pro načtení struktury `LOGBRUSH` volejte tuto členskou funkci.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parametry

*pLogBrush*<br/>
Odkazuje na strukturu [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) , která obsahuje informace o štětci.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná a *pLogBrush* je platný ukazatel, návratová hodnota je počet bajtů uložených do vyrovnávací paměti.

Pokud je funkce úspěšná a *pLogBrush* má hodnotu null, návratová hodnota je počet bajtů vyžadovaných k uložení informací, které by funkce ukládala do vyrovnávací paměti.

Pokud dojde k chybě funkce, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Struktura `LOGBRUSH` definuje styl, barvu a vzorek štětce.

Například volejte `GetLogBrush`, aby odpovídala konkrétní barvě nebo vzoru rastrového obrázku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>CBrush –:: operator HBRUSH

Tento operátor použijte k získání připojené obslužné rutiny Windows GDI objektu `CBrush`.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, popisovač objektu GDI systému Windows reprezentovaného objektem `CBrush`; jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HBRUSH.

Další informace o použití grafických objektů naleznete v tématu [Graphics Objects](/windows/win32/gdi/graphic-objects) in Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Viz také

[PROPDLG Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBitmap – třída](../../mfc/reference/cbitmap-class.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)
