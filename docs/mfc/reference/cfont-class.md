---
title: CFont – třída
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373833"
---
# <a name="cfont-class"></a>CFont – třída

Zapouzdřuje písmo rozhraní grafického zařízení systému Windows (GDI) a poskytuje členské funkce pro manipulaci s písmem.

## <a name="syntax"></a>Syntaxe

```
class CFont : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFont::CFont](#cfont)|Vytvoří `CFont` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Inicializuje `CFont` a se zadanými vlastnostmi.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializuje `CFont` objekt s charakteristikami `LOGFONT` uvedenými ve struktuře.|
|[CFont::CreatePointFont](#createpointfont)|Inicializuje `CFont` a se zadanou výškou, měřenou v desetinách bodu, a písmem.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Stejné `CreateFontIndirect` jako s tím rozdílem, že výška písma se měří v desetinách bodu, nikoli v logických jednotkách.|
|[CFont::FromHandle](#fromhandle)|Vrátí ukazatel na `CFont` objekt při dané Windows HFONT.|
|[CFont::GetLogFont](#getlogfont)|Vyplní `LOGFONT` informace o logickém písmu `CFont` připojeném k objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CFont::operátor HFONT](#operator_hfont)|Vrátí popisovač písma Windows GDI připojený k objektu. `CFont`|

## <a name="remarks"></a>Poznámky

Chcete-li `CFont` `CFont` použít objekt, vytvořte objekt a připojte k němu písmo systému Windows pomocí [createfontu](#createfont), [createfontu nepřímého](#createfontindirect) [písma , createpointfontu](#createpointfont)nebo [objektu CreatePointFontIndirect](#createpointfontindirect)a potom pomocí členských funkcí objektu manipulujte s písmem.

Funkce `CreatePointFont` `CreatePointFontIndirect` a jsou často jednodušší `CreateFont` `CreateFontIndirect` než nebo od té doby, než provádějí převod výšky písma z velikosti bodu na logické jednotky automaticky.

Další informace `CFont`naleznete v tématu [Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CGdi](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont::CFont

Vytvoří `CFont` objekt.

```
CFont();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt musí být inicializován pomocí `CreateFont` `CreateFontIndirect`, , `CreatePointFont`nebo `CreatePointFontIndirect` před jeho použitím.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont::CreateFont

Inicializuje `CFont` objekt se zadanými vlastnostmi.

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>Parametry

*nVýška*<br/>
Určuje požadovanou výšku (v logických jednotkách) písma. Popis `lfHeight` naleznete v části Člen struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)v sadě Windows SDK. Absolutní hodnota *nHeight* nesmí po převodu překročit 16 384 jednotek zařízení. Pro všechna porovnání výšky mapovač písma hledá největší písmo, které nepřesahuje požadovanou velikost nebo nejmenší písmo, pokud všechna písma překročí požadovanou velikost.

*nŠířka*<br/>
Určuje průměrnou šířku (v logických jednotkách) znaků v písmu. Pokud *nWidth* je 0, poměr stran zařízení bude porovnán s poměrem stran digitalizace dostupných písem najít nejbližší shodu, která je určena absolutní hodnotou rozdílu.

*nÚtěk*<br/>
Určuje úhel (v jednotkách 0,1 stupně) mezi vektorem escapement unikače a osou x zobrazovací plochy. Vektor escapement je čára přes počátky prvního a posledního znaku na řádku. Úhel se měří proti směru hodinových ručiček od osy x. Další `lfEscapement` informace naleznete `LOGFONT` v části Člen ve struktuře sady Windows SDK.

*nOrientace*<br/>
Určuje úhel (v jednotkách 0,1 stupně) mezi účaří znaku a osou x. Úhel se měří proti směru hodinových ručiček od osy x pro souřadné systémy, ve kterých je směr y dolů, a ve směru hodinových ručiček od osy x pro souřadnicové systémy, ve kterých je směr y nahoru.

*nHmotnost*<br/>
Určuje tloušťku písma (v barvených obrazových bodech na 1000). Další informace naleznete v `LOGFONT` členu *lfWeight* ve struktuře sady Windows SDK. Popsané hodnoty jsou přibližné; skutečný vzhled závisí na písmu. Některá písma mají pouze FW_NORMAL, FW_REGULAR a FW_BOLD hmotnosti. Pokud je zadán FW_DONTCARE, použije se výchozí hmotnost.

*bItalic*<br/>
Určuje, zda je písmo kurzívou.

*bPodtržení*<br/>
Určuje, zda je písmo podtrženo.

