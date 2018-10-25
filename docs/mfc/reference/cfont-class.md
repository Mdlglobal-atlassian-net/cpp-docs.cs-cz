---
title: Cfont – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c914bab9ab7a4bb15f6fe3d2820d7ff2534c3c6e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053640"
---
# <a name="cfont-class"></a>Cfont – třída

Zapouzdřuje písmo rozhraní GDI systému Windows grafiky zařízení a poskytuje členské funkce pro manipulaci s písmem.

## <a name="syntax"></a>Syntaxe

```
class CFont : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFont::CFont](#cfont)|Vytvoří `CFont` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Inicializuje `CFont` se zadané vlastnosti.|
|[CFont::CreateFontIndirect](#createfontindirect)|Inicializuje `CFont` objekt s vlastnostmi podle `LOGFONT` struktury.|
|[CFont::CreatePointFont](#createpointfont)|Inicializuje `CFont` s zadaná výška, měřený v desetiny bodu a řez písma.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Stejné jako `CreateFontIndirect` s tím rozdílem, že výšku písma se měří v desetiny bod spíše než logické jednotky.|
|[CFont::FromHandle](#fromhandle)|Vrací ukazatel `CFont` objektu při Windows HFONT.|
|[CFont::GetLogFont](#getlogfont)|Vyplní `LOGFONT` s informacemi o připojen k logické písmo `CFont` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFont::operator HFONT](#operator_hfont)|Vrátí popisovač písem Windows GDI připojené k `CFont` objektu.|

## <a name="remarks"></a>Poznámky

Použití `CFont` objektu, sestavit `CFont` objektu a připojit se k němu pomocí Windows písma [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont), nebo [CreatePointFontIndirect](#createpointfontindirect)a pak pomocí objektu členské funkce pro manipulaci s písma.

`CreatePointFont` a `CreatePointFontIndirect` funkce jsou často jednodušší než `CreateFont` nebo `CreateFontIndirect` od dělají převod výška písma z bodu velikost logické jednotky automaticky.

Další informace o `CFont`, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cgdiobject –](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cfont"></a>  CFont::CFont

Vytvoří `CFont` objektu.

```
CFont();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt je nutné inicializovat s `CreateFont`, `CreateFontIndirect`, `CreatePointFont`, nebo `CreatePointFontIndirect` předtím, než je možné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>  CFont::CreateFont

Inicializuje `CFont` objekt se zadanou vlastností.

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
Určuje požadovanou výšku (v logických jednotkách) písma. Najdete v článku `lfHeight` člena [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)struktura v sadě Windows SDK pro popis. Absolutní hodnota *nHeight* nesmí být delší než 16 384 jednotky zařízení po převedení. Pro všechny výška porovnání Mapovač písma hledá největší písmo, které není delší než požadovaná velikost nebo nejmenší velikost písma všechna písma překročení požadované velikosti.

*nWidth*<br/>
Určuje průměrnou šířku (v logických jednotkách) znaků v písmu. Pokud *nWidth* je 0, poměru stran zařízení, bude hledána digitalizaci poměr stran dostupných písem najít nejbližší shodu, což je dáno absolutní hodnota rozdílu.

*nEscapement*<br/>
Určuje úhel (v jednotkách mírou 0,1) mezi escapement vektoru a osu x zobrazovacím povrchu. Vektor escapement je přeškrtnutým počátek první a poslední znak na řádku. Úhel měří proti směru hodinových ručiček od osy x. Najdete v článku `lfEscapement` člen `LOGFONT` struktura v sadě Windows SDK pro další informace.

*nOrientation*<br/>
Určuje úhel (v jednotkách mírou 0,1) mezi osy x a snímek směrného plánu znaku. Úhel měří proti směru hodinových ručiček od osy x souřadnicových systémů, ve kterých je směru osy y po směru hodinových ručiček od osy x souřadnicových systémů, ve kterých směru y se nahoru a dolů.

*nWeight*<br/>
Určuje tloušťku písma (v pixelech propojeno na 1000). Najdete v článku *lfWeight* člen `LOGFONT` struktura v sadě Windows SDK pro další informace. Popisuje hodnoty jsou jen přibližné; skutečné vzhled závisí na řezu písma. Některá písma mají pouze FW_NORMAL FW_REGULAR a FW_BOLD váhy. Pokud FW_DONTCARE není zadán, použije se váhu výchozí.

*bItalic*<br/>
Určuje, zda je písmo kurzíva.

*bUnderline*<br/>
Určuje, zda je písmo podtržené.

