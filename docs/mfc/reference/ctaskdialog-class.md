---
title: CTaskDialog – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 83b56c82248397c3d355fb365ccb630760a4a741
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076045"
---
# <a name="ctaskdialog-class"></a>CTaskDialog – třída

Místní dialogové okno, které funguje jako okno se zprávou, ale můžete zobrazit další informace pro uživatele. `CTaskDialog` Také zahrnuje funkce pro shromažďování informací od uživatele.

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
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Přidá na příkazové tlačítko `CTaskDialog`.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Přidá tlačítko přepínače a `CTaskDialog`.|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Příkazové tlačítko nebo běžné tlačítko klikne prostřednictvím kódu programu.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Přepínací tlačítko klikne prostřednictvím kódu programu.|
|[CTaskDialog::DoModal](#domodal)|Zobrazí `CTaskDialog`.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Získá počet běžné tlačítka, které jsou k dispozici.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Převede standardní tlačítko Windows společný typ. tlačítko přidružené `CTaskDialog` třídy.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Jeden z běžných typů tlačítko přidružené k převede `CTaskDialog` třída pro standardní tlačítko Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Vrátí možnost příznaky pro tuto `CTaskDialog`.|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Vrátí ovládací prvek tlačítko vybraný příkaz.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Vrátí vybraného přepínače.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Načte stav zaškrtávacího políčka pro ověření.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Určuje, zda je povoleno na příkazové tlačítko nebo běžné tlačítko.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Určuje, zda je povoleno přepínač.|
|[CTaskDialog::IsSupported](#issupported)|Určuje, zda počítač, na kterém běží aplikace podporuje `CTaskDialog`.|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Přidá příkaz Ovládací prvky tlačítka pomocí dat z tabulky řetězců.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Přidá přepínačů s použitím dat z tabulky řetězců.|
|[CTaskDialog::NavigateTo](#navigateto)|Přenese fokus do jiného `CTaskDialog`.|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Rozhraní volá tuto metodu, když uživatel klikne příkazové tlačítko.|
|[CTaskDialog::OnCreate](#oncreate)|Rozhraní volá tuto metodu po vytvoření `CTaskDialog`.|
|[CTaskDialog::OnDestroy](#ondestroy)|Rozhraní volá tuto metodu, bezprostředně před zničí `CTaskDialog`.|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Rozhraní volá tuto metodu, když uživatel klikne na tlačítko rozšíření.|
|[CTaskDialog::OnHelp](#onhelp)|Rozhraní volá tuto metodu, když si uživatel vyžádá nápovědu.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Rozhraní volá tuto metodu, když uživatel klikne na hypertextový odkaz.|
|[CTaskDialog::OnInit](#oninit)|Rozhraní volá tuto metodu, když `CTaskDialog` je inicializován.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Rozhraní volá tuto metodu, když uživatel přesune fokus s ohledem na ovládací prvky `CTaskDialog`.|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Rozhraní volá tuto metodu, když uživatel vybere ovládací prvek přepínač.|
|[CTaskDialog::OnTimer](#ontimer)|Rozhraní volá tuto metodu, když čas vyprší.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Rozhraní volá tuto metodu, když uživatel klikne na tlačítko zaškrtnutí políčka pro ověření.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Odebere všechny ovládací prvky pro příkaz z `CTaskDialog`.|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Odebere všechny přepínače z `CTaskDialog`.|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Aktualizace na příkazové tlačítko `CTaskDialog`.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podmnožiny běžných tlačítka povolena a vyžaduje nástroje Řízení uživatelských účtů ke zvýšení úrovně oprávnění.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Přidá společné tlačítka `CTaskDialog`.|
|[CTaskDialog::SetContent](#setcontent)|Aktualizuje obsah `CTaskDialog`.|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Určuje výchozí příkazové tlačítko.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Určuje výchozí přepínač.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Nastavuje šířku `CTaskDialog`.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizace rozšíření oblasti `CTaskDialog`.|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Aktualizace na ikonu zápatí `CTaskDialog`.|
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizuje text v zápatí `CTaskDialog`.|
|[CTaskDialog::SetMainIcon](#setmainicon)|Aktualizuje hlavní ikonu `CTaskDialog`.|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Aktualizuje hlavní instrukce `CTaskDialog`.|
|[CTaskDialog::SetOptions](#setoptions)|Konfiguruje možnosti pro `CTaskDialog`.|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Nakonfiguruje rámeček panelu pro `CTaskDialog` a přidá jej do dialogového okna.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Nastaví pozici indikátor průběhu.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Nastaví rozsah indikátor průběhu.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Nastaví stav indikátoru průběhu a zobrazí ho na `CTaskDialog`.|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Povolí nebo zakáže přepínač.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Nastaví zaškrtnutý stav zaškrtávacího políčka pro ověření.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Nastaví text na pravé straně zaškrtněte políčko ověřování.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Nastaví název `CTaskDialog`.|
|[CTaskDialog::ShowDialog](#showdialog)|Vytvoří a zobrazí `CTaskDialog`.|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Rozhraní volá to v reakci na různé zprávy Windows.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|`m_aButtons`|Pole ovládací prvky tlačítka příkazu pro `CTaskDialog`.|
|`m_aRadioButtons`|Pole ovládacích prvků přepínačů pro `CTaskDialog`.|
|`m_bVerified`|`TRUE` indikuje, že je zaškrtnuté políčko ověřování; `FALSE` označuje není.|
|`m_footerIcon`|Ikona v zápatí `CTaskDialog`.|
|`m_hWnd`|Popisovač okna pro `CTaskDialog`.|
|`m_mainIcon`|Hlavní ikona `CTaskDialog`.|
|`m_nButtonDisabled`|Masku, která označuje, které common tlačítek jsou zakázané.|
|`m_nButtonElevation`|Masku, která označuje, které common tlačítek vyžadují nástroje Řízení uživatelských účtů ke zvýšení úrovně oprávnění.|
|`m_nButtonId`|ID ovládacího prvku tlačítko vybraný příkaz.|
|`m_nCommonButton`|Masku, která označuje, která běžné tlačítka jsou zobrazeny v `CTaskDialog`.|
|`m_nDefaultCommandControl`|ID příkazového tlačítka, ovládací prvek, který je vybrán při `CTaskDialog` se zobrazí.|
|`m_nDefaultRadioButton`|ID přepínač ovládací prvek, který je vybrán při `CTaskDialog` se zobrazí.|
|`m_nFlags`|Maska, který určuje možnosti pro `CTaskDialog`.|
|`m_nProgressPos`|Aktuální pozice pro indikátor průběhu.  Tato hodnota musí být mezi `m_nProgressRangeMin` a `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|Maximální hodnota indikátoru průběhu.|
|`m_nProgressRangeMin`|Minimální hodnota indikátoru průběhu.|
|`m_nProgressState`|Stav indikátor průběhu. Další informace najdete v tématu [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|ID ovládacího prvku tlačítko vybraného přepínače.|
|`m_nWidth`|Šířka `CTaskDialog` v pixelech.|
|`m_strCollapse`|Řetězec `CTaskDialog` zobrazí napravo od pole rozšíření, když je skrytý rozšířené informace.|
|`m_strContent`|Řetězec obsahu objektu `CTaskDialog`.|
|`m_strExpand`|Řetězec `CTaskDialog` zobrazí napravo od pole rozšíření, když se zobrazí dodatečné informace.|
|`m_strFooter`|V zápatí je uvedené `CTaskDialog`.|
|`m_strInformation`|Rozšířené informace o `CTaskDialog`.|
|`m_strMainInstruction`|Hlavní instrukce `CTaskDialog`.|
|`m_strTitle`|Název `CTaskDialog`.|
|`m_strVerification`|Řetězec, který `CTaskDialog` zobrazí napravo od zaškrtávacího políčka pro ověření.|

## <a name="remarks"></a>Poznámky

`CTaskDialog` Třídy nahradí pole standardní zprávy Windows a obsahuje další funkce, jako jsou nové ovládací prvky k získání informací od uživatele. Tato třída je v knihovně MFC v sadě Visual Studio 2010 a novější. `CTaskDialog` Je k dispozici od verze Windows Vista. Nelze zobrazit dřívější verze Windows `CTaskDialog` objektu. Použití `CTaskDialog::IsSupported` určit za běhu, zda aktuální uživatel mohl zobrazit dialogové okno úlohy. Pole pro standardní zprávy Windows je nadále podporován.

`CTaskDialog` Je k dispozici pouze při sestavení aplikace s použitím knihovny kódování Unicode.

`CTaskDialog` Má dva různé konstruktory. Jeden konstruktor umožňuje zadat dvě příkazová tlačítka a až šest ovládací prvky pro běžné tlačítko. Po vytvoření můžete přidat další příkazová tlačítka `CTaskDialog`. Druhý konstruktor nepodporuje žádné příkazová tlačítka, ale můžete přidat neomezený počet ovládací prvky pro běžné tlačítko. Další informace o konstruktorech naleznete v tématu [CTaskDialog::CTaskDialog](#ctaskdialog).

Následující obrázek znázorňuje ukázku `CTaskDialog` pro ilustraci umístění některých prvků.

![Příkladem objektu CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "ctaskdialogsample") CTaskDialog vzorku

## <a name="requirements"></a>Požadavky

**Minimální požadovaný operační systém:** Windows Vista

**Záhlaví:** afxtaskdialog.h

##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl

Přidá nový ovládací prvek tlačítko příkazu k `CTaskDialog`.

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Příkaz Ovládací prvek identifikační číslo.

*strCaption*<br/>
[in] Řetězec, který `CTaskDialog` zobrazí uživateli. Použijte tento řetězec vysvětlující účel příkazu.

*bEnabled*<br/>
[in] Parametr logické hodnoty označující, pokud je tlačítko Povolit nebo zakázat.

*bRequiresElevation*<br/>
[in] Parametr logické hodnoty, která určuje, zda příkaz vyžaduje zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

`CTaskDialog Class` Neomezený počet ovládací prvky tlačítka příkazu můžete zobrazit. Nicméně pokud `CTaskDialog` zobrazí libovolný příkaz tlačítko – ovládací prvky, může zobrazit maximálně 6 tlačítka. Pokud `CTaskDialog` nemá žádné ovládací prvky tlačítka příkaz, může zobrazit neomezený počet tlačítek.

Když uživatel vybere ovládací prvek tlačítko příkazu `CTaskDialog` zavře. Pokud vaše aplikace zobrazí dialogové okno s použitím [CTaskDialog::DoModal](#domodal), `DoModal` vrátí *nCommandControlID* vybraný příkaz ovládacího prvku tlačítka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton

Přidá tlačítko přepínače a `CTaskDialog`.

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Identifikační číslo přepínač.

*strCaption*<br/>
[in] Řetězec, který `CTaskDialog` zobrazí vedle přepínač.

*bEnabled*<br/>
[in] Parametr logické hodnoty označující, zda je povoleno přepínač.

### <a name="remarks"></a>Poznámky

Přepínačů pro [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md) vám ke shromažďování informací od uživatele. Použijte funkci [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) k určení, které přepínače.

`CTaskDialog` Nevyžaduje *nRadioButtonID* parametry jsou jedinečné pro každý přepínač. Pokud nepoužijete odlišné identifikátor u obou přepínačů, však může dojít neočekávané chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl

Příkazové tlačítko nebo běžné tlačítko klikne prostřednictvím kódu programu.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] ID příkazu ovládacího prvku klikněte na tlačítko.

### <a name="remarks"></a>Poznámky

Tato metoda generuje TDM_CLICK_BUTTON zprávy systému windows.

##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton

Přepínací tlačítko klikne prostřednictvím kódu programu.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] ID klikněte na přepínač.

### <a name="remarks"></a>Poznámky

Tato metoda generuje TDM_CLICK_RADIO_BUTTON zprávy systému windows.

##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog

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
[in] Řetězec, který má použít pro obsah `CTaskDialog`.

*strMainInstruction*<br/>
[in] Hlavní instrukce `CTaskDialog`.

*strTitle*<br/>
[in] Název `CTaskDialog`.

*nCommonButtons*<br/>
[in] Maska běžné tlačítka pro přidání do `CTaskDialog`.

*nTaskDialogOptions*<br/>
[in] Sadu možností pro `CTaskDialog`.

*strFooter*<br/>
[in] Řetězec, který chcete použít jako zápatí.

*nIDCommandControlsFirst*<br/>
[in] Řetězec ID prvního příkazu.

*nIDCommandControlsLast*<br/>
[in] Řetězec ID poslední příkaz.

### <a name="remarks"></a>Poznámky

Existují dva způsoby, které můžete přidat `CTaskDialog` do vaší aplikace. Prvním způsobem je použití jednoho z konstruktorů k vytvoření `CTaskDialog` a zobrazit ji pomocí [CTaskDialog::DoModal](#domodal). Druhý způsob je použití statické funkce [CTaskDialog::ShowDialog](#showdialog), což vám umožní zobrazit `CTaskDialog` bez explicitního vytváření `CTaskDialog` objektu.

Druhý konstruktor vytvoří příkazového tlačítka s použitím dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými řetězcovými ID. Tato metoda přidá příkazové tlačítko pro každou platnou položku v tabulce řetězců mezi *nIDCommandControlsFirst* a *nCommandControlsLast*včetně. Pro tyto ovládací prvky tlačítka příkazu řetězec do tabulky řetězců je popisek ovládacího prvku a řetězec ID je ID ovládacího prvku.

Zobrazit [CTaskDialog::SetOptions](#setoptions) seznam platné možnosti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>  CTaskDialog::DoModal

Ukazuje, `CTaskDialog` a díky tomu modální.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hParent*<br/>
[in] Nadřazené okno pro `CTaskDialog`.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které odpovídá výběru uživatelem.

### <a name="remarks"></a>Poznámky

Zobrazí tuto instanci [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Aplikace pak čeká uživateli dialogové okno zavřete.

`CTaskDialog` Zavře, když uživatel vybere common tlačítka, ovládací prvek odkazu příkazu nebo zavře `CTaskDialog`. Vrácená hodnota je identifikátor, který určuje, jak uživatel zavření dialogových oken.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount

Získá počet běžné tlačítka.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet běžné tlačítka, které jsou k dispozici.

### <a name="remarks"></a>Poznámky

Běžné tlačítka jsou výchozí tlačítka, které zadáte [CTaskDialog::CTaskDialog](#ctaskdialog). [Třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md) zobrazí tlačítek v dolní části dialogového okna.

Výčtový seznam tlačítek je součástí CommCtrl.h.

##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag

Převede standardní tlačítko Windows společný typ. tlačítko přidružené [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parametry

*nButtonId*<br/>
[in] Standardní tlačítko hodnotu Windows.

### <a name="return-value"></a>Návratová hodnota

Hodnota odpovídající `CTaskDialog` běžné tlačítko. Pokud neexistuje žádný odpovídající běžné tlačítko, tato metoda vrátí hodnotu 0.

##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId

Převede jednu z běžné typy tlačítek, které jsou přidružené k [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md) standardní tlačítko Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parametry

*načit*<br/>
[in] Společný typ tlačítko přidružené `CTaskDialog` třídy.

### <a name="return-value"></a>Návratová hodnota

Hodnota odpovídající standardní tlačítko Windows. Pokud neexistuje žádný odpovídající tlačítka Windows, metoda vrátí hodnotu 0.

##  <a name="getoptions"></a>  CTaskDialog::GetOptions

Vrátí možnost příznaky pro tuto `CTaskDialog`.

```
int GetOptions() const;
```

### <a name="return-value"></a>Návratová hodnota

Příznaky pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Další informace o dostupných možnostech [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md), naleznete v tématu [CTaskDialog::SetOptions](#setoptions).

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

Není nutné tuto metodu použijte k načtení ID příkazového tlačítka, který uživatel vybral. Toto ID je vrácený buď [CTaskDialog::DoModal](#domodal) nebo [CTaskDialog::ShowDialog](#showdialog).

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

Tuto metodu můžete použít, až uživatel zavře dialogové okno Načíst vybraný přepínač.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState

Načte stav zaškrtávacího políčka pro ověření.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se zaškrtávací políčko je zaškrtnuto, FALSE. Pokud není.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled

Určuje, zda je povoleno na příkazové tlačítko nebo tlačítko.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] ID příkazové tlačítko nebo tlačítko test.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ovládací prvek je povoleno, FALSE. Pokud není.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete použít k určení dostupnosti i příkaz Ovládací prvky tlačítka a běžné tlačítek `CTaskDialog` třídy *.

Pokud *nCommandControlID* je neplatný identifikátor pro buď běžný `CTaskDialog` tlačítko nebo příkazové tlačítko, tato metoda vyvolá výjimku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled

Určuje, zda je povoleno přepínač.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] ID přepínač k testování.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud přepínací tlačítko je povolené FALSE. Pokud není.

### <a name="remarks"></a>Poznámky

Pokud *nRadioButtonID* není platný identifikátor pro přepínací tlačítko, tato metoda vyvolá výjimku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>  CTaskDialog::IsSupported

Určuje, zda počítač, na kterém běží aplikace podporuje `CTaskDialog`.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud počítač podporuje `CTaskDialog`; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení za běhu, pokud počítač, na kterém běží vaše aplikace podporuje `CTaskDialog` třídy. Pokud počítač není podporován `CTaskDialog`, měli byste zadat jinou metodu sdělování informací uživateli. Vaše aplikace se chybově ukončit, pokud se pokusí použít `CTaskDialog` na počítači, který nepodporuje `CTaskDialog` třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls

Přidá příkaz Ovládací prvky tlačítka pomocí dat z tabulky řetězců.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parametry

*nIDCommandControlsFirst*<br/>
[in] Řetězec ID prvního příkazu.

*nIDCommandControlsLast*<br/>
[in] Řetězec ID poslední příkaz.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří ovládací prvky příkazového tlačítka s použitím dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými řetězcovými ID. Nové ovládací prvky tlačítka příkazu přidat pomocí této metody použijte řetězec pro záhlaví ovládacího prvku a řetězec ID pro ID ovládacího prvku. Poskytuje řadu řetězce vybrané *nIDCommandControlsFirst* a *nCommandControlsLast*včetně. Pokud je v rozsahu prázdná položka, metoda nepřidá příkazové tlačítko pro tuto položku.

Ve výchozím nastavení nové ovládací prvky tlačítka příkazu jsou povolené a nevyžadují, aby zvýšení oprávnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons

Přidá ovládací prvky tlačítek přepínače s použitím dat z tabulky řetězců.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parametry

*nIDRadioButtonsFirst*<br/>
[in] Řetězec ID první přepínač.

*nIDRadioButtonsLast*<br/>
[in] Řetězec ID poslední přepínač.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří přepínačů s použitím dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými řetězcovými ID. Přidat tímto způsobem nové přepínače použijte řetězec pro titulek přepínací tlačítko a řetězec ID pro ID přepínací tlačítko. Poskytuje řadu řetězce vybrané *nIDRadioButtonsFirst* a *nRadioButtonsLast*včetně. Pokud je v rozsahu prázdná položka, metoda nepřidá přepínač pro tuto položku.

Ve výchozím nastavení jsou povolené přepínačů nové.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>  CTaskDialog::NavigateTo

Přenese fokus do jiného `CTaskDialog`.

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parametry

*oTaskDialog*<br/>
[in] `CTaskDialog` , Který získá fokus.

### <a name="remarks"></a>Poznámky

Tato metoda skrývá aktuální `CTaskDialog` když se zobrazí *oTaskDialog*. *OTaskDialog* se zobrazí ve stejném umístění jako aktuální `CTaskDialog`.

##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick

Rozhraní volá tuto metodu, když uživatel klikne příkazové tlačítko.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] ID ovládacího prvku tlačítko příkazu, který uživatel vybral.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="oncreate"></a>  CTaskDialog::OnCreate

Rozhraní volá tuto metodu po vytvoření `CTaskDialog`.

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy

Rozhraní volá tuto metodu, bezprostředně před zničí `CTaskDialog`.

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick

Rozhraní volá tuto metodu, když uživatel klikne na tlačítko rozšíření.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parametry

*bExpanded*<br/>
[in] Nenulová hodnota označuje, že se zobrazí další informace. Hodnota 0 znamená, že je skrytý dodatečné informace.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="onhelp"></a>  CTaskDialog::OnHelp

Rozhraní volá tuto metodu, když si uživatel vyžádá nápovědu.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick

Rozhraní volá tuto metodu, když uživatel klikne na hypertextový odkaz.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parametry

*strHref*<br/>
[in] Řetězec, který reprezentuje hypertextový odkaz.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Tato metoda volá [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) dříve, než vrátí hodnotu S_OK.

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="oninit"></a>  CTaskDialog::OnInit

Rozhraní volá tuto metodu, když `CTaskDialog` je inicializován.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage

Rozhraní volá tuto metodu v reakci [CTaskDialog::NavigateTo](#navigateto) metody.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick

Rozhraní volá tuto metodu, když uživatel vybere ovládací prvek přepínač.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] ID ovládacího prvku tlačítko přepínače, který uživatel klikl na.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="ontimer"></a>  CTaskDialog::OnTimer

Rozhraní volá tuto metodu, když čas vyprší.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parametry

*lTime*<br/>
[in] Doba v milisekundách, protože `CTaskDialog` byl vytvořen nebo byl resetován časovač.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick

Rozhraní volá tuto metodu, když uživatel klikne na tlačítko zaškrtnutí políčka pro ověření.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
[in] Hodnota TRUE označuje, že je zaškrtnuto políčko ověřování. Hodnota FALSE označuje, že není.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě implementovat vlastní chování.

##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls

Odebere všechny prvky tlačítko příkazu z `CTaskDialog`.

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons

Odebere všechny přepínače z `CTaskDialog`.

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions

Aktualizace na příkazové tlačítko `CTaskDialog`.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] ID ovládacího prvku příkaz k aktualizaci.

*bEnabled*<br/>
[in] Parametr logické hodnoty, která určuje povolený nebo zakázaný ovládací prvek tlačítko zadaný příkaz.

*bRequiresElevation*<br/>
[in] Parametr logické hodnoty označující, pokud ovládací prvek tlačítko zadaný příkaz požaduje zvýšení oprávnění.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete určit, zda je povoleno příkazové tlačítko nebo vyžaduje zvýšená oprávnění po přidání do `CTaskDialog` třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions

Aktualizuje podmnožinu běžné tlačítka, aby byla povolená a tak, aby vyžadovala nástroj Řízení uživatelských účtů ke zvýšení úrovně oprávnění.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nDisabledButtonMask*<br/>
[in] Maska pro běžné tlačítka zakázat.

*nElevationButtonMask*<br/>
[in] Maska pro běžné tlačítka, které vyžadují ke zvýšení úrovně oprávnění.

### <a name="remarks"></a>Poznámky

Dostupné běžné tlačítka lze nastavit na instanci [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md) pomocí konstruktoru [CTaskDialog::CTaskDialog](#ctaskdialog) a metodu [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` nepodporuje přidávání nové společné tlačítka.

Pokud použijete tuto metodu můžete zakázat nebo zvýšení běžné tlačítko, které není k dispozici pro tento `CTaskDialog`, tato metoda vyvolá výjimku pomocí [Ujistěte se, že](diagnostic-services.md#ensure) – makro.

Tato metoda umožňuje využívat jakékoli tlačítko, které je k dispozici na `CTaskDialog` , ale není součástí *nDisabledButtonMask*i v případě, že byla zakázaná. Tato metoda zpracovává zvýšení podobným způsobem: zaznamenává běžné tlačítek nevyžaduje ke zvýšení úrovně oprávnění, pokud běžné tlačítko je k dispozici, ale není zahrnutý v *nElevationButtonMask*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons

Přidá společné tlačítka `CTaskDialog`.

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nButtonMask*<br/>
[in] Maska tlačítka pro přidání do `CTaskDialog`.

*nDisabledButtonMask*<br/>
[in] Maska tlačítka zakázat.

*nElevationButtonMask*<br/>
[in] Maska tlačítka, které vyžadují ke zvýšení úrovně oprávnění.

### <a name="remarks"></a>Poznámky

Tuto metodu nelze volat po zobrazit okno pro tuto instanci `CTaskDialog` je vytvořená třída. Pokud ano, tato metoda vyvolá výjimku.

Tlačítka indikován *nButtonMask* přepsat všechny běžné tlačítka předtím přidaly do `CTaskDialog`. Pouze tlačítka podle *nButtonMask* jsou k dispozici.

Pokud *nDisabledButtonMask* nebo *nElevationButtonMask* obsahuje tlačítko, který není součástí *nButtonMask*, tato metoda vyvolá výjimku pomocí [Ujistěte se, že](diagnostic-services.md#ensure) – makro.

Ve výchozím nastavení všechny běžné tlačítka jsou povolené a nevyžadují, aby zvýšení oprávnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>  CTaskDialog::SetContent

Aktualizuje obsah `CTaskDialog`.

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
[in] Řetězec, který se má zobrazit uživateli.

### <a name="remarks"></a>Poznámky

Obsah `CTaskDialog` třída je text, který se zobrazí uživateli v hlavní části dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl

Určuje výchozí příkazové tlačítko.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] ID ovládacího prvku tlačítko příkazu na výchozí.

### <a name="remarks"></a>Poznámky

Výchozí příkazové tlačítko je ovládací prvek, který je zaškrtnuto, pokud `CTaskDialog` se nejprve zobrazí uživateli.

Tato metoda vyvolá výjimku, pokud nemůže najít ovládací prvek tlačítko příkaz určený *nCommandControlID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton

Určuje výchozí přepínač.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] ID přepínač na výchozí.

### <a name="remarks"></a>Poznámky

Výchozí přepínací tlačítko je tlačítko, které je zaškrtnuto, pokud `CTaskDialog` se nejprve zobrazí uživateli.

Tato metoda vyvolá výjimku, pokud nemůže najít přepínač určené *nRadioButtonID*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth

Nastavuje šířku `CTaskDialog`.

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
[in] Šířka pole dialogového okna v pixelech.

### <a name="remarks"></a>Poznámky

Parametr *nWidth* musí být větší než nebo rovna 0. Jinak tato metoda vyvolá výjimku.

Pokud *nWidth* je nastavena na hodnotu 0, tato metoda sady dialogovém na výchozí velikost.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea

Aktualizace rozšíření oblasti `CTaskDialog`.

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parametry

*strExpandedInformation*<br/>
[in] Řetězec, který `CTaskDialog` zobrazí v hlavní části dialogového okna, když uživatel klikne na tlačítko rozšíření.

*strCollapsedLabel*<br/>
[in] Řetězec, který `CTaskDialog` při sbalení rozšířené oblasti se zobrazí vedle tlačítka, rozšíření.

*strExpandedLabel*<br/>
[in] Řetězec, který `CTaskDialog` zobrazí vedle tlačítka, rozšíření, když se zobrazí rozšířené oblast.

### <a name="remarks"></a>Poznámky

V oblasti rozšíření `CTaskDialog` třída umožňuje zadat další informace o uživateli. Rozšíření oblasti je v hlavní části `CTaskDialog`, který je umístěn bezprostředně pod název a obsah řetězce.

Když `CTaskDialog` je první zobrazuje, nezobrazuje rozšířené informace a vloží `strCollapsedLabel` vedle tlačítka, rozšíření. Když uživatel klikne na tlačítko rozšíření `CTaskDialog` zobrazí *strExpandedInformation* a změní popisek *strExpandedLabel*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon

Aktualizuje ikonu zápatí `CTaskDialog`.

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parametry

*hFooterIcon*<br/>
[in] Na novou ikonu `CTaskDialog`.

*lpszFooterIcon*<br/>
[in] Na novou ikonu `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Ikona zápatí se zobrazí v dolní části [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Mohou být přidruženy text zápatí. Můžete změnit text zápatí s [CTaskDialog::SetFooterText](#setfootertext).

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud `CTaskDialog` se zobrazí nebo vstupní parametr má hodnotu NULL.

A `CTaskDialog` přijmout jenom `HICON` nebo `LPCWSTR` jako ikona zápatí. Ta se nakonfiguruje tak, že nastavíte možnost TDF_USE_HICON_FOOTER v konstruktoru nebo [CTaskDialog::SetOptions](#setoptions). Ve výchozím nastavení `CTaskDialog` je nakonfigurován na použití `LPCWSTR` jako vstupní typ pro ikonu zápatí. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodný typu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText

Aktualizuje text v zápatí `CTaskDialog`.

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parametry

*strFooterText*<br/>
[in] Nový text zápatí.

### <a name="remarks"></a>Poznámky

Ikona zápatí se zobrazí vedle textu zápatí v dolní části `CTaskDialog`. Můžete změnit ikonu zápatí [CTaskDialog::SetFooterIcon](#setfootericon).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon

Aktualizuje hlavní ikonu `CTaskDialog`.

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parametry

*hMainIcon*<br/>
[in] Na ikonu nový.

*lpszMainIcon*<br/>
[in] Na ikonu nový.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud `CTaskDialog` se zobrazí nebo vstupní parametr má hodnotu NULL.

A `CTaskDialog` přijmout jenom `HICON` nebo `LPCWSTR` jako hlavní ikonu. To můžete nakonfigurovat nastavení možnosti TDF_USE_HICON_MAIN v konstruktoru nebo v [CTaskDialog::SetOptions](#setoptions) metody. Ve výchozím nastavení `CTaskDialog` je nakonfigurován na použití `LPCWSTR` jako vstupní typ pro hlavní ikonu. Tato metoda generuje výjimku, pokud se pokusíte nastavit ikonu pomocí nevhodný typu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction

Aktualizuje hlavní instrukce `CTaskDialog`.

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parametry

*strInstructions*<br/>
[in] Nový hlavní instrukce.

### <a name="remarks"></a>Poznámky

Hlavní instrukce `CTaskDialog` třída je text, zobrazený uživateli velké tučným písmem. Nachází se v dialogovém okně pod záhlavím.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>  CTaskDialog::SetOptions

Konfiguruje možnosti pro `CTaskDialog`.

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parametry

*nOptionFlag*<br/>
[in] Sada příznaků pro `CTaskDialog`.

### <a name="remarks"></a>Poznámky

Tato metoda odstraní všechny aktuální možnosti pro `CTaskDialog`. Pokud chcete zachovat aktuální možnosti, musíte je nejdřív načíst s [CTaskDialog::GetOptions](#getoptions) a zkombinujte je s možnostmi, které chcete nastavit.

V následující tabulce jsou uvedeny platné možnosti.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Umožňuje hypertextové odkazy `CTaskDialog`.|
|TDF_USE_HICON_MAIN|Konfiguruje `CTaskDialog` používat `HICON` pro hlavní ikona. Alternativou je použití `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|Konfiguruje `CTaskDialog` používat `HICON` pro ikonu zápatí. Alternativou je použití `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Umožňuje uživateli zavřete `CTaskDialog` pomocí klávesnice nebo pomocí ikony v pravém horním rohu dialogového okna, i v případě, **zrušit** není dostupné tlačítko. Pokud tento příznak není nastavený a **zrušit** není dostupné tlačítko, uživatel nelze dialogové okno zavřete stisknutím kombinace kláves Alt + F4, klávesou ESC nebo záhlaví okna tlačítko Zavřít.|
|TDF_USE_COMMAND_LINKS|Konfiguruje `CTaskDialog` používat ovládací prvky tlačítka příkazu.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Konfiguruje `CTaskDialog` používat ovládací prvky příkazového tlačítka bez zobrazení ikonu vedle ovládacího prvku. TDF_USE_COMMAND_LINKS přepíše TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Označuje, že je v současné době rozšířeno oblasti rozšíření.|
|TDF_EXPANDED_BY_DEFAULT|Určuje, zda je ve výchozím nastavení rozbalený oblasti rozšíření.|
|TDF_VERIFICATION_FLAG_CHECKED|Označuje, že je zaškrtávací políčko ověření aktuálně vybraný.|
|TDF_SHOW_PROGRESS_BAR|Konfiguruje `CTaskDialog` zobrazíte indikátor průběhu.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Nakonfiguruje indikátor průběhu bude marquee indikátor průběhu. Pokud tuto možnost povolíte, je nutné nastavit TDF_SHOW_PROGRESS_BAR mít očekávané chování.|
|TDF_CALLBACK_TIMER|Označuje, že `CTaskDialog` zpětného volání interval je nastavená na přibližně 200 MS.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Konfiguruje `CTaskDialog` být zarovnaný na střed vzhledem k nadřazeného okna. Pokud tento příznak není povolen, `CTaskDialog` je zarovnaný na střed vzhledem k monitorování.|
|TDF_RTL_LAYOUT|Konfiguruje `CTaskDialog` rozložení čtení zprava doleva.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Označuje, že je vybrána žádná přepínač při `CTaskDialog` se zobrazí.|
|TDF_CAN_BE_MINIMIZED|Umožňuje uživateli minimalizovat `CTaskDialog`. Podporu této možnosti `CTaskDialog` nemůže být modální okno. MFC nepodporuje tuto možnost, protože nepodporuje MFC nemodální `CTaskDialog`.|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee

Nakonfiguruje rámeček panelu pro `CTaskDialog` a přidá jej do dialogového okna.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parametry

*bEnabled*<br/>
[in] TRUE, pokud chcete povolit výběr řádku; FALSE, pokud chcete zakázat výběr řádku a odebere ho z `CTaskDialog`.

*nMarqueeSpeed*<br/>
[in] Celé číslo udávající rychlost výběr řádku.

### <a name="remarks"></a>Poznámky

Na výběr panelu se zobrazí pod do hlavního textu `CTaskDialog` třídy.

Použití *nMarqueeSpeed* rychlost výběr řádku; nastavit vyšší hodnoty znamenat nižší přenosovou rychlost. Hodnota 0 pro *nMarqueeSpeed* panel marquee přesunout rychlostí výchozí pro Windows.

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud *nMarqueeSpeed* je menší než 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition

Nastaví pozici indikátor průběhu.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
[in] Pozice pro indikátor průběhu.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud *nProgressPos* není v rozsahu panelu průběh. Můžete změnit rozsah panelu průběh v [CTaskDialog::SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange

Nastaví rozsah indikátor průběhu.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
[in] Dolní mez indikátor průběhu.

*nRangeMax*<br/>
[in] Horní mez indikátor průběhu.

### <a name="remarks"></a>Poznámky

Pozice panelu průběh je vzhledem k *nRangeMin* a *nRangeMax*. Například pokud *nRangeMin* je 50 a *nRangeMax* 100, pozice 75 je uprostřed mezi indikátor průběhu. Použití [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) nastavení pozice indikátor průběhu.

Pokud chcete zobrazit indikátor průběhu, nesmí být povolena možnost TDF_SHOW_PROGRESS_BAR musí být povolená a TDF_SHOW_MARQUEE_PROGRESS_BAR. Tato metoda automaticky nastaví TDF_SHOW_PROGRESS_BAR a vymaže TDF_SHOW_MARQUEE_PROGRESS_BAR. Použití [CTaskDialog::SetOptions](#setoptions) ručně změnit možnosti pro tuto instanci [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud *nRangeMin* je nejméně *nRangeMax*. Tato metoda také vyvolá výjimku, pokud `CTaskDialog` již zobrazena a má marquee indikátor průběhu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState

Nastaví stav indikátoru průběhu a zobrazí ho na `CTaskDialog`.

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parametry

*nInformace*<br/>
[in] Stav indikátor průběhu. Možné hodnoty v části poznámky.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud `CTaskDialog` již zobrazena a má marquee indikátor průběhu.

V následující tabulce jsou uvedeny možné hodnoty pro *nInformace*. Ve všech těchto případech se vyplní indikátor průběhu barvou regulární, dokud nedosáhne určené stop pozice. V tomto okamžiku změní barvu na základě stavu.

|||
|-|-|
|PBST_NORMAL|Po průběh nevyplní, `CTaskDialog` nezmění barev panelu. Ve výchozím nastavení je zelenou barvu regulárních.|
|PBST_ERROR|Po průběh nevyplní, `CTaskDialog` změní barvu řádku barva chyby. Ve výchozím nastavení toto je červený.|
|PBST_PAUSED|Po průběh nevyplní, `CTaskDialog` změní barvu na panelu pozastaveného barvu. Ve výchozím nastavení toto je žlutý.|

Můžete nastavit, kdy přestane indikátor průběhu s [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

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

*nRadioButtonID*<br/>
[in] ID ovládacího prvku tlačítko přepínače.

*bEnabled*<br/>
[in] TRUE, pokud chcete povolit přepínač; FALSE, pokud chcete zakázat přepínač.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro Pokud *nRadioButtonID* není platné ID pro přepínač.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox

Nastaví zaškrtnutý stav zaškrtávacího políčka pro ověření.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
[in] Hodnota true pro mají ověření zaškrtávací políčko zaškrtnuto, pokud `CTaskDialog` , se zobrazí. Zrušení výběru hodnotu FALSE má zaškrtávací políčko ověřování, kdy `CTaskDialog` se zobrazí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText

Nastaví text, který se zobrazí napravo od zaškrtávacího políčka pro ověření.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parametry

*strVerificationText*<br/>
[in] Text, který tato metoda se zobrazí vedle zaškrtnutí políčka pro ověření.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá výjimku [Ujistěte se, že](diagnostic-services.md#ensure) – makro, pokud tato instance `CTaskDialog` třída je již zobrazen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle

Nastaví název `CTaskDialog`.

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parametry

*strWindowTitle*<br/>
[in] Nový název `CTaskDialog`.

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

*strContent*<br/>
[in] Řetězec, který má použít pro obsah `CTaskDialog`.

*strMainInstruction*<br/>
[in] Hlavní instrukce `CTaskDialog`.

*strTitle*<br/>
[in] Název `CTaskDialog`.

*nIDCommandControlsFirst*<br/>
[in] Řetězec ID prvního příkazu.

*nIDCommandControlsLast*<br/>
[in] Řetězec ID poslední příkaz.

*nCommonButtons*<br/>
[in] Maska tlačítka pro přidání do `CTaskDialog`.

*nTaskDialogOptions*<br/>
[in] Sadu možností pro `CTaskDialog`.

*strFooter*<br/>
[in] Řetězec, který chcete použít jako zápatí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které odpovídá výběru uživatelem.

### <a name="remarks"></a>Poznámky

Tato statická metoda vám umožňuje vytvořit instanci `CTaskDialog` třídy bez explicitního vytváření `CTaskDialog` objekt v kódu. Protože neexistuje žádný `CTaskDialog` objektu nelze volat jiným způsobem `CTaskDialog` Pokud pomocí této metody můžete zobrazit `CTaskDialog` uživateli.

Tato metoda vytvoří ovládací prvky příkazového tlačítka s použitím dat ze souboru prostředků vaší aplikace. Tabulka řetězců v souboru prostředků má několik řetězců s přidruženými řetězcovými ID. Tato metoda přidá příkazové tlačítko pro každou platnou položku v tabulce řetězců mezi *nIDCommandControlsFirst* a *nCommandControlsLast*včetně. Pro tyto ovládací prvky tlačítka příkazu řetězec do tabulky řetězců je popisek ovládacího prvku a řetězec ID je ID ovládacího prvku.

Zobrazit [CTaskDialog::SetOptions](#setoptions) seznam platné možnosti.

`CTaskDialog` Zavře, když uživatel vybere common tlačítka, ovládací prvek odkazu příkazu nebo zavře `CTaskDialog`. Vrácená hodnota je identifikátor, který určuje, jak uživatel zavření dialogových oken.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback

Rozhraní volá tuto metodu v reakci na různé zprávy Windows.

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

*hWnd*<br/>
[in] Popisovač `m_hWnd` strukturu pro `CTaskDialog`.

*uNotification*<br/>
[in] Určuje zprávu, která vygenerovaný kód oznámení.

*wParam*<br/>
[in] Další informace o zprávě.

*lParam*<br/>
[in] Další informace o zprávě.

*dwRefData*<br/>
[in] Ukazatel `CTaskDialog` objekt, který zpětného volání zpráv se vztahuje na.

### <a name="return-value"></a>Návratová hodnota

Závisí na kódu konkrétní upozornění. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Výchozí implementace `TaskDialogCallback` zpracovává konkrétní zprávu a pak zavolá metody odpovídající [třídy CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Například v reakci na zprávu TDN_BUTTON_CLICKED `TaskDialogCallback` volání [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Hodnoty pro *wParam* a *lParam* závisí na konkrétní generovanou zprávu. Je možné u jednoho nebo obou těchto hodnot být prázdná. V následující tabulce jsou uvedeny výchozí oznámení, které jsou podporovány a jaké hodnoty *wParam* a *lParam* představují. Pokud je přepsat tuto metodu v odvozené třídě, měli byste implementovat kód zpětného volání pro každou zprávu v následující tabulce.

|Oznámení|*wParam* hodnota|*lParam* hodnota|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nepoužívá se.|Nepoužívá se.|
|TDN_NAVIGATED|Nepoužívá se.|Nepoužívá se.|
|TDN_BUTTON_CLICKED|Příkazové tlačítko ovládací prvek ID.|Nepoužívá se.|
|TDN_HYPERLINK_CLICKED|Nepoužívá se.|A [LPCWSTR](/windows/desktop/WinProg/windows-data-types) strukturu, která obsahuje odkaz.|
|TDN_TIMER|Doba v milisekundách, protože `CTaskDialog` byl vytvořen nebo byl resetován časovač.|Nepoužívá se.|
|TDN_DESTROYED|Nepoužívá se.|Nepoužívá se.|
|TDN_RADIO_BUTTON_CLICKED|ID přepínač tlačítko.|Nepoužívá se.|
|TDN_DIALOG_CONSTRUCTED|Nepoužívá se.|Nepoužívá se.|
|TDN_VERIFICATION_CLICKED|1, pokud je zaškrtnuto zaškrtávací políčko, 0, pokud není.|Nepoužívá se.|
|TDN_HELP|Nepoužívá se.|Nepoužívá se.|
|TDN_EXPANDO_BUTTON_CLICKED|0, pokud je sbalené oblast rozšíření; nenulové, pokud se zobrazí text rozšíření.|Nepoužívá se.|

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Návod: Přidání objektu CTaskDialog do aplikace](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