*cStrikeOut*<br/>
Určuje, zda jsou znaky v písmu vyškrtnuty. Určuje přeškrtávací písmo, pokud je nastaveno na nenulovou hodnotu.

*nSada char*<br/>
Určuje znakovou sadu písma: `lfCharSet` Seznam `LOGFONT` hodnot naleznete v sadě Windows SDK ve struktuře systému Windows.

Znaková sada OEM je závislá na systému.

Písma s jinými znakovými sadami mohou v systému existovat. Aplikace, která používá písmo s neznámou znakovou sadou, se nesmí pokoušet překládat nebo interpretovat řetězce, které mají být vykresleny pomocí tohoto písma. Místo toho řetězce by měly být předány přímo ovladač výstupního zařízení.

Mapovač písem nepoužívá hodnotu DEFAULT_CHARSET. Aplikace může tuto hodnotu použít k tomu, aby název a velikost písma plně popsala logické písmo. Pokud písmo se zadaným názvem neexistuje, může být zadaným písmem nahrazeno písmo z libovolné znakové sady. Aby se zabránilo neočekávaným výsledkům, aplikace by měly používat DEFAULT_CHARSET hodnotu střídmě.

*nOutPrecision*<br/>
Určuje požadovanou výstupní přesnost. Přesnost výstupu definuje, jak přesně musí výstup odpovídat výšce, šířce, orientaci znaku, úniku a rozteči požadovaného písma. Seznam `lfOutPrecision` hodnot a `LOGFONT` další informace naleznete v členu ve struktuře sady Windows SDK.

*nPřesnostklipů*<br/>
Určuje požadovanou přesnost oříznutí. Přesnost oříznutí definuje, jak oříznout znaky, které jsou částečně mimo oblast oříznutí. Seznam `lfClipPrecision` hodnot naleznete `LOGFONT` v seznamu členů ve struktuře sady Windows SDK.

Chcete-li použít vložené písmo jen pro čtení, musí aplikace určit CLIP_ENCAPSULATE.

Chcete-li dosáhnout konzistentní otočení zařízení, TrueType a vektorová písma, aplikace můžete použít operátor OR kombinovat CLIP_LH_ANGLES hodnotu s některou z ostatních hodnot *nClipPrecision.* Pokud je nastaven CLIP_LH_ANGLES bit, otočení pro všechna písma závisí na tom, zda je orientace souřadnicového systému levák nebo pravák. (Další informace o orientaci souřadnicových systémů naleznete v popisu parametru *nOrientation.)* Pokud CLIP_LH_ANGLES není nastavena, písma zařízení se vždy otáčejí proti směru hodinových ručiček, ale otočení jiných písem závisí na orientaci souřadnicového systému.

*nKvalita*<br/>
Určuje kvalitu výstupu písma, která definuje, jak pečlivě se gdi musí pokoušet spárovat atributy logického písma s atributy skutečného fyzického písma. Seznam `lfQuality` hodnot naleznete `LOGFONT` v seznamu členů ve struktuře sady Windows SDK.

*nPitchAndFamily*<br/>
Určuje výšku a rodinu písma. Seznam `lfPitchAndFamily` hodnot a `LOGFONT` další informace naleznete v členu ve struktuře sady Windows SDK.

*lpszFacename*<br/>
A `CString` nebo ukazatel na řetězec s nulovým ukončením, který určuje název písma. Délka tohoto řetězce nesmí přesáhnout 30 znaků. Funkce Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) lze použít k vytvoření výčtu všech aktuálně dostupných písem. Pokud *lpszFacename* je NULL, GDI používá písmo nezávislé na zařízení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Písmo lze následně vybrat jako písmo pro libovolný kontext zařízení.

Funkce `CreateFont` nevytvoří nové písmo GDI systému Windows. Pouze vybere nejbližší shodu z fyzických písem, které jsou k dispozici pro GDI.

Aplikace mohou při vytváření logického písma používat výchozí nastavení pro většinu parametrů. Parametry, které by měly být vždy uvedeny konkrétní hodnoty jsou *nHeight* a *lpszFacename*. Pokud *nHeight* a *lpszFacename* nejsou nastaveny aplikací, logické písmo, které je vytvořeno je závislé na zařízení.

Po dokončení s `CFont` objektem `CreateFont` vytvořeným `CDC::SelectObject` funkcí použijte k výběru jiného písma do kontextu zařízení a odstraňte `CFont` objekt, který již není potřeba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont::CreateFontIndirect

