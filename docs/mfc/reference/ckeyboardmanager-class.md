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
ms.openlocfilehash: 5d0f544943cc8584960bb2668ee7ce326547e2fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372319"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager – třída

Spravuje tabulky klávesových zkratek pro okno hlavního rámce a podřízená okna rámců.

## <a name="syntax"></a>Syntaxe

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Vytvoří `CKeyboardManager` objekt.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CKeyboardManager::Vyčištění](#cleanup)|Vymaže tabulky klávesových zkratek.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Načte výchozí klávesovou zkratku pro zadaný příkaz a okno.|
|[CKeyboardManager::IskeyHandled](#iskeyhandled)|Určuje, zda je klíč zpracován tabulkou akcelerátoru.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Označuje, zda lze znak vytisknout.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Označuje, zda nabídky zobrazují všechny klávesové zkratky pro příkaz nebo pouze výchozí klávesovou zkratku.|
|[CKeyboardManager::LoadState](#loadstate)|Načte tabulky klávesových zkratek z registru systému Windows.|
|[CKeyboardManager::Resetall](#resetall)|Znovu načte tabulky klávesových zkratek z prostředku aplikace.|
|[CKeyboardManager::SaveState](#savestate)|Uloží tabulky klávesových zkratek do registru systému Windows.|
|[CKeyboardManager::Zobrazitvšechnyakcelery](#showallaccelerators)|Určuje, zda se v rámci zobrazí všechny klávesové zkratky pro všechny příkazy nebo jednu klávesovou zkratku pro každý příkaz. Tato metoda nemá vliv na příkazy, které mají pouze jednu přidruženou klávesovou zkratku.|
|[CKeyboardManager::PřeložitChartoupper](#translatechartoupper)|Převede znak na jeho horní registr.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje tabulku klávesových zkratek novou tabulkou klávesových zkratek.|

## <a name="remarks"></a>Poznámky

Členové této třídy umožňují ukládat a načítat tabulky klávesových zkratek do registru systému Windows, používat šablonu k aktualizaci krátkých tabulek kláves a najít výchozí klávesovou zkratku pro příkaz v okně rámce. Kromě toho `CKeyboardManager` objekt umožňuje řídit, jak se zobrazí klávesové zkratky pro uživatele.

Objekt byste neměli vytvářet `CKeyboardManager` ručně. Bude vytvořen automaticky v rámci vaší aplikace. Měli byste však volat [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) během procesu inicializace vaší aplikace. Chcete-li získat ukazatel na správce klávesnice pro vaši aplikaci, volejte [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst `CKeyboardManager` ukazatel na `CWinAppEx` objekt z třídy a jak zobrazit všechny klávesové zkratky přidružené k příkazům nabídky. Tento fragment kódu je součástí [ukázky vlastních stránek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager

Vytvoří `CKeyboardManager` objekt.

```
CKeyboardManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů není třeba vytvořit `CKeyboardManager` přímo. Ve výchozím nastavení rozhraní vytvoří jeden pro vás. Chcete-li získat `CKeyboardManager`ukazatel na , volejte [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Pokud jej vytvoříte ručně, musíte jej inicializovat metodou [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>CKeyboardManager::Vyčištění

Uvolní `CKeyboardManager` prostředky a vymaže všechna mapování klávesových zkratek.

```
static void CleanUp();
```

### <a name="remarks"></a>Poznámky

Další informace o klávesových zkratkách naleznete v [tématu Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).

Není nutné volat tuto funkci při ukončení aplikace, protože rozhraní framework volá automaticky během ukončení aplikace.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator

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
[v] ID příkazu.

*Str*<br/>
[out] Odkaz na `CString` objekt.

*pWndRám*<br/>
[v] Ukazatel na okno rámce.

*bIsDefaultFrame*<br/>
[v] Určuje, zda je okno rámce výchozím oknem rámce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zkratka nalezena; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá příkaz určený *uiCmd* a načte výchozí klávesovou zkratku. Potom metoda převezme řetězec přidružený k této klávesové zkratce a zapíše hodnotu do parametru *str.*

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>CKeyboardManager::IskeyHandled

Určuje, zda je zadaný klíč zpracován [třídou CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

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
|*nKlíč*|[v] Klíč ke kontrole.|
|*fVirt*|[v] Určuje chování klávesové zkratky. Seznam možných hodnot naleznete v tématu [ACCEL Structure](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndRám*|[v] Okno rámce. Tato metoda určuje, zda je v tomto rámci zpracována klávesová zkratka.|
|*bIsDefaultFrame*|[v] Logický parametr, který označuje, zda *pWndFrame* je výchozí okno rámce.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je klávesová zkratka zpracována. FALSE, pokud klíč není zpracovánnebo pokud *pWndFrame* je NULL.

### <a name="remarks"></a>Poznámky

Vstupní parametry se musí shodovat se vstupem v tabulce akcelerátoru jak pro *nKey,* tak *pro fVirt,* aby bylo možné určit, zda je klávesová zkratka zpracována v *pWndFrame*.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable

Označuje, zda lze znak vytisknout.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Nchar*|[v] Znak, který tato metoda kontroluje.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je znak tisknutelný, nula, pokud není.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud volání [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) selže.

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllAccelerators

Označuje, zda nabídky zobrazují všechny klávesové zkratky přidružené k příkazům nabídky nebo pouze výchozí klávesové zkratky.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud aplikace obsahuje všechny klávesové zkratky pro příkazy nabídky; 0, pokud aplikace zobrazuje pouze výchozí klávesové zkratky.

### <a name="remarks"></a>Poznámky

Aplikace obsahuje seznam klávesových zkratek pro příkazy nabídek v řádku nabídek. Pomocí funkce [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) můžete určit, zda aplikace obsahuje všechny klávesové zkratky nebo pouze výchozí klávesové zkratky.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>CKeyboardManager::LoadState

Načte tabulky klávesových zkratek z registru systému Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta registru, `CKeyboardManager` kde jsou uložena data.

*pVýchozí rámec*<br/>
[v] Ukazatel na okno rámce, které se má použít jako výchozí okno.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl stav úspěšně načten nebo 0 jinak.

### <a name="remarks"></a>Poznámky

Pokud je parametr *lpszProfileName* NULL, tato metoda `CKeyboardManager` zkontroluje výchozí umístění registru pro data. Výchozí umístění registru je určeno [třídou CWinAppEx](../../mfc/reference/cwinappex-class.md). Data musí být dříve zapsána metodou [CKeyboardManager::SaveState](#savestate).

Pokud nezadáte výchozí okno, bude použito okno hlavního rámce aplikace.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>CKeyboardManager::Resetall

Znovu načte tabulky klávesových zkratek z prostředku aplikace.

```
void ResetAll();
```

### <a name="remarks"></a>Poznámky

Tato funkce vymaže `CKeyboardManager` zkratky uložené v instanci. Potom znovu načte stav správce klávesnice z prostředku aplikace.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>CKeyboardManager::SaveState

Uloží tabulky klávesových zkratek do registru systému Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta registru pro `CKeyboardManager` uložení stavu.

*pVýchozí rámec*<br/>
[v] Ukazatel na okno rámce, které se stane výchozím oknem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl stav správce klávesnice úspěšně uložen, nebo 0 jinak.

### <a name="remarks"></a>Poznámky

Pokud je parametr *lpszProfileName* null, tato `CKeyboardManager` metoda zapíše stav do výchozího umístění určeného [třídou CWinAppEx](../../mfc/reference/cwinappex-class.md). Pokud zadáte umístění, můžete data načíst později pomocí metody [CKeyboardManager::LoadState](#loadstate).

Pokud nezadáte výchozí okno, bude jako výchozí okno použito okno hlavního rámce.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>CKeyboardManager::Zobrazitvšechnyakcelery

Zobrazí všechny klávesové zkratky přidružené k příkazům nabídky.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parametry

*bZobrazitVše*<br/>
[v] Pokud true, zobrazí se všechny klávesové zkratky. Pokud false, zobrazí se pouze první klávesová zkratka.

*lpszDelimiter*<br/>
[v] Řetězec, který chcete vložit mezi klávesové zkratky. Tento oddělovač nemá žádný vliv, pokud je zobrazena pouze jedna klávesová zkratka.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, pokud má příkaz přidruženo více než jednu klávesovou zkratku, zobrazí se pouze první klávesová zkratka. Tato funkce umožňuje vypsat všechny klávesové zkratky přidružené ke všem příkazům.

Klávesové zkratky budou uvedeny vedle příkazu v řádku nabídek. Pokud jsou zobrazeny všechny klávesové zkratky, řetězec poskytnutý *lpszDelimiter* oddělí jednotlivé klávesové zkratky.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>CKeyboardManager::PřeložitChartoupper

Převede znak na jeho horní registr.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*Nchar*<br/>
[v] Znak převést.

### <a name="return-value"></a>Návratová hodnota

Znak, který je horním registrem vstupního parametru.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable

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

*pŠablona*<br/>
[v] Ukazatel na šablonu dokumentu.

*lpAccel*<br/>
[v] Ukazatel na novou klávesovou zkratku.

*nVelikost*<br/>
[v] Velikost nové tabulky zástupců.

*pVýchozí rámec*<br/>
[v] Ukazatel na výchozí okno rámce.

*hAccelNovinka*<br/>
[v] Úchyt pro novou klávesovou tabulku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete nahradit existující tabulku zkratek novými klávesovými zkratkami pro několik objektů okna rámce. Funkce obdrží šablonu dokumentu jako parametr pro získání přístupu ke všem objektům okna rámce připojeným k dané šabloně dokumentu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)
