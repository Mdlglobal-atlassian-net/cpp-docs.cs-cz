---
title: CFont – – třída
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
ms.openlocfilehash: c37b2f657105e0065e0cddb2c508424bd6c89b0a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418620"
---
# <a name="cfont-class"></a>CFont – – třída

Zapouzdřuje písmo rozhraní grafického zařízení (GDI) systému Windows a poskytuje členské funkce pro manipulaci s písmem.

## <a name="syntax"></a>Syntaxe

```
class CFont : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFont –:: CFont –](#cfont)|Vytvoří objekt `CFont`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFont –:: CreateFont](#createfont)|Inicializuje `CFont` se zadanými charakteristikami.|
|[CFont –:: CreateFontIndirect](#createfontindirect)|Inicializuje objekt `CFont` s charakteristikami, které jsou zadány ve struktuře `LOGFONT`.|
|[CFont –:: CreatePointFont](#createpointfont)|Inicializuje `CFont` se zadanou výškou měřenou desetinnou čárkou a typem písma.|
|[CFont –:: CreatePointFontIndirect](#createpointfontindirect)|Stejné jako `CreateFontIndirect` s tím rozdílem, že výška písma je měřena v desetinách bodu a nikoli v logických jednotkách.|
|[CFont –:: FromHandle](#fromhandle)|Vrací ukazatel na objekt `CFont` v případě, že se předali Windows HFONT.|
|[CFont –:: GetLogFont](#getlogfont)|Vyplní `LOGFONT` informacemi o logickém písmu připojeném k objektu `CFont`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFont –:: operator HFONT](#operator_hfont)|Vrátí popisovač písma GDI systému Windows připojený k objektu `CFont`.|

## <a name="remarks"></a>Poznámky

Chcete-li použít objekt `CFont`, Sestavte objekt `CFont` a k němu připojte písmo systému Windows s [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)nebo [CreatePointFontIndirect](#createpointfontindirect)a pak použijte členské funkce objektu pro manipulaci s písmem.

Funkce `CreatePointFont` a `CreatePointFontIndirect` často usnadňují použití než `CreateFont` nebo `CreateFontIndirect`, protože provádějí převod výšky písma z velikosti bodu na logické jednotky automaticky.

Další informace o `CFont`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cfont"></a>CFont –:: CFont –

Vytvoří objekt `CFont`.

```
CFont();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt musí být inicializován pomocí `CreateFont`, `CreateFontIndirect`, `CreatePointFont`nebo `CreatePointFontIndirect` předtím, než je možné jej použít.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>CFont –:: CreateFont

Inicializuje objekt `CFont` se zadanými charakteristikami.

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

*nHeight*<br/>
Určuje požadovanou výšku (v logických jednotkách) písma. Popis najdete v části `lfHeight` člen struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)v Windows SDK. Absolutní hodnota *nHeight* nesmí po převedení překročit 16 384 jednotek zařízení. U všech porovnání výškou vyhledá Mapovač písma největší písmo, které nepřekračuje požadovanou velikost, nebo nejmenší písmo, pokud všechna písma překračují požadovanou velikost.

*nWidth*<br/>
Určuje průměrnou šířku (v logických jednotkách) znaků písma. Pokud je *nWidth* 0, poměr stran zařízení se bude shodovat s poměrem stran podle počtu dostupných písem, aby bylo možné najít nejbližší shodu, který je určený absolutní hodnotou rozdílu.

*nEscapement*<br/>
Určuje úhel (ve stupních 0,1 jednotek) mezi vektorem řídicího panelu a osou x zobrazované plochy. Vektor řídicí sekvence je řádek od začátku prvního a posledního znaku na řádku. Úhel se měří po směru hodinových ručiček od osy x. Další informace najdete v části `lfEscapement` člen ve struktuře `LOGFONT` v Windows SDK.

*nOrientation*<br/>
Určuje úhel (v jednotkách úrovně 0,1) mezi účaří znaku a osou x. Úhel se měří po směru hodinových ručiček od osy x pro systémy souřadnic, ve kterých je směr y dolů a od osy x pro systémy souřadnic, ve kterých je směr y.

*nWeight*<br/>
Určuje tloušťku písma (v Inked pixelech na 1000). Další informace najdete v části člen *lfWeight* ve struktuře `LOGFONT` v Windows SDK. Popsané hodnoty jsou přibližné. skutečný vzhled závisí na řezu písma. Některá písma mají jenom FW_NORMAL, FW_REGULAR a FW_BOLD váhy. Je-li zadán FW_DONTCARE, je použita výchozí váha.

