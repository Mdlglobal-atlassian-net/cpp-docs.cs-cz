---
title: Objektu CTaskDialog – třída
ms.date: 11/19/2018
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
ms.openlocfilehash: e2f77a2eda4397ed368e477165e876f9b8fbf936
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502348"
---
# <a name="ctaskdialog-class"></a>Objektu CTaskDialog – třída

Automaticky otevírané okno, které funguje jako okno se zprávou, ale může uživateli zobrazit další informace. Zahrnuje `CTaskDialog` také funkce pro shromažďování informací od uživatele.

## <a name="syntax"></a>Syntaxe

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|`CTaskDialog` Vytvoří objekt.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Přidá ovládací prvek příkazové tlačítko do `CTaskDialog`.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Přidá přepínač na `CTaskDialog`.|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Klikne na ovládací prvek příkazové tlačítko nebo na společné tlačítko programově.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Klikne na přepínací tlačítko programově.|
|[CTaskDialog::DoModal](#domodal)|`CTaskDialog`Zobrazí.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Načte počet společných tlačítek k dispozici.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Převede standardní tlačítko Windows na společný typ tlačítka přidružený `CTaskDialog` ke třídě.|
|[Objektu CTaskDialog:: GetCommonButtonId](#getcommonbuttonid)|Převede jeden z obecných typů tlačítek přidružených `CTaskDialog` ke třídě na standardní tlačítko Windows.|
|[Objektu CTaskDialog:: GetOptions](#getoptions)|Vrátí příznaky možností pro tento `CTaskDialog`parametr.|
|[Objektu CTaskDialog:: GetSelectedCommandControlID](#getselectedcommandcontrolid)|Vrátí vybraný ovládací prvek příkazového tlačítka.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Vrátí vybraný přepínač.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Načte stav zaškrtávacího políčka ověřování.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Určuje, zda je povoleno ovládací prvek příkazové tlačítko nebo společné tlačítko.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Určuje, zda je přepínač povolen.|
|[Objektu CTaskDialog:: podporuje se](#issupported)|Určuje, zda počítač, ve kterém je spuštěna aplikace, `CTaskDialog`podporuje.|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Přidá ovládací prvky příkazového tlačítka pomocí dat z tabulky řetězců.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Přidá přepínače pomocí dat z tabulky řetězců.|
|[CTaskDialog::NavigateTo](#navigateto)|Přenese fokus na jiný `CTaskDialog`.|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Rozhraní volá tuto metodu, když uživatel klikne na ovládací prvek příkazové tlačítko.|
|[CTaskDialog::OnCreate](#oncreate)|Rozhraní volá tuto metodu poté, co vytvoří `CTaskDialog`.|
|[CTaskDialog::OnDestroy](#ondestroy)|Rozhraní volá tuto metodu těsně před zničením `CTaskDialog`.|
|[Objektu CTaskDialog:: OnExpandButtonClick](#onexpandbuttonclick)|Rozhraní volá tuto metodu, když uživatel klikne na tlačítko rozšíření.|
|[Objektu CTaskDialog:: help](#onhelp)|Rozhraní volá tuto metodu, když si uživatel požádá o technickou podporu.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Rozhraní volá tuto metodu, když uživatel klikne na hypertextový odkaz.|
|[CTaskDialog::OnInit](#oninit)|Rozhraní volá tuto metodu, když `CTaskDialog` je inicializována.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Rozhraní volá tuto metodu, když uživatel přesune fokus s ohledem na ovládací prvky v `CTaskDialog`.|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Rozhraní volá tuto metodu, když uživatel vybere ovládací prvek přepínač.|
|[CTaskDialog::OnTimer](#ontimer)|Rozhraní volá tuto metodu, když vyprší platnost časovače.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Rozhraní volá tuto metodu, když uživatel klikne na zaškrtávací políčko ověřování.|
|[Objektu CTaskDialog:: RemoveAllCommandControls](#removeallcommandcontrols)|Odebere všechny ovládací prvky příkazu z `CTaskDialog`.|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Odebere všechna přepínací tlačítka z `CTaskDialog`.|
|[Objektu CTaskDialog:: SetCommandControlOptions](#setcommandcontroloptions)|Aktualizuje ovládací prvek příkazové tlačítko na `CTaskDialog`.|
|[Objektu CTaskDialog:: SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podmnožinu společných tlačítek, která se mají povolit, a vyžaduje zvýšení oprávnění nástroje řízení uživatelských účtů.|
|[Objektu CTaskDialog:: SetCommonButtons](#setcommonbuttons)|Přidá do `CTaskDialog`. společná tlačítka.|
|[Objektu CTaskDialog:: SetContent](#setcontent)|Aktualizuje obsah `CTaskDialog`.|
|[Objektu CTaskDialog:: SetDefaultCommandControl](#setdefaultcommandcontrol)|Určuje výchozí ovládací prvek příkazového tlačítka.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Určuje výchozí přepínač.|
|[Objektu CTaskDialog:: SetDialogWidth](#setdialogwidth)|Upraví šířku `CTaskDialog`.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizuje oblast rozšíření v `CTaskDialog`.|
|[Objektu CTaskDialog:: SetFooterIcon](#setfootericon)|Aktualizuje ikonu zápatí pro `CTaskDialog`.|
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizuje text v zápatí `CTaskDialog`.|
|[Objektu CTaskDialog:: SetMainIcon](#setmainicon)|Aktualizuje hlavní ikonu `CTaskDialog`.|
|[Objektu CTaskDialog:: SetMainInstruction](#setmaininstruction)|Aktualizuje hlavní instrukci `CTaskDialog`.|
|[Objektu CTaskDialog:: SetOptions](#setoptions)|Konfiguruje možnosti pro `CTaskDialog`.|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Nakonfiguruje pruh výběru pro `CTaskDialog` a přidá ho do dialogového okna.|
|[Objektu CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)|Upraví umístění indikátoru průběhu.|
|[Objektu CTaskDialog:: SetProgressBarRange](#setprogressbarrange)|Upraví rozsah indikátoru průběhu.|
|[Objektu CTaskDialog:: SetProgressBarState](#setprogressbarstate)|Nastaví stav indikátoru průběhu a zobrazí jej v `CTaskDialog`.|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Povolí nebo zakáže přepínač.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Nastaví zaškrtnuté políčko ověřování.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Nastaví text na pravé straně ověřování.|
|[Objektu CTaskDialog:: SetWindowTitle](#setwindowtitle)|Nastaví název `CTaskDialog`.|
|[Objektu CTaskDialog:: ShowDialog](#showdialog)|Vytvoří a zobrazí `CTaskDialog`.|
|[Objektu CTaskDialog:: TaskDialogCallback](#taskdialogcallback)|Rozhraní volá toto v reakci na různé zprávy systému Windows.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|`m_aButtons`|Pole ovládacích prvků příkazového tlačítka pro `CTaskDialog`.|
|`m_aRadioButtons`|Pole ovládacích prvků přepínačů pro `CTaskDialog`.|
|`m_bVerified`|`TRUE`indikuje, že je zaškrtnuté políčko ověřování. `FALSE` označuje, že není.|
|`m_footerIcon`|Ikona v zápatí `CTaskDialog`.|
|`m_hWnd`|Popisovač okna pro `CTaskDialog`.|
|`m_mainIcon`|Hlavní ikona `CTaskDialog`.|
|`m_nButtonDisabled`|Maska, která označuje, které z běžných tlačítek jsou zakázané.|
|`m_nButtonElevation`|Maska, která určuje, který z běžných tlačítek vyžaduje zvýšení oprávnění nástroje řízení uživatelských účtů.|
|`m_nButtonId`|ID vybraného ovládacího prvku příkazového tlačítka|
|`m_nCommonButton`|Maska, která určuje, která společná tlačítka se zobrazí v `CTaskDialog`.|
|`m_nDefaultCommandControl`|ID ovládacího prvku příkazového tlačítka, který je vybrán při `CTaskDialog` zobrazení.|
|`m_nDefaultRadioButton`|Identifikátor ovládacího prvku přepínač, který je vybrán při `CTaskDialog` zobrazení.|
|`m_nFlags`|Maska, která určuje možnosti pro `CTaskDialog`.|
|`m_nProgressPos`|Aktuální pozice indikátoru průběhu.  Tato hodnota musí být mezi `m_nProgressRangeMin` a `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|Maximální hodnota indikátoru průběhu.|
|`m_nProgressRangeMin`|Minimální hodnota indikátoru průběhu.|
|`m_nProgressState`|Stav indikátoru průběhu. Další informace najdete v tématu [objektu CTaskDialog:: SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|ID vybraného ovládacího prvku přepínače|
|`m_nWidth`|Šířka `CTaskDialog` v pixelech.|
|`m_strCollapse`|Řetězec, který `CTaskDialog` se zobrazí napravo od pole rozšíření, když jsou rozšířené informace skryté.|
|`m_strContent`|Řetězec obsahu pro `CTaskDialog`.|
|`m_strExpand`|Řetězec, který `CTaskDialog` se zobrazí napravo od pole rozšíření při zobrazení rozbalených informací.|
|`m_strFooter`|Zápatí `CTaskDialog`.|
|`m_strInformation`|Rozšířené informace pro `CTaskDialog`.|
|`m_strMainInstruction`|Hlavní instrukce pro `CTaskDialog`.|
|`m_strTitle`|Název `CTaskDialog`.|
|`m_strVerification`|Řetězec, který se `CTaskDialog` zobrazí napravo od zaškrtávacího políčka ověření.|

## <a name="remarks"></a>Poznámky

`CTaskDialog` Třída nahradí standardní okno se zprávou Windows a má další funkce, jako jsou nové ovládací prvky pro shromáždění informací od uživatele. Tato třída je v knihovně MFC v aplikaci Visual Studio 2010 nebo novější. `CTaskDialog` Je k dispozici od systému Windows Vista. Starší verze systému Windows nemohou `CTaskDialog` objekt zobrazit. Použijte `CTaskDialog::IsSupported` k určení za běhu, zda může aktuální uživatel zobrazit dialogové okno úlohy. Standardní okno se zprávou Windows se pořád podporuje.

`CTaskDialog` Je k dispozici pouze v případě, že sestavíte aplikaci pomocí knihovny Unicode.

`CTaskDialog` Má dva různé konstruktory. Jeden konstruktor umožňuje zadat dvě příkazová tlačítka a maximálně šest běžných ovládacích prvků tlačítek. Po vytvoření `CTaskDialog`můžete přidat další příkazové tlačítko. Druhý konstruktor nepodporuje žádné příkazové tlačítko, ale lze přidat neomezený počet běžných ovládacích prvků tlačítek. Další informace o konstruktorech naleznete v tématu [objektu CTaskDialog:: objektu CTaskDialog](#ctaskdialog).

Následující obrázek ukazuje ukázku `CTaskDialog` pro ilustraci umístění některých ovládacích prvků.

![Příklad objektu CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Příklad objektu CTaskDialog") <br/>
Ukázka objektu CTaskDialog

## <a name="requirements"></a>Požadavky

**Minimální požadovaný operační systém:** Windows Vista

**Záhlaví:** afxtaskdialog. h

##  <a name="addcommandcontrol"></a>Objektu CTaskDialog:: AddCommandControl

Přidá k `CTaskDialog`ovládacímu prvku nové příkazové tlačítko.

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
pro Identifikační číslo ovládacího prvku příkazu

*strCaption*<br/>
pro Řetězec, který se `CTaskDialog` zobrazí uživateli. Pomocí tohoto řetězce můžete vysvětlit účel příkazu.

*bEnabled*<br/>
pro Logický parametr, který označuje, zda je tlačítko Nový povoleno nebo zakázáno.

*bRequiresElevation*<br/>
pro Logický parametr, který označuje, zda příkaz vyžaduje zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

`CTaskDialog Class` Může zobrazit neomezený počet ovládacích prvků příkazového tlačítka. Pokud `CTaskDialog` však zobrazí jakékoli ovládací prvky příkazového tlačítka, může zobrazit maximálně šest tlačítek. `CTaskDialog` Pokud neobsahuje žádné ovládací prvky příkazového tlačítka, může zobrazit neomezený počet tlačítek.

Když uživatel vybere ovládací prvek příkazové tlačítko, zavře se `CTaskDialog` . Pokud vaše aplikace zobrazí dialogové okno pomocí [objektu CTaskDialog::D omodal](#domodal), `DoModal` vrátí *nCommandControlID* vybraného ovládacího prvku příkazového tlačítka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>Objektu CTaskDialog:: AddRadioButton

Přidá přepínač na `CTaskDialog`.

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
pro Identifikační číslo přepínače

*strCaption*<br/>
pro Řetězec, který se `CTaskDialog` zobrazí vedle přepínače.

*bEnabled*<br/>
pro Logický parametr, který označuje, zda je přepínač povolen.

### <a name="remarks"></a>Poznámky

Přepínače pro [třídu objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) umožňují shromažďovat informace od uživatele. Pomocí funkce [objektu CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid) určete, který přepínač je vybrán.

Nepožaduje, aby byly parametry nRadioButtonID pro každý přepínač jedinečné. `CTaskDialog` Pokud však pro každý přepínač nepoužíváte odlišný identifikátor, může docházet k neočekávanému chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>Objektu CTaskDialog:: ClickCommandControl

Klikne na ovládací prvek příkazové tlačítko nebo na společné tlačítko programově.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
pro ID příkazu ovládacího prvku, který se má kliknout

### <a name="remarks"></a>Poznámky

Tato metoda generuje zprávu Windows TDM_CLICK_BUTTON.

##  <a name="clickradiobutton"></a>Objektu CTaskDialog:: ClickRadioButton

Klikne na přepínací tlačítko programově.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
pro ID přepínacího tlačítka, na které se má kliknout

### <a name="remarks"></a>Poznámky

Tato metoda generuje zprávu Windows TDM_CLICK_RADIO_BUTTON.

##  <a name="ctaskdialog"></a>Objektu CTaskDialog:: objektu CTaskDialog

Vytvoří instanci [třídy objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

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

*strContent*<br/>
pro Řetězec, který má být použit pro obsah `CTaskDialog`.

*strMainInstruction*<br/>
pro Hlavní instrukce pro `CTaskDialog`.

*strTitle*<br/>
pro Název `CTaskDialog`.

*nCommonButtons*<br/>
pro Maska společných tlačítek, která se mají přidat do `CTaskDialog`.

*nTaskDialogOptions*<br/>
pro Sada možností, které se mají použít pro `CTaskDialog`.

*strFooter*<br/>
pro Řetězec, který má být použit jako zápatí.

*nIDCommandControlsFirst*<br/>
pro ID řetězce prvního příkazu

*nIDCommandControlsLast*<br/>
pro ID řetězce posledního příkazu

### <a name="remarks"></a>Poznámky

Existují dva způsoby, jak můžete přidat `CTaskDialog` do aplikace. Prvním způsobem je použít jeden z konstruktorů k vytvoření `CTaskDialog` a zobrazení pomocí [objektu CTaskDialog::D omodal](#domodal). Druhým způsobem je použít statickou funkci [objektu CTaskDialog:: ShowDialog](#showdialog), která umožňuje zobrazit `CTaskDialog` `CTaskDialog` objekt bez explicitního vytvoření objektu.

Druhý konstruktor vytvoří ovládací prvky příkazového tlačítka pomocí dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými identifikátory řetězců. Tato metoda přidá ovládací prvek příkazové tlačítko pro každou platnou položku v tabulce řetězců mezi *nIDCommandControlsFirst* a *nCommandControlsLast*(včetně). Pro toto příkazové tlačítko ovládací prvky je řetězec v tabulce String titulkem ovládacího prvku a ID řetězce je ID ovládacího prvku.

Seznam platných možností naleznete v tématu [objektu CTaskDialog:: SetOptions](#setoptions) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>Objektu CTaskDialog::D oModal

Zobrazí a `CTaskDialog` nastaví ho jako modální.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hParent*<br/>
pro Nadřazené okno pro `CTaskDialog`.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které odpovídá výběru provedenému uživatelem.

### <a name="remarks"></a>Poznámky

Zobrazí tuto instanci [objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Aplikace potom počká, až uživatel dialogové okno zavřete.

Zavře, když uživatel vybere společné tlačítko, ovládací prvek odkaz na příkazy nebo `CTaskDialog`zavře. `CTaskDialog` Vrácená hodnota je identifikátor, který označuje, jak uživatel zavřel dialogové okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>Objektu CTaskDialog:: GetCommonButtonCount

Načte počet běžných tlačítek.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet běžných tlačítek, která jsou k dispozici.

### <a name="remarks"></a>Poznámky

Společná tlačítka jsou výchozími tlačítky, které zadáte do [objektu CTaskDialog:: objektu CTaskDialog](#ctaskdialog). [Třída objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) zobrazí tlačítka podél dolního okraje dialogového okna.

Výčtový seznam tlačítek je k dispozici v CommCtrl. h.

##  <a name="getcommonbuttonflag"></a>Objektu CTaskDialog:: GetCommonButtonFlag

Převede standardní tlačítko Windows na společný typ tlačítka přidružený ke [třídě objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parametry

*nButtonId*<br/>
pro Standardní hodnota tlačítka Windows

### <a name="return-value"></a>Návratová hodnota

Hodnota odpovídajícího `CTaskDialog` obecného tlačítka Pokud není k dispozici odpovídající tlačítko Common, vrátí tato metoda hodnotu 0.

##  <a name="getcommonbuttonid"></a>Objektu CTaskDialog:: GetCommonButtonId

Převede jeden z obecných typů tlačítek přidružených k [třídě objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) na standardní tlačítko Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parametry

*načit*<br/>
pro Společný typ tlačítka přidružený `CTaskDialog` ke třídě.

### <a name="return-value"></a>Návratová hodnota

Hodnota odpovídajícího tlačítka pro standardní Windows Pokud není k dispozici odpovídající tlačítko Windows, vrátí metoda 0.

##  <a name="getoptions"></a>Objektu CTaskDialog:: GetOptions

Vrátí příznaky možností pro tento `CTaskDialog`parametr.

```
int GetOptions() const;
```

### <a name="return-value"></a>Návratová hodnota

Příznaky pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Další informace o možnostech dostupných pro [třídu objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md)naleznete v tématu [objektu CTaskDialog:: SetOptions](#setoptions).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>Objektu CTaskDialog:: GetSelectedCommandControlID

Vrátí vybraný ovládací prvek příkazového tlačítka.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID aktuálně vybraného ovládacího prvku příkazové tlačítko

### <a name="remarks"></a>Poznámky

Tuto metodu není nutné používat k načtení ID příkazového tlačítka, které uživatel vybral. IDENTIFIKÁTOR je vrácen buď pomocí [objektu CTaskDialog::D omodal](#domodal) , nebo [objektu CTaskDialog:: ShowDialog](#showdialog).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>Objektu CTaskDialog:: GetSelectedRadioButtonID

Vrátí vybraný přepínač.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID vybraného přepínacího tlačítka

### <a name="remarks"></a>Poznámky

Tuto metodu můžete použít poté, co uživatel zavře dialogové okno, aby načetl vybraný přepínač.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>Objektu CTaskDialog:: GetVerificationCheckboxState

Načte stav zaškrtávacího políčka ověřování.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zaškrtávací políčko zaškrtnuto, FALSE, pokud není.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>Objektu CTaskDialog:: IsCommandControlEnabled

Určuje, zda je povoleno ovládací prvek nebo tlačítko příkazového tlačítka.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
pro ID ovládacího prvku příkazového tlačítka nebo tlačítka k otestování

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je ovládací prvek povolený, FALSE, pokud není.

### <a name="remarks"></a>Poznámky

Tuto metodu lze použít k určení dostupnosti obou ovládacích prvků příkazového tlačítka a společných tlačítek `CTaskDialog` třídy *.

Pokud *nCommandControlID* není platným identifikátorem pro společné `CTaskDialog` tlačítko nebo ovládací prvek příkazové tlačítko, tato metoda vyvolá výjimku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>Objektu CTaskDialog:: IsRadioButtonEnabled

Určuje, zda je přepínač povolen.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
pro ID přepínacího přepínače, které chcete otestovat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je přepínač povolený, FALSE, pokud není.

### <a name="remarks"></a>Poznámky

Pokud *nRadioButtonID* není platný identifikátor pro přepínač, tato metoda vyvolá výjimku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>Objektu CTaskDialog:: podporuje se

Určuje, zda počítač, ve kterém je spuštěna aplikace, `CTaskDialog`podporuje.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud počítač podporuje `CTaskDialog`; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení za běhu, pokud počítač, na kterém je spuštěna vaše aplikace `CTaskDialog` , podporuje třídu. Pokud počítač nepodporuje `CTaskDialog`, měli byste zadat jinou metodu sdělování informací uživateli. Dojde k chybě aplikace, pokud se pokusí použít `CTaskDialog` na počítači, který `CTaskDialog` třídu nepodporuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>Objektu CTaskDialog:: LoadCommandControls

Přidá ovládací prvky příkazového tlačítka pomocí dat z tabulky řetězců.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parametry

*nIDCommandControlsFirst*<br/>
pro ID řetězce prvního příkazu

*nIDCommandControlsLast*<br/>
pro ID řetězce posledního příkazu

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří ovládací prvky příkazového tlačítka pomocí dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými identifikátory řetězců. Nové ovládací prvky příkazového tlačítka přidané pomocí této metody používají řetězec pro titulek ovládacího prvku a ID řetězce pro ID ovládacího prvku. Rozsah vybraných řetězců je poskytován *nIDCommandControlsFirst* a *nCommandControlsLast*(včetně). Pokud je v rozsahu prázdná položka, metoda nepřidá ovládací prvek příkazové tlačítko pro tuto položku.

Ve výchozím nastavení jsou k dispozici nové ovládací prvky příkazového tlačítka a nevyžadují zvýšení úrovně oprávnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>Objektu CTaskDialog:: LoadRadioButtons

Přidá ovládací prvky přepínačů pomocí dat z tabulky řetězců.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parametry

*nIDRadioButtonsFirst*<br/>
pro ID řetězce prvního přepínacího tlačítka.

*nIDRadioButtonsLast*<br/>
pro ID řetězce posledního přepínacího tlačítka

### <a name="remarks"></a>Poznámky

Tato metoda vytváří přepínací tlačítka pomocí dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými identifikátory řetězců. Nová přepínací tlačítka přidaná pomocí této metody používají řetězec pro titulek přepínače a ID řetězce pro ID přepínacího tlačítka. Rozsah vybraných řetězců je poskytován *nIDRadioButtonsFirst* a *nRadioButtonsLast*(včetně). Pokud je v rozsahu prázdná položka, metoda nepřidá přepínač pro tuto položku.

Ve výchozím nastavení jsou povolená nová přepínačová tlačítka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>Objektu CTaskDialog:: NavigateTo

Přenese fokus na jiný `CTaskDialog`.

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parametry

*oTaskDialog*<br/>
pro `CTaskDialog` , Který dostane fokus.

### <a name="remarks"></a>Poznámky

Tato metoda skryje aktuální `CTaskDialog` , když se zobrazí *oTaskDialog*. *OTaskDialog* se zobrazí ve stejném umístění jako aktuální `CTaskDialog`.

##  <a name="oncommandcontrolclick"></a>Objektu CTaskDialog:: OnCommandControlClick

Rozhraní volá tuto metodu, když uživatel klikne na ovládací prvek příkazové tlačítko.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
pro ID ovládacího prvku příkazového tlačítka, který uživatel vybral

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="oncreate"></a>Objektu CTaskDialog:: Create

Rozhraní volá tuto metodu poté, co vytvoří `CTaskDialog`.

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="ondestroy"></a>Objektu CTaskDialog:: Destroy – zničení

Rozhraní volá tuto metodu těsně před zničením `CTaskDialog`.

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="onexpandbuttonclick"></a>Objektu CTaskDialog:: OnExpandButtonClick

Rozhraní volá tuto metodu, když uživatel klikne na tlačítko rozšíření.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parametry

*bExpanded*<br/>
pro Nenulová hodnota znamená, že se zobrazí další informace; 0 značí, že jsou další informace skryté.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="onhelp"></a>Objektu CTaskDialog:: help

Rozhraní volá tuto metodu, když si uživatel požádá o technickou podporu.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="onhyperlinkclick"></a>Objektu CTaskDialog:: OnHyperlinkClick

Rozhraní volá tuto metodu, když uživatel klikne na hypertextový odkaz.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parametry

*strHref*<br/>
pro Řetězec, který představuje hypertextový odkaz.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Tato metoda volá [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) před tím, než vrátí S_OK.

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="oninit"></a>Objektu CTaskDialog:: OnInit

Rozhraní volá tuto metodu, když `CTaskDialog` je inicializována.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="onnavigatepage"></a>Objektu CTaskDialog:: OnNavigatePage

Rozhraní volá tuto metodu v reakci na metodu [objektu CTaskDialog:: NavigateTo](#navigateto) .

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="onradiobuttonclick"></a>Objektu CTaskDialog:: OnRadioButtonClick

Rozhraní volá tuto metodu, když uživatel vybere ovládací prvek přepínač.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
pro ID ovládacího prvku přepínacího tlačítka, na kterého uživatel kliknul

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="ontimer"></a>Objektu CTaskDialog::-Timeer

Rozhraní volá tuto metodu, když vyprší platnost časovače.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parametry

*lTime*<br/>
pro Doba v milisekundách od `CTaskDialog` jejího vytvoření nebo resetování časovače.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="onverificationcheckboxclick"></a>Objektu CTaskDialog:: OnVerificationCheckboxClick

Rozhraní volá tuto metodu, když uživatel klikne na zaškrtávací políčko ověřování.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
pro Hodnota TRUE označuje, že je zaškrtnuto zaškrtávací políčko ověřování. Hodnota FALSE znamená, že není.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro implementaci vlastního chování.

##  <a name="removeallcommandcontrols"></a>Objektu CTaskDialog:: RemoveAllCommandControls

Odebere všechny ovládací prvky příkazového tlačítka z `CTaskDialog`.

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>Objektu CTaskDialog:: RemoveAllRadioButtons

Odebere všechna přepínací tlačítka z `CTaskDialog`.

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>Objektu CTaskDialog:: SetCommandControlOptions

Aktualizuje ovládací prvek příkazové tlačítko na `CTaskDialog`.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
pro ID ovládacího prvku příkazu, který se má aktualizovat

*bEnabled*<br/>
pro Logický parametr, který označuje, zda je zadané nebo zakázané ovládací prvek příkazového tlačítka.

*bRequiresElevation*<br/>
pro Logický parametr, který určuje, zda určené ovládací prvky příkazového tlačítka vyžadují zvýšení úrovně oprávnění.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li změnit, zda je ovládací prvek příkazové tlačítko povolen nebo vyžaduje zvýšení oprávnění poté, co `CTaskDialog` bylo přidáno do třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>Objektu CTaskDialog:: SetCommonButtonOptions

Aktualizuje podmnožinu společných tlačítek, která se mají povolit, a vyžaduje zvýšení oprávnění nástroje řízení uživatelských účtů.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nDisabledButtonMask*<br/>
pro Maska pro společná tlačítka, která se mají zakázat.

*nElevationButtonMask*<br/>
pro Maska pro společná tlačítka, která vyžadují zvýšení úrovně oprávnění.

### <a name="remarks"></a>Poznámky

Můžete nastavit společná tlačítka dostupná pro instanci [třídy objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) pomocí konstruktoru [objektu CTaskDialog:: objektu CTaskDialog](#ctaskdialog) a metody [objektu CTaskDialog:: SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`nepodporuje přidávání nových společných tlačítek.

Použijete-li tuto metodu k zakázání nebo zvýšení úrovně společného tlačítka, které není k dispozici `CTaskDialog`, tato metoda vyvolá výjimku pomocí makra pro [zajištění](diagnostic-services.md#ensure) .

Tato metoda povoluje jakékoli tlačítko, které je k dispozici pro `CTaskDialog` , ale není v *nDisabledButtonMask*, i když bylo dříve zakázáno. Tato metoda zpracovává zvýšení oprávnění podobným způsobem: zaznamenává společná tlačítka jako nevyžadující zvýšení oprávnění, pokud je toto společné tlačítko k dispozici, ale není součástí *nElevationButtonMask*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>Objektu CTaskDialog:: SetCommonButtons

Přidá do `CTaskDialog`. společná tlačítka.

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nButtonMask*<br/>
pro Maska tlačítek, která se mají přidat do `CTaskDialog`.

*nDisabledButtonMask*<br/>
pro Maska tlačítek, která se mají zakázat

*nElevationButtonMask*<br/>
pro Maska tlačítek, která vyžadují zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

Tuto metodu nelze volat po vytvoření okna zobrazení této instance `CTaskDialog` třídy. V případě, tato metoda vyvolá výjimku.

Tlačítka označená *nButtonMask* přepíšou všechna společná tlačítka, která jste přidali do `CTaskDialog`. K dispozici jsou pouze tlačítka označená v *nButtonMask* .

Pokud buď *nDisabledButtonMask* nebo *nElevationButtonMask* obsahuje tlačítko, které není v *nButtonMask*, vyvolá tato metoda výjimku pomocí makra pro [zajištění](diagnostic-services.md#ensure) .

Ve výchozím nastavení jsou všechna společná tlačítka povolena a nevyžadují zvýšení úrovně oprávnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>Objektu CTaskDialog:: SetContent

Aktualizuje obsah `CTaskDialog`.

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
pro Řetězec, který se má zobrazit uživateli

### <a name="remarks"></a>Poznámky

Obsah `CTaskDialog` třídy je text, který se zobrazí uživateli v hlavní části dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>Objektu CTaskDialog:: SetDefaultCommandControl

Určuje výchozí ovládací prvek příkazového tlačítka.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
pro ID ovládacího prvku příkazové tlačítko, které se má nastavit jako výchozí

### <a name="remarks"></a>Poznámky

Výchozí ovládací prvek příkazové tlačítko je ovládací prvek, který je vybrán při `CTaskDialog` prvním zobrazení uživatele.

Tato metoda vyvolá výjimku, pokud nemůže najít ovládací prvek příkazové tlačítko určený parametrem *nCommandControlID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>Objektu CTaskDialog:: SetDefaultRadioButton

Určuje výchozí přepínač.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
pro ID přepínacího tlačítka, které bude výchozím nastavením.

### <a name="remarks"></a>Poznámky

Výchozí přepínač je tlačítko, které je vybráno při `CTaskDialog` prvním zobrazení uživatele.

Tato metoda vyvolá výjimku, nemůže-li najít přepínač určený parametrem *nRadioButtonID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>Objektu CTaskDialog:: SetDialogWidth

Upraví šířku `CTaskDialog`.

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
pro Šířka dialogového okna v pixelech

### <a name="remarks"></a>Poznámky

Parametr *nWidth* musí být větší nebo roven 0. V opačném případě tato metoda vyvolá výjimku.

Pokud je *nWidth* nastaveno na hodnotu 0, tato metoda nastaví výchozí velikost dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>Objektu CTaskDialog:: SetExpansionArea

Aktualizuje oblast rozšíření v `CTaskDialog`.

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parametry

*strExpandedInformation*<br/>
pro Řetězec, který se `CTaskDialog` zobrazí v hlavním těle dialogového okna, když uživatel klikne na tlačítko rozšíření.

*strCollapsedLabel*<br/>
pro Řetězec, který se `CTaskDialog` zobrazí vedle tlačítka pro rozšíření při sbalení rozbalené oblasti.

*strExpandedLabel*<br/>
pro Řetězec, který se `CTaskDialog` zobrazí vedle tlačítka pro rozšíření při zobrazení rozbalené oblasti.

### <a name="remarks"></a>Poznámky

Oblast `CTaskDialog` rozšíření třídy vám umožní poskytnout uživateli další informace. Oblast rozšíření je v hlavní části `CTaskDialog`, která je umístěna hned pod nadpisem a řetězcem obsahu.

Při prvním zobrazení se nezobrazují rozšířené informace a vloží `strCollapsedLabel` se vedle tlačítka rozšíření. `CTaskDialog` Když uživatel klikne na tlačítko rozšíření, `CTaskDialog` zobrazí *strExpandedInformation* a změní popisek na *strExpandedLabel*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>Objektu CTaskDialog:: SetFooterIcon

Aktualizuje ikonu `CTaskDialog`zápatí.

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parametry

*hFooterIcon*<br/>
pro Nová ikona pro `CTaskDialog`.

*lpszFooterIcon*<br/>
pro Nová ikona pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Ikona zápatí se zobrazí v dolní části [třídy objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Může mít přidružený text zápatí. Můžete změnit text zápatí pomocí [objektu CTaskDialog:: SetFooterText](#setfootertext).

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, `CTaskDialog` Pokud je zobrazeno, nebo vstupní parametr má hodnotu null.

Může přijmout pouze ikonu `LPCWSTR` zápatí nebo.`HICON` `CTaskDialog` To je nakonfigurováno nastavením možnosti TDF_USE_HICON_FOOTER v konstruktoru nebo [objektu CTaskDialog:: SetOptions](#setoptions). Ve výchozím nastavení je `CTaskDialog` Tato ikona nakonfigurovaná `LPCWSTR` tak, aby se použila jako typ vstupu pro ikonu zápatí. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodného typu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>Objektu CTaskDialog:: SetFooterText

Aktualizuje text v zápatí `CTaskDialog`.

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parametry

*strFooterText*<br/>
pro Nový text pro zápatí

### <a name="remarks"></a>Poznámky

Ikona zápatí se zobrazí vedle textu zápatí v dolní části okna `CTaskDialog`. Můžete změnit ikonu zápatí pomocí [objektu CTaskDialog:: SetFooterIcon](#setfootericon).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>Objektu CTaskDialog:: SetMainIcon

Aktualizuje hlavní ikonu `CTaskDialog`.

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parametry

*hMainIcon*<br/>
pro Nová ikona

*lpszMainIcon*<br/>
pro Nová ikona

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, `CTaskDialog` Pokud je zobrazeno, nebo vstupní parametr má hodnotu null.

Může přijmout pouze hlavní `LPCWSTR` ikonu nebo.`HICON` `CTaskDialog` To můžete nakonfigurovat nastavením možnosti TDF_USE_HICON_MAIN v konstruktoru nebo v metodě [objektu CTaskDialog:: SetOptions](#setoptions) . Ve výchozím nastavení `CTaskDialog` je nakonfigurována pro použití `LPCWSTR` jako typ vstupu hlavní ikony. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodného typu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>Objektu CTaskDialog:: SetMainInstruction

Aktualizuje hlavní instrukci `CTaskDialog`.

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parametry

*strInstructions*<br/>
pro Nová hlavní instrukce.

### <a name="remarks"></a>Poznámky

Hlavní pokyn `CTaskDialog` třídy je text zobrazený uživateli velkými tučným písmem. Nachází se v dialogovém okně pod záhlavím.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>Objektu CTaskDialog:: SetOptions

Konfiguruje možnosti pro `CTaskDialog`.

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parametry

*nOptionFlag*<br/>
pro Sada příznaků, které mají být použity pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Tato metoda vymaže všechny aktuální možnosti pro `CTaskDialog`. Chcete-li zachovat aktuální možnosti, je nutné je nejprve načíst pomocí [objektu CTaskDialog:: GetOptions](#getoptions) a kombinovat je s možnostmi, které chcete nastavit.

V následující tabulce jsou uvedeny všechny platné možnosti.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Povolí hypertextové odkazy `CTaskDialog`v.|
|TDF_USE_HICON_MAIN|Nakonfiguruje `HICON` pro použití pro hlavní ikonu. `CTaskDialog` Alternativou je použití `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|Nakonfiguruje `CTaskDialog` , aby se `HICON` pro ikonu zápatí používala. Alternativou je použití `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Umožňuje uživateli zavřít `CTaskDialog` pomocí klávesnice nebo pomocí ikony v pravém horním rohu dialogového okna, a to i v případě, že tlačítko **Storno** není povolené. Pokud tento příznak není nastavený a tlačítko **Storno** není povolené, uživatel nemůže dialogové okno zavřít pomocí ALT + F4, řídicí klávesy nebo tlačítka Zavřít záhlaví.|
|TDF_USE_COMMAND_LINKS|Nakonfiguruje ovládací prvky pro použití příkazového tlačítka. `CTaskDialog`|
|TDF_USE_COMMAND_LINKS_NO_ICON|Nakonfiguruje ovládací prvky pro použití příkazového tlačítka bez zobrazení ikony vedle ovládacího prvku. `CTaskDialog` TDF_USE_COMMAND_LINKS Přepisuje TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Označuje, že oblast rozšíření je aktuálně rozbalená.|
|TDF_EXPANDED_BY_DEFAULT|Určuje, zda je oblast rozšíření ve výchozím nastavení rozbalená.|
|TDF_VERIFICATION_FLAG_CHECKED|Určuje, zda je zaškrtnuto políčko ověřování.|
|TDF_SHOW_PROGRESS_BAR|Nakonfiguruje `CTaskDialog` pro zobrazení indikátoru průběhu.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Nakonfiguruje indikátor průběhu na indikátor průběhu rámečku. Pokud tuto možnost povolíte, musíte nastavit TDF_SHOW_PROGRESS_BAR na očekávané chování.|
|TDF_CALLBACK_TIMER|Označuje, že `CTaskDialog` interval zpětného volání je nastaven na přibližně 200 milisekund.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Nakonfiguruje na zarovnání do středu vzhledem k nadřazenému oknu. `CTaskDialog` Pokud tento příznak není povolený, `CTaskDialog` je zarovnán na střed vzhledem k monitoru.|
|TDF_RTL_LAYOUT|Nakonfiguruje `CTaskDialog` pro čtení rozložení zprava doleva.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Označuje, že po `CTaskDialog` zobrazení není vybrán přepínač bez přepínače.|
|TDF_CAN_BE_MINIMIZED|Umožňuje uživateli minimalizovat `CTaskDialog`. Pro podporu této možnosti `CTaskDialog` nemůže být modální. Knihovna MFC tuto možnost nepodporuje, protože knihovna MFC nepodporuje nemodální `CTaskDialog`.|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee

Nakonfiguruje pruh výběru pro `CTaskDialog` a přidá ho do dialogového okna.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parametry

*bEnabled*<br/>
pro TRUE, pokud chcete povolit pruh výběru; FALSE, pokud chcete vypnout pruhový text a odebrat ho z `CTaskDialog`.

*nMarqueeSpeed*<br/>
pro Celé číslo, které označuje rychlost pruhu běžícího rámečku.

### <a name="remarks"></a>Poznámky

Pod hlavním textem `CTaskDialog` třídy se zobrazí pruh rámečku.

Pomocí *nMarqueeSpeed* nastavte rychlost pruhu výběru. větší hodnoty znamenají pomalejší rychlost. Hodnota 0 pro *nMarqueeSpeed* způsobí, že se pruh rámečku přesune na výchozí rychlost pro Windows.

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, pokud *nMarqueeSpeed* je menší než 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>Objektu CTaskDialog:: SetProgressBarPosition

Upraví umístění indikátoru průběhu.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
pro Pozice indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, pokud *nProgressPos* není v rozsahu indikátoru průběhu. Rozsah indikátoru průběhu můžete změnit pomocí [objektu CTaskDialog:: SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>Objektu CTaskDialog:: SetProgressBarRange

Upraví rozsah indikátoru průběhu.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
pro Dolní mez indikátoru průběhu.

*nRangeMax*<br/>
pro Horní mez indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Pozice indikátoru průběhu je relativní vzhledem k *nRangeMin* a *nRangeMax*. Například pokud je *nRangeMin* 50 a *nRangeMax* je 100, pozice 75 je uprostřed v průběhu indikátoru průběhu. K nastavení pozice indikátoru průběhu použijte [objektu CTaskDialog:: SetProgressBarPosition](#setprogressbarposition) .

Chcete-li zobrazit indikátor průběhu, je nutné povolit možnost TDF_SHOW_PROGRESS_BAR a TDF_SHOW_MARQUEE_PROGRESS_BAR nesmí být povoleny. Tato metoda automaticky nastaví TDF_SHOW_PROGRESS_BAR a vymaže TDF_SHOW_MARQUEE_PROGRESS_BAR. Pomocí [objektu CTaskDialog:: SetOptions](#setoptions) ručně změňte možnosti této instance [třídy objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, pokud *nRangeMin* není menší než *nRangeMax*. Tato metoda také vyvolá výjimku, pokud `CTaskDialog` je již zobrazena a má indikátor průběhu běžícího textu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>Objektu CTaskDialog:: SetProgressBarState

Nastaví stav indikátoru průběhu a zobrazí jej v `CTaskDialog`.

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parametry

*nInformace*<br/>
pro Stav indikátoru průběhu. Možné hodnoty najdete v části s poznámkami.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, `CTaskDialog` Pokud je již zobrazeno a má indikátor průběhu běžícího textu.

V následující tabulce jsou uvedeny možné hodnoty pro *nInformace*. Ve všech těchto případech indikátor průběhu bude plnit běžnou barvou, dokud nedosáhne určené pozice zastavení. V tomto okamžiku změní barvu na základě stavu.

|||
|-|-|
|PBST_NORMAL|Po vyplňování indikátoru průběhu se `CTaskDialog` nezmění barva pruhu. Ve výchozím nastavení je obvyklá barva zelená.|
|PBST_ERROR|Po vyplňování indikátoru průběhu se `CTaskDialog` změní barva pruhu na barvu chyby. Ve výchozím nastavení je to červené.|
|PBST_PAUSED|Po vyplňování indikátoru průběhu se `CTaskDialog` změní barva pruhu na pozastavenou barvu. Ve výchozím nastavení je to žlutá.|

Můžete nastavit, kde se indikátor průběhu zastaví pomocí [objektu CTaskDialog:: SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setradiobuttonoptions"></a>Objektu CTaskDialog:: SetRadioButtonOptions

Povolí nebo zakáže přepínač.

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
pro ID ovládacího prvku přepínač

*bEnabled*<br/>
pro TRUE pro povolení přepínače; FALSE, pokud chcete zakázat přepínač.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěte, pokud *nRadioButtonID* není platným identifikátorem pro přepínač.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>Objektu CTaskDialog:: SetVerificationCheckbox

Nastaví zaškrtnuté políčko ověřování.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
pro TRUE, pokud má být zaškrtnuto políčko ověřování při `CTaskDialog` zobrazení; FALSE, pokud má být políčko ověření při `CTaskDialog` zobrazení nevybrané.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>Objektu CTaskDialog:: SetVerificationCheckboxText

Nastaví text, který se zobrazí napravo od zaškrtávacího políčka ověření.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parametry

*strVerificationText*<br/>
pro Text, který tato metoda zobrazuje vedle zaškrtávacího políčka pro ověření.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makrem [](diagnostic-services.md#ensure) zajistěit, pokud je tato `CTaskDialog` instance třídy již zobrazena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>Objektu CTaskDialog:: SetWindowTitle

Nastaví název `CTaskDialog`.

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parametry

*strWindowTitle*<br/>
pro Nový název pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="showdialog"></a>Objektu CTaskDialog:: ShowDialog

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

*strContent*<br/>
pro Řetězec, který má být použit pro obsah `CTaskDialog`.

*strMainInstruction*<br/>
pro Hlavní instrukce pro `CTaskDialog`.

*strTitle*<br/>
pro Název `CTaskDialog`.

*nIDCommandControlsFirst*<br/>
pro ID řetězce prvního příkazu

*nIDCommandControlsLast*<br/>
pro ID řetězce posledního příkazu

*nCommonButtons*<br/>
pro Maska tlačítek, která se mají přidat do `CTaskDialog`.

*nTaskDialogOptions*<br/>
pro Sada možností, které se mají použít pro `CTaskDialog`.

*strFooter*<br/>
pro Řetězec, který má být použit jako zápatí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které odpovídá výběru provedenému uživatelem.

### <a name="remarks"></a>Poznámky

Tato statická metoda umožňuje vytvořit instanci `CTaskDialog` třídy bez explicitního `CTaskDialog` vytvoření objektu ve vašem kódu. Vzhledem k tomu, `CTaskDialog` že není k dispozici žádný objekt, nelze volat `CTaskDialog` žádné jiné metody, pokud použijete `CTaskDialog` tuto metodu k zobrazení uživatele.

Tato metoda vytvoří ovládací prvky příkazového tlačítka pomocí dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými identifikátory řetězců. Tato metoda přidá ovládací prvek příkazové tlačítko pro každou platnou položku v tabulce řetězců mezi *nIDCommandControlsFirst* a *nCommandControlsLast*(včetně). Pro toto příkazové tlačítko ovládací prvky je řetězec v tabulce String titulkem ovládacího prvku a ID řetězce je ID ovládacího prvku.

Seznam platných možností naleznete v tématu [objektu CTaskDialog:: SetOptions](#setoptions) .

Zavře, když uživatel vybere společné tlačítko, ovládací prvek odkaz na příkazy nebo `CTaskDialog`zavře. `CTaskDialog` Vrácená hodnota je identifikátor, který označuje, jak uživatel zavřel dialogové okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>Objektu CTaskDialog:: TaskDialogCallback

Rozhraní volá tuto metodu v reakci na různé zprávy systému Windows.

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

*HWND*<br/>
pro Popisovač `m_hWnd` struktury`CTaskDialog`pro.

*uNotification*<br/>
pro Kód oznámení, který určuje vygenerovanou zprávu.

*wParam*<br/>
pro Další informace o této zprávě

*lParam*<br/>
pro Další informace o této zprávě

*dwRefData*<br/>
pro Ukazatel na `CTaskDialog` objekt, na který se vztahuje zpráva zpětného volání.

### <a name="return-value"></a>Návratová hodnota

Závisí na konkrétním kódu oznámení. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Výchozí implementace `TaskDialogCallback` zpracuje konkrétní zprávu a pak zavolá příslušnou metodu [třídy objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Například v reakci na zprávu `TaskDialogCallback` TDN_BUTTON_CLICKED volá [objektu CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick).

Hodnoty pro *wParam* a *lParam* závisí na konkrétní generované zprávě. Je možné, že některé z těchto hodnot jsou prázdné. V následující tabulce jsou uvedena výchozí oznámení, která jsou podporována a jaké hodnoty *wParam* a *lParam* představují. Pokud přepíšete tuto metodu v odvozené třídě, měli byste implementovat kód zpětného volání pro každou zprávu v následující tabulce.

|Zpráva oznámení|*wParam* Osa|*lParam* Osa|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nepoužívá se.|Nepoužívá se.|
|TDN_NAVIGATED|Nepoužívá se.|Nepoužívá se.|
|TDN_BUTTON_CLICKED|ID ovládacího prvku příkazového tlačítka|Nepoužívá se.|
|TDN_HYPERLINK_CLICKED|Nepoužívá se.|Struktura [LPCWSTR](/windows/win32/WinProg/windows-data-types) , která obsahuje odkaz.|
|TDN_TIMER|Doba v milisekundách od `CTaskDialog` jejího vytvoření nebo resetování časovače.|Nepoužívá se.|
|TDN_DESTROYED|Nepoužívá se.|Nepoužívá se.|
|TDN_RADIO_BUTTON_CLICKED|ID přepínacího tlačítka|Nepoužívá se.|
|TDN_DIALOG_CONSTRUCTED|Nepoužívá se.|Nepoužívá se.|
|TDN_VERIFICATION_CLICKED|1, pokud je zaškrtávací políčko zaškrtnuto, 0, pokud není.|Nepoužívá se.|
|TDN_HELP|Nepoužívá se.|Nepoužívá se.|
|TDN_EXPANDO_BUTTON_CLICKED|0, pokud je rozbalená oblast rozšíření; nenulová, pokud je zobrazený text rozšíření.|Nepoužívá se.|

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Návod: Přidání objektu CTaskDialog do aplikace](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
