---
title: CKeyboardManager – třída
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: e4f8f678e76113b5d012242f474ff0ab8b0628dd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505782"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager – třída

Slouží ke správě tabulek klávesových zkratek pro hlavní okno rámce a pro okna podřízených rámečků.

## <a name="syntax"></a>Syntaxe

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name|Popis|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|`CKeyboardManager` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name|Popis|
|[CKeyboardManager:: CleanUp](#cleanup)|Vymaže tabulky klávesových zkratek.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Načte výchozí klávesovou zkratku pro zadaný příkaz a okno.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Určuje, zda je klíč zpracováván tabulkou akcelerátoru.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Označuje, zda je znak tisknutelný.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Označuje, zda jsou v nabídkách zobrazeny všechny klávesové zkratky pro příkaz nebo pouze výchozí klávesovou zkratku.|
|[CKeyboardManager:: LoadState](#loadstate)|Načte z registru Windows tabulky klávesových zkratek.|
|[CKeyboardManager::ResetAll](#resetall)|Znovu načte tabulky klávesových zkratek z prostředku aplikace.|
|[CKeyboardManager:: SaveState](#savestate)|Uloží tabulky klávesových zkratek do registru systému Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Určuje, zda se v rozhraní zobrazí všechny klávesové zkratky pro všechny příkazy nebo jedna klávesová zkratka pro každý příkaz. Tato metoda nemá vliv na příkazy, které mají pouze jednu přidruženou klávesovou zkratku.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Převede znak na jeho horní registr.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje tabulku klávesových zkratek novou tabulkou klávesových zkratek.|

## <a name="remarks"></a>Poznámky

Členové této třídy vám umožňují uložit a načíst tabulky klávesových zkratek do registru systému Windows, pomocí šablony aktualizovat tabulky krátkého vyjmutí klíče a vyhledat výchozí klávesovou zkratku pro příkaz v okně rámce. Kromě toho `CKeyboardManager` objekt umožňuje řídit, jak se budou zobrazovat klávesové zkratky uživateli.

`CKeyboardManager` Objekt byste neměli vytvářet ručně. Vytvoří se automaticky architekturou vaší aplikace. Během procesu inicializace vaší aplikace byste však měli zavolat metodu [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) . Chcete-li získat ukazatel na správce klávesnice pro vaši aplikaci, zavolejte [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst ukazatel na `CKeyboardManager` objekt `CWinAppEx` z třídy a jak zobrazit všechny klávesové zkratky přidružené k příkazům nabídky. Tento fragment kódu je součástí [ukázky vlastních stránek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager. h

##  <a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager

`CKeyboardManager` Vytvoří objekt.

```
CKeyboardManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů nemusíte vytvářet `CKeyboardManager` přímo. Ve výchozím nastavení vytvoří rozhraní jednu za vás. Chcete-li získat ukazatel na `CKeyboardManager`, zavolejte [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Pokud vytvoříte jednu ručně, musíte ji inicializovat pomocí metody [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

##  <a name="cleanup"></a>CKeyboardManager:: CleanUp

`CKeyboardManager` Uvolní prostředky a vymaže všechna mapování klávesových zkratek.

```
static void CleanUp();
```

### <a name="remarks"></a>Poznámky

Další informace o klávesových zkratkách naleznete v tématu [Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).

Tuto funkci není nutné volat, pokud dojde k ukončení aplikace, protože ji rozhraní volá automaticky během ukončení aplikace.

##  <a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator

Načte výchozí klávesovou zkratku pro zadaný příkaz a okno.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu

*str*<br/>
mimo Odkaz na `CString` objekt.

*pWndFrame*<br/>
pro Ukazatel na okno rámce.

*bIsDefaultFrame*<br/>
pro Určuje, zda je okno rámce výchozím oknem rámce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se zástupce najde; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá příkaz určený parametrem *uiCmd* a načte výchozí klávesovou zkratku. Pak metoda převezme řetězec přidružený k této klávesové zkratce a zapíše hodnotu do parametru *str* .

##  <a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled

Určuje, zda je zadaný klíč zpracován třídou [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*nKey*|pro Klíč, který se má kontrolovat|
|*fVirt*|pro Určuje chování klávesových zkratek. Seznam možných hodnot naleznete v tématu [Struktura akcelerace](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndFrame*|pro Okno rámce. Tato metoda určuje, zda je v tomto snímku zpracovávána klávesová zkratka.|
|*bIsDefaultFrame*|pro Logický parametr, který označuje, zda je *pWndFrame* výchozím oknem rámce.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zpracována klávesová zkratka. FALSE, pokud klíč není zpracován nebo pokud má *pWndFrame* hodnotu null.

### <a name="remarks"></a>Poznámky

Vstupní parametry se musí shodovat s položkou v tabulce akcelerátoru pro *nKey* a *fVirt* , aby bylo možné určit, zda je v *pWndFrame*zpracována klávesová zkratka.

##  <a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable

Označuje, zda je znak tisknutelný.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*nChar*|pro Znak, který tato metoda kontroluje.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je znak tisknutelný, nula, pokud není.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila, pokud volání [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) selhává.

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

Označuje, zda jsou v nabídkách zobrazeny všechny klávesové zkratky přidružené k příkazům nabídky nebo pouze výchozí klávesové zkratky.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud aplikace obsahuje seznam všech klávesových zkratek pro příkazy nabídky; 0, pokud aplikace zobrazuje pouze výchozí klávesové zkratky.

### <a name="remarks"></a>Poznámky

Aplikace zobrazí seznam klávesových zkratek pro příkazy nabídky na řádku nabídek. Pomocí funkce [CKeyboardManager:: ShowAllAccelerators](#showallaccelerators) určete, zda aplikace obsahuje seznam všech klávesových zkratek nebo pouze výchozí klávesové zkratky.

##  <a name="loadstate"></a>CKeyboardManager:: LoadState

Načte z registru Windows tabulky klávesových zkratek.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Cesta v registru, `CKeyboardManager` kam se ukládají data.

*pDefaultFrame*<br/>
pro Ukazatel na okno rámce, které má být použito jako výchozí okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl stav úspěšně načten nebo 0, jinak.

### <a name="remarks"></a>Poznámky

Pokud má parametr *lpszProfileName* hodnotu null, tato metoda zkontroluje výchozí umístění registru pro `CKeyboardManager` data. Výchozí umístění registru je určeno [třídou CWinAppEx](../../mfc/reference/cwinappex-class.md). Data musí být napsána dříve pomocí metody [CKeyboardManager:: SaveState](#savestate).

Pokud nezadáte výchozí okno, bude použito okno hlavního rámce vaší aplikace.

##  <a name="resetall"></a>CKeyboardManager::ResetAll

Znovu načte tabulky klávesových zkratek z prostředku aplikace.

```
void ResetAll();
```

### <a name="remarks"></a>Poznámky

Tato funkce vymaže zástupce uložené v `CKeyboardManager` instanci. Pak znovu nasadí stav správce klávesnice z prostředku aplikace.

##  <a name="savestate"></a>CKeyboardManager:: SaveState

Uloží tabulky klávesových zkratek do registru systému Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Cesta v registru pro uložení `CKeyboardManager` stavu.

*pDefaultFrame*<br/>
pro Ukazatel na okno rámce, které se změní na výchozí okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl stav správce klávesnice úspěšně uložen nebo 0 jinak.

### <a name="remarks"></a>Poznámky

Pokud má parametr *lpszProfileName* hodnotu null, tato metoda zapíše `CKeyboardManager` stav do výchozího umístění určeného třídou [CWinAppEx](../../mfc/reference/cwinappex-class.md). Pokud zadáte umístění, můžete načíst data později pomocí metody [CKeyboardManager:: LoadState](#loadstate).

Pokud nezadáte výchozí okno, použije se jako výchozí okno hlavní okno rámce.

##  <a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators

Zobrazí všechny klávesové zkratky přidružené k příkazům nabídky.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parametry

*bShowAll*<br/>
pro Při hodnotě TRUE se zobrazí všechny klávesové zkratky. Pokud má hodnotu FALSE, zobrazí se pouze první klávesová zkratka.

*lpszDelimiter*<br/>
pro Řetězec, který má být vložen mezi klávesové zkratky. Tento oddělovač nemá žádný vliv, pokud se zobrazí pouze jedna klávesová zkratka.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení platí, že pokud k příkazu je přidruženo více klávesových zkratek, bude zobrazena pouze první klávesová zkratka. Tato funkce umožňuje zobrazit seznam všech klávesových zkratek přidružených ke všem příkazům.

Klávesové zkratky budou uvedeny vedle příkazu v řádku nabídek. Pokud se zobrazí všechny klávesové zkratky, řetězec poskytnutý pomocí *lpszDelimiter* bude oddělit jednotlivé klávesové zkratky.

##  <a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToUpper

Převede znak na jeho horní registr.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
pro Znak, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Znak, který je horní registr vstupního parametru.

##  <a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable

Aktualizuje tabulku klávesových zkratek novou tabulkou klávesových zkratek.

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
pro Ukazatel na šablonu dokumentu.

*lpAccel*<br/>
pro Ukazatel na novou klávesovou zkratku.

*nSize*<br/>
pro Velikost nové zkratky tabulky

*pDefaultFrame*<br/>
pro Ukazatel na výchozí okno rámce.

*hAccelNew*<br/>
pro Popisovač nové místní tabulky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze nahradit existující zkratku pomocí nových klávesových zkratek pro několik objektů okna rámce. Funkce obdrží šablonu dokumentu jako parametr pro získání přístupu ke všem objektům okna rámce připojeným k dané šabloně dokumentu.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)