*bItalic*<br/>
Určuje, zda je písmo kurzívou.

*bUnderline*<br/>
Určuje, zda je písmo podtržené.

*cStrikeOut*<br/>
Určuje, zda jsou znaky v písmu potaženy. Určuje přeškrtnutí písma, pokud je nastaveno na nenulovou hodnotu.

*nCharSet*<br/>
Určuje znak písma setSee člena `lfCharSet` ve struktuře `LOGFONT` v Windows SDK pro seznam hodnot.

Znaková sada OEM je závislá na systému.

V systému mohou existovat písma s jinými znakovými sadami. Aplikace, která používá písmo s neznámou znakovou sadou nesmí zkoušet nebo interpretovat řetězce, které mají být vykresleny s tímto písmem. Místo toho by se měly řetězce předat přímo do ovladače výstupního zařízení.

Mapovač písem nepoužívá hodnotu DEFAULT_CHARSET. Aplikace může tuto hodnotu použít, pokud chcete, aby název a velikost písma byly plně popsány u logického písma. Pokud písmo se zadaným názvem neexistuje, může být pro zadané písmo nahrazeno písmo z libovolné znakové sady. Aby nedocházelo k neočekávaným výsledkům, aplikace by měly DEFAULT_CHARSET hodnotu používat zřídka.

*nOutPrecision*<br/>
Určuje požadovanou přesnost výstupu. Přesnost výstupu definuje, jak blízko musí výstup odpovídat požadované výšce písma, šířku, orientaci znaků, řídicímu znaku a rozteči. Seznam hodnot a další informace najdete v části `lfOutPrecision` člen ve struktuře `LOGFONT` v Windows SDK.

*nClipPrecision*<br/>
Určuje požadovanou přesnost oříznutí. Přesnost oříznutí definuje, jak se mají vystřihnout znaky částečně mimo oblast oříznutí. Seznam hodnot naleznete v části `lfClipPrecision` člen ve struktuře `LOGFONT` v Windows SDK.

Chcete-li použít vložené písmo jen pro čtení, musí aplikace zadat CLIP_ENCAPSULATE.

Aby bylo možné zajistit konzistentní rotaci písem zařízení, TrueType a vektoru, může aplikace pomocí operátoru OR kombinovat CLIP_LH_ANGLES hodnotu s jakoukoliv jinou hodnotou *nClipPrecision* . Pokud je nastaven bit CLIP_LH_ANGLES, bude rotace všech písem závislá na tom, zda je orientace systému souřadnic nastavena na levou stranu nebo pravá. (Další informace o orientaci systémů souřadnic naleznete v popisu parametru *nOrientation* .) Pokud CLIP_LH_ANGLES není nastavená, písma zařízení vždycky otočí po směru hodinových ručiček, ale rotace jiných písem závisí na orientaci systému souřadnic.

*nQuality*<br/>
Určuje kvalitu výstupu písma, která definuje, jak se musí rozhraní GDI pokusit vyhledat shodu s atributy logického písma na základě skutečného fyzického písma. Seznam hodnot naleznete v části `lfQuality` člen ve struktuře `LOGFONT` v Windows SDK.

*nPitchAndFamily*<br/>
Určuje rozteč a rodinu písma. Seznam hodnot a další informace najdete v části `lfPitchAndFamily` člen ve struktuře `LOGFONT` v Windows SDK.

*lpszFacename*<br/>
`CString` nebo ukazatel na řetězec zakončený hodnotou null, který určuje název řezu písma. Délka tohoto řetězce nesmí přesáhnout 30 znaků. Funkci Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) lze použít k zobrazení výčtu všech aktuálně dostupných písem. Pokud má *lpszFacename* hodnotu null, používá GDI řez písma nezávislý na zařízení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Písmo lze následně vybrat jako písmo pro libovolný kontext zařízení.

Funkce `CreateFont` nevytvoří nové písmo GDI systému Windows. Pouze vybere nejbližší shodu od fyzických písem dostupných pro GDI.

Aplikace mohou při vytváření logického písma použít výchozí nastavení pro většinu parametrů. Parametry, které by měly vždy mít konkrétní hodnoty, jsou *nHeight* a *lpszFacename*. Pokud aplikace *nHeight* a *lpszFacename* nenastaví, logické písmo, které je vytvořeno, je závislé na zařízení.

Až skončíte s objektem `CFont` vytvořeným funkcí `CreateFont`, použijte `CDC::SelectObject` k výběru jiného písma do kontextu zařízení a pak odstraňte objekt `CFont`, který už není potřeba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>CFont –:: CreateFontIndirect