*cStrikeOut*<br/>
Určuje, zda jsou znaky v písmu dopadu navýšení kapacity. Určuje přeškrtnuté písmo-li nastavit na nenulovou hodnotu.

*nCharSet*<br/>
Určuje znak setSee písma `lfCharSet` člen `LOGFONT` struktura v sadě Windows SDK pro seznam hodnot.

Znakové sady OEM je závislé na systému.

V systému může existovat písem s jiných množin znaků. Aplikace, která používá písmo s Neznámý znaková sada se nesmíte pokoušet přeložit nebo interpretace řetězce, které mají být vykreslen pomocí písma. Místo toho řetězce by měly být předány přímo výstup ovladač zařízení.

Mapovač písma nepoužívá DEFAULT_CHARSET hodnotu. Aplikace může použít tato hodnota umožňuje název a velikost písma, která plně popisují logické písma. Pokud písma se zadaným názvem neexistuje, můžete pro zadaný font nahrazena písmo z jakékoli znakovou sadu. Aby se zabránilo neočekávaným výsledkům, aplikace by měly používat hodnotu DEFAULT_CHARSET opatrně.

*nOutPrecision*<br/>
Určuje přesnost požadovaný výstup. Výstup přesnosti definuje, jak blízko se musí shodovat ve výstupu, výšku, šířku, orientace znak, escapement a od požadované písmo. Najdete v článku `lfOutPrecision` člen `LOGFONT` struktura v sadě Windows SDK pro seznam hodnot a další informace.

*nClipPrecision*<br/>
Určuje požadovanou výstřižek přesnosti. Výstřižek přesnosti definuje, jak Galerie znaky, které jsou částečně mimo oblast ořezu. Najdete v článku `lfClipPrecision` člen `LOGFONT` struktura v sadě Windows SDK pro seznam hodnot.

Pokud chcete používat vložené písmo jen pro čtení, musíte zadat aplikaci CLIP_ENCAPSULATE.

K dosažení konzistentní otáčení zařízení TrueType a vektorová písma, aplikace může použít operátor OR na hodnoty CLIP_LH_ANGLES kombinovat s žádným z druhé *nClipPrecision* hodnoty. Pokud je nastaven CLIP_LH_ANGLES bit, otočení pro všechna písma závisí na tom orientace souřadnicový systém levou nebo pravou rukou. (Další informace o orientaci souřadnicových systémů, najdete v popisu *nOrientation* parametru.) Pokud není nastavena CLIP_LH_ANGLES, písma zařízení vždy Otočit proti směru hodinových ručiček, ale otočení jiná písma je závislá na orientaci souřadnicový systém.

*nQuality*<br/>
Určuje, Kvalita výstupu písma, která definuje, jak pečlivě rozhraní GDI musí pokus o porovnání atributů logické písma u těch, které skutečné fyzické písma. Najdete v článku `lfQuality` člen `LOGFONT` struktura v sadě Windows SDK pro seznam hodnot.

*nPitchAndFamily*<br/>
Určuje rozteč a rodiny písma. Najdete v článku `lfPitchAndFamily` člen `LOGFONT` struktura v sadě Windows SDK pro seznam hodnot a další informace.

*lpszFacename*<br/>
A `CString` nebo ukazatel na řetězec zakončený hodnotou null, který určuje název řez písma. Délka tohoto řetězce nesmí být delší než 30 znaků. Windows [EnumFontFamilies](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesa) funkce je možné vytvořit výčet všech aktuálně dostupných písma. Pokud *lpszFacename* má hodnotu NULL, používá rozhraní GDI řez písma nezávislých na zařízení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Písmo je následně vybrat jako písma pro jakýkoli kontext zařízení.

`CreateFont` Funkce nevytvoří nový písem Windows GDI. Vybere pouze nejvíce odpovídá z fyzických písma, které jsou k dispozici pro rozhraní GDI.

Aplikace můžete použít výchozí nastavení pro většinu parametrů při vytváření logické písma. Parametry, které by měly vždy mít konkrétní hodnoty jsou *nHeight* a *lpszFacename*. Pokud *nHeight* a *lpszFacename* nejsou nastavená, aplikací, je logický písmo, které se vytvoří závislé na zařízení.

Po dokončení se `CFont` objekt vytvořený pomocí `CreateFont` funkci, použijte `CDC::SelectObject` do kontextu zařízení vyberte jiné písmo, odstraňte `CFont` objekt, který už je nepotřebujete.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>  CFont::CreateFontIndirect

