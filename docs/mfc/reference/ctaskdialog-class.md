---
title: Třída objektu CTaskDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 096423e08b470efea55e790e7ad038eb04715ccb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379005"
---
# <a name="ctaskdialog-class"></a>Třída objektu CTaskDialog
Místní dialogové okno, který funguje jako okno se zprávou, ale můžete zobrazit další informace o uživateli. `CTaskDialog` Také zahrnuje funkce pro shromažďování informací o od uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTaskDialog : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Vytvoří `CTaskDialog` objektu.|  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Přidá příkazové tlačítko na `CTaskDialog`.|  
|[CTaskDialog::AddRadioButton](#addradiobutton)|Přidá na přepínač `CTaskDialog`.|  
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Kliknutím na příkaz tlačítko – ovládací prvek nebo běžné tlačítko prostřednictvím kódu programu.|  
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Kliknutím na přepínač prostřednictvím kódu programu.|  
|[CTaskDialog::DoModal](#domodal)|Zobrazí `CTaskDialog`.|  
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Načte počet běžné tlačítka, které jsou k dispozici.|  
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Převede standardní přidružené Windows tlačítko běžné typ tlačítka `CTaskDialog` třídy.|  
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Jeden z běžných typů tlačítko přidružené převede `CTaskDialog` třída pro standardní tlačítko Windows.|  
|[CTaskDialog::GetOptions](#getoptions)|Vrátí příznaky možnost pro tuto `CTaskDialog`.|  
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Vrátí ovládací prvek tlačítko vybraný příkaz.|  
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Vrátí vybraného přepínače.|  
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Načte stav ověření zaškrtávacího políčka.|  
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Určuje, zda je povoleno příkazové tlačítko nebo běžné tlačítko.|  
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Určuje, zda je povoleno přepínače.|  
|[CTaskDialog::IsSupported](#issupported)|Určuje, zda počítač, který je spuštěna aplikace podporuje `CTaskDialog`.|  
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Přidá příkaz tlačítko – ovládací prvky s použitím dat z tabulky řetězec.|  
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Přidá přepínačů pomocí dat z tabulky řetězec.|  
|[CTaskDialog::NavigateTo](#navigateto)|Přenese fokus na jiný `CTaskDialog`.|  
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Rozhraní framework volá tuto metodu, když uživatel klikne příkazové tlačítko.|  
|[CTaskDialog::OnCreate](#oncreate)|Tato metoda volá framework po vytvoření `CTaskDialog`.|  
|[CTaskDialog::OnDestroy](#ondestroy)|Tato metoda volá framework okamžitě před zničí `CTaskDialog`.|  
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Rozhraní framework volá tuto metodu, když uživatel klikne na tlačítko rozšíření.|  
|[CTaskDialog::OnHelp](#onhelp)|Rozhraní framework volá tuto metodu, když uživatel požádá nápovědy.|  
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Rozhraní framework volá tuto metodu, když uživatel klikne na hypertextový odkaz.|  
|[CTaskDialog::OnInit](#oninit)|Tato metoda volá framework při `CTaskDialog` je inicializován.|  
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Rozhraní framework volá tuto metodu, když se uživatel přesune fokus s ohledem na ovládací prvky `CTaskDialog`.|  
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Rozhraní framework volá tuto metodu, když uživatel vybere ovládací prvek přepínač.|  
|[CTaskDialog::OnTimer](#ontimer)|Rozhraní framework volá tuto metodu, když vyprší platnost časovač.|  
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Rozhraní framework volá tuto metodu, když uživatel klikne políčko ověření.|  
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Odebere všechny ovládací prvky pro příkaz z `CTaskDialog`.|  
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Odebere všechny přepínačů z `CTaskDialog`.|  
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Aktualizace příkazové tlačítko `CTaskDialog`.|  
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podmnožinu běžné tlačítka a povolit vyžadují zvýšení nástroje Řízení uživatelských účtů.|  
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Přidá běžné tlačítek `CTaskDialog`.|  
|[CTaskDialog::SetContent](#setcontent)|Aktualizuje obsah `CTaskDialog`.|  
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Určuje výchozí příkazové tlačítko.|  
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Určuje výchozí přepínač.|  
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Upraví šířku `CTaskDialog`.|  
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizace oblasti rozšíření `CTaskDialog`.|  
|[CTaskDialog::SetFooterIcon](#setfootericon)|Aktualizace na ikonu zápatí `CTaskDialog`.|  
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizace textu na zápatí `CTaskDialog`.|  
|[CTaskDialog::SetMainIcon](#setmainicon)|Aktualizace na hlavní ikonu `CTaskDialog`.|  
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Aktualizuje hlavní pokyny `CTaskDialog`.|  
|[CTaskDialog::SetOptions](#setoptions)|Konfiguruje nastavení pro `CTaskDialog`.|  
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Nakonfiguruje rámeček panelu pro `CTaskDialog` a přidá ji do dialogového okna.|  
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Upraví pozici indikátor průběhu.|  
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Upraví rozsahu indikátoru průběhu.|  
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Nastaví stav indikátoru průběhu a zobrazí na `CTaskDialog`.|  
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Povolí nebo zakáže přepínač.|  
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Nastaví stav zaškrtnutí zaškrtávacího políčka ověření.|  
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Nastaví text, na pravé straně zaškrtněte políčko ověřování.|  
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Nastaví název `CTaskDialog`.|  
|[CTaskDialog::ShowDialog](#showdialog)|Vytvoří a zobrazí `CTaskDialog`.|  
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Volá framework to v reakci na různých zpráv systému Windows.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|`m_aButtons`|Příkaz tlačítko – ovládací prvky pro pole `CTaskDialog`.|  
|`m_aRadioButtons`|Pole prvků přepínačů pro `CTaskDialog`.|  
|`m_bVerified`|`TRUE` Označuje, že je zaškrtnuté políčko ověření; `FALSE` signalizuje není.|  
|`m_footerIcon`|Ikona v zápatí `CTaskDialog`.|  
|`m_hWnd`|Popisovač pro okno pro `CTaskDialog`.|  
|`m_mainIcon`|Na hlavní ikonu `CTaskDialog`.|  
|`m_nButtonDisabled`|Maska, která určuje, které běžné tlačítek jsou zakázány.|  
|`m_nButtonElevation`|Maska, která určuje, které běžné tlačítek vyžadují zvýšení nástroje Řízení uživatelských účtů.|  
|`m_nButtonId`|ID ovládacího prvku tlačítko vybraný příkaz.|  
|`m_nCommonButton`|Maska, která určuje, která běžné tlačítka se zobrazí na `CTaskDialog`.|  
|`m_nDefaultCommandControl`|Řízení ID příkazového tlačítka, který je vybraný při `CTaskDialog` se zobrazí.|  
|`m_nDefaultRadioButton`|ID přepínač řídit, když je vybraný `CTaskDialog` se zobrazí.|  
|`m_nFlags`|Maska, která určuje možnosti `CTaskDialog`.|  
|`m_nProgressPos`|Aktuální pozici pro indikátor průběhu.  Tato hodnota musí být mezi `m_nProgressRangeMin` a `m_nProgressRangeMax`.|  
|`m_nProgressRangeMax`|Maximální hodnota indikátoru průběhu.|  
|`m_nProgressRangeMin`|Minimální hodnota indikátoru průběhu.|  
|`m_nProgressState`|Stav indikátoru průběhu. Další informace najdete v tématu [CTaskDialog::SetProgressBarState](#setprogressbarstate).|  
|`m_nRadioId`|ID ovládacího prvku tlačítko vybraného přepínače.|  
|`m_nWidth`|Šířka `CTaskDialog` v pixelech.|  
|`m_strCollapse`|Řetězec `CTaskDialog` zobrazuje vpravo od pole rozšíření rozšířené informace skryt.|  
|`m_strContent`|Řetězec obsahu `CTaskDialog`.|  
|`m_strExpand`|Řetězec `CTaskDialog` zobrazuje vpravo od pole rozšíření rozšířené informace se zobrazí.|  
|`m_strFooter`|Zápatí `CTaskDialog`.|  
|`m_strInformation`|Rozšířené informace o `CTaskDialog`.|  
|`m_strMainInstruction`|Hlavní pokyny `CTaskDialog`.|  
|`m_strTitle`|Název `CTaskDialog`.|  
|`m_strVerification`|Řetězec, `CTaskDialog` zobrazí napravo od pole ověření.|  
  
## <a name="remarks"></a>Poznámky  
 `CTaskDialog` Třída nahrazuje pole standardní zprávy Windows a má další funkce, jako je například nové ovládací prvky získat informace o od uživatele. Tato třída je v knihovně MFC v [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]. `CTaskDialog` Je k dispozici počínaje systémem Windows Vista. Nelze zobrazit dřívějších verzích systému Windows `CTaskDialog` objektu. Použití `CTaskDialog::IsSupported` k určení za běhu, zda má aktuální uživatel může zobrazit dialogové okno úloh. Pole pro standardní zprávy Windows se pořád podporuje v [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)].  
  
 `CTaskDialog` Je k dispozici pouze při vytváření aplikace s použitím knihovny kódování Unicode.  
  
 `CTaskDialog` Má dva různé konstruktory. Jeden konstruktor můžete určit dva příkazová tlačítka a nesmí být delší než šest regulární tlačítko – ovládací prvky. Po vytvoření můžete přidat další příkazová tlačítka `CTaskDialog`. Druhý konstruktor nepodporuje žádné příkazová tlačítka, ale můžete přidat libovolný počet pravidelných tlačítko – ovládací prvky. Další informace o konstruktorů najdete v tématu [CTaskDialog::CTaskDialog](#ctaskdialog).  
  
 Následující obrázek ukazuje ukázku `CTaskDialog` pro ilustraci umístění některé ovládací prvky.  
  
 ![Příklad objektu CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "ctaskdialogsample")  
Ukázka objektu CTaskDialog  
  
## <a name="requirements"></a>Požadavky  
 **Minimální požadovaný operační systém:** Windows Vista  
  
 **Záhlaví:** afxtaskdialog.h  
  
##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl  
 Přidá nový ovládací prvek tlačítko příkaz na `CTaskDialog`.  
  
```  
void AddCommandControl(
    int nCommandControlID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandControlID`  
 Příkaz ovládacího prvku identifikační číslo.  
  
 [v] `strCaption`  
 Řetězec, `CTaskDialog` zobrazí uživateli. Použijte tento řetězec vysvětlující účel příkazu.  
  
 [v] `bEnabled`  
 Logický parametr, který určuje povolená nebo zakázaná na tlačítko Nový.  
  
 [v] `bRequiresElevation`  
 Parametr typu Boolean, která určuje, zda příkaz vyžaduje zvýšení oprávnění.  
  
### <a name="remarks"></a>Poznámky  
 `CTaskDialog Class` Můžete zobrazit neomezený počet příkaz tlačítko – ovládací prvky. Ale pokud `CTaskDialog` zobrazí všechny příkazového tlačítka ovládacích prvků, ho můžete zobrazit maximálně šest tlačítka. Pokud `CTaskDialog` nemá žádný příkaz tlačítko – ovládací prvky, ho můžete zobrazit neomezený počet tlačítka.  
  
 Když uživatel vybere příkazové tlačítko, `CTaskDialog` zavře. Pokud vaše aplikace zobrazí dialogové okno s použitím [CTaskDialog::DoModal](#domodal), `DoModal` vrátí `nCommandControlID` ovládacího prvku tlačítko vybraný příkaz.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton  
 Přidá na přepínač `CTaskDialog`.  
  
```  
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRadioButtonID`  
 Identifikační číslo přepínače.  
  
 [v] `strCaption`  
 Řetězec, `CTaskDialog` zobrazí vedle přepínač.  
  
 [v] `bEnabled`  
 Parametr typu Boolean, která určuje, zda je povoleno přepínač.  
  
### <a name="remarks"></a>Poznámky  
 Přepínačů pro [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md) vám umožní shromažďovat informace od uživatele. Pomocí funkce [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) k určení, které přepínače.  
  
 `CTaskDialog` Nevyžaduje `nRadioButtonID` parametry jsou jedinečné pro každý přepínač. Neočekávané chování však může nastat, pokud nepoužijete odlišné identifikátor pro každý přepínač.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl  
 Kliknutím na příkaz tlačítko – ovládací prvek nebo běžné tlačítko prostřednictvím kódu programu.  
  
```  
protected:  
void ClickCommandControl(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandControlID`  
 ID příkazu ovládacího prvku na tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda generuje zpráv windows `TDM_CLICK_BUTTON`.  
  
##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton  
 Kliknutím na přepínač prostřednictvím kódu programu.  
  
```  
protected:  
void ClickRadioButton(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRadioButtonID`  
 ID klikněte na přepínač.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda generuje zpráv windows `TDM_CLICK_RADIO_BUTTON`.  
  
##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog  
 Vytvoří instanci [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md).  
  
```  
CTaskDialog(
    const CString& strContent,  
    const CString& strMainInstruction,  
    const CString& strTitle,  
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,  
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,  
    const CString& strFooter = _T(""));

 
CTaskDialog(
    const CString& strContent,  
    const CString& strMainInstruction,  
    const CString& strTitle,  
    int nIDCommandControlsFirst,  
    int nIDCommandControlsLast,  
    int nCommonButtons,  
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,  
    const CString& strFooter = _T(""));
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strContent`  
 Řetězec, který má používat pro obsah `CTaskDialog`.  
  
 [v] `strMainInstruction`  
 Hlavní pokyny `CTaskDialog`.  
  
 [v] `strTitle`  
 Název `CTaskDialog`.  
  
 [v] `nCommonButtons`  
 Maska běžné tlačítka pro přidání do `CTaskDialog`.  
  
 [v] `nTaskDialogOptions`  
 Sada možností pro `CTaskDialog`.  
  
 [v] `strFooter`  
 Řetězec, který se má použít jako zápatí.  
  
 [v] `nIDCommandControlsFirst`  
 Řetězec ID prvního příkazu.  
  
 [v] `nIDCommandControlsLast`  
 Řetězec ID poslední příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Existují dva způsoby, které můžete přidat `CTaskDialog` do vaší aplikace. První způsob je pomocí některého z konstruktorů můžete vytvořit `CTaskDialog` a zobrazit ji pomocí [CTaskDialog::DoModal](#domodal). Druhý způsob je použití statické funkce [CTaskDialog::ShowDialog](#showdialog), což umožňuje zobrazit `CTaskDialog` bez explicitně vytvoření `CTaskDialog` objektu.  
  
 Druhý konstruktor vytvoří ovládací prvky tlačítek příkaz s použitím dat ze zdrojového souboru aplikace. Tabulky řetězců v souboru prostředků má několik řetězce řetězcem přidružené ID. Tato metoda přidá příkazové tlačítko pro každý platný záznam v tabulce řetězců mezi `nIDCommandControlsFirst` a `nCommandControlsLast`(včetně). Pro tyto ovládací prvky tlačítko příkaz řetězec v tabulce řetězců ovládacího prvku popisek a řetězec ID je ID ovládacího prvku.  
  
 V tématu [CTaskDialog::SetOptions](#setoptions) seznam platné možnosti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="domodal"></a>  CTaskDialog::DoModal  
 Ukazuje `CTaskDialog` a udělá z něj modální.  
  
```  
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hParent`  
 Nadřazené okno pro `CTaskDialog`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo, které odpovídá výběru provedené uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazí tuto instanci [objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Aplikace se pak čeká uživateli dialogové okno zavřete.  
  
 `CTaskDialog` Zavře, když uživatel vybere běžné tlačítko ovládacího prvku příkaz odkaz, nebo zavření `CTaskDialog`. Vrácená hodnota je identifikátor, který určuje, jak uživatel zavřel dialogové okno.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount  
 Načte počet běžné tlačítek.  
  
```  
int GetCommonButtonCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet běžné tlačítka, které jsou k dispozici.  
  
### <a name="remarks"></a>Poznámky  
 Běžné tlačítka jsou výchozích tlačítek, které poskytnete [CTaskDialog::CTaskDialog](#ctaskdialog). [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md) zobrazí tlačítka ve spodní části dialogových oken.  
  
 Výčtové seznamu tlačítka je součástí CommCtrl.h.  
  
##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag  
 Převede standardní přidružené Windows tlačítko běžné typ tlačítka [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md).  
  
```  
int GetCommonButtonFlag(int nButtonId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nButtonId`  
 Standardní hodnota tlačítko Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota odpovídající `CTaskDialog` běžné tlačítko. Pokud není odpovídající běžné tlačítko, tato metoda vrátí hodnotu 0.  
  
##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId  
 Jeden z běžných typů tlačítko přidružené převede [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md) pro standardní tlačítko Windows.  
  
```  
int GetCommonButtonId(int nFlag);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nFlag`  
 Běžný typ přidružené `CTaskDialog` třídy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota na odpovídající tlačítko Windows standard. Pokud není odpovídající tlačítko Windows, vrátí metoda hodnotu 0.  
  
##  <a name="getoptions"></a>  CTaskDialog::GetOptions  
 Vrátí příznaky možnost pro tuto `CTaskDialog`.  
  
```  
int GetOptions() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro příznaky `CTaskDialog`.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o možnostech, které jsou k dispozici [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md), najdete v části [CTaskDialog::SetOptions](#setoptions).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID  
 Vrátí ovládací prvek tlačítko vybraný příkaz.  
  
```  
int GetSelectedCommandControlID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID ovládacího prvku tlačítko aktuálně vybraný příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Nemusíte tuto metodu použijte k načtení ID příkazového tlačítka, který uživatel vybral. Toto ID je vrácen rutinou buď [CTaskDialog::DoModal](#domodal) nebo [CTaskDialog::ShowDialog](#showdialog).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="getselectedradiobuttonid"></a>  CTaskDialog::GetSelectedRadioButtonID  
 Vrátí vybraného přepínače.  
  
```  
int GetSelectedRadioButtonID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID vybraného přepínače.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu můžete použít, až uživatel zavře dialogové okno načíst vybraného přepínače.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState  
 Načte stav ověření zaškrtávacího políčka.  
  
```  
BOOL GetVerificationCheckboxState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je zaškrtnuto políčko, `FALSE` Pokud není.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled  
 Určuje, zda je povoleno příkazové tlačítko nebo tlačítko.  
  
```  
BOOL IsCommandControlEnabled(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandControlID`  
 ID příkazu tlačítko – ovládací prvek nebo tlačítko pro testování.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je povoleno ovládacího prvku, `FALSE` Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu můžete použít k určení dostupnosti jak příkaz ovládacích prvků a běžné tlačítek `CTaskDialog Class`.  
  
 Pokud `nCommandControlID` není platný identifikátor pro buď společného `CTaskDialog` tlačítko nebo příkazové tlačítko, tato metoda vyvolá výjimku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled  
 Určuje, zda je povoleno přepínače.  
  
```  
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRadioButtonID`  
 ID přepínač k testování.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je přepínač je povoleno, `FALSE` Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nRadioButtonID` není platný identifikátor pro přepínače, tato metoda vyvolá výjimku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="issupported"></a>  CTaskDialog::IsSupported  
 Určuje, zda počítač, který je spuštěna aplikace podporuje `CTaskDialog`.  
  
```  
static BOOL IsSupported();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud počítač podporuje `CTaskDialog`; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k určení za běhu, pokud počítač, který běží vaše aplikace podporuje `CTaskDialog Class`. Pokud počítač nepodporuje `CTaskDialog`, měli byste jim poskytnout další metodou sdělování informací uživateli. Pokud se ji pokusí použít dojde k chybě aplikace `CTaskDialog` na počítači, který nepodporuje `CTaskDialog` – třída.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls  
 Přidá příkaz tlačítko – ovládací prvky s použitím dat z tabulky řetězec.  
  
```  
void LoadCommandControls(
    int nIDCommandControlsFirst,  
    int nIDCommandControlsLast);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIDCommandControlsFirst`  
 Řetězec ID prvního příkazu.  
  
 [v] `nIDCommandControlsLast`  
 Řetězec ID poslední příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří ovládací prvky tlačítek příkaz s použitím dat ze zdrojového souboru aplikace. Tabulky řetězců v souboru prostředků má několik řetězce řetězcem přidružené ID. Nové ovládací prvky příkazového tlačítka, pomocí této metody přidat použít řetězec pro popisek ovládacího prvku a řetězec ID pro ID ovládacího prvku. Poskytuje řadu řetězce vybrané `nIDCommandControlsFirst` a `nCommandControlsLast`(včetně). Pokud je v rozsahu prázdná položka, metoda nepřidá příkazové tlačítko pro tuto položku.  
  
 Ve výchozím nastavení nový příkaz tlačítko – ovládací prvky jsou povoleny a nevyžadují zvýšení oprávnění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons  
 Přidá přepínač pomocí dat z tabulky řetězec.  
  
```  
void LoadRadioButtons(
    int nIDRadioButtonsFirst,  
    int nIDRadioButtonsLast);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIDRadioButtonsFirst`  
 Řetězec ID první přepínače.  
  
 [v] `nIDRadioButtonsLast`  
 Řetězec ID poslední přepínače.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří přepínačů s použitím dat ze zdrojového souboru aplikace. Tabulky řetězců v souboru prostředků má několik řetězce řetězcem přidružené ID. Pomocí této metody přidat nové přepínače použít řetězec pro přepínač tlačítka a řetězec ID pro ID na přepínač. Poskytuje řadu řetězce vybrané `nIDRadioButtonsFirst` a `nRadioButtonsLast`(včetně). Pokud je v rozsahu prázdná položka, metoda nepřidá přepínač pro tuto položku.  
  
 Ve výchozím nastavení jsou povolené nového přepínače.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="navigateto"></a>  CTaskDialog::NavigateTo  
 Přenese fokus na jiný `CTaskDialog`.  
  
```  
protected:  
void NavigateTo(CTaskDialog& oTaskDialog) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `oTaskDialog`  
 `CTaskDialog` , Bude vybrán.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda skryje aktuální `CTaskDialog` když se zobrazí `oTaskDialog`. `oTaskDialog` Se zobrazí ve stejném umístění jako aktuální `CTaskDialog`.  
  
##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick  
 Rozhraní framework volá tuto metodu, když uživatel klikne příkazové tlačítko.  
  
```  
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandControlID`  
 ID ovládacího prvku tlačítko příkaz, který uživatel vybral.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="oncreate"></a>  CTaskDialog::OnCreate  
 Tato metoda volá framework po vytvoření `CTaskDialog`.  
  
```  
virtual HRESULT OnCreate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy  
 Tato metoda volá framework okamžitě před zničí `CTaskDialog`.  
  
```  
virtual HRESULT OnDestroy();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick  
 Rozhraní framework volá tuto metodu, když uživatel klikne na tlačítko rozšíření.  
  
```  
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bExpanded`  
 Nenulová hodnota označuje, že se zobrazují doplňující informace; Hodnota 0 znamená, že je skrytý doplňující informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="onhelp"></a>  CTaskDialog::OnHelp  
 Rozhraní framework volá tuto metodu, když uživatel požádá nápovědy.  
  
```  
virtual HRESULT OnHelp();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick  
 Rozhraní framework volá tuto metodu, když uživatel klikne na hypertextový odkaz.  
  
```  
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strHref`  
 Řetězec, který reprezentuje hypertextový odkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) před vrátí `S_OK`.  
  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="oninit"></a>  CTaskDialog::OnInit  
 Tato metoda volá framework při `CTaskDialog` je inicializován.  
  
```  
virtual HRESULT OnInit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage  
 Tato metoda volá framework v reakci [CTaskDialog::NavigateTo](#navigateto) metoda.  
  
```  
virtual HRESULT OnNavigatePage();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick  
 Rozhraní framework volá tuto metodu, když uživatel vybere ovládací prvek přepínač.  
  
```  
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRadioButtonID`  
 ID prvek přepínač, který klikl na uživatele.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="ontimer"></a>  CTaskDialog::OnTimer  
 Rozhraní framework volá tuto metodu, když vyprší platnost časovač.  
  
```  
virtual HRESULT OnTimer(long lTime);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lTime`  
 Doba v milisekundách od `CTaskDialog` byl vytvořen nebo byl resetován časovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick  
 Rozhraní framework volá tuto metodu, když uživatel klikne políčko ověření.  
  
```  
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bChecked`  
 `TRUE` Označuje, že je zaškrtnuté políčko ověření; `FALSE` signalizuje není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.  
  
##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls  
 Odebere všechny prvky tlačítko příkaz z `CTaskDialog`.  
  
```  
void RemoveAllCommandControls();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons  
 Odebere všechny přepínačů z `CTaskDialog`.  
  
```  
void RemoveAllRadioButtons();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions  
 Aktualizace příkazové tlačítko `CTaskDialog`.  
  
```  
void SetCommandControlOptions(
    int nCommandControlID,  
    BOOL bEnabled,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandControlID`  
 ID ovládacího prvku příkaz k aktualizaci.  
  
 [v] `bEnabled`  
 Parametr typu Boolean, která určuje, zda ovládacího prvku tlačítko zadaný příkaz je povolena nebo zakázána.  
  
 [v] `bRequiresElevation`  
 Logický parametr, který určuje, zda ovládacího prvku tlačítko zadaný příkaz vyžaduje zvýšení oprávnění.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete změnit, zda je povoleno příkazové tlačítko nebo po byl přidán do se vyžaduje zvýšení oprávnění `CTaskDialog Class`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions  
 Aktualizuje podmnožinu běžné tlačítka, aby byl povolen a jak vyžadovat zvýšení oprávnění nástroje Řízení uživatelských účtů.  
  
```  
void SetCommonButtonOptions(
    int nDisabledButtonMask,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nDisabledButtonMask`  
 Maska pro běžné tlačítka zakázat.  
  
 [v] `nElevationButtonMask`  
 Maska pro běžné tlačítka, které vyžadují zvýšení oprávnění.  
  
### <a name="remarks"></a>Poznámky  
 K dispozici společné tlačítka můžete nastavit na instanci [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md) pomocí konstruktoru [CTaskDialog::CTaskDialog](#ctaskdialog) a metodu [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` nepodporuje přidávání nová tlačítka běžné.  
  
 Pokud použijete tuto metodu můžete zakázat nebo zvýšení oprávnění běžné tlačítko, které není k dispozici pro tento `CTaskDialog`, tato metoda vyvolá výjimku pomocí [zajistěte, aby](diagnostic-services.md#ensure) makro.  
  
 Tato metoda umožňuje libovolné tlačítko, které jsou k dispozici `CTaskDialog` , ale není součástí `nDisabledButtonMask`i v případě, že byla předtím zakázaná. Tato metoda zpracovává zvýšení podobným způsobem: zaznamenává běžné tlačítka jako není nutnosti zvýšení oprávnění, pokud běžné tlačítko je k dispozici, ale není zahrnutý v `nElevationButtonMask`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons  
 Přidá běžné tlačítek `CTaskDialog`.  
  
```  
void SetCommonButtons(
    int nButtonMask,  
    int nDisabledButtonMask = 0,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nButtonMask`  
 Maska tlačítka pro přidání do `CTaskDialog`.  
  
 [v] `nDisabledButtonMask`  
 Maska tlačítka zakázat.  
  
 [v] `nElevationButtonMask`  
 Maska tlačítka, které vyžadují zvýšení oprávnění.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu nelze volat po zobrazit okno pro tuto instanci `CTaskDialog Class` je vytvořena. Pokud tak učiníte, tato metoda vyvolá výjimku.  
  
 Tlačítka indikován `nButtonMask` přepsat všechny běžné tlačítka dříve přidány do `CTaskDialog`. Pouze tlačítka uvedené v `nButtonMask` jsou k dispozici.  
  
 Pokud buď `nDisabledButtonMask` nebo `nElevationButtonMask` obsahovat tlačítka, který není součástí `nButtonMask`, tato metoda vyvolá výjimku pomocí [zajistěte, aby](diagnostic-services.md#ensure) makro.  
  
 Ve výchozím nastavení všechny běžné tlačítka jsou povolené a nevyžadují zvýšení oprávnění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcontent"></a>  CTaskDialog::SetContent  
 Aktualizuje obsah `CTaskDialog`.  
  
```  
void SetContent(const CString& strContent);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strContent`  
 Řetězec, který se má zobrazit uživateli.  
  
### <a name="remarks"></a>Poznámky  
 Obsah `CTaskDialog Class` je text, který se zobrazí uživateli v hlavní části dialogového okna.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl  
 Určuje výchozí příkazové tlačítko.  
  
```  
void SetDefaultCommandControl(int nCommandControlID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nCommandControlID`  
 ID ovládacího prvku tlačítko příkaz jako výchozí.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí příkazové tlačítko je ovládací prvek, který je vybrána, když `CTaskDialog` se napřed zobrazí uživateli.  
  
 Tato metoda vyvolá výjimku, pokud nelze nalézt příkazové tlačítko určeného `nCommandControlID`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton  
 Určuje výchozí přepínač.  
  
```  
void SetDefaultRadioButton(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRadioButtonID`  
 ID přepínač jako výchozí.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí přepínač je tlačítka, které je vybrána, když `CTaskDialog` se napřed zobrazí uživateli.  
  
 Tato metoda vyvolá výjimku, pokud nemůže najít přepínač určeného `nRadioButtonID`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth  
 Upraví šířku `CTaskDialog`.  
  
```  
void SetDialogWidth(int nWidth = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nWidth`  
 Šířka dialogovém okně v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Parametr `nWidth` musí být větší než nebo rovna 0. Jinak tato metoda vyvolá výjimku.  
  
 Pokud `nWidth` je nastaven na hodnotu 0, tato metoda nastaví dialogové okno pole na výchozí velikost.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea  
 Aktualizace oblasti rozšíření `CTaskDialog`.  
  
```  
void SetExpansionArea(
    const CString& strExpandedInformation,  
    const CString& strCollapsedLabel = _T(""),  
    const CString& strExpandedLabel = _T(""));
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strExpandedInformation`  
 Řetězec, `CTaskDialog` zobrazí v hlavní části dialogových oken, když uživatel klikne na tlačítko rozšíření.  
  
 [v] `strCollapsedLabel`  
 Řetězec, `CTaskDialog` zobrazí vedle tlačítko rozšíření, když oblasti rozšířené sbalena.  
  
 [v] `strExpandedLabel`  
 Řetězec, `CTaskDialog` zobrazí vedle tlačítko rozšíření, když se zobrazí oblasti rozšířené.  
  
### <a name="remarks"></a>Poznámky  
 Oblasti rozšíření `CTaskDialog Class` můžete zadat další informace o uživateli. Oblast rozšíření je v hlavní části `CTaskDialog`umístění bezprostředně pod text nadpisu a obsahu.  
  
 Když `CTaskDialog` je první zobrazí, nezobrazuje rozšířené informace a vloží `strCollapsedLabel` u tlačítka rozšíření. Když uživatel klikne na tlačítko rozšíření `CTaskDialog` zobrazí `strExpandedInformation` a změní štítek, který chcete `strExpandedLabel`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon  
 Aktualizace na ikonu zápatí `CTaskDialog`.  
  
```  
void SetFooterIcon(HICON hFooterIcon);  
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hFooterIcon`  
 Na novou ikonu `CTaskDialog`.  
  
 [v] `lpszFooterIcon`  
 Na novou ikonu `CTaskDialog`.  
  
### <a name="remarks"></a>Poznámky  
 Ikona zápatí se zobrazí v dolní části [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md). Můžete mít přidružené text zápatí. Můžete změnit text zápatí s [CTaskDialog::SetFooterText](#setfootertext).  
  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `CTaskDialog` se zobrazí, nebo vstupní parametr `NULL`.  
  
 A `CTaskDialog` přijmout jenom `HICON` nebo `LPCWSTR` jako ikona zápatí stránky. Ta se nakonfiguruje nastavte možnost `TDF_USE_HICON_FOOTER` v konstruktoru nebo [CTaskDialog::SetOptions](#setoptions). Ve výchozím nastavení `CTaskDialog` je nakonfigurovaný na použití `LPCWSTR` jako vstupní typ ikony zápatí stránky. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodných typu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText  
 Aktualizace textu na zápatí `CTaskDialog`.  
  
```  
void SetFooterText(const CString& strFooterText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strFooterText`  
 Nový text zápatí.  
  
### <a name="remarks"></a>Poznámky  
 Ikona zápatí se zobrazí vedle textu zápatí v dolní části `CTaskDialog`. Můžete změnit na ikonu zápatí s [CTaskDialog::SetFooterIcon](#setfootericon).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon  
 Aktualizace na hlavní ikonu `CTaskDialog`.  
  
```  
void SetMainIcon(HICON hMainIcon);  
void SetMainIcon(LPCWSTR lpszMainIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hMainIcon`  
 Na ikonu nový.  
  
 [v] `lpszMainIcon`  
 Na ikonu nový.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `CTaskDialog` se zobrazí, nebo vstupní parametr `NULL`.  
  
 A `CTaskDialog` přijmout jenom `HICON` nebo `LPCWSTR` jako hlavní ikona. To můžete nakonfigurovat pomocí nastavení `TDF_USE_HICON_MAIN` možnost v konstruktoru nebo v [CTaskDialog::SetOptions](#setoptions) metoda. Ve výchozím nastavení `CTaskDialog` je nakonfigurovaný na použití `LPCWSTR` jako vstupní typ hlavní ikony. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodných typu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction  
 Aktualizuje hlavní pokyny `CTaskDialog`.  
  
```  
void SetMainInstruction(const CString& strInstructions);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strInstructions`  
 Nový hlavní instrukcí.  
  
### <a name="remarks"></a>Poznámky  
 Hlavní pokyny `CTaskDialog Class` je text zobrazený uživateli velké tučným písmem. Nachází se v dialogovém okně pod záhlaví.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setoptions"></a>  CTaskDialog::SetOptions  
 Konfiguruje nastavení pro `CTaskDialog`.  
  
```  
void SetOptions(int nOptionFlag);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nOptionFlag`  
 Sada příznaky, které chcete použít pro `CTaskDialog`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vymaže všechny aktuální možnosti pro `CTaskDialog`. Pokud chcete zachovat aktuální možnosti, je nutné ji načíst je nejdřív s [CTaskDialog::GetOptions](#getoptions) a zkombinovat s možnostmi, které chcete nastavit.  
  
 V následující tabulce jsou uvedeny všechny platné možnosti.  
  
 `TDF_ENABLE_HYPERLINKS`  
 Umožňuje hypertextové odkazy `CTaskDialog`.  
  
 `TDF_USE_HICON_MAIN`  
 Nakonfiguruje `CTaskDialog` sloužící `HICON` hlavní ikony. Alternativou je použít `LPCWSTR`.  
  
 `TDF_USE_HICON_FOOTER`  
 Nakonfiguruje `CTaskDialog` sloužící `HICON` ikony zápatí stránky. Alternativou je použít `LPCWSTR`.  
  
 `TDF_ALLOW_DIALOG_CANCELLATION`  
 Umožňuje uživatelům zavřete `CTaskDialog` pomocí klávesnice nebo pomocí ikony v pravém horním rohu dialogu, i když **zrušit** není dostupné tlačítko. Pokud není nastavený tento příznak a **zrušit** není dostupné tlačítko, uživatel nemůže zavřít dialogové okno s použitím Alt + F4, řídicí klíč, nebo v záhlaví tlačítko Zavřít.  
  
 `TDF_USE_COMMAND_LINKS`  
 Nakonfiguruje `CTaskDialog` použít příkaz tlačítko – ovládací prvky.  
  
 `TDF_USE_COMMAND_LINKS_NO_ICON`  
 Nakonfiguruje `CTaskDialog` k využití řízení příkazového tlačítka bez zobrazení ikonu vedle ovládacího prvku. `TDF_USE_COMMAND_LINKS` přepsání `TDF_USE_COMMAND_LINKS_NO_ICON`.  
  
 `TDF_EXPAND_FOOTER_AREA`  
 Označuje, že je aktuálně rozšířena oblasti rozšíření.  
  
 `TDF_EXPANDED_BY_DEFAULT`  
 Určuje, zda je ve výchozím nastavení rozšířena oblasti rozšíření.  
  
 `TDF_VERIFICATION_FLAG_CHECKED`  
 Označuje, že je aktuálně zaškrtnuté políčko ověření.  
  
 `TDF_SHOW_PROGRESS_BAR`  
 Nakonfiguruje `CTaskDialog` zobrazíte indikátor průběhu.  
  
 `TDF_SHOW_MARQUEE_PROGRESS_BAR`  
 Nakonfiguruje indikátor průběhu na výběr indikátor průběhu. Pokud povolíte tuto možnost, musíte nastavit `TDF_SHOW_PROGRESS_BAR` tak, aby měl očekávané chování.  
  
 `TDF_CALLBACK_TIMER`  
 Určuje, že `CTaskDialog` zpětného volání interval je nastavený na přibližně 200 MS.  
  
 `TDF_POSITION_RELATIVE_TO_WINDOW`  
 Nakonfiguruje `CTaskDialog` být zarovnaný na střed vzhledem k nadřazené okno. Pokud tento příznak není povolen, `CTaskDialog` je umístěn na střed vzhledem k monitorování.  
  
 `TDF_RTL_LAYOUT`  
 Nakonfiguruje `CTaskDialog` rozložení čtení zprava doleva.  
  
 `TDF_NO_DEFAULT_RADIO_BUTTON`  
 Označuje, že je vybrán žádný přepínač při `CTaskDialog` se zobrazí.  
  
 `TDF_CAN_BE_MINIMIZED`  
 Umožňuje uživatelům minimalizovat `CTaskDialog`. Podporu této možnosti `CTaskDialog` nemůže být modální. MFC nepodporuje tuto možnost, protože MFC nepodporuje nemodální `CTaskDialog`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee  
 Nakonfiguruje rámeček panelu pro `CTaskDialog` a přidá ji do dialogového okna.  
  
```  
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,  
    int nMarqueeSpeed = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnabled`  
 `TRUE` Chcete-li povolit panelu Výběr; `FALSE` zakázat panelu běžící text a odeberte jej z `CTaskDialog`.  
  
 [v] `nMarqueeSpeed`  
 Celé číslo, které určuje rychlost panelu výběr.  
  
### <a name="remarks"></a>Poznámky  
 Na panelu běžící text se zobrazí pod do hlavního textu `CTaskDialog Class`.  
  
 Použití `nMarqueeSpeed` nastavit rychlosti panelu Výběr; vyšší hodnoty znamenat nižší přenosovou rychlost. Hodnota 0 pro `nMarqueeSpeed` díky panelu výběr přesunout rychlostí výchozí pro Windows.  
  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `nMarqueeSpeed` je menší než 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition  
 Upraví pozici indikátor průběhu.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nProgressPos`  
 Pozice pro indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `nProgressPos` není v rozsahu panelu průběhu. Můžete změnit rozsah panelu průběhu s [CTaskDialog::SetProgressBarRange](#setprogressbarrange).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange  
 Upraví rozsahu indikátoru průběhu.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRangeMin`  
 Dolní mez indikátor průběhu.  
  
 [v] `nRangeMax`  
 Horní mez indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Umístění indikátoru průběhu je vzhledem k `nRangeMin` a `nRangeMax`. Například pokud `nRangeMin` je 50 a `nRangeMax` 100, pozice 75 je uprostřed napříč indikátor průběhu. Použití [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) nastavíte umístění indikátoru průběhu.  
  
 Chcete-li zobrazit průběh panelu možnost `TDF_SHOW_PROGRESS_BAR` musí být povolená a `TDF_SHOW_MARQUEE_PROGRESS_BAR` nesmí být povolena. Tato metoda automaticky nastaví `TDF_SHOW_PROGRESS_BAR` a vymaže `TDF_SHOW_MARQUEE_PROGRESS_BAR`. Použití [CTaskDialog::SetOptions](#setoptions) ručně změnit možnosti pro tuto instanci [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md).  
  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `nRangeMin` je menší než `nRangeMax`. Tato metoda také vyvolá výjimku, pokud `CTaskDialog` je již zobrazen a má výběr indikátor průběhu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState  
 Nastaví stav indikátoru průběhu a zobrazí na `CTaskDialog`.  
  
```  
void SetProgressBarState(int nState = PBST_NORMAL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nState`  
 Stav indikátoru průběhu. Možné hodnoty v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `CTaskDialog` je již zobrazen a má výběr indikátor průběhu.  
  
 Následující tabulka uvádí možné hodnoty pro `nState`. V těchto případech bude indikátor průběhu vyplnit regulární barvou dokud nedosáhne určené zastavení pozici. V tomto bodě změní barvu na základě stavu.  
  
 PBST_NORMAL  
 Po průběh nevyplní, `CTaskDialog` nezmění barvu panelu. Ve výchozím nastavení je zelenou barvu regulární.  
  
 PBST_ERROR  
 Po průběh nevyplní, `CTaskDialog` změní barvu panelu na barvu chyby. Ve výchozím nastavení toto je red.  
  
 PBST_PAUSED  
 Po průběh nevyplní, `CTaskDialog` změní barvu panelu na barvu pozastavena. Ve výchozím nastavení toto je žlutý.  
  
 Můžete nastavit, kdy přestane indikátoru průběhu s [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setradiobuttonoptions"></a>  CTaskDialog::SetRadioButtonOptions  
 Povolí nebo zakáže přepínač.  
  
```  
void SetRadioButtonOptions(
    int nRadioButtonID,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nRadioButtonID`  
 ID ovládací prvek přepínač.  
  
 [v] `bEnabled`  
 `TRUE` Povolit přepínač; `FALSE` zakázat přepínač.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud `nRadioButtonID` není platné ID pro přepínače.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox  
 Nastaví stav zaškrtnutí zaškrtávacího políčka ověření.  
  
```  
void SetVerificationCheckbox(BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bChecked`  
 `TRUE` mít ověření políčko zaškrtnuto, kdy `CTaskDialog` se zobrazí; `FALSE` tak, aby měl ověření zaškrtnutí políčka zrušit, když `CTaskDialog` se zobrazí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText  
 Nastaví text, který se zobrazí vpravo od pole ověření.  
  
```  
void SetVerificationCheckboxText(CString& strVerificationText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strVerificationText`  
 Text, který tato metoda zobrazí vedle políčka ověření.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyvolá výjimku s [zajistěte, aby](diagnostic-services.md#ensure) makro Pokud instanci `CTaskDialog Class` je již zobrazen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle  
 Nastaví název `CTaskDialog`.  
  
```  
void SetWindowTitle(CString& strWindowTitle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strWindowTitle`  
 Nový název `CTaskDialog`.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="showdialog"></a>  CTaskDialog::ShowDialog  
 Vytvoří a zobrazí `CTaskDialog`.  
  
```  
static INT_PTR ShowDialog(
    const CString& strContent,  
    const CString& strMainInstruction,  
    const CString& strTitle,  
    int nIDCommandControlsFirst,  
    int nIDCommandControlsLast,  
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,  
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,  
    const CString& strFooter = _T(""));
```  
  
### <a name="parameters"></a>Parametry  
 [v] `strContent`  
 Řetězec, který má používat pro obsah `CTaskDialog`.  
  
 [v] `strMainInstruction`  
 Hlavní pokyny `CTaskDialog`.  
  
 [v] `strTitle`  
 Název `CTaskDialog`.  
  
 [v] `nIDCommandControlsFirst`  
 Řetězec ID prvního příkazu.  
  
 [v] `nIDCommandControlsLast`  
 Řetězec ID poslední příkaz.  
  
 [v] `nCommonButtons`  
 Maska tlačítka pro přidání do `CTaskDialog`.  
  
 [v] `nTaskDialogOptions`  
 Sada možností pro `CTaskDialog`.  
  
 [v] `strFooter`  
 Řetězec, který se má použít jako zápatí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo, které odpovídá výběru provedené uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 Tato statickou metodu umožňuje vytvořit instanci `CTaskDialog Class` bez explicitně vytvoření `CTaskDialog` objektu v kódu. Protože není žádná `CTaskDialog` objektu nelze volat jiné metody třídy `CTaskDialog` Pokud použijete tuto metodu zobrazíte `CTaskDialog` uživateli.  
  
 Tato metoda vytvoří ovládací prvky tlačítek příkaz s použitím dat ze zdrojového souboru aplikace. Tabulky řetězců v souboru prostředků má několik řetězce řetězcem přidružené ID. Tato metoda přidá příkazové tlačítko pro každý platný záznam v tabulce řetězců mezi `nIDCommandControlsFirst` a `nCommandControlsLast`(včetně). Pro tyto ovládací prvky tlačítko příkaz řetězec v tabulce řetězců ovládacího prvku popisek a řetězec ID je ID ovládacího prvku.  
  
 V tématu [CTaskDialog::SetOptions](#setoptions) seznam platné možnosti.  
  
 `CTaskDialog` Zavře, když uživatel vybere běžné tlačítko ovládacího prvku příkaz odkaz, nebo zavření `CTaskDialog`. Vrácená hodnota je identifikátor, který určuje, jak uživatel zavřel dialogové okno.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback  
 Tato metoda volá framework v reakci na různých zpráv systému Windows.  
  
```  
friend:  
HRESULT TaskDialogCallback(
    HWND hWnd,  
    UINT uNotification,  
    WPARAM wParam,  
    LPARAM lParam,  
    LONG_PTR dwRefData);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hwnd`  
 Popisovač pro `m_hWnd` struktury pro `CTaskDialog`.  
  
 [v] `uNotification`  
 Určuje zprávu, která generovaný kód oznámení.  
  
 [v] `wParam`  
 Další informace o zprávě.  
  
 [v] `lParam`  
 Další informace o zprávě.  
  
 [v] `dwRefData`  
 Ukazatel `CTaskDialog` objekt, který zpětné volání zprávy se vztahuje na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Závisí na konkrétní oznámení kód. Další informace naleznete v části Poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementaci `TaskDialogCallback` zpracovává konkrétní zpráva a potom zavolá na metody odpovídající [CTaskDialog třída](../../mfc/reference/ctaskdialog-class.md). Například v reakci `TDN_BUTTON_CLICKED` zpráva `TaskDialogCallback` volání [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).  
  
 Hodnoty pro `wParam` a `lParam` závisí na konkrétní generovaného zpráva. Je možné pro jednu nebo obě hodnoty byly prázdné. Následující tabulka uvádí výchozí oznámení, které jsou podporovány a jaké hodnoty `wParam` a `lParam` představují. Pokud tuto metodu v odvozené třídě přepíšete, měli byste implementovat kód zpětného volání pro každou zprávu v následující tabulce.  
  
|Zpráva upozornění|`wParam` Hodnota|`lParam` Hodnota|  
|--------------------------|--------------------|--------------------|  
|`TDN_CREATED`|Nepoužívá se.|Nepoužívá se.|  
|`TDN_NAVIGATED`|Nepoužívá se.|Nepoužívá se.|  
|`TDN_BUTTON_CLICKED`|Příkazové tlačítko řízení ID.|Nepoužívá se.|  
|`TDN_HYPERLINK_CLICKED`|Nepoužívá se.|A [LPCWSTR](http://msdn.microsoft.com/library/windows/desktop/aa383751) struktura, která obsahuje odkaz.|  
|`TDN_TIMER`|Doba v milisekundách od `CTaskDialog` byl vytvořen nebo byl resetován časovač.|Nepoužívá se.|  
|`TDN_DESTROYED`|Nepoužívá se.|Nepoužívá se.|  
|`TDN_RADIO_BUTTON_CLICKED`|ID přepínač tlačítko.|Nepoužívá se.|  
|`TDN_DIALOG_CONSTRUCTED`|Nepoužívá se.|Nepoužívá se.|  
|`TDN_VERIFICATION_CLICKED`|1, pokud je zaškrtnuté políčko, 0, pokud není.|Nepoužívá se.|  
|`TDN_HELP`|Nepoužívá se.|Nepoužívá se.|  
|`TDN_EXPANDO_BUTTON_CLICKED`|0, pokud je sbalený oblasti rozšíření; nenulové hodnoty, pokud se zobrazí text rozšíření.|Nepoužívá se.|  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Návod: Přidání objektu CTaskDialog do aplikace](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)



