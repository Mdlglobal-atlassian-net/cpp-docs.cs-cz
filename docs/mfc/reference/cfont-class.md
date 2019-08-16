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
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506487"
---
# <a name="cfont-class"></a>CFont – – třída

Zapouzdřuje písmo rozhraní grafického zařízení (GDI) systému Windows a poskytuje členské funkce pro manipulaci s písmem.

## <a name="syntax"></a>Syntaxe

```
class CFont : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFont –:: CFont –](#cfont)|`CFont` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|`CFont` Inicializuje se zadanými charakteristikami.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializuje objekt s vlastnostmi, které jsou zadány `LOGFONT` ve struktuře. `CFont`|
|[CFont::CreatePointFont](#createpointfont)|Inicializuje a `CFont` se zadanou výškou měřenou desetinnou čárkou a typem písma.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Totéž jako `CreateFontIndirect` s tím rozdílem, že výška písma je měřena v desetinách bodu a nikoli na logických jednotkách.|
|[CFont –:: FromHandle](#fromhandle)|Vrací ukazatel na `CFont` objekt v případě, že je zadán systém Windows HFONT.|
|[CFont::GetLogFont](#getlogfont)|Vyplní informace o logickém písmu připojeném `CFont` k objektu. `LOGFONT`|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CFont –:: operator HFONT](#operator_hfont)|Vrátí popisovač písma GDI systému Windows připojený k `CFont` objektu.|

## <a name="remarks"></a>Poznámky

Chcete-li `CFont` použít objekt, `CFont` Sestavte objekt a připojte k němu písmo systému Windows pomocí [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)nebo [CreatePointFontIndirect](#createpointfontindirect)a pak použijte člena objektu. funkce pro manipulaci s písmem.

`CreateFont` `CreateFontIndirect` Funkce a jsou`CreatePointFontIndirect` často jednodušší použít než nebo, protože provádějí převod výšky písma z velikosti bodu na logické jednotky automaticky. `CreatePointFont`

Další informace o `CFont`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cfont"></a>CFont –:: CFont –

`CFont` Vytvoří objekt.

```
CFont();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt musí `CreateFont`být inicializován pomocí,, `CreateFontIndirect` `CreatePointFont`nebo `CreatePointFontIndirect` předtím, než může být použit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>CFont –:: CreateFont

`CFont` Inicializuje objekt se zadanými charakteristikami.

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
Určuje požadovanou výšku (v logických jednotkách) písma. Popis najdete v části Windows SDK struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw) `lfHeight` Absolutní hodnota *nHeight* nesmí po převedení překročit 16 384 jednotek zařízení. U všech porovnání výškou vyhledá Mapovač písma největší písmo, které nepřekračuje požadovanou velikost, nebo nejmenší písmo, pokud všechna písma překračují požadovanou velikost.

*nWidth*<br/>
Určuje průměrnou šířku (v logických jednotkách) znaků písma. Pokud je *nWidth* 0, poměr stran zařízení se bude shodovat s poměrem stran podle počtu dostupných písem, aby bylo možné najít nejbližší shodu, který je určený absolutní hodnotou rozdílu.

*nEscapement*<br/>
Určuje úhel (ve stupních 0,1 jednotek) mezi vektorem řídicího panelu a osou x zobrazované plochy. Vektor řídicí sekvence je řádek od začátku prvního a posledního znaku na řádku. Úhel se měří po směru hodinových ručiček od osy x. Další informace najdete v tématu `LOGFONT` o členovivestruktuřevWindowsSDK.`lfEscapement`

*nOrientation*<br/>
Určuje úhel (v jednotkách úrovně 0,1) mezi účaří znaku a osou x. Úhel se měří po směru hodinových ručiček od osy x pro systémy souřadnic, ve kterých je směr y dolů a od osy x pro systémy souřadnic, ve kterých je směr y.

*nWeight*<br/>
Určuje tloušťku písma (v Inked pixelech na 1000). Další informace najdete v tématu lfWeight `LOGFONT` člen ve struktuře v Windows SDK. Popsané hodnoty jsou přibližné. skutečný vzhled závisí na řezu písma. Některá písma mají pouze váhy FW_NORMAL, FW_REGULAR a FW_BOLD. Je-li zadán parametr FW_DONTCARE, je použita výchozí váha.

*bItalic*<br/>
Určuje, zda je písmo kurzívou.

*bUnderline*<br/>
Určuje, zda je písmo podtržené.

