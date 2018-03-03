---
title: "Třída CEditView | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 78aa34f1790b2e86dae183b96c88b4ed35483927
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ceditview-class"></a>CEditView – třída
Typ třídy zobrazení, který poskytuje funkci Windows ovládacích prvků pro úpravy a lze použít k implementaci funkce jednoduchého textového editoru.  
  
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
|[CEditView::FindText](#findtext)|Hledání řetězce v rámci textu.|  
|[CEditView::GetBufferLength](#getbufferlength)|Získá délka vyrovnávací paměti znak.|  
|[CEditView::GetEditCtrl](#geteditctrl)|Poskytuje přístup k `CEdit` část `CEditView` objektu (Windows ovládacích prvků pro úpravy).|  
|[CEditView::GetPrinterFont](#getprinterfont)|Načte aktuální písmo tiskárny.|  
|[CEditView::GetSelectedText](#getselectedtext)|Načte aktuální výběr textu.|  
|[CEditView::LockBuffer](#lockbuffer)|Zamkne vyrovnávací paměti.|  
|[CEditView::PrintInsideRect](#printinsiderect)|Vykreslí text v rámci dané obdélníku.|  
|[CEditView::SerializeRaw](#serializeraw)|Serializuje `CEditView` objekt, který má disk jako nezpracovaný text.|  
|[CEditView::SetPrinterFont](#setprinterfont)|Nastaví nového písma tiskárny.|  
|[CEditView::SetTabStops](#settabstops)|Nastaví tabulátorů pro zobrazení na obrazovce a tisku.|  
|[CEditView::UnlockBuffer](#unlockbuffer)|Odemkne vyrovnávací paměti.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|Vyhledá další výskyt textového řetězce.|  
|[CEditView::OnReplaceAll](#onreplaceall)|Nahradí všechny výskyty daného řetězec nového řetězce.|  
|[CEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|  
|[CEditView::OnTextNotFound](#ontextnotfound)|Volá se při hledání nezdaří tak, aby odpovídaly jakýkoli další text.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|Výchozí styl pro objekty typu **CEditView.**|  
  
## <a name="remarks"></a>Poznámky  
 `CEditView` Třída poskytuje následující další funkce:  
  
-   Vytiskněte.  
  
-   Najít a nahradit.  
  
 Protože třída `CEditView` je odvozený třídy `CView`, objekty třídy `CEditView` lze použít s dokumenty a šablony dokumentů.  
  
 Každý `CEditView` text ovládacího prvku je uložen v jeho vlastní objekt globální paměť. Aplikace může mít libovolný počet `CEditView` objekty.  
  
 Vytváření objektů tohoto typu `CEditView` Pokud chcete okno s upravit s přidání funkce uvedených výše, nebo pokud chcete, aby funkce jednoduchého textového editoru. A `CEditView` objekt zabírat celého klienta časového období. Vlastní odvozovat z `CEditView` přidat nebo upravit základních funkcí, nebo k deklaraci třídy, které mohou být přidány do šablony dokumentu.  
  
 Výchozí implementaci třídy `CEditView` zpracovává následující příkazy: **id_edit_select_all –**, **id_edit_find –**, **id_edit_replace –**, **Id_edit_repeat –**, a **id_file_print –**.  
  
 Výchozí limit znak pro `CEditView` je (1024 \* 1024-1 = 1048575). To se dá změnit pomocí volání **EM_LIMITTEXT** funkce základní ovládacích prvků pro úpravy. Však omezení se liší podle operačního systému a upravit typ ovládacího prvku (jeden nebo víc řádků). Další informace o těchto mezních hodnot najdete v tématu [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607).  
  
 Chcete-li změnit tento limit v vlastního ovládacího prvku, přepište `OnCreate()` funkce pro vaše `CEditView` třídy a vložte následující kód:  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 Objekty typu `CEditView` (nebo typy odvozené z `CEditView`) mají následující omezení:  
  
- `CEditView`neimplementuje true zobrazené je co získáte úpravy (WYSIWYG). Tam, kde je výběr mezi čitelnost na obrazovce a odpovídající tištěné výstup, `CEditView` placené služby čitelnost na obrazovce.  
  
- `CEditView`můžete zobrazit text pouze jeden písmeny. Formátování žádné speciální znak je podporována. Viz třída [cricheditview –](../../mfc/reference/cricheditview-class.md) pro větší možnosti.  
  
-   Objem textu `CEditView` může obsahovat je omezená. Omezení jsou stejné jako u `CEdit` ovládacího prvku.  
  
 Další informace o `CEditView`, najdete v části [odvozené zobrazení třídy dostupné v prostředí MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="ceditview"></a>CEditView::CEditView  
 Vytvoří objekt typu `CEditView`.  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>Poznámky  
 Poté, co vytvořen objekt, je třeba zavolat [CWnd::Create](../../mfc/reference/cwnd-class.md#create) funkce před použitím ovládací prvek upravit. Pokud odvodíte třídu od `CEditView` a přidejte ji do šablony pomocí `CWinApp::AddDocTemplate`, jak tento konstruktor volá framework a **vytvořit** funkce.  
  
##  <a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 Obsahuje výchozí styl `CEditView` objektu.  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>Poznámky  
 Předat tuto statický člen jako `dwStyle` parametr **vytvořit** funkce získat výchozí styl pro `CEditView` objektu.  
  
##  <a name="findtext"></a>CEditView::FindText  
 Volání `FindText` funkce hledání `CEditView` objektu textovou vyrovnávací paměť.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, která se má najít.  
  
 `bNext`  
 Určuje směr, hledání. Pokud **TRUE**, směr vyhledávání je na konci vyrovnávací paměti. Pokud **FALSE**, směr vyhledávání je k začátku vyrovnávací paměti.  
  
 `bCase`  
 Určuje, zda při hledání velká a malá písmena. Pokud **TRUE**, hledání je malá a velká písmena. Pokud **FALSE**, hledání nerozlišuje velká a malá písmena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je nalezen hledaný text; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vyhledá text ve vyrovnávací paměti pro textem určeným parametrem `lpszFind`začínající aktuální výběr ve směru určeného `bNext`a s rozlišování určeného `bCase`. Pokud je nalezen text, nastaví výběr na nalezen text a vrátí nenulovou hodnotu. Pokud text není nalezen, funkce vrátí hodnotu 0.  
  
 Normálně není potřeba volat `FindText` Pokud přepíšete fungovat `OnFindNext`, který volá `FindText`.  
  
##  <a name="getbufferlength"></a>CEditView::GetBufferLength  
 Volání této funkce člen získat počet znaků, které aktuálně ve vyrovnávací paměti textové pole, včetně není null ukončení.  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce ve vyrovnávací paměti.  
  
##  <a name="geteditctrl"></a>CEditView::GetEditCtrl  
 Volání `GetEditCtrl` k získání odkazu na ovládací prvek upravit používá zobrazení upravit.  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CEdit` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tento ovládací prvek je typu [CEdit](../../mfc/reference/cedit-class.md), takže můžete upravit upravit ovládacího prvku Windows přímo pomocí `CEdit` členské funkce.  
  
> [!CAUTION]
>  Pomocí `CEdit` objektu můžete změnit stav základní Windows ovládacích prvků pro úpravy. Například byste neměli měnit nastavení karet pomocí [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) fungovat, protože `CEditView` ukládá do mezipaměti, tato nastavení pro použití v ovládacím prvku upravit i v tisku. Místo toho použijte [CEditView::SetTabStops](#settabstops).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>CEditView::GetPrinterFont  
 Volání `GetPrinterFont` získání ukazatele na [CFont](../../mfc/reference/cfont-class.md) objektu, která popisuje aktuální písmo tiskárny.  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CFont` objekt, který určuje aktuální písmo tiskárny; **NULL** Pokud písmo tiskárny nebyl nastaven. Ukazatele může být v dočasné a by neměly být uloženy pro pozdější použití.  
  
### <a name="remarks"></a>Poznámky  
 Pokud písmo tiskárny nebyla nastavena, výchozí chování pro tisk `CEditView` třída je tisknout pomocí stejné písmo použité pro zobrazení.  
  
 Pomocí této funkce můžete zjistit aktuální písmo tiskárny. Pokud není požadované tiskárně písmo, použijte [CEditView::SetPrinterFont](#setprinterfont) ho změnit.  
  
##  <a name="getselectedtext"></a>CEditView::GetSelectedText  
 Volání `GetSelectedText` zkopírovat vybraný text do `CString` objekt, do konce výběru nebo znak před první znak návratu ve výběru.  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strResult`  
 Odkaz na `CString` objekt, který se zobrazí vybraný text.  
  
##  <a name="lockbuffer"></a>CEditView::LockBuffer  
 Volání této funkce člen k získání ukazatele do vyrovnávací paměti. Vyrovnávací paměť se nesmí upravovat.  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládací prvek upravit vyrovnávací paměti.  
  
##  <a name="onfindnext"></a>CEditView::OnFindNext  
 Vyhledá text ve vyrovnávací paměti pro textem určeným parametrem `lpszFind`, ve směru určeného `bNext`, s rozlišování určeného `bCase`.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, která se má najít.  
  
 `bNext`  
 Určuje směr, hledání. Pokud **TRUE**, směr vyhledávání je na konci vyrovnávací paměti. Pokud **FALSE**, směr vyhledávání je k začátku vyrovnávací paměti.  
  
 `bCase`  
 Určuje, zda při hledání velká a malá písmena. Pokud **TRUE**, hledání je malá a velká písmena. Pokud **FALSE**, hledání nerozlišuje velká a malá písmena.  
  
### <a name="remarks"></a>Poznámky  
 Hledání spustí na začátku aktuální výběr a se provádí prostřednictvím volání [řetězec FindText](#findtext). Výchozí implementace `OnFindNext` volání [OnTextNotFound](#ontextnotfound) Pokud text není nalezen.  
  
 Přepsání `OnFindNext` změnit způsob `CEditView`-odvozené objekt vyhledá text. `CEditView`volání `OnFindNext` když uživatel vybere možnost Najít další v dialogovém okně Standardní najít.  
  
##  <a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`volání `OnReplaceAll` když uživatel vybere tlačítko Nahradit vše v dialogovém okně Standardní nahradit.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, která se má najít.  
  
 `lpszReplace`  
 Text nahradit hledaný text.  
  
 `bCase`  
 Určuje, zda hledání velká a malá písmena. Pokud **TRUE**, hledání je malá a velká písmena. Pokud **FALSE**, hledání nerozlišuje velká a malá písmena.  
  
### <a name="remarks"></a>Poznámky  
 `OnReplaceAll`Vyhledá text ve vyrovnávací paměti pro textem určeným parametrem `lpszFind`, s rozlišování určeného `bCase`. Hledání se spustí na začátku aktuální výběr. Pokaždé, když je nalezen text vyhledávání, tato funkce nahrazuje že výskyt textu s textem určeným parametrem `lpszReplace`. Hledání se provádí prostřednictvím volání [řetězec FindText](#findtext). Výchozí implementace [OnTextNotFound](#ontextnotfound) je volána, pokud není nalezen text.  
  
 Pokud aktuální výběr neodpovídá `lpszFind`, výběr se aktualizuje na první výskyt textem určeným parametrem `lpszFind` a nahrazení nebude provedeno. To umožňuje uživateli potvrďte, že je co chce udělat, když výběr neodpovídá text, který má být nahrazen.  
  
 Přepsání `OnReplaceAll` změnit způsob `CEditView`-odvozené objektu nahradí text.  
  
##  <a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`volání `OnReplaceSel` když uživatel vybere tlačítko nahraďte v dialogovém okně Standardní nahradit.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, která se má najít.  
  
 `bNext`  
 Určuje směr, hledání. Pokud **TRUE**, směr vyhledávání je na konci vyrovnávací paměti. Pokud **FALSE**, směr vyhledávání je k začátku vyrovnávací paměti.  
  
 `bCase`  
 Určuje, zda při hledání velká a malá písmena. Pokud **TRUE**, hledání je malá a velká písmena. Pokud **FALSE**, hledání nerozlišuje velká a malá písmena.  
  
 `lpszReplace`  
 Text, který nahradí nalezen text.  
  
### <a name="remarks"></a>Poznámky  
 Po nahrazení výběr, tato funkce vyhledá text ve vyrovnávací paměti pro další výskyt textem určeným parametrem `lpszFind`, ve směru určeného `bNext`, s rozlišování určeného `bCase`. Hledání se provádí prostřednictvím volání [řetězec FindText](#findtext). Pokud text není nalezen, [OnTextNotFound](#ontextnotfound) je volána.  
  
 Přepsání `OnReplaceSel` změnit způsob `CEditView`-odvozené objektu nahradí vybraný text.  
  
##  <a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 Přepsání této funkci můžete změnit výchozí implementace, která volá funkci Windows **MessageBeep**.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, která se má najít.  
  
##  <a name="printinsiderect"></a>CEditView::PrintInsideRect  
 Volání `PrintInsideRect` tisk textu v obdélníku určeného *rectLayout*.  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext zařízení tiskárny.  
  
 *rectLayout*  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect – struktura](../../mfc/reference/rect-structure1.md) zadání obdélníku, ve kterém má být vykreslen text.  
  
 `nIndexStart`  
 Index v rámci vyrovnávací paměť první znak, který má být vykreslen.  
  
 `nIndexStop`  
 Index v rámci vyrovnávací paměť znaku následující poslední znak, který má být vykreslen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index další znak, který má být vytištěn (tedy znak za jeho poslední znak vykresluje).  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CEditView` ovládací prvek nemá styl **es_autohscroll –**, zabalená textu v obdélníku pro vykreslování. Pokud ovládací prvek nemá styl **es_autohscroll –**, text je oříznut na pravý okraj rámečku.  
  
 **Rect.bottom** element *rectLayout* objekt se změnilo tak, že dimenze obdélníku definovat součástí původní obdélníku, která je zaneprázdněn text.  
  
##  <a name="serializeraw"></a>CEditView::SerializeRaw  
 Volání `SerializeRaw` tak, aby měl `CArchive` objektu pro čtení nebo zápis textu `CEditView` objektu do textového souboru.  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 Odkaz na `CArchive` objekt, který ukládá serializovaných text.  
  
### <a name="remarks"></a>Poznámky  
 `SerializeRaw`se liší od `CEditView`na interní implementace `Serialize` v, že ho čte a zapisuje pouze text, bez předchozích dat popis objektu.  
  
##  <a name="setprinterfont"></a>CEditView::SetPrinterFont  
 Volání `SetPrinterFont` nastavení tiskárny písma pro písmo určeného `pFont`.  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Ukazatel na objekt typu `CFont`. Pokud **NULL**, písmo použité pro tisk je založena na zobrazení písma.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete vždy používat zvolené písmo k dispozici pro tisk zobrazení, zahrnují volání `SetPrinterFont` ve své třídě `OnPreparePrinting` funkce. Tato virtuální funkce je volána, než dojde k tisku, změna písma probíhá před tisku obsah zobrazení.  
  
##  <a name="settabstops"></a>CEditView::SetTabStops  
 Volání této funkce pro nastavení zarážek používá pro zobrazení a tisk.  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>Parametry  
 `nTabStops`  
 Šířka každou zarážku v jednotky dialogu.  
  
### <a name="remarks"></a>Poznámky  
 Je podporován pouze jeden Šířka zarážky. ( `CEdit` objekty podporují více karta šířky.) V dialogovém okně jednotkách, které rovnat jeden čtvrtý šířky průměrná znak písmo použité v době tisku nebo zobrazení (podle velká a malá písmena abecední znaky pouze) jsou šířky. Neměli byste používat `CEdit::SetTabStops` protože `CEditView` musí mezipaměti hodnota zarážky.  
  
 Tato funkce změní pouze karty objektu, pro kterou je volána. Chcete-li změnit na kartě zastaví pro každou `CEditView` objektu v aplikaci, volání každý objekt `SetTabStops` funkce.  
  
### <a name="example"></a>Příklad  
 Tento fragment kódu nastaví zarážky v ovládacím prvku pro každý čtvrtý znak pečlivě měřením písmo, které používá ovládacího prvku.  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 Volání této funkce člen k odemknutí vyrovnávací paměti.  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Volání `UnlockBuffer` po dokončení pomocí ukazatele vrácený [LockBuffer](#lockbuffer).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC SUPERPAD](../../visual-cpp-samples.md)   
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [CDocument – třída](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
