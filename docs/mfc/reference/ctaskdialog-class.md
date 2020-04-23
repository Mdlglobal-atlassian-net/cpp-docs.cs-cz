---
title: Třída CTaskDialog
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
ms.openlocfilehash: 79f52d275d360cf8447b8977b8196ea5f95eacd8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752281"
---
# <a name="ctaskdialog-class"></a>Třída CTaskDialog

Automaticky otevírané dialogové okno, které funguje jako okno se zprávou, ale může uživateli zobrazit další informace. Obsahuje `CTaskDialog` také funkce pro shromažďování informací od uživatele.

## <a name="syntax"></a>Syntaxe

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Vytvoří `CTaskDialog` objekt.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Přidá ovládací prvek příkazového tlačítka do pole `CTaskDialog`.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Přidá k souboru `CTaskDialog`.|
|[CTaskDialog::Příkaz ClickCommandControl](#clickcommandcontrol)|Klikne na ovládací prvek příkazového tlačítka nebo na běžné tlačítko programově.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Na přepínací tlačítko klikne programově.|
|[CTaskDialog::DoModální](#domodal)|Zobrazí `CTaskDialog`soubor .|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Načte počet běžných tlačítek, která jsou k dispozici.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Převede standardní tlačítko systému Windows na `CTaskDialog` běžný typ tlačítka přidružený ke třídě.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Převede jeden z běžných typů `CTaskDialog` tlačítek přidružených ke třídě na standardní tlačítko systému Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Vrátí příznaky možností `CTaskDialog`pro tento .|
|[CtaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Vrátí vybraný ovládací prvek příkazového tlačítka.|
|[CtaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Vrátí vybrané přepínací tlačítko.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Načte stav zaškrtávacího políčka ověření.|
|[Ctítdialogové okno::Ovládací prvek IsCommandControlpovolen](#iscommandcontrolenabled)|Určuje, zda je povolen ovládací prvek příkazového tlačítka nebo běžné tlačítko.|
|[CtaskDialog::isRadioButtonEnabled](#isradiobuttonenabled)|Určuje, zda je přepínací tlačítko povoleno.|
|[CtaskDialog::IsSupported](#issupported)|Určuje, zda počítač se spuštěnou `CTaskDialog`aplikací podporuje program .|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Přidá ovládací prvky příkazového tlačítka pomocí dat z tabulky řetězců.|
|[CTaskDialog::Načíst přepínače](#loadradiobuttons)|Přidá přepínací tlačítka pomocí dat z tabulky řetězců.|
|[CtaskDialog::Přejít](#navigateto)|Přenese fokus na jiný `CTaskDialog`.|
|[CtaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Rozhraní Framework volá tuto metodu, když uživatel klepne na ovládací prvek příkazového tlačítka.|
|[CtaskDialog::OnCreate](#oncreate)|Framework volá tuto metodu `CTaskDialog`po vytvoření .|
|[CtaskDialog::OnDestroy](#ondestroy)|Framework volá tuto metodu bezprostředně `CTaskDialog`před zničením .|
|[CtaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Rozhraní Framework volá tuto metodu, když uživatel klepne na tlačítko rozšíření.|
|[CtaskDialog::OnHelp](#onhelp)|Rozhraní Framework volá tuto metodu, když uživatel požaduje pomoc.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Rozhraní Framework volá tuto metodu, když uživatel klepne na hypertextový odkaz.|
|[CTaskDialog::OnInit](#oninit)|Rozhraní Framework volá tuto `CTaskDialog` metodu při inicializování.|
|[CtaskDialog::OnnavigatePage](#onnavigatepage)|Rozhraní Framework volá tuto metodu, když uživatel přesune `CTaskDialog`fokus s ohledem na ovládací prvky na rozhraní .|
|[CtaskDialog::onRadiobuttonClick](#onradiobuttonclick)|Framework volá tuto metodu, když uživatel vybere ovládací prvek přepínacího tlačítka.|
|[CtaskDialog::OnTimer](#ontimer)|Rozhraní Framework volá tuto metodu při vypršení časovače.|
|[CTaskDialog::OnVerificationCheckboxKlepněte](#onverificationcheckboxclick)|Rozhraní Framework volá tuto metodu, když uživatel klepne na ověřovací zaškrtávací políčko.|
|[CTATDialogové okno::RemoveAllCommandControls](#removeallcommandcontrols)|Odebere všechny ovládací prvky příkazů z rozhraní `CTaskDialog`.|
|[Ctasktdialog::RemoveallRadioButtons](#removeallradiobuttons)|Odstraní všechna přepínací `CTaskDialog`tlačítka z .|
|[CTaskDialog::SetControlControlOptions](#setcommandcontroloptions)|Aktualizuje ovládací prvek příkazového tlačítka na ovládacím prvku `CTaskDialog`.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podmnožinu běžných tlačítek, která mají být povolena a vyžadují zvýšení počtu registrací.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Přidá do aplikace `CTaskDialog`tlačítka běžné tlačítka.|
|[CTaskDialog::SetContent](#setcontent)|Aktualizuje obsah . `CTaskDialog`|
|[CTaskDialog::Ovládací prvek SetDefaultCommandControl](#setdefaultcommandcontrol)|Určuje výchozí ovládací prvek příkazového tlačítka.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Určuje výchozí přepínací tlačítko.|
|[CTaskTDialog::SetDialogWidth](#setdialogwidth)|Upraví šířku `CTaskDialog`.|
|[CTaskTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizuje oblast rozšíření `CTaskDialog`oblasti .|
|[CTaskDialog::Ikona setfooter](#setfootericon)|Aktualizuje ikonu zápatí `CTaskDialog`pro .|
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizuje text v zápatí `CTaskDialog`.|
|[CTaskDialog::Ikona SetMain](#setmainicon)|Aktualizuje hlavní ikonu `CTaskDialog`aplikace .|
|[CTaskTaskDialog::Nastavit maininstruction](#setmaininstruction)|Aktualizuje hlavní instrukce `CTaskDialog`.|
|[CTaskDialog::SetOptions](#setoptions)|Konfiguruje `CTaskDialog`možnosti pro rozhraní .|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Nakonfiguruje pruh `CTaskDialog` výběru pro a přidá jej do dialogového okna.|
|[CtaskDialog::Nastavitpozici ProgressBaru](#setprogressbarposition)|Upraví pozici indikátoru průběhu.|
|[CtaskDialog::SetProgressBarRange](#setprogressbarrange)|Upraví rozsah indikátoru průběhu.|
|[CtaskDialog::SetProgressBarState](#setprogressbarstate)|Nastaví stav indikátoru průběhu a `CTaskDialog`zobrazí jej na .|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Povolí nebo zakáže přepínací tlačítko.|
|[CTaskDialog::Zaškrtávací políčko SetVerificationCheckbox](#setverificationcheckbox)|Nastaví zaškrtnutý stav ověřovacího zaškrtávacího políčka.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Nastaví text na pravé straně ověřovacího zaškrtávacího políčka.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Nastaví název `CTaskDialog`.|
|[CTaskDialog::Zobrazitdialog](#showdialog)|Vytvoří a `CTaskDialog`zobrazí .|
|[CTaskDialog::Zpětné volání aplikace TaskDialog](#taskdialogcallback)|Rozhraní Framework volá v reakci na různé zprávy systému Windows.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|`m_aButtons`|Pole ovládacích prvků příkazového tlačítka pro `CTaskDialog`rozhraní .|
|`m_aRadioButtons`|Pole ovládacích prvků přepínacích tlačítek pro `CTaskDialog`rozhraní .|
|`m_bVerified`|`TRUE`označuje, že je zaškrtnuto ověřovací políčko; `FALSE` znamená, že tomu tak není.|
|`m_footerIcon`|Ikona v zápatí `CTaskDialog`.|
|`m_hWnd`|Úchyt k `CTaskDialog`oknu pro .|
|`m_mainIcon`|Hlavní ikona . `CTaskDialog`|
|`m_nButtonDisabled`|Maska, která označuje, která z běžných tlačítek jsou zakázána.|
|`m_nButtonElevation`|Maska, která označuje, která z běžných tlačítek vyžadují zvýšení počtu stop.|
|`m_nButtonId`|ID vybraného ovládacího prvku příkazového tlačítka.|
|`m_nCommonButton`|Maska, která označuje, která běžná tlačítka jsou zobrazena na . `CTaskDialog`|
|`m_nDefaultCommandControl`|ID ovládacího prvku příkazového tlačítka, `CTaskDialog` který je vybrán při zobrazení.|
|`m_nDefaultRadioButton`|ID ovládacího prvku přepínacího `CTaskDialog` tlačítka, který je vybrán při zobrazení.|
|`m_nFlags`|Maska, která označuje `CTaskDialog`možnosti pro .|
|`m_nProgressPos`|Aktuální pozice indikátoru průběhu.  Tato hodnota musí `m_nProgressRangeMin` `m_nProgressRangeMax`být mezi a .|
|`m_nProgressRangeMax`|Maximální hodnota indikátoru průběhu.|
|`m_nProgressRangeMin`|Minimální hodnota pro indikátor průběhu.|
|`m_nProgressState`|Stav indikátoru průběhu. Další informace naleznete v tématu [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|ID vybraného ovládacího prvku přepínacího tlačítka.|
|`m_nWidth`|Šířka `CTaskDialog` v pixelech.|
|`m_strCollapse`|Řetězec `CTaskDialog` zobrazí na pravé straně rozšiřujícího pole, když rozšířené informace jsou skryté.|
|`m_strContent`|Řetězec obsahu . `CTaskDialog`|
|`m_strExpand`|Řetězec `CTaskDialog` se zobrazí napravo od rozšiřujícího pole při zobrazení rozbalených informací.|
|`m_strFooter`|Zápatí `CTaskDialog`.|
|`m_strInformation`|Rozšířené informace pro `CTaskDialog`.|
|`m_strMainInstruction`|Hlavní instrukce `CTaskDialog`.|
|`m_strTitle`|Název `CTaskDialog`.|
|`m_strVerification`|Řetězec, který `CTaskDialog` se zobrazí napravo od ověřovacího zaškrtávacího políčka.|

## <a name="remarks"></a>Poznámky

Třída `CTaskDialog` nahrazuje standardní okno se zprávou systému Windows a má další funkce, jako jsou nové ovládací prvky pro shromažďování informací od uživatele. Tato třída je v knihovně knihovny Knihovny MFC v sadě Visual Studio 2010 a novější. Je `CTaskDialog` k dispozici počínaje systémem Windows Vista. Starší verze systému Windows `CTaskDialog` nemohou objekt zobrazit. Slouží `CTaskDialog::IsSupported` k určení za běhu, zda může aktuální uživatel zobrazit dialogové okno úlohy. Standardní okno se zprávou systému Windows je stále podporováno.

K `CTaskDialog` dispozici je pouze při vytváření aplikace pomocí knihovny Unicode.

Má `CTaskDialog` dva různé konstruktory. Jeden konstruktor umožňuje zadat dvě příkazová tlačítka a maximálně šest běžných ovládacích prvků tlačítek. Po vytvoření příkazových tlačítek můžete `CTaskDialog`přidat další příkazová tlačítka. Druhý konstruktor nepodporuje žádná příkazová tlačítka, ale můžete přidat neomezený počet běžných ovládacích prvků tlačítek. Další informace o konstruktorech naleznete v tématu [CTaskDialog::CTaskDialog](#ctaskdialog).

Následující obrázek znázorňuje ukázku `CTaskDialog` pro ilustraci umístění některých ovládacích prvků.

![Příklad ctaskdialog](../../mfc/reference/media/ctaskdialogsample.png "Příklad ctaskdialog") <br/>
Ukázka ctaskdialog

## <a name="requirements"></a>Požadavky

**Minimální požadovaný operační systém:** Windows Vista

**Záhlaví:** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTaskDialog::AddCommandControl

Přidá do pole `CTaskDialog`.

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nPříkaz ControlID*<br/>
[v] Identifikační číslo řídicího systému.

*strTitulek*<br/>
[v] Řetězec, který `CTaskDialog` se zobrazí uživateli. Tento řetězec slouží k vysvětlení účelu příkazu.

*bPovoleno*<br/>
[v] Logický parametr, který označuje, zda je nové tlačítko povoleno nebo zakázáno.

*bVyžaduje zvýšení oprávnění*<br/>
[v] Logický parametr, který označuje, zda příkaz vyžaduje zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

Může `CTaskDialog Class` zobrazit neomezený počet ovládacích prvků příkazového tlačítka. Pokud však `CTaskDialog` ovládací prvky příkazového tlačítka zobrazí, může zobrazit maximálně šest tlačítek. Pokud `CTaskDialog` a nemá žádné ovládací prvky příkazového tlačítka, může zobrazit neomezený počet tlačítek.

Když uživatel vybere ovládací prvek příkazového tlačítka, `CTaskDialog` zavře se. Pokud aplikace zobrazí dialogové okno pomocí [CTaskDialog::DoModal](#domodal), `DoModal` vrátí *příkaz nCommandControlID* vybraného ovládacího prvku příkazového tlačítka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTaskDialog::AddRadioButton

Přidá k souboru `CTaskDialog`.

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[v] Identifikační číslo přepínacího tlačítka.

*strTitulek*<br/>
[v] Řetězec, který `CTaskDialog` se zobrazí vedle přepínacího tlačítka.

*bPovoleno*<br/>
[v] Logický parametr, který označuje, zda je přepínač povolen.

### <a name="remarks"></a>Poznámky

Přepínací tlačítka pro [třídu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) umožňují shromažďovat informace od uživatele. Pomocí funkce [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) určete, které přepínací tlačítko je vybráno.

Nevyžaduje, `CTaskDialog` aby parametry *nRadioButtonID* byly jedinečné pro každé přepínací tlačítko. Však může dojít k neočekávanému chování, pokud nepoužijete odlišný identifikátor pro každé přepínací tlačítko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTaskDialog::Příkaz ClickCommandControl

Klikne na ovládací prvek příkazového tlačítka nebo na běžné tlačítko programově.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nPříkaz ControlID*<br/>
[v] ID příkazu ovládacího prvku, na který chcete klepnout.

### <a name="remarks"></a>Poznámky

Tato metoda generuje TDM_CLICK_BUTTON zpráv systému Windows.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTaskDialog::ClickRadioButton

Na přepínací tlačítko klikne programově.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[v] ID přepínacího tlačítka pro klepnutí.

### <a name="remarks"></a>Poznámky

Tato metoda generuje TDM_CLICK_RADIO_BUTTON zpráv systému Windows.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>CTaskDialog::CTaskDialog

Vytvoří instanci [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

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
[v] Řetězec, který chcete použít `CTaskDialog`pro obsah .

*strMainInstruction*<br/>
[v] Hlavní instrukce `CTaskDialog`.

*strTitle*<br/>
[v] Název `CTaskDialog`.

*nCommonTlačítka*<br/>
[v] Maska běžných tlačítek, která `CTaskDialog`chcete přidat do aplikace .

*nMožnosti dialogu úloh*<br/>
[v] Sada možností, které chcete `CTaskDialog`použít pro .

*strFooter*<br/>
[v] Řetězec, který chcete použít jako zápatí.

*nIDCommandControlsFirst*<br/>
[v] ID řetězce prvního příkazu.

*nIDCommandControlsLast*<br/>
[v] ID řetězce posledního příkazu.

### <a name="remarks"></a>Poznámky

Existují dva způsoby, které `CTaskDialog` můžete přidat do aplikace. Prvním způsobem je použít jeden z konstruktorů `CTaskDialog` k vytvoření a zobrazení pomocí [CTaskDialog::DoModal](#domodal). Druhým způsobem je použití statické funkce [CTaskDialog::ShowDialog](#showdialog), která `CTaskDialog` umožňuje zobrazit `CTaskDialog` a bez explicitního vytvoření objektu.

Druhý konstruktor vytvoří ovládací prvky příkazového tlačítka pomocí dat ze souboru prostředků aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými ID řetězce. Tato metoda přidá ovládací prvek příkazového tlačítka pro každou platnou položku v tabulce řetězců mezi *nIDCommandControlsFirst* a *nCommandControlsLast*, včetně. Pro tyto ovládací prvky příkazového tlačítka je řetězec v tabulce řetězců titulek ovládacího prvku a ID řetězce je ID ovládacího prvku.

Seznam platných možností naleznete v tématu [CTaskDialog::SetOptions.](#setoptions)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTaskDialog::DoModální

Ukazuje `CTaskDialog` a dělá to modální.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hRodič*<br/>
[v] Nadřazené `CTaskDialog`okno pro .

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které odpovídá výběru provedenému uživatelem.

### <a name="remarks"></a>Poznámky

Zobrazí tuto instanci [ctaskdialog](../../mfc/reference/ctaskdialog-class.md). Aplikace pak čeká na uživatele zavřít dialogové okno.

Zavře `CTaskDialog` se, když uživatel vybere společné tlačítko, ovládací prvek propojení `CTaskDialog`příkazů nebo zavře . Vrácená hodnota je identifikátor, který označuje, jak uživatel zavřel dialogové okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTaskDialog::GetCommonButtonCount

Načte počet běžných tlačítek.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet běžných tlačítek k dispozici.

### <a name="remarks"></a>Poznámky

Běžná tlačítka jsou výchozí tlačítka, která poskytujete [ctaskdialog::CTaskDialog](#ctaskdialog). [Třída CTaskDialog](../../mfc/reference/ctaskdialog-class.md) zobrazuje tlačítka v dolní části dialogového okna.

Výčet tlačítek je k dispozici v CommCtrl.h.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTaskDialog::GetCommonButtonFlag

Převede standardní tlačítko systému Windows na běžný typ tlačítka přidružený ke [třídě CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[v] Standardní hodnota tlačítka systému Windows.

### <a name="return-value"></a>Návratová hodnota

Hodnota odpovídající `CTaskDialog` společné tlačítko. Pokud neexistuje žádné odpovídající společné tlačítko, tato metoda vrátí 0.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTaskDialog::GetCommonButtonId

Převede jeden z běžných typů tlačítek přidružených ke [třídě CTaskDialog](../../mfc/reference/ctaskdialog-class.md) na standardní tlačítko systému Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parametry

*nPříznak*<br/>
[v] Běžný typ tlačítka přidružený `CTaskDialog` ke třídě.

### <a name="return-value"></a>Návratová hodnota

Hodnota odpovídajícího standardního tlačítka systému Windows. Pokud neexistuje žádné odpovídající tlačítko systému Windows, metoda vrátí 0.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTaskDialog::GetOptions

Vrátí příznaky možností `CTaskDialog`pro tento .

```
int GetOptions() const;
```

### <a name="return-value"></a>Návratová hodnota

Příznaky pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Další informace o možnostech, které jsou k dispozici [pro třídu CTaskDialog](../../mfc/reference/ctaskdialog-class.md), naleznete v tématu [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CtaskDialog::GetSelectedCommandControlID

Vrátí vybraný ovládací prvek příkazového tlačítka.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID aktuálně vybraného ovládacího prvku příkazového tlačítka.

### <a name="remarks"></a>Poznámky

Tuto metodu není třeba použít k načtení ID příkazového tlačítka, které uživatel vybral. Toto ID je vráceno [buď CTaskDialog::DoModal](#domodal) nebo [CTaskDialog::ShowDialog](#showdialog).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CtaskDialog::GetSelectedRadioButtonID

Vrátí vybrané přepínací tlačítko.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Návratová hodnota

ID vybraného přepínacího tlačítka.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete použít po zavření dialogového okna uživatelem k načtení vybraného přepínacího tlačítka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTaskDialog::GetVerificationCheckboxState

Načte stav zaškrtávacího políčka ověření.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zaškrtávací políčko zaškrtnuto, NEPRAVDA, pokud není.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>Ctítdialogové okno::Ovládací prvek IsCommandControlpovolen

Určuje, zda je ovládací prvek příkazového tlačítka nebo tlačítko povolen.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nPříkaz ControlID*<br/>
[v] ID ovládacího prvku příkazového tlačítka nebo tlačítka k testování.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je ovládací prvek povolen, NEPRAVDA, pokud není.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete použít k určení dostupnosti ovládacích prvků `CTaskDialog` příkazového tlačítka a běžných tlačítek třídy*.

Pokud *nCommandControlID* není platný identifikátor pro `CTaskDialog` společné tlačítko nebo ovládací prvek příkazového tlačítka, tato metoda vyvolá výjimku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CtaskDialog::isRadioButtonEnabled

Určuje, zda je přepínací tlačítko povoleno.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[v] ID přepínacího tlačítka k testování.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je přepínací tlačítko povoleno, NEPRAVDA, pokud není.

### <a name="remarks"></a>Poznámky

Pokud *nRadioButtonID* není platný identifikátor pro přepínací tlačítko, tato metoda vyvolá výjimku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CtaskDialog::IsSupported

Určuje, zda počítač se spuštěnou `CTaskDialog`aplikací podporuje program .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud počítač `CTaskDialog`podporuje ; FALSE jinak.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete určit za běhu, pokud počítač, ve který je spuštěna vaše aplikace, podporuje třídu. `CTaskDialog` Pokud počítač nepodporuje `CTaskDialog`, měli byste zadat jiný způsob sdělování informací uživateli. Aplikace se zhroutí, pokud se `CTaskDialog` pokusí použít v počítači, který nepodporuje třídu. `CTaskDialog`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>CTaskDialog::LoadCommandControls

Přidá ovládací prvky příkazového tlačítka pomocí dat z tabulky řetězců.

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parametry

*nIDCommandControlsFirst*<br/>
[v] ID řetězce prvního příkazu.

*nIDCommandControlsLast*<br/>
[v] ID řetězce posledního příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří ovládací prvky příkazového tlačítka pomocí dat ze souboru prostředků aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými ID řetězce. Nové ovládací prvky příkazového tlačítka přidané pomocí této metody používají řetězec pro titulek ovládacího prvku a ID řetězce pro ID ovládacího prvku. Rozsah vybraných řetězců poskytuje *nIDCommandControlsFirst* a *nCommandControlsLast*, včetně. Pokud je prázdná položka v rozsahu, metoda nepřidá ovládací prvek příkazového tlačítka pro tuto položku.

Ve výchozím nastavení jsou nové ovládací prvky příkazového tlačítka povoleny a nevyžadují zvýšení oprávnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTaskDialog::Načíst přepínače

Přidá ovládací prvky přepínacích tlačítek pomocí dat z tabulky řetězců.

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parametry

*nIDRadioButtonsPrvní*<br/>
[v] ID řetězce prvního přepínacího tlačítka.

*nIDRadioButtonsLast*<br/>
[v] ID řetězce posledního přepínacího tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří přepínací tlačítka pomocí dat ze souboru prostředků aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými ID řetězce. Nová přepínací tlačítka přidaná pomocí této metody používají řetězec pro titulek přepínacího tlačítka a ID řetězce pro ID přepínacího tlačítka. Rozsah vybraných řetězců poskytuje *nIDRadioButtonsFirst* a *nRadioButtonsLast*, včetně. Pokud je prázdná položka v rozsahu, metoda nepřidá přepínací tlačítko pro tuto položku.

Ve výchozím nastavení jsou povolena nová přepínací tlačítka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CtaskDialog::Přejít

Přenese fokus na jiný `CTaskDialog`.

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parametry

*oTaskDialog*<br/>
[v] Který `CTaskDialog` přijímá zaměření.

### <a name="remarks"></a>Poznámky

Tato metoda skryje proud `CTaskDialog` při zobrazení *oTaskDialog*. *OTaskDialog* se zobrazí ve stejném umístění `CTaskDialog`jako aktuální .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CtaskDialog::OnCommandControlClick

Rozhraní Framework volá tuto metodu, když uživatel klepne na ovládací prvek příkazového tlačítka.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nPříkaz ControlID*<br/>
[v] ID ovládacího prvku příkazového tlačítka, který uživatel vybral.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CtaskDialog::OnCreate

Framework volá tuto metodu `CTaskDialog`po vytvoření .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>CtaskDialog::OnDestroy

Framework volá tuto metodu bezprostředně `CTaskDialog`před zničením .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CtaskDialog::OnExpandButtonClick

Rozhraní Framework volá tuto metodu, když uživatel klepne na tlačítko rozšíření.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parametry

*bRozbalen*<br/>
[v] Nenulová hodnota označuje, že jsou zobrazeny další informace; 0 označuje, že další informace jsou skryté.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CtaskDialog::OnHelp

Rozhraní Framework volá tuto metodu, když uživatel požaduje pomoc.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTaskDialog::OnHyperlinkClick

Rozhraní Framework volá tuto metodu, když uživatel klepne na hypertextový odkaz.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parametry

*strHref*<br/>
[v] Řetězec, který představuje hypertextový odkaz.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Tato metoda volá [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) před vrátí S_OK.

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTaskDialog::OnInit

Rozhraní Framework volá tuto `CTaskDialog` metodu při inicializování.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CtaskDialog::OnnavigatePage

Framework volá tuto metodu v reakci na [metodu CTaskDialog::NavigateTo.](#navigateto)

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CtaskDialog::onRadiobuttonClick

Framework volá tuto metodu, když uživatel vybere ovládací prvek přepínacího tlačítka.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[v] ID ovládacího prvku přepínacího tlačítka, na který uživatel klepnul.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CtaskDialog::OnTimer

Rozhraní Framework volá tuto metodu při vypršení časovače.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parametry

*lČas*<br/>
[v] Čas v milisekundách od `CTaskDialog` vytvoření nebo resetování časovače.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTaskDialog::OnVerificationCheckboxKlepněte

Rozhraní Framework volá tuto metodu, když uživatel klepne na ověřovací zaškrtávací políčko.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bZaškrtnuto*<br/>
[v] PRAVDA označuje, že je zaškrtnuté políčko ověření; FALSE označuje, že není.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí S_OK.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě implementovat vlastní chování.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTATDialogové okno::RemoveAllCommandControls

Odebere všechny ovládací prvky `CTaskDialog`příkazového tlačítka z rozhraní .

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>Ctasktdialog::RemoveallRadioButtons

Odstraní všechna přepínací `CTaskDialog`tlačítka z .

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTaskDialog::SetControlControlOptions

Aktualizuje ovládací prvek příkazového tlačítka na ovládacím prvku `CTaskDialog`.

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nPříkaz ControlID*<br/>
[v] ID ovládacího prvku příkazu aktualizovat.

*bPovoleno*<br/>
[v] Logický parametr, který označuje, zda je zadaný ovládací prvek příkazového tlačítka povolen nebo zakázán.

*bVyžaduje zvýšení oprávnění*<br/>
[v] Logický parametr, který označuje, zda zadaný ovládací prvek příkazového tlačítka vyžaduje zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete změnit, zda je ovládací prvek příkazového `CTaskDialog` tlačítka povolen nebo vyžaduje zvýšení po jeho přidání do třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTaskDialog::SetCommonButtonOptions

Aktualizuje podmnožinu běžných tlačítek, která mají být povolena a vyžadují zvýšení počtu registrací.

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nMaskdisabledButton*<br/>
[v] Maska pro běžné tlačítka zakázat.

*nElevationButtonMask*<br/>
[v] Maska pro běžná tlačítka, která vyžadují zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

Běžná tlačítka, která jsou k dispozici pro instanci [třídy CTaskDialog,](../../mfc/reference/ctaskdialog-class.md) můžete nastavit pomocí konstruktoru [CTaskDialog::CTaskDialog](#ctaskdialog) a metody [CTaskDialog::SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`nepodporuje přidávání nových běžných tlačítek.

Pokud použijete tuto metodu zakázat nebo zvýšit společné `CTaskDialog`tlačítko, které není k dispozici pro tento , tato metoda vyvolá výjimku pomocí [zajistit](diagnostic-services.md#ensure) makro.

Tato metoda umožňuje jakékoli tlačítko, `CTaskDialog` které je k dispozici, ale není v *nDisabledButtonMask*, i v případě, že byl dříve zakázán. Tato metoda zachází zvýšení podobným způsobem: zaznamenává běžné tlačítka jako nevyžadující zvýšení, pokud společné tlačítko je k dispozici, ale není součástí *nElevationButtonMask*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTaskDialog::SetCommonButtons

Přidá do aplikace `CTaskDialog`tlačítka běžné tlačítka.

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nMaska tlačítka*<br/>
[v] Maska tlačítek, která chcete `CTaskDialog`přidat do .

*nMaskdisabledButton*<br/>
[v] Maska tlačítek zakázat.

*nElevationButtonMask*<br/>
[v] Maska tlačítek, které vyžadují zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

Tuto metodu nelze volat po vytvoření okna `CTaskDialog` zobrazení pro tuto instanci třídy. Pokud tak učiníte, tato metoda vyvolá výjimku.

Tlačítka označená *nButtonMask* přepíší všechna běžná `CTaskDialog`tlačítka, která byla dříve přidána do aplikace . K dispozici jsou pouze tlačítka uvedená v *nButtonMask.*

Pokud *buď nDisabledButtonMask* nebo *nElevationButtonMask* obsahují tlačítko, které není v *nButtonMask*, tato metoda vyvolá výjimku pomocí [zajistit](diagnostic-services.md#ensure) makro.

Ve výchozím nastavení jsou všechna běžná tlačítka povolena a nevyžadují zvýšení oprávnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>CTaskDialog::SetContent

Aktualizuje obsah . `CTaskDialog`

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
[v] Řetězec, který se má uživateli zobrazit.

### <a name="remarks"></a>Poznámky

Obsah třídy `CTaskDialog` je text, který se zobrazí uživateli v hlavní části dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTaskDialog::Ovládací prvek SetDefaultCommandControl

Určuje výchozí ovládací prvek příkazového tlačítka.

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nPříkaz ControlID*<br/>
[v] ID ovládacího prvku příkazového tlačítka má být výchozí.

### <a name="remarks"></a>Poznámky

Výchozí ovládací prvek příkazového tlačítka je `CTaskDialog` ovládací prvek, který je vybrán při prvním zobrazení uživateli.

Tato metoda vyvolá výjimku, pokud nemůže najít ovládací prvek příkazového tlačítka určený *nCommandControlID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTaskDialog::SetDefaultRadioButton

Určuje výchozí přepínací tlačítko.

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[v] ID přepínacího tlačítka je výchozí.

### <a name="remarks"></a>Poznámky

Výchozí přepínací tlačítko je tlačítko, které je vybráno při `CTaskDialog` prvním zobrazení uživateli.

Tato metoda vyvolá výjimku, pokud nemůže najít přepínací tlačítko určené *nRadioButtonID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>CTaskTDialog::SetDialogWidth

Upraví šířku `CTaskDialog`.

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
[v] Šířka dialogového okna v obrazových bodech.

### <a name="remarks"></a>Poznámky

Parametr *nWidth* musí být větší nebo roven 0. Jinak tato metoda vyvolá výjimku.

Pokud je *hodnota nWidth* nastavena na hodnotu 0, tato metoda nastaví dialogové okno na výchozí velikost.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>CTaskTaskDialog::SetExpansionArea

Aktualizuje oblast rozšíření `CTaskDialog`oblasti .

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parametry

*strExpandedInformace*<br/>
[v] Řetězec, který `CTaskDialog` se zobrazí v hlavním těle dialogového okna, když uživatel klepne na tlačítko pro rozšíření.

*strCollapsedLabel*<br/>
[v] Řetězec, který `CTaskDialog` se zobrazí vedle rozšiřujícího tlačítka při sbalení rozbalené oblasti.

*strExpandedLabel*<br/>
[v] Řetězec, který `CTaskDialog` se zobrazí vedle rozšiřujícího tlačítka při zobrazení rozšířené oblasti.

### <a name="remarks"></a>Poznámky

Oblast rozšíření třídy `CTaskDialog` umožňuje poskytnout uživateli další informace. Oblast rozšíření se nachází v `CTaskDialog`hlavní části , která se nachází bezprostředně pod názvem a řetězcem obsahu.

`CTaskDialog` Při prvním zobrazení nezobrazuje rozbalené informace a `strCollapsedLabel` umístí se vedle rozšiřujícího tlačítka. Když uživatel klepne na tlačítko `CTaskDialog` rozšíření, zobrazí *strExpandedInformation* a změní popisek *na strExpandedLabel*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTaskDialog::Ikona setfooter

Aktualizuje ikonu zápatí `CTaskDialog`aplikace .

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parametry

*hFooterIcon*<br/>
[v] Nová ikona pro `CTaskDialog`.

*lpszFooterIkona*<br/>
[v] Nová ikona pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Ikona zápatí se zobrazí v dolní části [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Může mít přidružený text zápatí. Text zápatí můžete změnit pomocí [ctaskdialog::SetFooterText](#setfootertext).

Tato metoda vyvolá výjimku s makro `CTaskDialog` [ZAJISTIT,](diagnostic-services.md#ensure) pokud je zobrazen nebo vstupní parametr je NULL.

Ikona `CTaskDialog` `HICON` zápatí `LPCWSTR` může přijmout pouze ikonu zápatí. To je nakonfigurováno nastavením možnosti TDF_USE_HICON_FOOTER v konstruktoru nebo [CTaskDialog::SetOptions](#setoptions). Ve výchozím `CTaskDialog` nastavení je `LPCWSTR` nakonfigurován pro použití jako vstupní typ pro ikonu zápatí. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodného typu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTaskDialog::SetFooterText

Aktualizuje text v zápatí `CTaskDialog`.

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parametry

*strFooterText*<br/>
[v] Nový text pro zápatí.

### <a name="remarks"></a>Poznámky

Ikona zápatí se zobrazí vedle textu zápatí v dolní části . `CTaskDialog` Ikonu zápatí můžete změnit pomocí [ctaskdialog::SetFooterIcon](#setfootericon).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTaskDialog::Ikona SetMain

Aktualizuje hlavní ikonu `CTaskDialog`aplikace .

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parametry

*hMainIcon*<br/>
[v] Nová ikona.

*lpszMainIcon*<br/>
[v] Nová ikona.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makro `CTaskDialog` [ZAJISTIT,](diagnostic-services.md#ensure) pokud je zobrazen nebo vstupní parametr je NULL.

A `CTaskDialog` může přijmout `HICON` `LPCWSTR` pouze nebo jako hlavní ikonu. Můžete to nakonfigurovat nastavením možnosti TDF_USE_HICON_MAIN v konstruktoru nebo v metodě [CTaskDialog::SetOptions.](#setoptions) Ve výchozím `CTaskDialog` nastavení je `LPCWSTR` nakonfigurován pro použití jako vstupní typ pro hlavní ikonu. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodného typu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTaskTaskDialog::Nastavit maininstruction

Aktualizuje hlavní instrukce `CTaskDialog`.

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parametry

*strInstructions*<br/>
[v] Nová hlavní instrukce.

### <a name="remarks"></a>Poznámky

Hlavní instrukce třídy `CTaskDialog` je text zobrazený uživateli velkým tučným písmem. Nachází se v dialogovém okně pod záhlavím.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>CTaskDialog::SetOptions

Konfiguruje `CTaskDialog`možnosti pro rozhraní .

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parametry

*nOptionFlag*<br/>
[v] Sada příznaků, které mají `CTaskDialog`být pro .

### <a name="remarks"></a>Poznámky

Tato metoda vymaže `CTaskDialog`všechny aktuální možnosti pro . Chcete-li zachovat aktuální možnosti, musíte je nejprve načíst pomocí [CTaskDialog::GetOptions](#getoptions) a zkombinovat je s možnostmi, které chcete nastavit.

V následující tabulce jsou uvedeny všechny platné možnosti.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Povolí hypertextové `CTaskDialog`odkazy v aplikaci .|
|TDF_USE_HICON_MAIN|`CTaskDialog` Nakonfiguruje `HICON` použití a pro hlavní ikonu. Alternativou je použití `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|`CTaskDialog` Nakonfiguruje `HICON` použití ikony zápatí. Alternativou je použití `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Umožňuje uživateli zavřít `CTaskDialog` pomocí klávesnice nebo pomocí ikony v pravém horním rohu dialogového okna, i když není povoleno tlačítko **Storno.** Pokud tento příznak není nastaven a tlačítko **Storno** není povoleno, uživatel nemůže zavřít dialogové okno pomocí Alt+F4, klávesy Escape nebo tlačítka zavření záhlaví.|
|TDF_USE_COMMAND_LINKS|Nakonfiguruje použití ovládacích `CTaskDialog` prvků příkazového tlačítka.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Nakonfiguruje použití ovládacích `CTaskDialog` prvků příkazového tlačítka bez zobrazení ikony vedle ovládacího prvku. TDF_USE_COMMAND_LINKS TDF_USE_COMMAND_LINKS_NO_ICON přepíše.|
|TDF_EXPAND_FOOTER_AREA|Označuje, že oblast rozšíření je aktuálně rozbalena.|
|TDF_EXPANDED_BY_DEFAULT|Určuje, zda je oblast rozšíření ve výchozím nastavení rozbalena.|
|TDF_VERIFICATION_FLAG_CHECKED|Označuje, že je nyní zaškrtnuto políčko ověření.|
|TDF_SHOW_PROGRESS_BAR|Nakonfiguruje `CTaskDialog` zobrazení indikátoru průběhu.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Nakonfiguruje indikátor průběhu jako indikátor průběhu výběru. Pokud tuto možnost povolíte, je nutné nastavit TDF_SHOW_PROGRESS_BAR očekávané chování.|
|TDF_CALLBACK_TIMER|Označuje, `CTaskDialog` že interval zpětného volání je nastaven na přibližně 200 milisekund.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Nakonfiguruje `CTaskDialog` vystředěný vzhledvzhled vzhledem k nadřazenému oknu. Pokud tento příznak není `CTaskDialog` povolen, je vystředěn vzhledem k monitoru.|
|TDF_RTL_LAYOUT|Konfiguruje `CTaskDialog` rozložení čtení zprava doleva.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Označuje, že při jeho `CTaskDialog` zjevu není vybráno žádné přepínací tlačítko.|
|TDF_CAN_BE_MINIMIZED|Umožňuje uživateli minimalizovat `CTaskDialog`rozhraní . Pro podporu této `CTaskDialog` možnosti, nemůže být modální. Knihovna MFC tuto možnost nepodporuje, protože `CTaskDialog`knihovna MFC nepodporuje nemodlavou .|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTaskDialog::SetProgressBarMarquee

Nakonfiguruje pruh `CTaskDialog` výběru pro a přidá jej do dialogového okna.

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parametry

*bPovoleno*<br/>
[v] TRUE povolit pruh výběru; Nepravda, chcete-li zakázat pruh `CTaskDialog`výběru a odebrat jej z .

*nMarqueeSpeed*<br/>
[v] Celé číslo, které označuje rychlost pruhu výběru.

### <a name="remarks"></a>Poznámky

Pod hlavním textem třídy se `CTaskDialog` zobrazí pruh výběru.

Pomocí *funkce nMarqueeSpeed* nastavte rychlost pruhu výběru; větší hodnoty označují pomalejší rychlost. Hodnota 0 pro *nMarqueeSpeed* způsobí, že pruh výběru se přesune výchozí rychlostí systému Windows.

Tato metoda vyvolá výjimku s [makro zajistit,](diagnostic-services.md#ensure) pokud *nMarqueeSpeed* je menší než 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>CtaskDialog::Nastavitpozici ProgressBaru

Upraví pozici indikátoru průběhu.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
[v] Pozice pro indikátor průběhu.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s [makro zajistit,](diagnostic-services.md#ensure) pokud *nProgressPos* není v rozsahu indikátoru průběhu. Rozsah indikátorů průběhu můžete změnit pomocí [ctaskdialog::SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CtaskDialog::SetProgressBarRange

Upraví rozsah indikátoru průběhu.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
[v] Dolní mez indikátoru průběhu.

*nRozsahMax*<br/>
[v] Horní hranice indikátoru průběhu.

### <a name="remarks"></a>Poznámky

Pozice indikátoru průběhu je relativní vzhledem k *nRangeMin* a *nRangeMax*. Například pokud *nRangeMin* je 50 a *nRangeMax* je 100, pozice 75 je v polovině přes indikátor průběhu. Pomocí [ctaskdialog::SetProgressBarPosition](#setprogressbarposition) nastavte pozici indikátoru průběhu.

Chcete-li zobrazit indikátor průběhu, musí být povolena možnost TDF_SHOW_PROGRESS_BAR a TDF_SHOW_MARQUEE_PROGRESS_BAR nesmí být povolena. Tato metoda automaticky nastaví TDF_SHOW_PROGRESS_BAR a vymaže TDF_SHOW_MARQUEE_PROGRESS_BAR. Pomocí [ctaskdialog::SetOptions](#setoptions) ručně změnit možnosti pro tuto instanci [ctaskdialog třídy](../../mfc/reference/ctaskdialog-class.md).

Tato metoda vyvolá výjimku s [makro ZAJISTIT,](diagnostic-services.md#ensure) pokud *nRangeMin* není menší než *nRangeMax*. Tato metoda také vyvolá výjimku, `CTaskDialog` pokud je již zobrazen a má pruh průběhu výběru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>CtaskDialog::SetProgressBarState

Nastaví stav indikátoru průběhu a `CTaskDialog`zobrazí jej na .

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parametry

*nStát*<br/>
[v] Stav indikátoru průběhu. Možné hodnoty naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s makro `CTaskDialog` [zajistit,](diagnostic-services.md#ensure) pokud je již zobrazen a má indikátor průběhu výběru.

V následující tabulce jsou uvedeny možné hodnoty pro *nState*. Ve všech těchto případech se indikátor průběhu vyplní běžnou barvou, dokud nedosáhne určené polohy zastavení. V tomto okamžiku se změní barva na základě stavu.

|||
|-|-|
|PBST_NORMAL|Po vyplnění indikátoru `CTaskDialog` průběhu se barva pruhu nezmění. Ve výchozím nastavení je běžná barva zelená.|
|PBST_ERROR|Po vyplnění indikátoru průběhu `CTaskDialog` se barva pruhu změní na chybovou barvu. Ve výchozím nastavení je to červená.|
|PBST_PAUSED|Po vyplnění indikátoru průběhu `CTaskDialog` se barva pruhu změní na pozastavenou barvu. Ve výchozím nastavení je to žlutá.|

Můžete nastavit, kde se indikátor průběhu zastaví pomocí [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTaskDialog::SetRadioButtonOptions

Povolí nebo zakáže přepínací tlačítko.

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[v] ID ovládacího prvku přepínacího tlačítka.

*bPovoleno*<br/>
[v] TRUE pro povolení přepínacího tlačítka; False zakázat přepínací tlačítko.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s [makro ZAJISTIT,](diagnostic-services.md#ensure) pokud *nRadioButtonID* není platné ID pro přepínací tlačítko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>CTaskDialog::Zaškrtávací políčko SetVerificationCheckbox

Nastaví zaškrtnutý stav ověřovacího zaškrtávacího políčka.

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bZaškrtnuto*<br/>
[v] TRUE, aby bylo při zobrazení `CTaskDialog` zaškrtnuto políčko ověření; FALSE, aby bylo při zobrazení `CTaskDialog` zaškrtnuto políčko ověření.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTaskDialog::SetVerificationCheckboxText

Nastaví text, který se zobrazí vpravo od ověřovacího zaškrtávacího políčka.

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parametry

*strVerificationText*<br/>
[v] Text, který tato metoda zobrazí vedle ověřovacího zaškrtávacího políčka.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku s [makro zajistit,](diagnostic-services.md#ensure) pokud tato instance `CTaskDialog` třídy je již zobrazena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>CTaskDialog::SetWindowTitle

Nastaví název `CTaskDialog`.

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parametry

*strWindowTitle*<br/>
[v] Nový název pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>CTaskDialog::Zobrazitdialog

Vytvoří a `CTaskDialog`zobrazí .

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
[v] Řetězec, který chcete použít `CTaskDialog`pro obsah .

*strMainInstruction*<br/>
[v] Hlavní instrukce `CTaskDialog`.

*strTitle*<br/>
[v] Název `CTaskDialog`.

*nIDCommandControlsFirst*<br/>
[v] ID řetězce prvního příkazu.

*nIDCommandControlsLast*<br/>
[v] ID řetězce posledního příkazu.

*nCommonTlačítka*<br/>
[v] Maska tlačítek, která chcete `CTaskDialog`přidat do .

*nMožnosti dialogu úloh*<br/>
[v] Sada možností, které chcete `CTaskDialog`použít pro .

*strFooter*<br/>
[v] Řetězec, který chcete použít jako zápatí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které odpovídá výběru provedenému uživatelem.

### <a name="remarks"></a>Poznámky

Tato statická metoda umožňuje vytvořit `CTaskDialog` instanci třídy bez explicitního vytvoření objektu `CTaskDialog` v kódu. Vzhledem k `CTaskDialog` tomu, že neexistuje žádný `CTaskDialog` objekt, nelze volat žádné `CTaskDialog` jiné metody, pokud použijete tuto metodu k zobrazení uživateli.

Tato metoda vytvoří ovládací prvky příkazového tlačítka pomocí dat ze souboru prostředků aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými ID řetězce. Tato metoda přidá ovládací prvek příkazového tlačítka pro každou platnou položku v tabulce řetězců mezi *nIDCommandControlsFirst* a *nCommandControlsLast*, včetně. Pro tyto ovládací prvky příkazového tlačítka je řetězec v tabulce řetězců titulek ovládacího prvku a ID řetězce je ID ovládacího prvku.

Seznam platných možností naleznete v tématu [CTaskDialog::SetOptions.](#setoptions)

Zavře `CTaskDialog` se, když uživatel vybere společné tlačítko, ovládací prvek propojení `CTaskDialog`příkazů nebo zavře . Vrácená hodnota je identifikátor, který označuje, jak uživatel zavřel dialogové okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>CTaskDialog::Zpětné volání aplikace TaskDialog

Rozhraní Framework volá tuto metodu v reakci na různé zprávy systému Windows.

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

*Hwnd*<br/>
[v] Úchyt `m_hWnd` ke `CTaskDialog`struktuře pro .

*uOznámení*<br/>
[v] Kód oznámení, který určuje vygenerovanou zprávu.

*wParam*<br/>
[v] Další informace o zprávě.

*Lparam*<br/>
[v] Další informace o zprávě.

*dwRefData*<br/>
[v] Ukazatel na `CTaskDialog` objekt, který se vztahuje na zprávu zpětného volání.

### <a name="return-value"></a>Návratová hodnota

Závisí na konkrétním kódu oznámení. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Výchozí implementace `TaskDialogCallback` zpracovává konkrétní zprávu a potom volá příslušnou metodu [On třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Například v reakci na zprávu `TaskDialogCallback` TDN_BUTTON_CLICKED, volá [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Hodnoty pro *wParam* a *lParam* závisí na konkrétní generované zprávy. Je možné, že jedna nebo obě tyto hodnoty budou prázdné. V následující tabulce jsou uvedeny výchozí oznámení, které jsou podporovány a co představují hodnoty *wParam* a *lParam.* Pokud tuto metodu přepíšete v odvozené třídě, měli byste implementovat kód zpětného volání pro každou zprávu v následující tabulce.

|Oznamovací zpráva|*wParam* Hodnotu|*LParam* Hodnotu|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nepoužívá se.|Nepoužívá se.|
|TDN_NAVIGATED|Nepoužívá se.|Nepoužívá se.|
|TDN_BUTTON_CLICKED|ID ovládacího prvku příkazového tlačítka.|Nepoužívá se.|
|TDN_HYPERLINK_CLICKED|Nepoužívá se.|Struktura [LPCWSTR,](/windows/win32/WinProg/windows-data-types) která obsahuje odkaz.|
|TDN_TIMER|Čas v milisekundách od `CTaskDialog` vytvoření nebo resetování časovače.|Nepoužívá se.|
|TDN_DESTROYED|Nepoužívá se.|Nepoužívá se.|
|TDN_RADIO_BUTTON_CLICKED|ID přepínacího tlačítka.|Nepoužívá se.|
|TDN_DIALOG_CONSTRUCTED|Nepoužívá se.|Nepoužívá se.|
|TDN_VERIFICATION_CLICKED|1 pokud je zaškrtávací políčko zaškrtnuto, 0, pokud není.|Nepoužívá se.|
|TDN_HELP|Nepoužívá se.|Nepoužívá se.|
|TDN_EXPANDO_BUTTON_CLICKED|0, pokud je oblast rozšíření sbalená; nenulová, pokud se zobrazí rozšiřující text.|Nepoužívá se.|

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Návod: Přidání objektu CTaskDialog do aplikace](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