Inicializuje `CFont` objekt s vlastnostmi podle [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)struktury.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje `LOGFONT` strukturu, která definuje vlastnosti logické písma.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Písmo je následně vybrat jako aktuální písmo pro libovolné zařízení.

Toto písmo má zadaná ve vlastnosti [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury. Když je vybraná písma s použitím [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) členskou funkci Mapovač písem GDI pokusí porovnat logické písma s existující fyzické písma. V případě, že mapovač písma nepodaří najít přesnou shodu pro logické písmo, poskytuje alternativní písma, jejichž vlastnosti odpovídají tolik požadované vlastnosti, jako je to možné.

Pokud už nepotřebujete `CFont` objekt vytvořený pomocí `CreateFontIndirect` funkci, použijte `CDC::SelectObject` do kontextu zařízení vyberte jiné písmo, odstraňte `CFont` objekt, který už je nepotřebujete.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>  CFont::CreatePointFont

Tato funkce poskytuje jednoduchý způsob, jak vytvořit písmo pro zadaný řez písma a velikost v bodech.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*nPointSize*<br/>
Požadovaná výška písma v desetiny bod. (Například předejte 120 požádat o 12 bodů písma.)

*lpszFaceName*<br/>
A `CString` nebo ukazatel na řetězec zakončený hodnotou null, který určuje název řez písma. Délka tohoto řetězce nesmí být delší než 30 znaků. Windows "EnumFontFamilies funkce je možné vytvořit výčet všech aktuálně dostupných písma. Pokud *lpszFaceName* má hodnotu NULL, používá rozhraní GDI řez písma nezávislých na zařízení.

*primární řadič domény*<br/>
Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, který se má použít k převodu výšku v *nPointSize* do logických jednotek. Pokud má hodnotu NULL, kontext zařízení obrazovky se používá pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Automaticky převede výšku v *nPointSize* do logických jednotek pomocí objektu CDC odkazované *primárního řadiče domény*.

Po dokončení se `CFont` objekt vytvořený pomocí `CreatePointFont` funkci, nejprve vyberte písmo mimo kontext zařízení a pak odstranit `CFont` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect

Tato funkce je stejná jako [CreateFontIndirect](#createfontindirect) s tím rozdílem, že `lfHeight` člena `LOGFONT` interpretována desetiny bodu spíše než zařízení jednotky.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
Odkazuje [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) strukturu, která definuje vlastnosti logické písma. `lfHeight` Člena `LOGFONT` struktura se měří v desetiny bod spíše než logické jednotky. (Například nastavit `lfHeight` 120 požádat o 12 bodů písma.)

*primární řadič domény*<br/>
Ukazatel [CDC](../../mfc/reference/cdc-class.md) objekt, který se má použít k převodu výšku v `lfHeight` do logických jednotek. Pokud má hodnotu NULL, kontext zařízení obrazovky se používá pro převod.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce automaticky převede výšku v `lfHeight` do logických jednotek pomocí objektu CDC odkazované *primárního řadiče domény* před předáním `LOGFONT` struktury k Windows.

Po dokončení se `CFont` objekt vytvořený pomocí `CreatePointFontIndirect` funkci, nejprve vyberte písmo mimo kontext zařízení a pak odstranit `CFont` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>  CFont::FromHandle

Vrací ukazatel `CFont` objektu při popisovač HFONT na objekt Windows GDI písma.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parametry

*hFont*<br/>
Popisovač HFONT písmo Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CFont` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud `CFont` objekt už není připojen ke zpracování, dočasný `CFont` objekt se vytvoří a připojí. Tento dočasný `CFont` objektu je platná pouze v až při příštím má aplikace čas nečinnosti v jeho smyčkou událostí, na které čas všechny dočasné obrázek objekty budou odstraněny. Jinými slovy to je, že dočasný objekt je platný pouze při zpracování zprávy jedno okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>  CFont::GetLogFont

Volání této funkce načtete kopii `LOGFONT` strukturu pro `CFont`.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parametry

*pLogFont*<br/>
Ukazatel [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) strukturu pro příjem těchto písmo.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce uspěje, jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>  CFont::operator HFONT

Získat popisovač Windows GDI písma připojené k použití tohoto operátoru `CFont` objektu.

```
operator HFONT() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu písem Windows GDI připojené k `CFont` Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Protože tento operátor se automaticky používá pro převody z `CFont` k [písem a textu](/windows/desktop/gdi/fonts-and-text), můžete předat `CFont` objekty funkce, které očekávají HFONTs.

Další informace o použití grafických objektů najdete v tématu [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

