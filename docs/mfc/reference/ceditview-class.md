---
title: Třída CEditView
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: 33b5975eea534eeaf308f73b5ca7fca2cd76787f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753195"
---
# <a name="ceditview-class"></a>Třída CEditView

Typ třídy zobrazení, která poskytuje funkce ovládacího prvku pro úpravy systému Windows a lze ji použít k implementaci jednoduchých funkcí textového editoru.

## <a name="syntax"></a>Syntaxe

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|Vytvoří objekt typu `CEditView`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CEditView::FindText](#findtext)|Vyhledá řetězec v textu.|
|[CEditView::GetBufferLength](#getbufferlength)|Získá délku vyrovnávací paměti znaků.|
|[CEditView::GetEditCtrl](#geteditctrl)|Poskytuje přístup `CEdit` k části `CEditView` objektu (ovládací prvek pro úpravy systému Windows).|
|[CEditView::GetPrinterFont](#getprinterfont)|Načte aktuální písmo tiskárny.|
|[CEditView::GetSelectedText](#getselectedtext)|Načte aktuální výběr textu.|
|[CEditView::LockBuffer](#lockbuffer)|Zamkne vyrovnávací paměť.|
|[CEditView::PrintInsideRect](#printinsiderect)|Vykreslí text uvnitř daného obdélníku.|
|[CEditView::SerializeRaw](#serializeraw)|Serializuje `CEditView` objekt na disk jako nezpracovaný text.|
|[CEditView::SetPrinterFont](#setprinterfont)|Nastaví nové písmo tiskárny.|
|[CEditView::SetTabstops](#settabstops)|Nastaví zarážky tabulátorů jak pro zobrazení na obrazovce, tak pro tisk.|
|[CEditView::Odemknoutvyrovnávací paměť](#unlockbuffer)|Odemkne vyrovnávací paměť.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CeditView::OnFindNext](#onfindnext)|Vyhledá další výskyt textového řetězce.|
|[CeditView::OnReplaceAll](#onreplaceall)|Nahradí všechny výskyty daného řetězce novým řetězcem.|
|[CEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|
|[CeditView::OnTextNotFound](#ontextnotfound)|Volána, když operace hledání se nezdaří odpovídat žádné další text.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Výchozí styl pro `CEditView`objekty typu .|

## <a name="remarks"></a>Poznámky

Třída `CEditView` poskytuje následující další funkce:

- Tisk.

- Najít a nahradit.

Protože `CEditView` třída je odvozenina třídy `CView`, objekty třídy `CEditView` lze použít s dokumenty a šablony dokumentů.

Každý `CEditView` ovládací prvek text je uložen ve svém vlastním objektu globální paměti. Aplikace může mít libovolný `CEditView` počet objektů.

Vytvořte objekty typu, `CEditView` pokud chcete upravit okno s přidanou funkcí uvedenou výše, nebo pokud chcete jednoduché funkce textového editoru. Objekt `CEditView` může zabírat celou klientskou oblast okna. Odvodit `CEditView` vlastní třídy z přidat nebo upravit základní funkce nebo deklarovat třídy, které lze přidat do šablony dokumentu.

Výchozí implementace třídy `CEditView` zpracovává následující příkazy: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT a ID_FILE_PRINT.

Výchozí limit znaků `CEditView` je (1024 \* 1024 - 1 = 1048575). To lze změnit voláním EM_LIMITTEXT funkce základního ovládacího prvku úprav. Limity se však liší v závislosti na operačním systému a typu ovládacího prvku úprav (jeden nebo víceřádkový). Další informace o těchto omezeních naleznete [v tématu EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Chcete-li změnit tento limit v `OnCreate()` ovládacím `CEditView` prvku, přepište funkci pro vaši třídu a vložte následující řádek kódu:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Objekty `CEditView` typu (nebo typů `CEditView`odvozených z ) mají následující omezení:

- `CEditView`neimplementuje pravda, co vidíte, je to, co dostanete (WYSIWYG) editace. Pokud je na obrazovce na výběr mezi čitelností `CEditView` na obrazovce a odpovídajícím tištěným výstupem, zvolí tesek čitelnost obrazovky.

- `CEditView`může zobrazovat text pouze v jednom písmu. Není podporováno žádné speciální formátování znaků. Viz třída [CRichEditView](../../mfc/reference/cricheditview-class.md) pro větší možnosti.

- Množství textu, `CEditView` který může obsahovat, je omezené. Limity jsou stejné jako `CEdit` pro ovládací prvek.

Další informace `CEditView`o tématu naleznete [v tématu Odvozené třídy zobrazení dostupné v knihovně MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>CEditView::CEditView

Vytvoří objekt typu `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu musíte volat funkci [CWnd::Create](../../mfc/reference/cwnd-class.md#create) před použitím ovládacího prvku pro úpravy. Pokud odvodit `CEditView` třídu z a `CWinApp::AddDocTemplate`přidat ji do šablony pomocí `Create` , rozhraní framework volá tento konstruktor a funkce.

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyleDefault

Obsahuje výchozí styl `CEditView` objektu.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Poznámky

Předajte tento statický člen jako parametr *dwStyle* `Create` funkce, abyste získali `CEditView` výchozí styl pro objekt.

## <a name="ceditviewfindtext"></a><a name="findtext"></a>CEditView::FindText

Volání `FindText` funkce prohledávat vyrovnávací paměti `CEditView` textu objektu.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nalezen.

*bDalší*<br/>
Určuje směr hledání. Pokud TRUE, směr hledání je směrem ke konci vyrovnávací paměti. Pokud false, směr hledání je směrem k začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud true, hledání je rozlišování velkých a malých písmen. Pokud false, hledání není malá a velká písmena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je nalezen hledaný text; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce prohledá text ve vyrovnávací paměti pro text určený *lpszFind*, počínaje aktuálním výběrem, ve směru určeném *bNext*a s rozlišením velkých a malých písmen určených *bCase*. Pokud je text nalezen, nastaví výběr na nalezený text a vrátí nenulovou hodnotu. Pokud text nebyl nalezen, funkce vrátí 0.

Obvykle není nutné volat `FindText` funkci, pokud `OnFindNext`přepsat , `FindText`který volá .

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>CEditView::GetBufferLength

Volání této členské funkce získat počet znaků aktuálně ve vyrovnávací paměti ovládacího prvku úpravy, bez zahrnutí zakončení null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka řetězce ve vyrovnávací paměti.

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>CEditView::GetEditCtrl

Volání `GetEditCtrl` pro získání odkazu na ovládací prvek úprav používaný v zobrazení úprav.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CEdit` objekt.

### <a name="remarks"></a>Poznámky

Tento ovládací prvek je typu [CEdit](../../mfc/reference/cedit-class.md), takže můžete manipulovat `CEdit` s ovládacím prvkem pro úpravy systému Windows přímo pomocí členských funkcí.

> [!CAUTION]
> Použití `CEdit` objektu může změnit stav podkladového ovládacího prvku pro úpravy systému Windows. Například byste neměli měnit nastavení tabulátoru pomocí funkce `CEditView` [CEdit::SetTabStops,](../../mfc/reference/cedit-class.md#settabstops) protože tato nastavení ukládá do mezipaměti pro použití v ovládacím prvku pro úpravy i při tisku. Místo toho použijte [CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>CEditView::GetPrinterFont

Volání `GetPrinterFont` získat ukazatel na [cfont](../../mfc/reference/cfont-class.md) objekt, který popisuje aktuální písmo tiskárny.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFont` objekt, který určuje aktuální písmo tiskárny; Null, pokud písmo tiskárny nebyla nastavena. Ukazatel může být dočasné a by neměly být uloženy pro pozdější použití.

### <a name="remarks"></a>Poznámky

Pokud písmo tiskárny nebylo nastaveno, je `CEditView` výchozím chováním tisku třídy tisk pomocí stejného písma, které bylo použito pro zobrazení.

Tato funkce slouží k určení aktuálního písma tiskárny. Pokud není požadované písmo tiskárny, změňte jej pomocí [ceditview::SetPrinterFont.](#setprinterfont)

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>CEditView::GetSelectedText

Volání `GetSelectedText` zkopírovat vybraný text `CString` do objektu, až do konce výběru nebo znak předcházející první znak carriage-return ve výběru.

```cpp
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parametry

*strVýsledek*<br/>
Odkaz na `CString` objekt, který má přijmout vybraný text.

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView::LockBuffer

Volání této členské funkce získat ukazatel vyrovnávací paměti. Vyrovnávací paměť by neměla být změněna.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť ovládacího prvku pro úpravy.

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>CeditView::OnFindNext

Prohledá text ve vyrovnávací paměti pro text určený *lpszFind*, ve směru určeném *bNext*, s rozlišování velkých a malých písmen určených *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nalezen.

*bDalší*<br/>
Určuje směr hledání. Pokud TRUE, směr hledání je směrem ke konci vyrovnávací paměti. Pokud false, směr hledání je směrem k začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud true, hledání je rozlišování velkých a malých písmen. Pokud false, hledání není malá a velká písmena.

### <a name="remarks"></a>Poznámky

Hledání začíná na začátku aktuálního výběru a je provedeno prostřednictvím volání [FindText](#findtext). Ve výchozí implementaci `OnFindNext` volá [OnTextNotFound,](#ontextnotfound) pokud text nebyl nalezen.

Přepsáním `OnFindNext` změníte `CEditView`způsob, jakým odvozený objekt prohledává text. `CEditView`hovory, `OnFindNext` když uživatel ve standardním dialogovém okně Najít zvolí tlačítko Najít další.

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>CeditView::OnReplaceAll

`CEditView`volání, `OnReplaceAll` když uživatel vybere tlačítko Nahradit vše ve standardním dialogovém okně Nahradit.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nalezen.

*lpszNahradit*<br/>
Text, který má nahradit hledaný text.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud true, hledání je rozlišování velkých a malých písmen. Pokud false, hledání není malá a velká písmena.

### <a name="remarks"></a>Poznámky

`OnReplaceAll`prohledá text ve vyrovnávací paměti pro text určený *lpszFind*, s rozlišování velkých a malých písmen zadaných *bCase*. Hledání začíná na začátku aktuálního výběru. Při každém nalezení hledaného textu nahradí tato funkce výskyt textu textem určeným *lpszReplace*. Hledání se provádí prostřednictvím volání [FindText](#findtext). Ve výchozí implementaci [OnTextNotFound](#ontextnotfound) se nazývá, pokud text nebyl nalezen.

Pokud aktuální výběr neodpovídá *lpszFind*, výběr je aktualizován na první výskyt textu určeného *lpszFind* a nahrazení není provedeno. To umožňuje uživateli potvrdit, že je to, co chtějí dělat, když výběr neodpovídá textu, který má být nahrazen.

Přepsáním `OnReplaceAll` změníte `CEditView`způsob, jakým odvozený objekt nahradí text.

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>CEditView::OnReplaceSel

`CEditView`volání, `OnReplaceSel` když uživatel vybere tlačítko Nahradit ve standardním dialogovém okně Nahradit.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nalezen.

*bDalší*<br/>
Určuje směr hledání. Pokud TRUE, směr hledání je směrem ke konci vyrovnávací paměti. Pokud false, směr hledání je směrem k začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud true, hledání je rozlišování velkých a malých písmen. Pokud false, hledání není malá a velká písmena.

*lpszNahradit*<br/>
Text, který má nahradit nalezený text.

### <a name="remarks"></a>Poznámky

Po nahrazení výběru tato funkce prohledá text ve vyrovnávací paměti pro další výskyt textu určeného *lpszFind*ve směru určeném *písmenem bNext*, s rozlišením velkých a malých písmen určených *písmenem bCase*. Hledání se provádí prostřednictvím volání [FindText](#findtext). Pokud text nebyl nalezen, [OnTextNotFound](#ontextnotfound) se nazývá.

Přepsáním `OnReplaceSel` změníte `CEditView`způsob, jakým odvozený objekt nahradí vybraný text.

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>CeditView::OnTextNotFound

Přepsáním této funkce změníte výchozí implementaci, která volá funkci `MessageBeep`systému Windows .

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nalezen.

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::PrintInsideRect

Volání `PrintInsideRect` pro tisk textu v obdélníku *určeném rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení tiskárny.

*rectLayout*<br/>
Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT struktury](/windows/win32/api/windef/ns-windef-rect) určující obdélník, ve kterém má být vykreslen text.

*nIndexStart*<br/>
Index ve vyrovnávací paměti první znak, který má být vykreslen.

*nIndexStop*<br/>
Index ve vyrovnávací paměti znaku následující poslední znak, který má být vykreslen.

### <a name="return-value"></a>Návratová hodnota

Index dalšího znaku, který má být vytištěn (to znamená znak za posledním vykresleným znakem).

### <a name="remarks"></a>Poznámky

Pokud `CEditView` ovládací prvek nemá styl ES_AUTOHSCROLL, text je zabalen v obdélníku vykreslování. Pokud ovládací prvek má styl ES_AUTOHSCROLL, text je oříznut na pravém okraji obdélníku.

Prvek `rect.bottom` *rectLayout* objektu se změní tak, aby rozměry obdélníku definovat část původní obdélník, který je obsazený text.

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView::SerializeRaw

Volání `SerializeRaw` objektu `CArchive` číst nebo zapsat `CEditView` text v objektu do textového souboru.

```cpp
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Odkaz na `CArchive` objekt, který ukládá serializovaný text.

### <a name="remarks"></a>Poznámky

`SerializeRaw`se liší `CEditView`od interní `Serialize` implementace programu v tom, že čte a zapisuje pouze text bez předchozích dat popisu objektu.

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>CEditView::SetPrinterFont

Voláním `SetPrinterFont` nastavte písmo tiskárny na písmo určené *příkazem pFont*.

```cpp
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
Ukazatel na objekt typu `CFont`. Pokud null, písmo použité pro tisk je založena na písmu zobrazení.

### <a name="remarks"></a>Poznámky

Pokud chcete, aby zobrazení vždy používalo určité písmo `SetPrinterFont` pro tisk, `OnPreparePrinting` zahrňte volání do funkce třídy. Tato virtuální funkce je volána před tiskem, takže změna písma probíhá před tiskem obsahu zobrazení.

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>CEditView::SetTabstops

Voláním této funkce nastavte zarážky tabulátoru používané pro zobrazení a tisk.

```cpp
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parametry

*nTabStops*<br/>
Šířka každé zarážky tabulátoru v dialogových jednotkách.

### <a name="remarks"></a>Poznámky

Je podporována pouze jedna šířka zarážky tabulátoru. (objekty `CEdit` podporují více šířek tabulátoru.) Šířky jsou v dialogových jednotkách, které se rovnají jedné čtvrtině průměrné šířky znaků (pouze na základě velkých a malých abecedních znaků) písma použitého v době tisku nebo zobrazení. Neměli byste `CEdit::SetTabStops` `CEditView` používat, protože musí ukládat do mezipaměti hodnotu stop tabulátoru.

Tato funkce upravuje pouze karty objektu, pro který je volána. Chcete-li změnit zarážky tabulátoru pro `CEditView` `SetTabStops` každý objekt v aplikaci, volání funkce každého objektu.

### <a name="example"></a>Příklad

Tento fragment kódu nastaví zarážky tabulátoru v ovládacím prvku na každý čtvrtý znak pečlivým měřením písma, které ovládací prvek používá.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView::Odemknoutvyrovnávací paměť

Volání této členské funkce odemknout vyrovnávací paměti.

```cpp
void UnlockBuffer() const;
```

### <a name="remarks"></a>Poznámky

Volání `UnlockBuffer` po dokončení použití ukazatele vráceného [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Viz také

[Vzorek mfc SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
