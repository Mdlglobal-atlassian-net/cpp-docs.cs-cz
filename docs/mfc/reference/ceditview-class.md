---
title: Ceditview – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 450f2444279847a7d537fe8fc48f8e4b09f04168
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423478"
---
# <a name="ceditview-class"></a>Ceditview – třída

Typ třídy zobrazení, která poskytuje funkce pro Windows ovládacích prvků pro úpravy a slouží k implementaci funkcí jednoduchého textového editoru.

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
|[CEditView::GetBufferLength](#getbufferlength)|Získá délku vyrovnávací paměti pro znaky.|
|[CEditView::GetEditCtrl](#geteditctrl)|Poskytuje přístup k `CEdit` část `CEditView` objektu (ovládacích prvků pro úpravy Windows).|
|[CEditView::GetPrinterFont](#getprinterfont)|Načte aktuální písmo tiskárny.|
|[CEditView::GetSelectedText](#getselectedtext)|Načte aktuálně vybraného textu.|
|[CEditView::LockBuffer](#lockbuffer)|Zamkne vyrovnávací paměti.|
|[CEditView::PrintInsideRect](#printinsiderect)|Generuje text v daném obdélníku.|
|[CEditView::SerializeRaw](#serializeraw)|Serializuje `CEditView` objektu na disk jako nezpracovaný text.|
|[CEditView::SetPrinterFont](#setprinterfont)|Nastaví nové písmo tiskárny.|
|[CEditView::SetTabStops](#settabstops)|Nastaví tabulátorů pro obrazovku a tisku.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Odemkne vyrovnávací paměti.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Najít další výskyty textového řetězce.|
|[CEditView::OnReplaceAll](#onreplaceall)|Nový řetězec nahradí všechny výskyty daného řetězce.|
|[CEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Volá se, když selže operace hledání tak, aby odpovídaly jakýkoli další text.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Výchozí styl pro objekty typu `CEditView`.|

## <a name="remarks"></a>Poznámky

`CEditView` Třída poskytující následující další funkce:

- Tisk.

- Najít a nahradit.

Protože třída `CEditView` je jejich odvozené třídy `CView`, objekty třídy `CEditView` jde použít s dokumenty a šablony dokumentů.

Každý `CEditView` text ovládacího prvku se ukládají v jeho vlastní globální paměti objektu. Vaše aplikace může mít libovolný počet `CEditView` objekty.

Vytvořit objekty tohoto typu `CEditView` Pokud chcete oknem upravit s přidané funkce uvedené výše, nebo pokud chcete funkčnost jednoduchého textového editoru. A `CEditView` objekt může zabírat celý klientské oblasti okna. Vlastní odvozovat z `CEditView` přidávat nebo upravovat základní funkce, nebo pro deklaraci třídy, které lze přidat do šablony dokumentu.

Výchozí implementace třídy `CEditView` zpracovává následující příkazy: id_edit_select_all – ID_EDIT_FIND, id_edit_replace –, id_edit_repeat – a ID_FILE_PRINT.

Výchozí omezení počtu znaků pro `CEditView` je (1024 \* 1024-1 = 1048575). To lze změnit pomocí volání funkce EM_LIMITTEXT ovládacích prvků pro základní úpravy. Však omezení se liší v závislosti na operační systém a typ upravit ovládací prvek (jednoduchá nebo víceřádkové). Další informace o těchto omezeních najdete v tématu [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext).

Chcete-li změnit toto omezení v ovládacím prvku, přepsat `OnCreate()` funkce pro vaše `CEditView` třídy a vložte následující řádek kódu:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Objekty typu `CEditView` (nebo typů odvozených z `CEditView`) mají následující omezení:

- `CEditView` neimplementuje hodnotu true, co vidíte je co všechno získáte úpravy (WYSIWYG). Pokud je možnost volby mezi čitelnost na obrazovce a odpovídající výstupem `CEditView` požádá o pro čitelnost na obrazovce.

- `CEditView` text můžete zobrazit pouze jeden písmeny. Žádné zvláštní formátování se nepodporuje. Viz třída [cricheditview –](../../mfc/reference/cricheditview-class.md) pro větší možnosti.

- Množství textu `CEditView` může obsahovat je omezený. Omezení jsou stejné jako v případě `CEdit` ovládacího prvku.

Další informace o `CEditView`, naleznete v tématu [odvozené zobrazení tříd k dispozici v knihovně MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview –](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="ceditview"></a>  CEditView::CEditView

Vytvoří objekt typu `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu, je třeba zavolat [CWnd::Create](../../mfc/reference/cwnd-class.md#create) funkci než textovém poli se používá. Pokud odvodíte třídu od `CEditView` a přidejte ji do šablony pomocí `CWinApp::AddDocTemplate`, volá tento konstruktor framework a `Create` funkce.

##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault

Obsahuje výchozí styl `CEditView` objektu.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Poznámky

Předejte tento statický člen jako *dwStyle* parametr `Create` funkce získat výchozí styl `CEditView` objektu.

##  <a name="findtext"></a>  CEditView::FindText

Volání `FindText` funkce pro hledání `CEditView` vyrovnávací paměť textu objektu.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, která se má najít.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE se ke konci vyrovnávací paměti je směr hledání. Pokud má hodnotu FALSE, je směr hledání směrem k začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda při hledání velká a malá písmena. Při hodnotě TRUE se vyhledávání je velká a malá písmena. Pokud má hodnotu FALSE, není hledání malá a velká písmena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nalezen hledaný text. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce vyhledá text ve vyrovnávací paměti pro textem určeným parametrem *lpszFind*začíná na aktuální výběr v určeném směru *bNext*a s určeným rozlišovánívelikostipísmen*bCase*. Pokud se text nenajde, nastaví výběr nalezen text a vrátí nenulovou hodnotu. Pokud text není nalezen, funkce vrátí 0.

Obvykle není potřeba volat `FindText` fungovat, pokud přepíšete `OnFindNext`, který volá `FindText`.

##  <a name="getbufferlength"></a>  CEditView::GetBufferLength

Voláním této členské funkce získat počet znaků aktuálně v textovém poli vyrovnávací paměti, nikoli včetně ukončovacího znaku null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka řetězce ve vyrovnávací paměti.

##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl

Volání `GetEditCtrl` k získání odkazu na textové pole používané zobrazení pro úpravy.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CEdit` objektu.

### <a name="remarks"></a>Poznámky

Tento ovládací prvek je typu [CEdit](../../mfc/reference/cedit-class.md), takže můžete pracovat s Windows ovládacího prvku pro úpravy přímo pomocí `CEdit` členské funkce.

> [!CAUTION]
>  Použití `CEdit` objektu můžete změnit stav základní Windows ovládacích prvků pro úpravy. Například byste neměli měnit nastavení karet pomocí [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) fungovat, protože `CEditView` ukládá do mezipaměti tyto nastavení určená pro ovládací prvek pro úpravy a tisk. Místo toho použijte [CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont

Volání `GetPrinterFont` získat ukazatel [cfont –](../../mfc/reference/cfont-class.md) objekt, který popisuje aktuální písmo tiskárny.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CFont` objekt, který určuje aktuální písmo tiskárny; Hodnota NULL, pokud nebyla nastavena písmo tiskárny. Ukazatel může být dočasné a neměl by být uložen pro pozdější použití.

### <a name="remarks"></a>Poznámky

Pokud písmo tiskárny nebyla nastavena, výchozí chování pro tisk `CEditView` třídy je tisk pomocí stejné písmo použité k zobrazení.

Tuto funkci použijte k určení aktuální písmo tiskárny. Pokud není požadované tiskárně písmo, použijte [CEditView::SetPrinterFont](#setprinterfont) ho změnit.

##  <a name="getselectedtext"></a>  CEditView::GetSelectedText

Volání `GetSelectedText` ke zkopírování vybraného textu do `CString` objekt až po konec výběru nebo znak, který předchází první znak pro návrat na začátek řádku ve výběru.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parametry

*strResult*<br/>
Odkaz na `CString` objekt, který se zobrazí vybraný text.

##  <a name="lockbuffer"></a>  CEditView::LockBuffer

Voláním této členské funkce na ukazatel do vyrovnávací paměti. Vyrovnávací paměti by se nemělo upravovat.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel do vyrovnávací paměti v textovém poli.

##  <a name="onfindnext"></a>  CEditView::OnFindNext

Vyhledá text ve vyrovnávací paměti pro textem určeným parametrem *lpszFind*, v určeném směru *bNext*, s malá a velká písmena stanovených *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, která se má najít.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE se ke konci vyrovnávací paměti je směr hledání. Pokud má hodnotu FALSE, je směr hledání směrem k začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda při hledání velká a malá písmena. Při hodnotě TRUE se vyhledávání je velká a malá písmena. Pokud má hodnotu FALSE, není hledání malá a velká písmena.

### <a name="remarks"></a>Poznámky

Hledání začne na začátku aktuálního výběru a se provádí pomocí volání [FindText](#findtext). Ve výchozí implementaci `OnFindNext` volání [OnTextNotFound](#ontextnotfound) Pokud nebude nalezen text.

Přepsat `OnFindNext` změnit způsob `CEditView`-odvozeného objektu vyhledá text. `CEditView` volání `OnFindNext` když uživatel vybere tlačítko Najít další standardní dialogové okno hledání.

##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll

`CEditView` volání `OnReplaceAll` když uživatel vybere tlačítko Nahradit vše v dialogovém okně Standardní nahradit.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, která se má najít.

*lpszReplace*<br/>
Text pro nahrazení hledaný text.

*bCase*<br/>
Určuje, zda hledání rozlišuje velikost písmen. Při hodnotě TRUE se vyhledávání je velká a malá písmena. Pokud má hodnotu FALSE, není hledání malá a velká písmena.

### <a name="remarks"></a>Poznámky

`OnReplaceAll` Vyhledá text ve vyrovnávací paměti pro textem určeným parametrem *lpszFind*, s malá a velká písmena stanovených *bCase*. Hledání začne na začátku aktuálního výběru. Pokaždé, když se nachází hledaný text, tato funkce nahrazuje výskytu textu s textem určeným parametrem *lpszReplace*. Vyhledávání se provádí pomocí volání [FindText](#findtext). Ve výchozí implementaci [OnTextNotFound](#ontextnotfound) je volána, pokud nebude nalezen text.

Pokud aktuální výběr neodpovídá *lpszFind*, výběr se aktualizuje na první výskyt textem určeným parametrem *lpszFind* a nahrazení se neprovádí. To umožňuje uživateli pro potvrzení, že toto je chtějí dělat, když se výběr se neshoduje s text, který má být nahrazen.

Přepsat `OnReplaceAll` změnit způsob `CEditView`-odvozeného objektu nahradí text.

##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel

`CEditView` volání `OnReplaceSel` když uživatel vybere tlačítko Nahradit v dialogovém okně Standardní nahradit.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, která se má najít.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE se ke konci vyrovnávací paměti je směr hledání. Pokud má hodnotu FALSE, je směr hledání směrem k začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda při hledání velká a malá písmena. Při hodnotě TRUE se vyhledávání je velká a malá písmena. Pokud má hodnotu FALSE, není hledání malá a velká písmena.

*lpszReplace*<br/>
Textu, který má být nahrazen nalezený text.

### <a name="remarks"></a>Poznámky

Po nahrazení výběr, tato funkce vyhledá text ve vyrovnávací paměti pro další výskyt textem určeným parametrem *lpszFind*, v určeném směru *bNext*, s malá a velká písmena určená *bCase*. Vyhledávání se provádí pomocí volání [FindText](#findtext). Pokud se text nenajde, [OnTextNotFound](#ontextnotfound) je volána.

Přepsat `OnReplaceSel` změnit způsob `CEditView`-odvozeného objektu nahradí vybraného textu.

##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound

Přepsat tuto funkci chcete-li změnit výchozí implementace, která volá funkci Windows `MessageBeep`.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, která se má najít.

##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect

Volání `PrintInsideRect` tisknout text v obdélníku určené *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Ukazatel na kontext zařízení tiskárny.

*rectLayout*<br/>
Odkaz [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [Rect – struktura](../../mfc/reference/rect-structure1.md) zadání obdélník, ve kterém má být vykreslen text.

*nIndexStart*<br/>
Index v rámci prvního znaku, které mají být vykresleny vyrovnávací paměti.

*nIndexStop*<br/>
Index v rámci vyrovnávací paměti znak následující po posledním znaku k vykreslení.

### <a name="return-value"></a>Návratová hodnota

Index dalšího znaku, které se mají vytisknout (to znamená, znak za jeho poslední znak vykreslen).

### <a name="remarks"></a>Poznámky

Pokud `CEditView` ovládací prvek nemá styl ES_AUTOHSCROLL, zalomit text v obdélníku vykreslování. Pokud ovládací prvek nemá styl ES_AUTOHSCROLL, je na pravé straně obdélníku oříznutí textu.

`rect.bottom` Elementu *rectLayout* objektu se změní tak, aby obdélníku dimenze definovat součástí původní obdélník, který je obsazena text.

##  <a name="serializeraw"></a>  CEditView::SerializeRaw

Volání `SerializeRaw` mít `CArchive` objekt pro čtení nebo zápis textu `CEditView` objektu do textového souboru.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Odkaz `CArchive` objekt, který uchovává serializovaná text.

### <a name="remarks"></a>Poznámky

`SerializeRaw` se liší od `CEditView`na interní implementaci `Serialize` čte a zapisuje pouze text, bez dat popis objektu.

##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont

Volání `SetPrinterFont` nastavit písmo tiskárny na určené písmo *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na objekt typu `CFont`. Pokud má hodnotu NULL, písmo použité pro tisk je založena na zobrazení písma.

### <a name="remarks"></a>Poznámky

Pokud chcete zobrazení vždy používat zvolené písmo k tisku, zahrnout volání `SetPrinterFont` ve své třídě `OnPreparePrinting` funkce. Tato virtuální funkce se volá předtím, než dojde k tisku, takže změna písma proběhne předtím, než se vytisknou zobrazit obsah.

##  <a name="settabstops"></a>  CEditView::SetTabStops

Voláním této funkce nastavit zarážky, používá pro zobrazení a tisk.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parametry

*nTabStops*<br/>
Šířka každou zarážku v jednotkách dialogového okna.

### <a name="remarks"></a>Poznámky

Je podporován pouze jeden šířku zarážek. ( `CEdit` objekty podporují více šířku karty.) Šířky jsou v jednotkách dialogového okna, které rovnat čtvrtinu šířky průměrné znaku písmo použité v době tisku nebo zobrazení (podle velká a malá písmena abecedy jenom znaky). Neměli byste používat `CEdit::SetTabStops` protože `CEditView` musí ukládat do mezipaměti hodnoty konec tabulátoru.

Tato funkce změní pouze karty objektu, pro kterou je volána. Chcete-li změnit kartu přestane pro každou `CEditView` objektu ve vaší aplikaci, každý objekt volat `SetTabStops` funkce.

### <a name="example"></a>Příklad

Tento fragment kódu nastaví zarážek tabulátoru v ovládacím prvku pro každý čtvrtý znak pečlivě měřením písmo, které používá ovládací prvek.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>  CEditView::UnlockBuffer

Voláním této členské funkce k odemknutí vyrovnávací paměti.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Poznámky

Volání `UnlockBuffer` po dokončení používání ukazatele vrácené [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC SUPERPAD](../../visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
