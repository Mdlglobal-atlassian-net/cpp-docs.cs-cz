---
title: CEditView – třída
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
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506730"
---
# <a name="ceditview-class"></a>CEditView – třída

Typ třídy zobrazení, která poskytuje funkce ovládacího prvku Windows Edit a lze jej použít k implementaci jednoduchých funkcí editoru textu.

## <a name="syntax"></a>Syntaxe

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CEditView:: CEditView](#ceditview)|Vytvoří objekt typu `CEditView`.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CEditView::FindText](#findtext)|Vyhledá řetězec v rámci textu.|
|[CEditView:: GetBufferLength](#getbufferlength)|Získá délku vyrovnávací paměti znaků.|
|[CEditView::GetEditCtrl](#geteditctrl)|Poskytuje přístup k `CEdit` části `CEditView` objektu (ovládací prvek Windows Edit).|
|[CEditView:: GetPrinterFont](#getprinterfont)|Načte aktuální písmo tiskárny.|
|[CEditView::GetSelectedText](#getselectedtext)|Načte aktuální výběr textu.|
|[CEditView::LockBuffer](#lockbuffer)|Zamkne vyrovnávací paměť.|
|[CEditView::PrintInsideRect](#printinsiderect)|Vykreslí text uvnitř daného obdélníku.|
|[CEditView:: SerializeRaw](#serializeraw)|Serializace `CEditView` objektu na disk jako nezpracovaný text.|
|[CEditView:: SetPrinterFont](#setprinterfont)|Nastaví nové písmo tiskárny.|
|[CEditView:: SetTabStops](#settabstops)|Nastaví zarážky tabulátoru pro zobrazení a tisk obrazovky.|
|[CEditView:: UnlockBuffer](#unlockbuffer)|Odemkne vyrovnávací paměť.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Najde další výskyt textového řetězce.|
|[CEditView::OnReplaceAll](#onreplaceall)|Nahradí všechny výskyty daného řetězce novým řetězcem.|
|[CEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Volá se, když operace Find nevyhovuje žádnému dalšímu textu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CEditView::d wStyleDefault](#dwstyledefault)|Výchozí styl pro objekty typu `CEditView`|

## <a name="remarks"></a>Poznámky

`CEditView` Třída poskytuje následující další funkce:

- Tisk.

- Vyhledejte a nahraďte.

Vzhledem k `CEditView` tomu, že třída je `CView`odvozena třídy, `CEditView` lze objekty třídy použít s dokumenty a šablonami dokumentů.

Text `CEditView` každého ovládacího prvku je uložen ve vlastním globálním objektu paměti. Vaše aplikace může mít libovolný počet `CEditView` objektů.

Vytvořte objekty typu `CEditView` , pokud chcete upravit okno s přidanými funkcemi, nebo pokud chcete funkce jednoduchého textového editoru. `CEditView` Objekt může zabírat celou klientskou oblast okna. Odvodit vlastní třídy z `CEditView` nástroje k přidání nebo úpravě základních funkcí nebo k deklaraci tříd, které lze přidat do šablony dokumentu.

Výchozí implementace třídy `CEditView` zpracuje následující příkazy: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT a ID_FILE_PRINT.

Výchozí omezení počtu znaků pro `CEditView` je (1024 \* 1024-1 = 1048575). To lze změnit voláním funkce EM_LIMITTEXT podkladového ovládacího prvku pro úpravy. Omezení se však liší v závislosti na operačním systému a typu ovládacího prvku pro úpravy (jedna nebo víceřádková). Další informace o těchto omezeních najdete v tématu [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Chcete-li změnit toto omezení v ovládacím prvku, `OnCreate()` přepište funkci `CEditView` pro třídu a vložte následující řádek kódu:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Objekty typu `CEditView` (nebo z typů odvozených z `CEditView`) mají následující omezení:

- `CEditView`neimplementuje hodnotu true, která se zobrazuje jako to, co získáte (WYSIWYG) pro úpravy. Kde je volba mezi možnostmi čitelnosti na obrazovce a porovnávacím výstupem `CEditView` tisku, výslovný pro čitelnost obrazovky.

- `CEditView`umožňuje zobrazit text pouze v jednom písmu. Není podporováno žádné speciální formátování znaků. Další možnosti najdete v tématu Třída [CRichEditView –](../../mfc/reference/cricheditview-class.md) .

- Množství textu, `CEditView` které může obsahovat, je omezené. Omezení jsou stejná jako u `CEdit` ovládacího prvku.

Další informace o `CEditView`naleznete v tématu [odvozené třídy zobrazení dostupné v knihovně MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="ceditview"></a>CEditView:: CEditView

Vytvoří objekt typu `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Poznámky

Po sestavení objektu je nutné zavolat funkci [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) před použitím ovládacího prvku pro úpravy. Pokud třídu Odvozujete z `CEditView` a přidáte ji do šablony pomocí `CWinApp::AddDocTemplate`, rozhraní volá `Create` jak tento konstruktor, tak funkci.

##  <a name="dwstyledefault"></a>CEditView::d wStyleDefault

Obsahuje výchozí styl `CEditView` objektu.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Poznámky

Předat tomuto statickému členu jako parametr `Create` dwStyle funkce, aby získala `CEditView` výchozí styl pro objekt.

##  <a name="findtext"></a>CEditView:: hledán FindText

Voláním `CEditView` funkce vyhledáte vyrovnávací paměť textu objektu. `FindText`

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který se má najít

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE je směr hledání na konci vyrovnávací paměti. Pokud je hodnota FALSE, směr hledání je na začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud je nastaveno na TRUE, hledání rozlišuje malá a velká písmena. Pokud je nastaveno na FALSE, hledání nerozlišuje velká a malá písmena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je nalezen hledaný text; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce vyhledá text ve vyrovnávací paměti pro text určený parametrem *lpszFind*počínaje aktuálním výběrem ve směru určeném parametrem *bNext*a rozlišuje velká a malá písmena zadaná v *bCase*. Pokud je text nalezen, nastaví výběr na nalezený text a vrátí nenulovou hodnotu. Pokud text není nalezen, funkce vrátí 0.

Obvykle není nutné volat `FindText` funkci, Pokud nepřepíšete `OnFindNext`, která volání `FindText`.

##  <a name="getbufferlength"></a>CEditView:: GetBufferLength

Zavolejte tuto členskou funkci, aby se získal počet znaků, které jsou aktuálně ve vyrovnávací paměti ovládacího prvku pro úpravy, včetně ukončovacího znaku null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka řetězce ve vyrovnávací paměti.

##  <a name="geteditctrl"></a>CEditView:: GetEditCtrl

Voláním `GetEditCtrl` získáte odkaz na ovládací prvek pro úpravy, který používá zobrazení pro úpravy.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CEdit` objekt.

### <a name="remarks"></a>Poznámky

Tento ovládací prvek je typu [CEdit](../../mfc/reference/cedit-class.md), takže můžete manipulovat s ovládacím prvkem Windows Edit přímo pomocí `CEdit` členských funkcí.

> [!CAUTION]
>  `CEdit` Použití objektu může změnit stav základního ovládacího prvku Windows Edit. Například byste neměli měnit nastavení tabulátoru pomocí funkce [CEdit:: SetTabStops](../../mfc/reference/cedit-class.md#settabstops) , protože `CEditView` ukládá tato nastavení do mezipaměti pro použití v ovládacím prvku pro úpravy i v tisku. Místo toho použijte [CEditView:: SetTabStops](#settabstops).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>CEditView:: GetPrinterFont

Voláním `GetPrinterFont` získáte ukazatel na objekt [CFont –](../../mfc/reference/cfont-class.md) , který popisuje aktuální písmo tiskárny.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFont` objekt, který určuje aktuální písmo tiskárny; Hodnota NULL, pokud písmo tiskárny nebylo nastaveno. Ukazatel může být dočasný a neměl by být uložen pro pozdější použití.

### <a name="remarks"></a>Poznámky

Pokud písmo tiskárny nebylo nastaveno, je výchozím chováním `CEditView` při tisku třídy tisk pomocí stejného písma používaného k zobrazení.

Pomocí této funkce lze určit aktuální písmo tiskárny. Pokud se nejedná o požadované písmo tiskárny, změňte jej pomocí [CEditView:: SetPrinterFont](#setprinterfont) .

##  <a name="getselectedtext"></a>CEditView:: GetSelectedText

Volání `GetSelectedText` pro zkopírování vybraného textu `CString` do objektu, až po konec výběru, nebo znak předchozí znak návratu na začátek řádku ve výběru.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parametry

*strResult*<br/>
Odkaz na `CString` objekt, který má přijmout vybraný text.

##  <a name="lockbuffer"></a>CEditView:: LockBuffer

Chcete-li získat ukazatel na vyrovnávací paměť, zavolejte tuto členskou funkci. Vyrovnávací paměť by se neměla upravovat.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť ovládacího prvku pro úpravy.

##  <a name="onfindnext"></a>CEditView:: OnFindNext

Vyhledá v textu ve vyrovnávací paměti text určený parametrem *lpszFind*ve směru určeném parametrem *bNext*a rozlišuje velká a malá písmena určená v *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který se má najít

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE je směr hledání na konci vyrovnávací paměti. Pokud je hodnota FALSE, směr hledání je na začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud je nastaveno na TRUE, hledání rozlišuje malá a velká písmena. Pokud je nastaveno na FALSE, hledání nerozlišuje velká a malá písmena.

### <a name="remarks"></a>Poznámky

Hledání začíná na začátku aktuálního výběru a je provedeno prostřednictvím volání [hledán FindText](#findtext). Ve výchozí implementaci volá `OnFindNext` [OnTextNotFound](#ontextnotfound) , pokud se text nenalezne.

Přepsat `OnFindNext` pro změnu `CEditView`způsobu, jakým objekt odvozeného objektu vyhledává text. `CEditView`volá `OnFindNext` , když uživatel zvolí tlačítko Najít další v dialogovém okně standardní hledání.

##  <a name="onreplaceall"></a>CEditView:: OnReplaceAll

`CEditView`volá `OnReplaceAll` , když uživatel vybere tlačítko Nahradit vše v dialogovém okně standardní nahrazení.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který se má najít

*lpszReplace*<br/>
Text, který má nahradit hledaný text

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud je nastaveno na TRUE, hledání rozlišuje malá a velká písmena. Pokud je nastaveno na FALSE, hledání nerozlišuje velká a malá písmena.

### <a name="remarks"></a>Poznámky

`OnReplaceAll`vyhledá v textu ve vyrovnávací paměti text určený parametrem *lpszFind*a rozlišuje velká a malá písmena zadaná v *bCase*. Hledání začne na začátku aktuálního výběru. Pokaždé, když se hledaný text najde, tato funkce nahradí tento výskyt textu textem zadaným parametrem *lpszReplace*. Hledání je provedeno prostřednictvím volání [hledán FindText](#findtext). Ve výchozí implementaci je volána metoda [OnTextNotFound](#ontextnotfound) , pokud text nebyl nalezen.

Pokud aktuální výběr neodpovídá *lpszFind*, je výběr aktualizován na první výskyt textu zadaného parametrem *lpszFind* a není provedena náhrada. To uživateli umožňuje potvrdit, že se jedná o to, co chtějí udělat, když výběr neodpovídá textu, který má být nahrazen.

Přepsáním `OnReplaceAll` změníte `CEditView`způsob, jakým objekt odvozeného objektu nahradí text.

##  <a name="onreplacesel"></a>CEditView:: OnReplaceSel

`CEditView`volá `OnReplaceSel` , když uživatel vybere tlačítko Nahradit v dialogovém okně standardní nahrazení.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který se má najít

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE je směr hledání na konci vyrovnávací paměti. Pokud je hodnota FALSE, směr hledání je na začátku vyrovnávací paměti.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena. Pokud je nastaveno na TRUE, hledání rozlišuje malá a velká písmena. Pokud je nastaveno na FALSE, hledání nerozlišuje velká a malá písmena.

*lpszReplace*<br/>
Text, který má nahradit nalezený text

### <a name="remarks"></a>Poznámky

Po nahrazení výběru Tato funkce vyhledá v textu ve vyrovnávací paměti další výskyt textu určeného funkcí *lpszFind*ve směru určeném parametrem *bNext*a rozlišuje velká a malá písmena zadaná v *bCase*. Hledání je provedeno prostřednictvím volání [hledán FindText](#findtext). Pokud text není nalezen, je volána metoda [OnTextNotFound](#ontextnotfound) .

Přepsáním `OnReplaceSel` změníte `CEditView`způsob, jakým objekt odvozený od nahradí vybraný text.

##  <a name="ontextnotfound"></a>CEditView:: OnTextNotFound

Přepsáním této funkce změníte výchozí implementaci, která volá funkci `MessageBeep`Windows.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který se má najít

##  <a name="printinsiderect"></a>CEditView::P rintInsideRect

Zavolejte `PrintInsideRect` k vytištění textu v obdélníku určeném parametrem *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení tiskárny.

*rectLayout*<br/>
Odkaz na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo [strukturu Rect](/windows/win32/api/windef/ns-windef-rect) určující obdélník, ve kterém má být vykreslen text.

*nIndexStart*<br/>
Index v rámci vyrovnávací paměti prvního znaku, který má být vykreslen.

*nIndexStop*<br/>
Index v rámci vyrovnávací paměti znaku za posledním znakem, který se má vykreslit

### <a name="return-value"></a>Návratová hodnota

Index dalšího znaku, který má být vytištěn (tj. znak za posledním vykresleným znakem).

### <a name="remarks"></a>Poznámky

`CEditView` Pokud ovládací prvek nemá styl ES_AUTOHSCROLL, text je zabalen do obdélníku vykreslování. Pokud má ovládací prvek styl ES_AUTOHSCROLL, text se ořízne na pravém okraji obdélníku.

Prvek objektu rectLayout je změněn tak, aby rozměry obdélníku definovaly část původního obdélníku, který je obsazen textem. `rect.bottom`

##  <a name="serializeraw"></a>CEditView:: SerializeRaw

Volání `SerializeRaw` , aby `CArchive` objekt četl nebo `CEditView` napsal text v objektu do textového souboru.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*snížen*<br/>
Odkaz na `CArchive` objekt, který ukládá serializovaný text.

### <a name="remarks"></a>Poznámky

`SerializeRaw`se liší od `CEditView`vnitřní `Serialize` implementace v tom, že čte a zapisuje pouze text, aniž by došlo k předchozím datům objektu-Description.

##  <a name="setprinterfont"></a>CEditView:: SetPrinterFont

Zavolejte `SetPrinterFont` pro nastavení písma tiskárny na písmo určené parametrem *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na objekt typu `CFont`. Pokud má hodnotu NULL, písmo použité pro tisk vychází z písma zobrazení.

### <a name="remarks"></a>Poznámky

Chcete-li, aby zobrazení vždy používalo konkrétní písmo pro tisk, zahrňte volání `SetPrinterFont` do `OnPreparePrinting` funkce vaší třídy. Tato virtuální funkce se volá před tím, než dojde k tisku, takže Změna písma proběhne před vytištěním obsahu zobrazení.

##  <a name="settabstops"></a>CEditView:: SetTabStops

Voláním této funkce nastavíte zarážky tabulátoru používané pro zobrazení a tisk.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parametry

*nTabStops*<br/>
Šířka jednotlivých zarážek tabulátoru v jednotkách dialogového okna.

### <a name="remarks"></a>Poznámky

Je podporována pouze jedna šířka zarážky tabulátoru. ( `CEdit` objekty podporují více šířek karet.) Šířky jsou v jednotkách dialogových oken, které se rovnají jedné čtvrtine průměrné šířky znaků (na základě velkých a malých písmen abeced) písma použitého v době tisku nebo zobrazení. Nepoužívejte, protože `CEdit::SetTabStops` `CEditView` je nutné zadat hodnotu zarážky tabulátoru do mezipaměti.

Tato funkce upraví pouze karty objektu, pro které je volána. Chcete-li změnit zarážky tabulátoru pro každý `CEditView` objekt v aplikaci, zavolejte `SetTabStops` funkci každého objektu.

### <a name="example"></a>Příklad

Tento fragment kódu nastaví zarážky tabulátoru v ovládacím prvku na každý čtvrtý znak tím, že pečlivě vyměří písmo, které ovládací prvek používá.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>CEditView:: UnlockBuffer

Chcete-li odemknout vyrovnávací paměť, zavolejte tuto členskou funkci.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Poznámky

Zavolejte `UnlockBuffer` po dokončení pomocí ukazatele vráceného funkcí [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Viz také:

[SUPERPAD Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