*cStrikeOut*<br/>
Určuje, zda jsou znaky v písmu potaženy. Určuje přeškrtnutí písma, pokud je nastaveno na nenulovou hodnotu.

*nCharSet*<br/>
Určuje znak písma setSee `lfCharSet` člena `LOGFONT` ve struktuře v Windows SDK pro seznam hodnot.

Znaková sada OEM je závislá na systému.

V systému mohou existovat písma s jinými znakovými sadami. Aplikace, která používá písmo s neznámou znakovou sadou nesmí zkoušet nebo interpretovat řetězce, které mají být vykresleny s tímto písmem. Místo toho by se měly řetězce předat přímo do ovladače výstupního zařízení.

Mapovač písma nepoužívá hodnotu DEFAULT_CHARSET. Aplikace může tuto hodnotu použít, pokud chcete, aby název a velikost písma byly plně popsány u logického písma. Pokud písmo se zadaným názvem neexistuje, může být pro zadané písmo nahrazeno písmo z libovolné znakové sady. Aby nedocházelo k neočekávaným výsledkům, aplikace by měly používat DEFAULT_CHARSET hodnotu.

*nOutPrecision*<br/>
Určuje požadovanou přesnost výstupu. Přesnost výstupu definuje, jak blízko musí výstup odpovídat požadované výšce písma, šířku, orientaci znaků, řídicímu znaku a rozteči. Seznam hodnot a další informace `LOGFONT` najdete v tématu o členovivestruktuřevWindowsSDK.`lfOutPrecision`

*nClipPrecision*<br/>
Určuje požadovanou přesnost oříznutí. Přesnost oříznutí definuje, jak se mají vystřihnout znaky částečně mimo oblast oříznutí. Seznam hodnot naleznete v části `LOGFONT` členvestruktuřevWindowsSDK.`lfClipPrecision`

Chcete-li použít vložené písmo jen pro čtení, musí aplikace zadat CLIP_ENCAPSULATE.

Aby bylo možné zajistit konzistentní rotaci písem zařízení, TrueType a vektoru, může aplikace pomocí operátoru OR kombinovat hodnotu CLIP_LH_ANGLES s jakoukoli jinou hodnotou *nClipPrecision* . Pokud je nastaven bit CLIP_LH_ANGLES, je rotace všech písem závislá na tom, zda je orientace systému souřadnic nastavena na levou stranu nebo pravá. (Další informace o orientaci systémů souřadnic naleznete v popisu parametru *nOrientation* .) Pokud není nastavená CLIP_LH_ANGLES, písma zařízení vždycky otočí proti směru hodinových ručiček, ale rotace jiných písem závisí na orientaci systému souřadnic.

*nQuality*<br/>
Určuje kvalitu výstupu písma, která definuje, jak se musí rozhraní GDI pokusit vyhledat shodu s atributy logického písma na základě skutečného fyzického písma. Seznam hodnot naleznete v části `LOGFONT` členvestruktuřevWindowsSDK.`lfQuality`

*nPitchAndFamily*<br/>
Určuje rozteč a rodinu písma. Seznam hodnot a další informace `LOGFONT` najdete v tématu o členovivestruktuřevWindowsSDK.`lfPitchAndFamily`

*lpszFacename*<br/>
Ukazatel `CString` nebo na řetězec zakončený hodnotou null, který určuje název řezu písma. Délka tohoto řetězce nesmí přesáhnout 30 znaků. Funkci Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) lze použít k zobrazení výčtu všech aktuálně dostupných písem. Pokud má *lpszFacename* hodnotu null, používá GDI řez písma nezávislý na zařízení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Písmo lze následně vybrat jako písmo pro libovolný kontext zařízení.

`CreateFont` Funkce nevytvoří nové písmo GDI systému Windows. Pouze vybere nejbližší shodu od fyzických písem dostupných pro GDI.

Aplikace mohou při vytváření logického písma použít výchozí nastavení pro většinu parametrů. Parametry, které by měly vždy mít konkrétní hodnoty, jsou *nHeight* a *lpszFacename*. Pokud aplikace *nHeight* a *lpszFacename* nenastaví, logické písmo, které je vytvořeno, je závislé na zařízení.

Po dokončení `CFont` objektu vytvořeného `CreateFont` funkcí použijte `CDC::SelectObject` k výběru jiného písma `CFont` do kontextu zařízení a pak odstraňte objekt, který již není potřeba.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>CFont –:: CreateFontIndirect

