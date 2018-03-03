---
title: "Třída CKeyboardManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7547887b4ad34ecbbea32516eaf76b6f4d1ab25d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager – třída
Spravuje zástupce klíče tabulky hlavního rámce okna a okna s rámečkem podřízené.  
  
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
|[CKeyboardManager::CleanUp](#cleanup)|Vymaže klíče tabulky zástupce.|  
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Načte výchozí klávesovou zkratku pro okno a zadaný příkaz.|  
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Určuje, zda je klíč zpracovávaných tabulky akcelerátorů.|  
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Určuje, zda znak je nastaveno.|  
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Určuje, zda nabídky Zobrazit všechny klávesové zkratky pro příkaz nebo pouze výchozí klávesovou zkratku.|  
|[CKeyboardManager::LoadState](#loadstate)|Načte klíče tabulky zástupce z registru systému Windows.|  
|[CKeyboardManager::ResetAll](#resetall)|Znovu načte zástupce klíče tabulky z prostředků aplikace.|  
|[CKeyboardManager::SaveState](#savestate)|Uloží zástupce klíče tabulky do registru systému Windows.|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Určuje, zda rozhraní zobrazí všechny klávesové zkratky pro všechny příkazy nebo jeden klávesovou zkratku u každého příkazu. Tato metoda neovlivňuje příkazy, které mají pouze jeden klíč přidružený zástupce.|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Převádí znak na jeho horní registrace.|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Aktualizuje zástupce klíče tabulky pomocí nového klíče tabulky zástupce.|  
  
## <a name="remarks"></a>Poznámky  
 Členové této třídy vám umožní uložit a načíst klíče tabulky zástupce do registru systému Windows, použijte šablonu aktualizovat klíče tabulky vyjmutí krátké a najít výchozí klávesovou zkratku příkazu v okně s rámečkem. Kromě toho `CKeyboardManager` objektu umožňuje řídit způsob zobrazení klávesové zkratky pro uživatele.  
  
 Byste je neměli vytvářet `CKeyboardManager` objekt ručně. Bude vytvořen automaticky rámcem vaší aplikace. Nicméně, by měly volat [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) během inicializace vaší aplikace. Získání ukazatele na manager klávesnice pro vaši aplikaci, volání [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst ukazatel `CKeyboardManager` objektu z `CWinAppEx` třídy a všechny klávesové zkratky přidružené příkazy nabídky zobrazení. Tento fragment kódu je součástí [vlastní stránky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxkeyboardmanager.h  
  
##  <a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager  
 Vytvoří `CKeyboardManager` objektu.  
  
```  
CKeyboardManager();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve většině případů není nutné vytvořit `CKeyboardManager` přímo. Ve výchozím nastavení vytvoří rozhraní framework za vás. Chcete-li získat ukazatel na `CKeyboardManager`, volání [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Pokud vytvoříte jeden ručně, je třeba inicializovat pomocí metody [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).  
  
##  <a name="cleanup"></a>CKeyboardManager::CleanUp  
 Uvolní `CKeyboardManager` prostředky a vymaže všechny mapování klíčů zástupce.  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace o klávesové zkratky najdete v tématu [přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).  
  
 Nemáte volání této funkce, pokud vaše aplikace bude ukončen, protože volá framework ji automaticky při ukončení aplikace.  
  
##  <a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator  
 Načte výchozí klávesovou zkratku pro okno a zadaný příkaz.  
  
```  
static BOOL FindDefaultAccelerator(
    UINT uiCmd,  
    CString& str,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu.  
  
 [out]`str`  
 Odkaz na `CString` objektu.  
  
 [v]`pWndFrame`  
 Ukazatel na rámec okna.  
  
 [v]`bIsDefaultFrame`  
 Určuje, jestli je okně s rámečkem výchozí rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je nalezen zástupce; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledá příkaz zadaný parametrem `uiCmd` a načte výchozí klávesovou zkratku. Potom metoda přebírá řetězec přidružený k této klávesové zkratky a zapíše hodnota, která má `str` parametr.  
  
##  <a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled  
 Určuje, zda je zadaný klíč zpracovávaných [CKeyboardManager třída](../../mfc/reference/ckeyboardmanager-class.md).  
  
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
|[v]`nKey`|Klíč, který chcete zkontrolovat.|  
|[v]`fVirt`|Určuje chování klávesovou zkratku. Seznam možných hodnot najdete v tématu [AKCELERACE struktura](http://msdn.microsoft.com/library/windows/desktop/ms646340).|  
|[v]`pWndFrame`|Okně s rámečkem. Tato metoda určuje, zda je tento rámce zpracována klávesovou zkratku.|  
|[v]`bIsDefaultFrame`|Parametr typu Boolean, která určuje, zda `pWndFrame` je výchozím okně rámce.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se zpracovává klávesovou zkratku. `FALSE`Pokud nejsou zpracovávány klíč nebo pokud `pWndFrame` je `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Vstupní parametry se musí shodovat záznam v akcelerátoru tabulce pro `nKey` a `fVirt` k určení, zda je klávesovou zkratku zpracována v `pWndFrame`.  
  
##  <a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable  
 Určuje, zda znak je nastaveno.  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`nChar`|Znak, který tato metoda ověří.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud znak je nastaveno, hodnotu není.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud volání [GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299) selže.  
  
##  <a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllAccelerators  
 Určuje, zda nabídky Zobrazit všechny klávesové zkratky přidružené příkazy nabídky nebo pouze výchozí klávesové zkratky.  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud aplikace zobrazí všechny klávesové zkratky pro příkazy nabídky; 0, pokud aplikace zobrazí pouze výchozí klávesové zkratky.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace uvádí klávesové zkratky pro příkazy nabídky v panelu nabídek. Pomocí funkce [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) k řízení jestli aplikace zobrazí seznam všech klávesových zkratek nebo jenom výchozí klávesové zkratky.  
  
##  <a name="loadstate"></a>CKeyboardManager::LoadState  
 Načte klíče tabulky zástupce z registru systému Windows.  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cesta v registru kde `CKeyboardManager` budou uložena data.  
  
 [v]`pDefaultFrame`  
 Ukazatel na okně s rámečkem používat jako výchozí okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud stav jinak bylo úspěšně načteno, nebo 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `lpszProfileName` parametr `NULL`, tato metoda zkontroluje výchozí umístění registru `CKeyboardManager` data. Výchozí umístění registru je zadána [CWinAppEx Class](../../mfc/reference/cwinappex-class.md). Data musí být dříve napsané pomocí metody [CKeyboardManager::SaveState](#savestate).  
  
 Pokud výchozím okně nezadáte, použije se hlavního rámce okna vaší aplikace.  
  
##  <a name="resetall"></a>CKeyboardManager::ResetAll  
 Znovu načte zástupce klíče tabulky z prostředků aplikace.  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vymaže zástupce uložené v `CKeyboardManager` instance. Pak ji bude znovu načíst stav manager klávesnice z prostředků aplikace.  
  
##  <a name="savestate"></a>CKeyboardManager::SaveState  
 Uloží zástupce klíče tabulky do registru systému Windows.  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cestu registru pro ukládání `CKeyboardManager` stavu.  
  
 [v]`pDefaultFrame`  
 Ukazatel na rámec okna, který se stane výchozím okně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud správce stavu klávesnice byl uložen úspěšně, nebo 0, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `lpszProfileName` parametr je `NULL`, tato metoda bude zapisovat `CKeyboardManager` stavu do výchozího umístění, které [CWinAppEx Class](../../mfc/reference/cwinappex-class.md). Pokud zadáte umístění, můžete načíst data později pomocí metody [CKeyboardManager::LoadState](#loadstate).  
  
 Pokud nezadáte výchozím okně, hlavního okna rámce se použije jako výchozí okna.  
  
##  <a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators  
 Zobrazí všechny klávesové zkratky přidružené příkazy nabídky.  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShowAll`  
 Pokud `true`, zobrazí se všechny klávesové zkratky. Pokud `false`, zobrazí se pouze první klávesovou zkratku.  
  
 [v]`lpszDelimiter`  
 Řetězec k vložení mezi klávesové zkratky. Tento oddělovač nemá žádný vliv, pokud pouze jeden klíč zástupce se zobrazí.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení Pokud příkaz obsahuje více než jeden klávesovou zkratku přidružený pouze první klávesovou zkratku budou zobrazeny. Tato funkce umožňuje zobrazit seznam všech klávesových zkratek přidružené všechny příkazy.  
  
 Klávesové zkratky budou zobrazeny vedle příkaz v panelu nabídek. Pokud jsou zobrazeny všechny klávesové zkratky, řetězec poskytované `lpszDelimiter` dojde k oddělení jednotlivých klávesové zkratky.  
  
##  <a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToUpper  
 Převádí znak na jeho horní registrace.  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nChar`  
 Znak, který se má převést.  
  
### <a name="return-value"></a>Návratová hodnota  
 Znak, který je horní rejstříku vstupní parametr.  
  
##  <a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable  
 Aktualizuje zástupce klíče tabulky pomocí nového klíče tabulky zástupce.  
  
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
 [v]`pTemplate`  
 Ukazatel na šablony dokumentu.  
  
 [v]`lpAccel`  
 Ukazatel na klávesovou zkratku.  
  
 [v]`nSize`  
 Velikost novou tabulku zástupce.  
  
 [v]`pDefaultFrame`  
 Ukazatel na rámec okna výchozí.  
  
 [v]`hAccelNew`  
 Popisovač pro novou tabulku zástupce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete nahradit existující tabulku zástupce nové klávesové zkratky pro několik objektů rámce okna. Funkce obdrží šablony dokumentu jako parametr, který se získat přístup ke všem objektům rámce okna připojené k šabloně daného dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)