Inicializuje objekt `CFont` s charakteristikami, které jsou zadány ve struktuře [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw).

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje na strukturu `LOGFONT` definující charakteristiky logického písma.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Písmo lze následně vybrat jako aktuální písmo libovolného zařízení.

Toto písmo má vlastnosti zadané ve struktuře [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) . Při výběru písma pomocí členské funkce [CDC:: VybratObjekt](../../mfc/reference/cdc-class.md#selectobject) se MAPOVAČ písem GDI pokusí vyhledat logické písmo s existujícím fyzickým fontem. Pokud se mapovači písem nenajde přesnou shodu pro logické písmo, poskytne to alternativní písmo, jehož charakteristiky odpovídají toliku požadovaných vlastností.

Pokud již nepotřebujete objekt `CFont` vytvořený funkcí `CreateFontIndirect`, použijte `CDC::SelectObject` k výběru jiného písma do kontextu zařízení a pak odstraňte `CFont` objekt, který již není potřeba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>CFont –:: CreatePointFont

Tato funkce poskytuje jednoduchý způsob, jak vytvořit písmo zadaného řezu a velikosti bodu.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*nPointSize*<br/>
Požadovaná výška písma v desetinách bodu (Například Pass 120 pro vyžádání písma o 12 bodů.)

*lpszFaceName*<br/>
`CString` nebo ukazatel na řetězec zakončený hodnotou null, který určuje název řezu písma. Délka tohoto řetězce nesmí přesáhnout 30 znaků. Funkce EnumFontFamilies systému Windows se dá použít k zobrazení výčtu všech aktuálně dostupných písem. Pokud má *lpszFaceName* hodnotu null, používá GDI řez písma nezávislý na zařízení.

*Emulátor*<br/>
Ukazatel na objekt [CDC](../../mfc/reference/cdc-class.md) , který se použije k převedení výšky v *nPointSize* na logické jednotky. Pokud má hodnotu NULL, je pro převod použit kontext zařízení obrazovky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Automaticky převede výšku v *nPointSize* na logické jednotky pomocí objektu CDC, na který odkazuje *primární řadič domény*.

Až skončíte s objektem `CFont` vytvořeným funkcí `CreatePointFont`, nejdřív vyberte písmo z kontextu zařízení a pak odstraňte objekt `CFont`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>CFont –:: CreatePointFontIndirect

Tato funkce je stejná jako [CreateFontIndirect](#createfontindirect) s tím rozdílem, že `lfHeight` člen `LOGFONT` je interpretována desetinami bodu místo jednotek zařízení.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje na strukturu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , která definuje charakteristiky logického písma. `lfHeight` člen struktury `LOGFONT` se měří v desetinách bodu místo logických jednotek. (Například nastavte `lfHeight` na 120 pro vyžádání písma na 12 bodů.)

*Emulátor*<br/>
Ukazatel na objekt [CDC](../../mfc/reference/cdc-class.md) , který se použije k převedení výšky v `lfHeight` na logické jednotky. Pokud má hodnotu NULL, je pro převod použit kontext zařízení obrazovky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky převede výšku v `lfHeight` na logické jednotky pomocí objektu CDC, na který odkazuje *primární řadič domény* , před předáním struktury `LOGFONT` do systému Windows.

Až skončíte s objektem `CFont` vytvořeným funkcí `CreatePointFontIndirect`, nejdřív vyberte písmo z kontextu zařízení a pak odstraňte objekt `CFont`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>CFont –:: FromHandle

Vrací ukazatel na objekt `CFont`, pokud je předána obslužná rutina HFONT objektu Font systému Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
HFONT popisovač písma systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CFont` v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt `CFont` již není k popisovači připojen, je vytvořen a připojen dočasný objekt `CFont`. Tento dočasný `CFont` objekt je platný pouze do okamžiku, kdy aplikace bude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to vyjádřit, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>CFont –:: GetLogFont

Voláním této funkce načtete kopii `LOGFONT` struktury pro `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parametry

*pLogFont*<br/>
Ukazatel na strukturu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , aby se zobrazily informace o písmech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná, jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>CFont –:: operator HFONT

Tento operátor použijte k získání popisovače Windows GDI písma připojeného k objektu `CFont`.

```
operator HFONT() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu písma GDI systému Windows připojeného k `CFont` v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že tento operátor je automaticky použit pro převody z `CFont` na [písma a text](/windows/win32/gdi/fonts-and-text), můžete předat objekty `CFont` funkcím, které očekávají HFONTs.

Další informace o použití grafických objektů naleznete v tématu [Graphics Objects](/windows/win32/gdi/graphic-objects) in Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Viz také

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