Inicializuje `CFont` objekt s vlastnostmi uvedenými ve struktuře [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje na `LOGFONT` strukturu, která definuje charakteristiky logického písma.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Písmo lze následně vybrat jako aktuální písmo pro libovolné zařízení.

Toto písmo má vlastnosti zadané ve struktuře [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw) Pokud je písmo vybráno pomocí členské funkce [CDC::SelectObject,](../../mfc/reference/cdc-class.md#selectobject) mapovač písem GDI se pokusí porovnat logické písmo s existujícím fyzickým písmem. Pokud mapovač písma nenalezne přesnou shodu pro logické písmo, poskytuje alternativní písmo, jehož vlastnosti odpovídají co nejvíce požadovaným charakteristikám.

Pokud již nepotřebujete `CFont` objekt vytvořený `CreateFontIndirect` funkcí, `CDC::SelectObject` použijte k výběru jiného písma `CFont` do kontextu zařízení a odstraňte objekt, který již není potřeba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::CreatePointFont

Tato funkce poskytuje jednoduchý způsob, jak vytvořit písmo zadaného písma a velikost bodu.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*nPointSize*<br/>
Požadovaná výška písma v desetinách bodu. (Například předavte 120 požádat o 12bodové písmo.)

*lpszFaceName*<br/>
A `CString` nebo ukazatel na řetězec s nulovým ukončením, který určuje název písma. Délka tohoto řetězce nesmí přesáhnout 30 znaků. Funkce Windows 'EnumFontFamilies lze použít k vytvoření výčtu všech aktuálně dostupných písem. Pokud *lpszFaceName* je NULL, GDI používá písmo nezávislé na zařízení.

*Pdc*<br/>
Ukazatel na [cdc](../../mfc/reference/cdc-class.md) objekt, který má být použit k převodu výšky v *nPointSize* na logické jednotky. Pokud null, kontext zařízení obrazovky se používá pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Automaticky převede výšku v *nPointSize* na logické jednotky pomocí objektu CDC, na který se vztahuje *bod pDC*.

Po dokončení s `CFont` objektem `CreatePointFont` vytvořeným funkcí nejprve vyberte písmo z `CFont` kontextu zařízení a odstraňte objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect

Tato funkce je stejná jako [CreateFontIndirect](#createfontindirect) s tím rozdílem, `lfHeight` že člen `LOGFONT` člen je interpretován v desetinách bodu, nikoli jednotky zařízení.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje na strukturu [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) která definuje charakteristiky logického písma. Člen `lfHeight` struktury `LOGFONT` se měří v desetinách bodu, nikoli v logických jednotkách. (Například nastavte `lfHeight` na 120 požádat o 12bodové písmo.)

*Pdc*<br/>
Ukazatel na objekt [CDC,](../../mfc/reference/cdc-class.md) který má `lfHeight` být použit k převodu výšky na logické jednotky. Pokud null, kontext zařízení obrazovky se používá pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky převede `lfHeight` výšku do logické jednotky pomocí CDC objekt `LOGFONT` upozorňovaný *pDC* před předáním struktury na Windows.

Po dokončení s `CFont` objektem `CreatePointFontIndirect` vytvořeným funkcí nejprve vyberte písmo z `CFont` kontextu zařízení a odstraňte objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>CFont::FromHandle

Vrátí ukazatel na `CFont` objekt, když je daný popisovač HFONT na objekt písma Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parametry

*hPísmo*<br/>
Popisovač HFONT písma systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFont` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CFont` objekt ještě není připojen k popisovač, dočasný `CFont` objekt je vytvořen a připojen. Tento `CFont` dočasný objekt je platný pouze do příště aplikace má nečinnosti čas ve smyčce událostí, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to říct, je, že dočasný objekt je platný pouze při zpracování jedné zprávy okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont::GetLogFont

Volání této funkce načíst `LOGFONT` kopii `CFont`struktury pro .

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parametry

*pLogFont*<br/>
Ukazatel na strukturu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) přijímat informace o písmu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná, jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::operátor HFONT

Pomocí tohoto operátoru získáte popisovač GDI systému `CFont` Windows písma připojeného k objektu.

```
operator HFONT() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu písma Windows GDI připojeného k `CFont` if successful; jinak NULL.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že `CFont` tento operátor se automaticky používá `CFont` pro převody z [písma a text](/windows/win32/gdi/fonts-and-text), můžete předat objekty funkce, které očekávají HfONTs.

Další informace o používání grafických objektů naleznete v [tématu Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