Inicializuje objekt s vlastnostmi, které jsou zadány ve struktuře [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw) `CFont`

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje na `LOGFONT` strukturu, která definuje charakteristiky logického písma.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Písmo lze následně vybrat jako aktuální písmo libovolného zařízení.

Toto písmo má vlastnosti zadané ve struktuře [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) . Při výběru písma pomocí členské funkce [CDC:: VybratObjekt](../../mfc/reference/cdc-class.md#selectobject) se MAPOVAČ písem GDI pokusí vyhledat logické písmo s existujícím fyzickým fontem. Pokud se mapovači písem nenajde přesnou shodu pro logické písmo, poskytne to alternativní písmo, jehož charakteristiky odpovídají toliku požadovaných vlastností.

Pokud již nepotřebujete `CFont` objekt vytvořený `CreateFontIndirect` funkcí, použijte `CDC::SelectObject` k výběru jiného písma `CFont` do kontextu zařízení a pak odstraňte objekt, který již není potřeba.

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
Ukazatel `CString` nebo na řetězec zakončený hodnotou null, který určuje název řezu písma. Délka tohoto řetězce nesmí přesáhnout 30 znaků. Funkce EnumFontFamilies systému Windows se dá použít k zobrazení výčtu všech aktuálně dostupných písem. Pokud má *lpszFaceName* hodnotu null, používá GDI řez písma nezávislý na zařízení.

*pDC*<br/>
Ukazatel na objekt [CDC](../../mfc/reference/cdc-class.md) , který se použije k převedení výšky v *nPointSize* na logické jednotky. Pokud má hodnotu NULL, je pro převod použit kontext zařízení obrazovky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Automaticky převede výšku v *nPointSize* na logické jednotky pomocí objektu CDC, na který odkazuje *primární řadič domény*.

Až skončíte s `CFont` objektem vytvořeným `CreatePointFont` funkcí, nejdřív vyberte písmo mimo `CFont` kontext zařízení a pak objekt odstraňte.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>CFont –:: CreatePointFontIndirect

Tato funkce je stejná jako [CreateFontIndirect](#createfontindirect) s tím rozdílem `lfHeight` , že člen `LOGFONT` je interpretován v desetinách bodu místo jednotek zařízení.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje na strukturu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , která definuje charakteristiky logického písma. `lfHeight` Člen`LOGFONT` struktury se měří v desetinách bodu místo logických jednotek. (Například nastavte `lfHeight` na 120 pro vyžádání písma o 12 bodů.)

*pDC*<br/>
Ukazatel na objekt [CDC](../../mfc/reference/cdc-class.md) , který se použije k převedení výšky `lfHeight` na logické jednotky. Pokud má hodnotu NULL, je pro převod použit kontext zařízení obrazovky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky převede výšku do `lfHeight` logických jednotek pomocí objektu CDC, na který odkazuje *primární řadič domény* , před předáním `LOGFONT` struktury na systém Windows.

Až skončíte s `CFont` objektem vytvořeným `CreatePointFontIndirect` funkcí, nejdřív vyberte písmo mimo `CFont` kontext zařízení a pak objekt odstraňte.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>CFont –:: FromHandle

Vrátí ukazatel na `CFont` objekt, pokud je předána obslužná rutina HFONT objektu Font systému Windows GDI.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
HFONT popisovač písma systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFont` objekt v případě úspěchu; jinak null.

### <a name="remarks"></a>Poznámky

Pokud objekt již není k popisovači připojen, je vytvořen a připojen `CFont` dočasný objekt. `CFont` Tento dočasný `CFont` objekt je platný pouze do příštího okamžiku, kdy aplikace nebude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to vyjádřit, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>CFont –:: GetLogFont

Voláním této funkce načtete kopii `LOGFONT` struktury pro. `CFont`

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

Tento operátor použijte k získání popisovače Windows GDI písma připojeného k `CFont` objektu.

```
operator HFONT() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu písma GDI systému Windows, který `CFont` je v případě úspěchu připojen, jinak null.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že tento operátor je automaticky `CFont` použit pro převody z na [písma a text](/windows/win32/gdi/fonts-and-text), můžete předat `CFont` objekty funkcím, které očekávají HFONTs.

Další informace o použití grafických objektů naleznete v tématu [Graphics Objects](/windows/win32/gdi/graphic-objects) in Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
