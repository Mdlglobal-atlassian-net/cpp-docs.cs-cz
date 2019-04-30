---
title: Ckeyboardmanager – třída
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
ms.openlocfilehash: 3360a28d50f64546837cc5ef35dcfc761b4fb0f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341495"
---
# <a name="ckeyboardmanager-class"></a>Ckeyboardmanager – třída

Spravuje tabulky klávesových zkratek pro hlavní okno rámce a podřízených oken rámce.

## <a name="syntax"></a>Syntaxe

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Vytvoří `CKeyboardManager` objektu.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CKeyboardManager::CleanUp](#cleanup)|Vymaže tabulky klávesových zkratek.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Načte výchozí klávesovou zkratku pro zadaný příkaz i jeho okna.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Určuje, zda klíč se zpracovává souborem tabulky akcelerátorů.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Určuje, zda je tisknutelný znak.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Označuje, zda zobrazovat nabídky všechny klávesové zkratky pro příkaz nebo pouze výchozí klávesovou zkratku.|
|[CKeyboardManager::LoadState](#loadstate)|Načte tabulky klávesových zkratek z registru Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Znovu načte tabulky klávesových zkratek z prostředků aplikace.|
|[CKeyboardManager::SaveState](#savestate)|Uloží zástupce klíče tabulky do registru Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Určuje, zda zobrazí rozhraní všech klávesových zkratek pro všechny příkazy nebo pro každý příkaz s jednoklávesovou zkratkou. Tato metoda nemá vliv na příkazy, které mají pouze jednu související klávesovou zkratku.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Převede znak na jeho horní registru.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizace klíče tabulky místní pomocí nového klíče tabulky místní.|

## <a name="remarks"></a>Poznámky

Členové této třídy umožňují uložit a načíst tabulky klávesových zkratek v registru Windows, použijte šablony k aktualizaci klíče tabulky místní a výchozí klávesovou zkratku pro příkaz Najít v okně s rámečkem. Kromě toho `CKeyboardManager` objektu umožňuje řídit, jak se uživateli zobrazí klávesové zkratky.

Nevytvářejte `CKeyboardManager` objekt ručně. Vytvoří se automaticky podle rozhraní framework vaší aplikace. Nicméně byste měli volat [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) během procesu inicializace vaší aplikace. Chcete-li získat ukazatel do správce klávesnice pro vaši aplikaci, zavolejte [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak se načítají ukazatel na `CKeyboardManager` objektu z `CWinAppEx` třídy a zobrazení všech klávesových zkratek spojené s příkazy nabídek. Tento fragment kódu je součástí [ukázková vlastní stránky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxkeyboardmanager.h

##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager

Vytvoří `CKeyboardManager` objektu.

```
CKeyboardManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů není nutné vytvořit `CKeyboardManager` přímo. Ve výchozím nastavení rozhraní ho vytvoří za vás. Chcete-li získat ukazatel `CKeyboardManager`, volání [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Pokud je vytvořit ručně, je třeba inicializovat metodou [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

##  <a name="cleanup"></a>  CKeyboardManager::CleanUp

Uvolňuje `CKeyboardManager` prostředky a vymaže všechny místní mapování klíčů.

```
static void CleanUp();
```

### <a name="remarks"></a>Poznámky

Další informace o klávesových zkratkách naleznete v tématu [přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).

Není nutné volat tuto funkci při ukončení aplikace, protože volá framework se automaticky při ukončení aplikace.

##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator

Načte výchozí klávesovou zkratku pro zadaný příkaz i jeho okna.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] ID příkazu.

*str*<br/>
[out] Odkaz na `CString` objektu.

*pWndFrame*<br/>
[in] Ukazatel na okno rámce.

*bIsDefaultFrame*<br/>
[in] Určuje, zda je okno rámce okna rámce výchozí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zástupce; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá určený příkaz *uiCmd* a načte výchozí klávesovou zkratku. Metoda přebírá řetězec přidružený k této klávesové zkratky a zapíše hodnota, která má *str* parametru.

##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled

Určuje, zda se zadaným klíčem zařizuje služba [ckeyboardmanager – třída](../../mfc/reference/ckeyboardmanager-class.md).

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
|*nKey*|[in] Klíč ke kontrole.|
|*fVirt*|[in] Určuje chování klávesovou zkratku. Seznam možných hodnot najdete v tématu [AKCELERACE struktura](/windows/desktop/api/winuser/ns-winuser-tagaccel).|
|*pWndFrame*|[in] Okno rámce. Tato metoda určuje, zda je zpracována klávesovou zkratku v tomto snímku.|
|*bIsDefaultFrame*|[in] Parametr logické hodnoty označující, zda *pWndFrame* je okno rámce výchozí.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se zpracovává klávesovou zkratku. FALSE Pokud nezpracovává klíči, nebo pokud *pWndFrame* má hodnotu NULL.

### <a name="remarks"></a>Poznámky

Vstupní parametry musí odpovídat záznam v akcelerátoru tabulce pro *nKey* a *fVirt* k určení, zda se v zpracovává klávesovou zkratku *pWndFrame*.

##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable

Určuje, zda je tisknutelný znak.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*nChar*|[in] Znak, který tato metoda zkontroluje.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je tisknutelný znak, hodnotu není.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud je volání [GetKeyboardState](/windows/desktop/api/winuser/nf-winuser-getkeyboardstate) selže.

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

Označuje, zda zobrazovat nabídky všech klávesových zkratek spojené s příkazy nabídky nebo pouze výchozí klávesové zkratky.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aplikace obsahuje seznam všech klávesových zkratek pro příkazy nabídky. 0, pokud aplikace zobrazí pouze výchozí klávesové zkratky.

### <a name="remarks"></a>Poznámky

Aplikace jsou uvedeny klávesové zkratky pro příkazy v panelu nabídek. Použijte funkci [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) řídit, jestli aplikace obsahuje seznam všech klávesových zkratek nebo jenom výchozí klávesové zkratky.

##  <a name="loadstate"></a>  CKeyboardManager::LoadState

Načte tabulky klávesových zkratek z registru Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cesta v registru kde `CKeyboardManager` data jsou uložena.

*pDefaultFrame*<br/>
[in] Ukazatel na okno rámce, který se použije jako výchozí okna.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud stav jinak bylo úspěšně načteny, nebo 0.

### <a name="remarks"></a>Poznámky

Pokud *lpszProfileName* parametr hodnotu NULL, tato metoda zkontroluje výchozí umístění registru `CKeyboardManager` data. Je určená výchozí umístění registru [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md). Data musí být dříve napsané pomocí metody [CKeyboardManager::SaveState](#savestate).

Pokud okno výchozí nezadáte, použije se hlavní okno rámce aplikace.

##  <a name="resetall"></a>  CKeyboardManager::ResetAll

Znovu načte tabulky klávesových zkratek z prostředků aplikace.

```
void ResetAll();
```

### <a name="remarks"></a>Poznámky

Tato funkce zruší zkratky uložené v `CKeyboardManager` instance. To se pak znovu načtěte stavu klávesnice správce z prostředku aplikace.

##  <a name="savestate"></a>  CKeyboardManager::SaveState

Uloží zástupce klíče tabulky do registru Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cestu registru pro ukládání `CKeyboardManager` stavu.

*pDefaultFrame*<br/>
[in] Ukazatel na rámec okna, který změní výchozí okna.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud správce stavu klávesnice byla uložena úspěšně, nebo jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *lpszProfileName* parametr hodnotu NULL, tato metoda bude zapisovat `CKeyboardManager` do výchozího umístění, které určuje stavu [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md). Pokud zadáte umístění, můžete načíst data později pomocí metody [CKeyboardManager::LoadState](#loadstate).

Pokud nezadáte výchozí okna, okna hlavního rámce se použije jako výchozí okna.

##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators

Zobrazí všechny klávesové zkratky spojené s příkazy nabídek.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parametry

*bShowAll*<br/>
[in] Pokud je hodnota TRUE, zobrazí se všechny klávesové zkratky. Pokud má hodnotu FALSE, zobrazí se pouze první klávesovou zkratku.

*lpszDelimiter*<br/>
[in] Řetězec se dá vložit mezi klávesových zkratek. Tento oddělovač nemá žádný vliv, pokud pouze zobrazí jednu klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení Pokud příkaz obsahuje více než jednu klávesovou zkratku přidruženo, pouze první klávesovou zkratku se nezobrazí. Tato funkce umožňuje seznam všech klávesových zkratek přidružené všechny příkazy.

Klávesové zkratky budou zobrazeny vedle příkazu v řádku nabídek. Pokud se zobrazí všechny klávesové zkratky, řetězec poskytované *lpszDelimiter* se oddělit jednotlivé klávesových zkratek.

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

Převede znak na jeho horní registru.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
[in] Znak pro převod.

### <a name="return-value"></a>Návratová hodnota

Znak, který je horní registr vstupního parametru.

##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable

Aktualizace klíče tabulky místní pomocí nového klíče tabulky místní.

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
[in] Ukazatel na šablonu dokumentu.

*lpAccel*<br/>
[in] Ukazatel na novou klávesovou zkratku.

*nSize*<br/>
[in] Velikost novou místní tabulku.

*pDefaultFrame*<br/>
[in] Ukazatel na okno rámce výchozí.

*hAccelNew*<br/>
[in] Popisovač do nové tabulky místní.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte, pokud chcete nahradit existující místní tabulky nové klávesové zkratky pro několik objektů oken rámce. Funkce šablony dokumentu přijímá jako parametr získat přístup ke všem objektům okno rámce připojený k šabloně dokumentu.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)
