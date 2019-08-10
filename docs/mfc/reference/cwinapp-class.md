---
title: CWinApp – třída
ms.date: 07/15/2019
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
ms.openlocfilehash: 066494f4ba0119f4576e0c8e3c06d87ff736aea3
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916722"
---
# <a name="cwinapp-class"></a>CWinApp – třída

Základní třída, ze které odvozujete objekt aplikace systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CWinApp:: CWinApp](#cwinapp)|`CWinApp` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CWinApp:: AddDocTemplate](#adddoctemplate)|Přidá šablonu dokumentu do seznamu dostupných šablon dokumentu aplikace.|
|[CWinApp:: AddToRecentFileList](#addtorecentfilelist)|Přidá název souboru do seznamu naposledy použitých souborů (MRU).|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Volá se rozhraním, když se aplikace neočekávaně ukončí.|
|[CWinApp:: CloseAllDocuments](#closealldocuments)|Zavře všechny otevřené dokumenty.|
|[CWinApp::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny.|
|[CWinApp::DelRegTree](#delregtree)|Odstraní zadaný klíč a všechny jeho podklíče.|
|[CWinApp::DoMessageBox](#domessagebox)|Implementuje [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) pro aplikaci.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Zapne nebo vypne čekací ukazatel.|
|[CWinApp:: EnableD2DSupport](#enabled2dsupport)|Povolí podporu D2D aplikace. Před inicializací hlavního okna volejte tuto metodu.|
|[CWinApp:: EnableHtmlHelp](#enablehtmlhelp)|Implementuje HTMLHelp pro aplikaci, nikoli WinHelp.|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Povoluje interakci hlavního panelu.|
|[CWinApp:: ExitInstance](#exitinstance)|Přepsat pro vyčištění při ukončení aplikace.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Načte vstupní parametr pro metodu obnovení aplikace.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Vrátí dobu, po kterou správce restartování počká, až vrátí funkci zpětného volání pro obnovení.|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Vrátí příznaky pro správce restartování.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Vrátí klíč pro HKEY_CURRENT_USER\\"software" \RegistryKey\ProfileName.|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Získá obslužnou rutinu obnovení dat pro tuto instanci aplikace.|
|[CWinApp:: GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Načte pozici první šablony dokumentu.|
|[CWinApp::GetHelpMode](#gethelpmode)|Načte typ nápovědě, kterou aplikace používá.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Načte pozici šablony dokumentu. Lze použít rekurzivní.|
|[CWinApp:: GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Načte výchozí hodnoty pro zařízení tiskárny.|
|[CWinApp:: GetProfileBinary](#getprofilebinary)|Načte binární data ze záznamu v aplikaci. Soubor INI.|
|[CWinApp::GetProfileInt](#getprofileint)|Načte celé číslo ze záznamu v aplikaci. Soubor INI.|
|[CWinApp:: GetProfileString](#getprofilestring)|Načte řetězec ze záznamu v aplikaci. Soubor INI.|
|[CWinApp::GetSectionKey](#getsectionkey)|Vrátí klíč pro HKEY_CURRENT_USER\\"software" \RegistryKey\AppName\lpszSection.|
|[CWinApp::HideApplication](#hideapplication)|Před zavřením všech dokumentů skryje aplikaci.|
|[CWinApp:: HtmlHelp](#htmlhelp)|Volá funkci `HTMLHelp` Windows.|
|[CWinApp:: InitInstance](#initinstance)|Přepište k provedení inicializace instance systému Windows, například vytvoření objektů okna.|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Určuje, zda je povolena interakce hlavního panelu systému Windows 7.|
|[CWinApp:: LoadCursor](#loadcursor)|Načte prostředek kurzoru.|
|[CWinApp:: LoadIcon](#loadicon)|Načte prostředek ikony.|
|[CWinApp:: LoadOEMCursor](#loadoemcursor)|Načte předdefinovaný ukazatel OEM systému Windows, který určuje konstanty **OCR_** ve Windows. Y.|
|[CWinApp::LoadOEMIcon](#loadoemicon)|Načte ikonu předdefinovaného Windows OEM, kterou **OIC_** konstanty určí ve Windows. Y.|
|[CWinApp:: LoadStandardCursor](#loadstandardcursor)|Načte předdefinovaný ovládací ukazatel na Windows, který **IDC_** konstanty specifikují v systému Windows. Y.|
|[CWinApp:: LoadStandardIcon](#loadstandardicon)|Načte předdefinovanou ikonu Windows, kterou **IDI_** konstanty určí ve Windows. Y.|
|[CWinApp:: OnDDECommand](#onddecommand)|Volá se rozhraním v reakci na příkaz Spustit dynamickou výměnu dat (DDE).|
|[CWinApp:: OnIdle](#onidle)|Přepište pro provádění zpracování specifického pro aplikaci.|
|[CWinApp::OpenDocumentFile](#opendocumentfile)|Volá se rozhraním, aby se otevřel dokument ze souboru.|
|[CWinApp::P arseCommandLine](#parsecommandline)|Analyzuje jednotlivé parametry a příznaky v příkazovém řádku.|
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|Filtruje zprávy předtím, než jsou odesílány do funkcí Windows Functions [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Zachycuje určité zprávy dřív, než dosáhnou aplikace.|
|[CWinApp::P rocessShellCommand](#processshellcommand)|Zpracovává argumenty a příznaky příkazového řádku.|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Zachycuje všechny neošetřené výjimky vyvolané obslužnými rutinami zpráv a příkazů aplikace.|
|[CWinApp:: Register](#register)|Provede přizpůsobenou registraci.|
|[CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)|Zaregistruje aplikaci pomocí správce restartování.|
|[CWinApp:: ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Určuje, zda správce restartování znovu otevře soubory otevřené při neočekávaném ukončení aplikace.|
|[CWinApp:: RestartInstance](#restartinstance)|Zpracovává restart aplikace inicializovaný správcem restartování.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Určuje, zda správce restartování obnoví automaticky uložené soubory při restartu aplikace.|
|[CWinApp:: Run](#run)|Spustí výchozí smyčku zpráv. Přepsáním přizpůsobíte smyčku zpráv.|
|[CWinApp:: RunAutomated](#runautomated)|Testuje příkazový řádek aplikace pro možnost **/Automation.** . Zastaralé. Místo toho použijte hodnotu v [CCommandLineInfo:: m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) po volání [ParseCommandLine](#parsecommandline).|
|[CWinApp:: RunEmbedded](#runembedded)|Testuje příkazový řádek aplikace pro možnost **přepínačem/Embedding** . Zastaralé. Místo toho použijte hodnotu v [CCommandLineInfo:: m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) po volání [ParseCommandLine](#parsecommandline).|
|[CWinApp::SaveAllModified](#saveallmodified)|Vyzve uživatele k uložení všech upravených dokumentů.|
|[CWinApp::SelectPrinter](#selectprinter)|Vybere tiskárnu, kterou dříve určil uživatel, prostřednictvím tiskového dialogového okna.|
|[CWinApp::SetHelpMode](#sethelpmode)|Nastaví a inicializuje typ nápovědě, kterou aplikace používá.|
|[CWinApp:: SupportsApplicationRecovery](#supportsapplicationrecovery)|Určuje, zda správce restartování obnoví aplikaci, která byla neočekávaně ukončena.|
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Určuje, zda správce restartování automaticky ukládá otevřené dokumenty v pravidelných intervalech.|
|[CWinApp:: SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Určuje, zda správce restartování automaticky uloží otevřené dokumenty, když se aplikace restartuje.|
|[CWinApp:: SupportsRestartManager](#supportsrestartmanager)|Určuje, zda aplikace podporuje správce restartování.|
|[CWinApp::Unregister](#unregister)|Zruší registraci všeho, co je známo, že `CWinApp` je zaregistrováno objektem.|
|[CWinApp:: WinHelp](#winhelp)|Volá funkci `WinHelp` Windows.|
|[CWinApp:: WriteProfileBinary](#writeprofilebinary)|Zapisuje binární data do položky v aplikaci. Soubor INI.|
|[CWinApp:: WriteProfileInt](#writeprofileint)|Zapíše celé číslo do položky v aplikaci. Soubor INI.|
|[CWinApp:: WriteProfileString](#writeprofilestring)|Zapíše řetězec do položky v aplikaci. Soubor INI.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CWinApp:: EnableShellOpen](#enableshellopen)|Povolí uživateli otevřít datové soubory ze Správce souborů systému Windows.|
|[CWinApp:: LoadStdProfileSettings](#loadstdprofilesettings)|Načte standardní. Nastavení souboru INI a povolení funkce seznamu naposledy použitých souborů.|
|[CWinApp::OnContextHelp](#oncontexthelp)|Zpracovává nápovědu SHIFT + F1 v rámci aplikace.|
|[CWinApp::OnFileNew](#onfilenew)|Implementuje příkaz ID_FILE_NEW.|
|[CWinApp:: OnFileOpen](#onfileopen)|Implementuje příkaz ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementuje příkaz ID_FILE_PRINT_SETUP.|
|[CWinApp:: InHelp](#onhelp)|Zpracovává nápovědu F1 v rámci aplikace (pomocí aktuálního kontextu).|
|[CWinApp:: OnHelpFinder](#onhelpfinder)|Zpracovává příkazy ID_HELP_FINDER a ID_DEFAULT_HELP.|
|[CWinApp:: OnHelpIndex](#onhelpindex)|Zpracuje příkaz ID_HELP_INDEX a poskytne výchozí téma nápovědy.|
|[CWinApp:: OnHelpUsing](#onhelpusing)|Zpracuje příkaz ID_HELP_USING.|
|[CWinApp:: RegisterShellFileTypes](#registershellfiletypes)|Zaregistruje všechny typy dokumentů aplikace pomocí Správce souborů systému Windows.|
|[CWinApp::SetAppID](#setappid)|Explicitně nastaví ID uživatelského modelu aplikace pro aplikaci. Tato metoda by měla být volána před tím, než se uživateli zobrazí jakékoli uživatelské rozhraní (nejlepším místem je konstruktor aplikace).|
|[CWinApp::SetRegistryKey](#setregistrykey)|Způsobí, že nastavení aplikace bude uloženo v registru místo. Soubory INI.|
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Zruší registraci všech typů dokumentů aplikace pomocí Správce souborů systému Windows.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Určuje, jestli je uživatel v kontextovém režimu Nápověda (obvykle se vyvolal pomocí SHIFT + F1).|
|[CWinApp:: m_eHelpType](#m_ehelptype)|Určuje typ nápovědě používané aplikací.|
|[CWinApp::m_hInstance](#m_hinstance)|Určuje aktuální instanci aplikace.|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Odkazuje na řetězec zakončený hodnotou null, který určuje příkazový řádek pro aplikaci.|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Určuje, jak se má okno zobrazovat na začátku.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace typu kontejner, pokud je server OLE aktivní na místě.|
|[CWinApp::m_pszAppID](#m_pszappid)|ID modelu uživatele aplikace|
|[CWinApp::m_pszAppName](#m_pszappname)|Určuje název aplikace.|
|[CWinApp::m_pszExeName](#m_pszexename)|Název modulu aplikace|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|Cesta k souboru Help aplikace|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|Aplikace. Název souboru INI|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Slouží k určení úplného klíče registru pro ukládání nastavení profilu aplikace.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Příznaky, které určují, jak se chovají správce restartování.|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|Doba v milisekundách mezi automaticky uloženými hodnotami.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Ukazatel na popisovač obnovení dat pro aplikaci.|

## <a name="remarks"></a>Poznámky

Objekt aplikace poskytuje členské funkce pro inicializaci vaší aplikace (a všechny její instance) a pro spuštění aplikace.

Každá aplikace, která používá třídu Microsoft Foundation, může obsahovat pouze jeden objekt odvozený z `CWinApp`. Tento objekt je vytvořen, pokud C++ jsou vytvořeny jiné globální objekty a je již k dispozici, `WinMain` když systém Windows zavolá funkci, která je poskytnuta knihovna Microsoft Foundation Class. Deklarujte svůj `CWinApp` odvozený objekt na globální úrovni.

Pokud odvodíte třídu aplikace z `CWinApp`, přepište členskou funkci [InitInstance](#initinstance) a vytvořte tak objekt hlavního okna vaší aplikace.

Kromě `CWinApp` členských funkcí poskytuje knihovna Microsoft Foundation Class následující globální funkce pro přístup k vašemu `CWinApp` objektu a dalším globálním informacím:

- [AfxGetApp](application-information-and-management.md#afxgetapp) Získá ukazatel na `CWinApp` objekt.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Získá popisovač aktuální instance aplikace.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Získá popisovač k prostředkům aplikace.

- [AfxGetAppName](application-information-and-management.md#afxgetappname) Získá ukazatel na řetězec obsahující název aplikace. Alternativně, pokud máte ukazatel na `CWinApp` objekt, použijte `m_pszExeName` k získání názvu aplikace.

Viz [CWinApp: Třída](../../mfc/cwinapp-the-application-class.md) aplikace pro další `CWinApp` třídu, včetně přehledu následujících:

- `CWinApp`– odvozený kód napsaný průvodcem aplikací.

- `CWinApp`role v sekvenci provádění vaší aplikace.

- `CWinApp`je výchozí implementace členské funkce.

- `CWinApp`klíč k přepisovatelným.

`m_hPrevInstance` Datový člen už neexistuje. Chcete-li zjistit, zda je spuštěna jiná instance aplikace, použijte pojmenovaný mutex. Pokud nedojde k otevření objektu mutex, nejsou spuštěny žádné další instance aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="adddoctemplate"></a>CWinApp:: AddDocTemplate

Zavolejte tuto členskou funkci pro přidání šablony dokumentu do seznamu dostupných šablon dokumentů, které aplikace udržuje.

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parametry

*pTemplate*<br/>
Ukazatel na, `CDocTemplate` který má být přidán.

### <a name="remarks"></a>Poznámky

Před voláním [RegisterShellFileTypes](#registershellfiletypes)byste měli do aplikace přidat všechny šablony dokumentů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="addtorecentfilelist"></a>CWinApp:: AddToRecentFileList

Voláním této členské funkce přidáte *lpszPathName* do seznamu naposledy použitých souborů.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Cesta k souboru

### <a name="remarks"></a>Poznámky

Než použijete tuto členskou funkci, měli byste zavolat členskou funkci [LoadStdProfileSettings](#loadstdprofilesettings) a načíst aktuální seznam souborů MRU.

Rozhraní volá tuto členskou funkci, když otevře soubor nebo spustí příkaz Uložit jako, který uloží soubor s novým názvem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="applicationrecoverycallback"></a>CWinApp:: ApplicationRecoveryCallback

Volá se rozhraním, když se aplikace neočekávaně ukončí.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parametry

*lpvParam*<br/>
pro Vyhrazeno pro budoucí použití.

### <a name="return-value"></a>Návratová hodnota

0, pokud je tato metoda úspěšná; nenulové, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace podporuje správce restartování, volá rozhraní tuto funkci, když vaše aplikace neočekávaně skončí.

Výchozí implementace `ApplicationRecoveryCallback` nástroje `CDataRecoveryHandler` používá k uložení seznamu aktuálně otevřených dokumentů do registru. Tato metoda neumožňuje ukládat žádné soubory.

Chcete-li přizpůsobit chování, přepište tuto funkci v odvozené [třídě CWinApp](../../mfc/reference/cwinapp-class.md) nebo předejte vlastní metodu obnovení aplikace jako parametr do [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager).

##  <a name="closealldocuments"></a>CWinApp:: CloseAllDocuments

Před ukončením zavoláte tuto členskou funkci, aby se zavřely všechny otevřené dokumenty.

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Určuje, jestli se už neukončila relace Windows. Má hodnotu TRUE, pokud je relace ukončena; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Před [](#hideapplication) voláním `CloseAllDocuments`volejte HideApplication.

##  <a name="createprinterdc"></a>CWinApp:: CreatePrinterDC

Zavolejte tuto členskou funkci pro vytvoření kontextu zařízení tiskárny (DC) z vybrané tiskárny.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
Odkaz na kontext zařízení tiskárny.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je kontext zařízení tiskárny úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CreatePrinterDC`Inicializuje kontext zařízení, který předáte odkazem, abyste ho mohli použít k tisku.

Pokud je funkce úspěšná, po dokončení tisku musíte zničit kontext zařízení. Můžete nechat destruktor objektu [CDC](../../mfc/reference/cdc-class.md) , nebo jej můžete provést explicitně voláním metody [CDC::D eletedc](../../mfc/reference/cdc-class.md#deletedc).

##  <a name="cwinapp"></a>CWinApp:: CWinApp

Vytvoří objekt a předá lpszAppName, aby se uložil jako název aplikace. `CWinApp`

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszAppName*<br/>
Řetězec zakončený hodnotou null, který obsahuje název aplikace, který používá systém Windows. Pokud tento argument není zadán nebo je null, `CWinApp` používá řetězec prostředků AFX_IDS_APP_TITLE nebo název souboru spustitelného souboru.

### <a name="remarks"></a>Poznámky

Měli byste vytvořit jeden globální objekt `CWinApp`odvozené třídy. V aplikaci může být pouze `CWinApp` jeden objekt. Konstruktor ukládá ukazatel na `CWinApp` objekt, `WinMain` aby mohl volat členské funkce objektu pro inicializaci a spuštění aplikace.

##  <a name="delregtree"></a>CWinApp::D elRegTree

Odstraní konkrétní klíč registru a všechny jeho podklíče.

```
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName);

LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hParentKey*<br/>
Zpracování klíče registru.

*strKeyName*<br/>
Název klíče registru, který se má odstranit

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="remarks"></a>Poznámky

Voláním této funkce odstraníte zadaný klíč a jeho podklíče.

##  <a name="domessagebox"></a>  CWinApp::DoMessageBox

Rozhraní volá tuto členskou funkci, aby implementovala okno se zprávou pro globální funkci [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parametry

*lpszPrompt*<br/>
Adresa textu v okně se zprávou.

*nType*<br/>
[Styl](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)okna se zprávou

*nIDPrompt*<br/>
Index pro řetězec kontextu v nápovědě.

### <a name="return-value"></a>Návratová hodnota

Vrátí stejné hodnoty jako `AfxMessageBox`.

### <a name="remarks"></a>Poznámky

Nevolejte tuto členskou funkci, aby otevřela okno se zprávou. místo `AfxMessageBox` toho použijte.

Přepište tuto členskou funkci pro přizpůsobení zpracování `AfxMessageBox` volání v rámci aplikace.

##  <a name="dowaitcursor"></a>CWinApp::D oWaitCursor

Tato členská funkce je volána rozhraním pro implementaci [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget:: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget:: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)a [CCmdTarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parametry

*nCode*<br/>
Pokud je tento parametr 1, zobrazí se kurzor čekání. Pokud je nastaveno na hodnotu 0, je obnovený kurzor bez zvýšení počtu odkazů. Pokud-1, konec čekání končí.

### <a name="remarks"></a>Poznámky

Výchozí hodnota implementuje ukazatel přesýpacích hodin. `DoWaitCursor`udržuje počet odkazů. Pokud je pozitivní, zobrazí se ukazatel přesýpacích hodin.

I když byste jinak nevolali `DoWaitCursor` přímo, můžete tuto členskou funkci přepsat, chcete-li změnit čekací ukazatel nebo provést další zpracování, zatímco se zobrazí čekací kurzor.

Pro snazší a efektivnější způsob implementace čekacího kurzoru použijte `CWaitCursor`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="enabled2dsupport"></a>CWinApp:: EnableD2DSupport

Je požadována sada Visual Studio 2010 SP1.

Povolí podporu D2D aplikace. Před inicializací hlavního okna volejte tuto metodu.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFactoryType*<br/>
Model vláken objektu D2D Factory a prostředky, které vytváří.

*writeFactoryType*<br/>
Hodnota, která určuje, zda bude objekt factory pro zápis sdílen nebo izolován

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byla povolena podpora D2D, FALSE – jinak.

##  <a name="enablehtmlhelp"></a>CWinApp:: EnableHtmlHelp

Zavolejte tuto členskou funkci z konstruktoru vaší `CWinApp`odvozené třídy pro použití HTMLHelp pro nápovědu vaší aplikace.

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>Poznámky

##  <a name="enableshellopen"></a>CWinApp:: EnableShellOpen

Voláním této funkce, obvykle z `InitInstance` přepsání, umožníte uživatelům vaší aplikace otevírat datové soubory, když dvakrát kliknete na soubory ve Správci souborů systému Windows.

```
void EnableShellOpen();
```

### <a name="remarks"></a>Poznámky

`RegisterShellFileTypes` Zavolejte členskou funkci ve spojení s touto funkcí nebo zadejte. Soubor REG s vaší aplikací pro ruční registraci typů dokumentů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="enabletaskbarinteraction"></a>CWinApp:: EnableTaskbarInteraction

Povoluje interakci hlavního panelu.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda má být povolena interakce s hlavním panelem systému Windows 7 (TRUE) nebo zakázáno (FALSE).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud je možné zapnout nebo vypnout interakci na hlavním panelu.

### <a name="remarks"></a>Poznámky

Tato metoda musí být volána před vytvořením hlavního okna, jinak uplatňuje a vrátí hodnotu FALSE.

##  <a name="exitinstance"></a>CWinApp:: ExitInstance

Volá se rozhraním v rámci `Run` členské funkce, aby se ukončila tato instance aplikace.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Ukončovací kód aplikace; 0 značí žádné chyby a hodnoty větší než 0 označují chybu. Tato hodnota se používá jako návratová hodnota z `WinMain`.

### <a name="remarks"></a>Poznámky

Nevolejte tuto členskou funkci odkudkoli, `Run` ale v rámci členské funkce.

Výchozí implementace této funkce zapisuje možnosti rozhraní do aplikace. Soubor INI. Přepište tuto funkci, aby se vyčistila při ukončení aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="getapplicationrecoveryparameter"></a>CWinApp:: GetApplicationRecoveryParameter

Načte vstupní parametr pro metodu obnovení aplikace.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí vstupní parametr pro metodu obnovení aplikace.

### <a name="remarks"></a>Poznámky

Výchozí chování této funkce vrací hodnotu NULL.

Další informace naleznete v tématu [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).

##  <a name="getapplicationrecoverypinginterval"></a>CWinApp:: GetApplicationRecoveryPingInterval

Vrátí dobu, po kterou správce restartování počká, až vrátí funkci zpětného volání pro obnovení.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Návratová hodnota

Délka času v milisekundách.

### <a name="remarks"></a>Poznámky

Při neočekávaném ukončení aplikace, která je zaregistrována správcem restartování, se aplikace pokusí uložit otevřené dokumenty a zavolá funkci zpětného volání pro obnovení. Výchozí funkce zpětného volání pro obnovení je [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).

Doba, po kterou Framework čeká na vrácení funkce zpětného volání pro obnovení, je intervalem testu. Můžete přizpůsobit interval pro odesílání pomocí přepsání `CWinApp::GetApplicationRecoveryPingInterval` nebo zadáním vlastní hodnoty na. `RegisterWithRestartManager`

##  <a name="getapplicationrestartflags"></a>CWinApp:: GetApplicationRestartFlags

Vrátí příznaky pro správce restartování.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Návratová hodnota

Příznaky pro správce restartování Výchozí implementace vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Příznaky pro správce restartování nemají žádný vliv na výchozí implementaci. Jsou k dispozici pro budoucí použití.

Příznaky se nastavují při registraci aplikace pomocí správce restartování pomocí [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager).

Možné hodnoty pro příznaky správce restartování jsou následující:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="getappregistrykey"></a>CWinApp:: GetAppRegistryKey

Vrátí klíč pro HKEY_CURRENT_USER\\"software" \RegistryKey\ProfileName.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*pTM*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Klíč aplikace, pokud je funkce úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

##  <a name="getdatarecoveryhandler"></a>CWinApp:: GetDataRecoveryHandler

Získá obslužnou rutinu obnovení dat pro tuto instanci aplikace.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Návratová hodnota

Obslužná rutina obnovení dat pro tuto instanci aplikace.

### <a name="remarks"></a>Poznámky

Každá aplikace, která používá správce restartování, musí mít jednu instanci [třídy CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Tato třída zodpovídá za monitorování otevřených dokumentů a souborů pro automatické ukládání. Chování `CDataRecoveryHandler` závisí na konfiguraci správce restartování. Další informace naleznete v tématu [Třída CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md).

Tato metoda vrátí hodnotu NULL v operačních systémech starších než Windows Vista. Správce restartování není podporován v operačních systémech starších než Windows Vista.

Pokud aplikace aktuálně nemá obslužnou rutinu obnovení dat, tato metoda vytvoří jeden a vrátí ukazatel na něj.

##  <a name="getfirstdoctemplateposition"></a>CWinApp:: GetFirstDocTemplatePosition

Získá pozici první šablony dokumentu v aplikaci.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, která se dá použít pro načtení ukazatele iterace nebo objektu; Hodnota NULL, pokud je seznam prázdný.

### <a name="remarks"></a>Poznámky

Použijte hodnotu pozice vrácenou voláním [GetNextDocTemplate](#getnextdoctemplate) k získání prvního objektu [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md) .

##  <a name="gethelpmode"></a>CWinApp:: GetHelpMode

Načte typ nápovědě, kterou aplikace používá.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Návratová hodnota

Typ nápovědě používaný aplikací Další informace naleznete v části [CWinApp:: m_eHelpType](#m_ehelptype) .

##  <a name="getnextdoctemplate"></a>CWinApp:: GetNextDocTemplate

Načte šablonu dokumentu identifikovanou *POS*a pak nastaví *POS* na hodnotu pozice.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Odkaz na hodnotu pozice vrácený předchozím voláním `GetNextDocTemplate` nebo [GetFirstDocTemplatePosition](#getfirstdoctemplateposition). Hodnota je aktualizována na další pozici tímto voláním.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md) .

### <a name="remarks"></a>Poznámky

Můžete použít `GetNextDocTemplate` ve smyčce dopředné iteraci, pokud vytvoříte počáteční pozici s `GetFirstDocTemplatePosition`voláním.

Je nutné zajistit, aby byla hodnota pozice platná. Pokud je neplatný, ladicí verze knihovna Microsoft Foundation Class výrazy.

Pokud je načtená šablona dokumentu poslední k dispozici, je nová hodnota *POS* nastavena na hodnotu null.

##  <a name="getprinterdevicedefaults"></a>CWinApp:: GetPrinterDeviceDefaults

Zavolejte tuto členskou funkci pro přípravu kontextu zařízení tiskárny pro tisk.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parametry

*pPrintDlg*<br/>
Ukazatel na strukturu [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Načte aktuální výchozí nastavení tiskárny z Windows. Soubor INI podle potřeby nebo použije poslední konfiguraci tiskárny nastavenou uživatelem v nastavení tisku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="getprofilebinary"></a>CWinApp:: GetProfileBinary

Zavolejte tuto členskou funkci pro načtení binárních dat ze záznamu v rámci zadaného oddílu registru aplikace nebo. Soubor INI.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž hodnota má být načtena.

*ppData*<br/>
Odkazuje na ukazatel, který získá adresu dat.

*pBytes*<br/>
Odkazuje na UINT, který získá velikost dat (v bajtech).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce nerozlišuje velká a malá písmena, takže řetězce v parametrech *lpszSection* a *lpszEntry* se můžou v případě potřeby lišit.

> [!NOTE]
> `GetProfileBinary`přidělí vyrovnávací paměť a vrátí její adresu v \* *ppData*. Volající je zodpovědný za uvolnění vyrovnávací paměti pomocí **DELETE []** .

> [!IMPORTANT]
> Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Další příklad naleznete v tématu [CWinApp:: WriteProfileBinary](#writeprofilebinary).

##  <a name="getprofileint"></a>CWinApp:: GetProfileInt

Voláním této členské funkce lze získat hodnotu celého čísla z položky v určitém oddíle registru aplikace nebo souboru .INI.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž hodnota má být načtena.

*nDefault*<br/>
Určuje výchozí vrácenou hodnotu, pokud rozhraní položku nemůže najít.

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota řetězce, který následuje zadanou položku, pokud je funkce úspěšná. Návratová hodnota je hodnota parametru *nDefault* , pokud funkce danou položku nenajde. Vrácená hodnota je 0, pokud hodnota, která odpovídá zadané položce, není celé číslo.

Tato členská funkce podporuje šestnáctkovou notaci hodnot v souboru .INI. Když načtete celé číslo se znaménkem, měli byste přetypovat hodnotu na **int**.

### <a name="remarks"></a>Poznámky

Tato členská funkce nerozlišuje velká a malá písmena, takže řetězce v parametrech *lpszSection* a *lpszEntry* se můžou v případě potřeby lišit.

> [!IMPORTANT]
> Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Další příklad naleznete v tématu [CWinApp:: WriteProfileInt](#writeprofileint).

##  <a name="getprofilestring"></a>CWinApp:: GetProfileString

Zavolejte tuto členskou funkci pro načtení řetězce přidruženého k položce v rámci zadané části v registru aplikace nebo. Soubor INI.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž řetězec má být načten. Tato hodnota nesmí být NULL.

*lpszDefault*<br/>
Odkazuje na výchozí hodnotu řetězce pro danou položku, pokud položka nebyla nalezena v inicializačním souboru.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je řetězec z aplikace. Soubor INI nebo *lpszDefault* , pokud řetězec nebyl nalezen. Maximální délka řetězce podporovaná rozhraním je _MAX_PATH. Pokud má *lpszDefault* hodnotu null, návratová hodnota je prázdný řetězec.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Další příklad naleznete v příkladu pro [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="getsectionkey"></a>CWinApp:: GetSectionKey

Vrátí klíč pro HKEY_CURRENT_USER\\"software" \RegistryKey\AppName\lpszSection.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Název klíče, který se má získat.

*pTM*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Klíč oddílu, pokud je funkce úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

##  <a name="hideapplication"></a>CWinApp:: HideApplication

Tuto členskou funkci volejte pro skrytí aplikace před zavřením otevřených dokumentů.

```
void HideApplication();
```

##  <a name="htmlhelp"></a>CWinApp:: HtmlHelp

Zavolejte tuto členskou funkci pro vyvolání aplikace HTMLHelp.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parametry

*dwData*<br/>
Určuje další data. Použitá hodnota závisí na hodnotě parametru *nCmd* . Ve výchozím nastavení to znamená [HH_HELP_CONTEXT.](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command) `0x000F`

*nCmd*<br/>
Určuje typ požadované aplikace Help. Seznam možných hodnot a jejich vliv na parametr *dwData* naleznete v parametru *uCommand* popsaném ve funkcích [HtmlHelpW](/windows/desktop/api/htmlhelp/nf-htmlhelp-htmlhelpw) nebo [HtmlHelpA](/windows/desktop/api/htmlhelp/nf-htmlhelp-htmlhelpa) rozhraní API v Windows SDK.  

### <a name="remarks"></a>Poznámky

Rozhraní také volá tuto funkci k vyvolání aplikace HTMLHelp.

Rozhraní při ukončení aplikace automaticky zavře aplikaci HTMLHelp.

##  <a name="initinstance"></a>CWinApp:: InitInstance

Systém Windows umožňuje spustit několik kopií stejného programu současně.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Inicializace aplikace je koncepčně rozdělena do dvou částí: jednorázová inicializace aplikace, která se provede při prvním spuštění programu, a inicializaci instance, která se spustí pokaždé, když se spustí kopie programu, včetně prvního. Implementace tohoto rozhraní `WinMain` volá tuto funkci.

Přepište `InitInstance` pro inicializaci každé nové instance aplikace spuštěné v systému Windows. Obvykle můžete přepsat `InitInstance` sestavení objektu hlavního okna a `CWinThread::m_pMainWnd` nastavit datový člen tak, aby odkazoval na toto okno. Další informace o přepsání této členské funkce naleznete v tématu [CWinApp: Třída](../../mfc/cwinapp-the-application-class.md)aplikace

> [!NOTE]
> Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Pokud zavoláte [funkce CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) do `InitInstance` svého přepsání, zadejte COINIT_APARTMENTTHREADED (místo COINIT_MULTITHREADED).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="istaskbarinteractionenabled"></a>  CWinApp::IsTaskbarInteractionEnabled

Určuje, zda je povolena interakce hlavního panelu systému Windows 7.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true `EnableTaskbarInteraction` , pokud byla volána a operační systém Windows 7 nebo novější.

### <a name="remarks"></a>Poznámky

Interakce hlavního panelu znamená, že aplikace MDI zobrazuje obsah podřízených objektů MDI v samostatných miniaturách s kartami, které se zobrazí, když je ukazatel myši nad tlačítkem aplikace na hlavním panelu.

##  <a name="loadcursor"></a>CWinApp:: LoadCursor

Načte prostředek Cursor s názvem *lpszResourceName* nebo zadaný pomocí *nIDResource* z aktuálního spustitelného souboru.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název prostředku kurzoru. `CString` Pro tento argument můžete použít.

*nIDResource*<br/>
ID prostředku kurzoru Seznam prostředků najdete v tématu [LoadCursor](/windows/desktop/api/winuser/nf-winuser-loadcursora) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ukazatel, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

`LoadCursor`Načte kurzor do paměti pouze v případě, že nebyl dříve načten; v opačném případě načte popisovač existujícího prostředku.

Pro přístup k předdefinovaným Kurzorům Windows použijte členskou funkci [LoadStandardCursor](#loadstandardcursor) nebo [LoadOEMCursor](#loadoemcursor) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="loadicon"></a>CWinApp:: LoadIcon

Načte prostředek Icon s názvem *lpszResourceName* nebo zadaný pomocí *nIDResource* ze spustitelného souboru.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název prostředku ikony. `CString` Pro tento argument můžete použít také.

*nIDResource*<br/>
Číslo ID prostředku ikony

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu, pokud je úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

`LoadIcon`Načte ikonu pouze v případě, že nebyla dříve načtena; v opačném případě načte popisovač existujícího prostředku.

Pro přístup k předdefinovaným ikonám Windows můžete použít členskou funkci [LoadStandardIcon](#loadstandardicon) nebo [LoadOEMIcon](#loadoemicon) .

> [!NOTE]
> Tato členská funkce volá funkci Win32 API [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona), která může načíst jenom ikonu, jejíž velikost odpovídá hodnotám systémové metriky SM_CXICON a SM_CYICON.

##  <a name="loadoemcursor"></a>CWinApp:: LoadOEMCursor

Načte prostředek předdefinovaného kurzoru systému Windows určený parametrem *nIDCursor*.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parametry

*nIDCursor*<br/>
Identifikátor konstanty manifestu **OCR_** , který určuje předdefinovaný kurzor Windows. Abyste mohli získat `#define OEMRESOURCE` přístup `#include \<afxwin.h>` k konstantám **OCR_** ve Windows, musíte mít dřív. Y.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ukazatel, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pro přístup k [](#loadstandardcursor) předdefinovaným Kurzorům Windows použijte členskou funkci nebo`LoadOEMCursor` LoadStandardCursor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="loadoemicon"></a>CWinApp:: LoadOEMIcon

Načte prostředek předdefinované ikony systému Windows určený parametrem *nIDIcon*.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parametry

*nIDIcon*<br/>
Identifikátor konstanty manifestu **OIC_** , který určuje předdefinovanou ikonu Windows. K konstantám `#define OEMRESOURCE` **OIC_** ve Windows musíte mít přístup. `#include \<afxwin.h>` Y.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu, pokud je úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Pro přístup k [](#loadstandardicon) předdefinovaným ikonám Windows použijte členskou funkci nebo`LoadOEMIcon` LoadStandardIcon.

##  <a name="loadstandardcursor"></a>CWinApp:: LoadStandardCursor

Načte prostředek předdefinovaného kurzoru Windows, který *lpszCursorName* určuje.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parametry

*lpszCursorName*<br/>
Identifikátor konstanty manifestu **IDC_** , který určuje předdefinovaný kurzor Windows. Tyto identifikátory jsou definované v systému WINDOWS. Y. Následující seznam uvádí možné předdefinované hodnoty a významy pro *lpszCursorName*:

- IDC_ARROW – standardní ukazatel na šipky

- IDC_IBEAM standardní text – vložení kurzoru

- IDC_WAIT přesýpací hodiny použité v případě, že systém Windows provádí časově náročný úkol

- IDC_CROSS křížek – kurzor pro výběr

- IDC_UPARROW šipka, která ukazuje rovnou nahoru

- IDC_SIZE zastaralá a Nepodporovaná; použití IDC_SIZEALL

- IDC_SIZEALL šipky se čtyřmi body. Kurzor, který se má použít pro změnu velikosti okna.

- IDC_ICON zastaralá a Nepodporovaná. Použijte IDC_ARROW.

- IDC_SIZENWSE dvojitou šipku nahoru a dolů v pravém horním rohu

- IDC_SIZENESW šipka s dvojitou šipkou a končí nahoře vpravo a vlevo dole.

- IDC_SIZEWE vodorovně obousměrnou šipkou

- IDC_SIZENS svislé obousměrné šipky

### <a name="return-value"></a>Návratová hodnota

Popisovač na ukazatel, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pro přístup k [](#loadoemcursor) předdefinovaným Kurzorům Windows použijte členskou funkci nebo`LoadStandardCursor` LoadOEMCursor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="loadstandardicon"></a>CWinApp:: LoadStandardIcon

Načte prostředek předdefinované ikony Windows, který *lpszIconName* určuje.

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parametry

*lpszIconName*<br/>
Identifikátor konstanty manifestu, který určuje předdefinovanou ikonu systému Windows. Tyto identifikátory jsou definované v systému WINDOWS. Y. Seznam možných předdefinovaných hodnot a jejich popisů naleznete v parametru *lpIconName* v [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu, pokud je úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Pro přístup k [](#loadoemicon) předdefinovaným ikonám Windows použijte členskou funkci nebo`LoadStandardIcon` LoadOEMIcon.

##  <a name="loadstdprofilesettings"></a>CWinApp:: LoadStdProfileSettings

Voláním této členské funkce z členské funkce [InitInstance](#initinstance) povolíte a načtete seznam naposledy použitých souborů (MRU) a poslední stav verze Preview.

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parametry

*nMaxMRU*<br/>
Počet naposledy použitých souborů ke sledování.

### <a name="remarks"></a>Poznámky

Pokud je *nMaxMRU* 0, nebude zachován žádný seznam naposledy použitých položek.

##  <a name="m_bhelpmode"></a>CWinApp:: m_bHelpMode

TRUE, pokud je aplikace v kontextovém režimu pro nápovědu (konvence vyvolaná pomocí SHIFT + F1); v opačném případě FALSE.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Poznámky

V kontextovém režimu se kurzor zobrazí jako otazník a uživatel ho může přesunout na obrazovku. Pokud chcete v režimu Help implementovat zvláštní zpracování, Projděte si tento příznak. `m_bHelpMode`je veřejná proměnná typu BOOL.

##  <a name="m_dwrestartmanagersupportflags"></a>  CWinApp::m_dwRestartManagerSupportFlags

Příznaky, které určují, jak se chovají správce restartování.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Poznámky

Pokud chcete správce restartování povolit, nastavte `m_dwRestartManagerSupportFlags` požadované chování. V následující tabulce jsou uvedeny příznaky, které jsou k dispozici.

|||
|-|-|
|Příznak|Popis|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Aplikace je zaregistrována pomocí [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager). Správce restartování zodpovídá za restartování aplikace, pokud se nečekaně ukončí.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Aplikace je zaregistrována se správcem restartování a správce restartování volá funkci zpětného volání pro obnovení při restartu aplikace. Výchozí funkce zpětného volání pro obnovení je [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Automatické ukládání je povolené a správce restartování automaticky uloží všechny otevřené dokumenty, když se aplikace restartuje.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Automatické ukládání je povolené a správce restartování automaticky ukládá všechny otevřené dokumenty v pravidelných intervalech. Interval je definován pomocí [CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval).|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Správce restartování otevře dříve otevřené dokumenty po restartování aplikace z neočekávaného ukončení. [Třída CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) ukládá seznam otevřených dokumentů a obnovuje je.|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Správce restartování vyzve uživatele, aby obnovil automaticky uložené soubory po restartování aplikace. `CDataRecoveryHandler` Třída se dotazuje na uživatele.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Sjednocení AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER a AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Sjednocení AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Sjednocení AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Union ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

##  <a name="m_ehelptype"></a>CWinApp:: m_eHelpType

Typ tohoto datového členu je výčtový typ AFX_HELP_TYPE, který je definován v rámci `CWinApp` třídy.

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Poznámky

Výčet AFX_HELP_TYPE je definován následujícím způsobem:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Chcete-li nastavit nápovědě aplikace na HTML, zavolejte [SetHelpMode](#sethelpmode) a zadejte `afxHTMLHelp`.

- Chcete-li nastavit pomocníka aplikace na WinHelp, `SetHelpMode` zavolejte a `afxWinHelp`zadejte.

##  <a name="m_hinstance"></a>  CWinApp::m_hInstance

Odpovídá parametru *HINSTANCE* předanému systémem Windows do `WinMain`.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Poznámky

`m_hInstance` Datový člen je popisovač aktuální instance aplikace spuštěné v systému Windows. Toto je vráceno globální funkcí [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance`je veřejná proměnná typu HINSTANCE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="m_lpcmdline"></a>CWinApp:: m_lpCmdLine

Odpovídá parametru *lpCmdLine* předanému systémem Windows do `WinMain`.

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Poznámky

Odkazuje na řetězec zakončený hodnotou null, který určuje příkazový řádek pro aplikaci. Použijte `m_lpCmdLine` pro přístup k jakýmkoli argumentům příkazového řádku, které uživatel zadal při spuštění aplikace. `m_lpCmdLine`je veřejná proměnná typu LPTSTR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="m_nautosaveinterval"></a>CWinApp:: m_nAutosaveInterval

Doba v milisekundách mezi automaticky uloženými hodnotami.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Poznámky

Správce restartování můžete nakonfigurovat tak, aby se v nastavených intervalech automaticky restartovaly otevřené dokumenty. Pokud vaše aplikace neumožňuje ukládat soubory, nemá tento parametr žádný vliv.

##  <a name="m_ncmdshow"></a>CWinApp:: m_nCmdShow

Odpovídá parametru *nCmdShow* předanému systémem Windows do `WinMain`.

```
int m_nCmdShow;
```

### <a name="remarks"></a>Poznámky

Při volání `m_nCmdShow` [CWnd::: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) pro hlavní okno vaší aplikace byste měli předat jako argument. `m_nCmdShow`je veřejná proměnná typu **int**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="m_pactivewnd"></a>CWinApp:: m_pActiveWnd

Tento datový člen slouží k uložení ukazatele do hlavního okna aplikace typu kontejner OLE, ve kterém je vaše aplikace serveru OLE aktivována místně.

### <a name="remarks"></a>Poznámky

Pokud je tento datový člen NULL, aplikace není na místě aktivní.

Rozhraní nastavuje tuto členskou proměnnou, když je okno rámce na místě aktivované aplikací kontejneru OLE.

##  <a name="m_pdatarecoveryhandler"></a>CWinApp:: m_pDataRecoveryHandler

Ukazatel na popisovač obnovení dat pro aplikaci.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Poznámky

Obslužná rutina obnovení dat aplikace monitoruje otevřené dokumenty a automaticky je ukládá. Rozhraní používá obslužnou rutinu obnovení dat k obnovení souborů automaticky uloženého po restartování aplikace po neočekávaném ukončení. Další informace naleznete v tématu [Třída CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md).

##  <a name="m_pszappname"></a>CWinApp:: m_pszAppName

Určuje název aplikace.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Poznámky

Název aplikace může pocházet z parametru předaného konstruktoru [CWinApp](#cwinapp) nebo, pokud není zadán, k řetězci prostředku s ID AFX_IDS_APP_TITLE. Pokud se název aplikace v prostředku nenajde, pochází z programu. Název souboru EXE.

Vráceno globální funkcí [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName`je veřejná proměnná typu const **char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte hodnotu k `m_pszAppName`, je nutné ji dynamicky přidělit na haldu. Destruktor volá Free () s tímto ukazatelem. `CWinApp` Chcete použít `_tcsdup`funkci běhové knihovny () pro přidělení. Než přiřadíte novou hodnotu, uvolněte také paměť přidružená k aktuálnímu ukazateli. Příklad:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="m_pszexename"></a>CWinApp:: m_pszExeName

Obsahuje název spustitelného souboru aplikace bez přípony.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Poznámky

Na rozdíl od [m_pszAppName](#m_pszappname)nesmí tento název obsahovat prázdné znaky. `m_pszExeName`je veřejná proměnná typu const **char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte hodnotu k `m_pszExeName`, je nutné ji dynamicky přidělit na haldu. Destruktor volá Free () s tímto ukazatelem. `CWinApp` Chcete použít `_tcsdup`funkci běhové knihovny () pro přidělení. Než přiřadíte novou hodnotu, uvolněte také paměť přidružená k aktuálnímu ukazateli. Příklad:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="m_pszhelpfilepath"></a>  CWinApp::m_pszHelpFilePath

Obsahuje cestu k souboru Help aplikace.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se rozhraní inicializuje `m_pszHelpFilePath` na název aplikace pomocí ". Připojí se HLP. Chcete-li změnit název souboru s příponou Help `m_pszHelpFilePath` , nastavte ukazatel na řetězec, který obsahuje úplný název požadovaného souboru Help. Vhodným místem, jak to udělat, je funkce [InitInstance](#initinstance) aplikace. `m_pszHelpFilePath`je veřejná proměnná typu const **char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte hodnotu k `m_pszHelpFilePath`, je nutné ji dynamicky přidělit na haldu. Destruktor volá Free () s tímto ukazatelem. `CWinApp` Chcete použít `_tcsdup`funkci běhové knihovny () pro přidělení. Než přiřadíte novou hodnotu, uvolněte také paměť přidružená k aktuálnímu ukazateli. Příklad:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName

Obsahuje název aplikace. Soubor INI.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Poznámky

`m_pszProfileName`je veřejná proměnná typu const **char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte hodnotu k `m_pszProfileName`, je nutné ji dynamicky přidělit na haldu. Destruktor volá Free () s tímto ukazatelem. `CWinApp` Chcete použít `_tcsdup`funkci běhové knihovny () pro přidělení. Než přiřadíte novou hodnotu, uvolněte také paměť přidružená k aktuálnímu ukazateli. Příklad:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="m_pszregistrykey"></a>  CWinApp::m_pszRegistryKey

Slouží k určení, kde v registru nebo souboru INI se ukládají nastavení profilu aplikace.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Poznámky

Obvykle je tento datový člen považován za jen pro čtení.

- Hodnota je uložena do klíče registru. Název nastavení profilu aplikace se připojí k následujícímu klíči registru: HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/.

Pokud přiřadíte hodnotu k `m_pszRegistryKey`, je nutné ji dynamicky přidělit na haldu. Destruktor volá Free () s tímto ukazatelem. `CWinApp` Chcete použít `_tcsdup`funkci běhové knihovny () pro přidělení. Než přiřadíte novou hodnotu, uvolněte také paměť přidružená k aktuálnímu ukazateli. Příklad:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID

ID modelu uživatele aplikace

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Poznámky

##  <a name="oncontexthelp"></a>CWinApp:: OnContextHelp

Zpracovává nápovědu SHIFT + F1 v rámci aplikace.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy a také přidat položku tabulky akcelerátoru, obvykle SHIFT + F1.

`OnContextHelp`Vloží aplikaci do režimu help. Kurzor se změní na šipku a otazník a uživatel pak může přesunout ukazatel myši a stisknutím levého tlačítka myši vybrat dialogové okno, okno, nabídku nebo příkazové tlačítko. Tato členská funkce načte kontext nápovědy objektu pod kurzorem a zavolá funkci Windows WinHelp s tímto kontextem nápovědy.

##  <a name="onddecommand"></a>CWinApp:: OnDDECommand

Volá se rozhraním, když hlavní okno rámce obdrží zprávu Execute DDE.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parametry

*lpszCommand*<br/>
Odkazuje na řetězec příkazu DDE přijatý aplikací.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je příkaz zpracován; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace ověří, zda je příkaz žádost o otevření dokumentu, a pokud ano, otevře zadaný dokument. Správce souborů systému Windows obvykle odesílá řetězce příkazů DDE, když uživatel dvakrát klikne na datový soubor. Tuto funkci potlačíte, pokud chcete zpracovat jiné příkazy DDE, jako je například příkaz pro tisk.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="onfilenew"></a>CWinApp:: OnFileNew

Implementuje příkaz ID_FILE_NEW.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_FILE_NEW, OnFileNew )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Pokud je tato funkce povolena, zpracovává spuštění příkazu soubor nový.

Informace o výchozím chování a návodech k tomu, jak tuto členskou funkci přepsat, najdete v tématu [technické poznámky 22](../../mfc/tn022-standard-commands-implementation.md) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileopen"></a>CWinApp:: OnFileOpen

Implementuje příkaz ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Pokud je tato funkce povolena, zpracovává spuštění příkazu otevřít soubor.

Informace o výchozím chování a návodech k tomu, jak tuto členskou funkci přepsat, najdete v části [technická Poznámka 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileprintsetup"></a>CWinApp:: OnFilePrintSetup

Implementuje příkaz ID_FILE_PRINT_SETUP.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Pokud je tato funkce povolena, zpracovává příkaz pro tisk souboru.

Informace o výchozím chování a návodech k tomu, jak tuto členskou funkci přepsat, najdete v části [technická Poznámka 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onhelp"></a>CWinApp:: InHelp

Zpracovává nápovědu F1 v rámci aplikace (pomocí aktuálního kontextu).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Poznámky

Obvykle přidáte také položku akcelerátor-klíč pro klávesu F1. Povolení klávesy F1 je pouze konvence, nikoli požadavek.

Chcete-li povolit `ON_COMMAND( ID_HELP, OnHelp )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Pokud je povoleno, volá se rozhraním, když uživatel stiskne klávesu F1.

Výchozí implementace této funkce obslužných rutin zpráv určuje kontext nápovědy, který odpovídá aktuálnímu oknu, dialogovému oknu nebo položce nabídky a potom volá WINHELP. Programu. Pokud není aktuálně k dispozici žádný kontext, funkce použije výchozí kontext.

Přepište tuto členskou funkci pro nastavení kontextu kontextové aplikace na jinou hodnotu než okno, dialogové okno, položku nabídky nebo tlačítko panelu nástrojů, které aktuálně má fokus. Zavolejte `WinHelp` s požadovaným identifikátorem kontextu helpu.

##  <a name="onhelpfinder"></a>CWinApp:: OnHelpFinder

Zpracovává příkazy ID_HELP_FINDER a ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Pokud je povoleno, rozhraní zavolá tuto funkci obslužné rutiny zpráv, když uživatel vaší aplikace vybere příkaz help Finder, který `WinHelp` se má vyvolat pomocí standardního tématu **HELP_FINDER** .

##  <a name="onhelpindex"></a>CWinApp:: OnHelpIndex

Zpracuje příkaz ID_HELP_INDEX a poskytne výchozí téma nápovědy.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Pokud je povoleno, rozhraní zavolá tuto funkci obslužné rutiny zpráv, když uživatel vaší aplikace vybere příkaz index nápovědy, který `WinHelp` se má vyvolat pomocí standardního tématu **HELP_INDEX** .

##  <a name="onhelpusing"></a>CWinApp:: OnHelpUsing

Zpracuje příkaz ID_HELP_USING.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` tuto členskou funkci `CWinApp` , je nutné přidat příkaz k mapě zpráv třídy. Rozhraní volá tuto funkci obslužné rutiny zpráv, když uživatel vaší aplikace vybere nápovědu pomocí příkazu k vyvolání `WinHelp` aplikace pomocí standardního tématu **HELP_HELPONHELP** .

##  <a name="onidle"></a>CWinApp:: OnIdle

Přepište tuto členskou funkci, aby prováděla zpracování nečinných časů.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
V případě, že je fronta `OnIdle` zpráv aplikace prázdná, dojde při každém volání čítače k jeho zvýšení. Tento počet se resetuje na 0 pokaždé, když se zpracuje nová zpráva. Pomocí parametru *lCount* můžete určit relativní dobu nečinnosti aplikace bez zpracování zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud chcete získat větší dobu nečinnosti při zpracování; 0, pokud není potřeba žádná další doba nečinnosti.

### <a name="remarks"></a>Poznámky

`OnIdle`se volá ve výchozí smyčce zpráv, když je fronta zpráv aplikace prázdná. Použijte své přepsání pro volání vlastních úloh obslužných rutin nečinných na pozadí.

`OnIdle`by měl vrátit 0, aby označoval, že není potřeba žádná nečinná doba zpracování. Parametr *lCount* se pokaždé zvýší pokaždé `OnIdle` , když se zavolá, když je fronta zpráv prázdná, a při každém zpracování nové zprávy se resetuje na 0. Na základě tohoto počtu můžete volat různé nečinné rutiny.

Následující shrnuje zpracování nečinných smyček:

1. Pokud smyčka zpráv v Knihovna Microsoft Foundation Class kontroluje frontu zpráv a nenajde žádné čekající zprávy, volá `OnIdle` objekt aplikace a jako argument *lCount* dodá 0.

2. `OnIdle`provede nějaké zpracování a vrátí nenulovou hodnotu, aby označoval, že by měl být znovu volán pro další zpracování.

3. Smyčka zpráv znovu vyhledá frontu zpráv. Pokud nečekají žádné zprávy, volá `OnIdle` se znovu a zvýší se argument *lCount* .

4. `OnIdle` Nakonec dokončí zpracování všech nečinných úloh a vrátí hodnotu 0. Tím se zaznamená, že smyčka `OnIdle` zpráv přestane volat, dokud nebude přijata další zpráva z fronty zpráv. v takovém případě je nečinný cyklus restartován s argumentem nastaveným na hodnotu 0.

Neprovádějte úlohy s zdlouhavými úlohami `OnIdle` , protože aplikace nemůže zpracovat vstup uživatele, dokud `OnIdle` se nevrátí.

> [!NOTE]
> Výchozí implementace `OnIdle` příkazů aktualizovat objekty uživatelského rozhraní, jako jsou položky nabídky a tlačítka panelu nástrojů, a provádí vyčištění interní struktury dat. Proto pokud přepíšete `OnIdle`, je nutné volat `CWinApp::OnIdle` s `lCount` v přepsané verzi. Nejdřív zavolejte všechny nečinné zpracování základní třídy (to znamená, dokud základní třída `OnIdle` nevrátí hodnotu 0). Pokud potřebujete provést práci, než se dokončí zpracování základní třídy, zkontrolujte implementaci základní třídy, abyste vybrali správný *lCount* , během kterého budete pracovat.

Pokud nechcete `OnIdle` být voláni pokaždé, když je načtena zpráva z fronty zpráv, můžete přepsat [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Pokud aplikace nastavila velmi krátký časovač, nebo pokud systém odesílá zprávu WM_SYSTIMER, `OnIdle` bude volána opakovaně a snižuje výkon.

### <a name="example"></a>Příklad

Následující dva příklady ukazují, jak používat `OnIdle`. První příklad zpracovává dvě nečinné úlohy pomocí argumentu *lCount* k určení priorit úloh. První úkol má vysokou prioritu a měli byste to udělat, kdykoli to bude možné. Druhá úloha je méně důležitá a měla by se provést pouze v případě, že se vstup uživatele dlouhou dobu pozastavuje. Poznamenejte si volání verze `OnIdle`základní třídy. Druhý příklad spravuje skupinu nečinných úloh s různými prioritami.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="opendocumentfile"></a>CWinApp:: OpenDocumentFile

Rozhraní volá tuto metodu, aby otevřela pojmenovaný soubor [objektu CDocument](../../mfc/reference/cdocument-class.md) pro aplikaci.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
pro Název souboru, který se má otevřít

*bAddToMRU*<br/>
pro Hodnota TRUE označuje, že dokument je jedním z nejaktuálnějších souborů; Hodnota FALSE znamená, že dokument není jedním z nejaktuálnějších souborů.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CDocument` if úspěch; jinak null.

### <a name="remarks"></a>Poznámky

Pokud je dokument s tímto názvem už otevřený, zobrazí se první okno rámce, které tento dokument obsahuje. Pokud aplikace podporuje více šablon dokumentů, rozhraní používá příponu názvu souboru k nalezení příslušné šablony dokumentu pro pokus o načtení dokumentu. V případě úspěchu šablona dokumentu potom vytvoří okno rámce a zobrazení pro dokument.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="parsecommandline"></a>CWinApp::P arseCommandLine

Zavolejte tuto členskou funkci k analýze příkazového řádku a odeslání parametrů, po jednom, do [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odkaz na objekt [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) .

### <a name="remarks"></a>Poznámky

Při spuštění nového projektu knihovny MFC pomocí Průvodce aplikací vytvoří `CCommandLineInfo`Průvodce aplikací místní instanci a potom zavolá `ProcessShellCommand` a `ParseCommandLine` v členské funkci [InitInstance](#initinstance) . Příkazový řádek následuje po trase popsané níže:

1. Po vytvoření `InitInstance` `CCommandLineInfo` je objekt předán do. `ParseCommandLine`

2. `ParseCommandLine`potom pro `CCommandLineInfo::ParseParam` každý parametr volá opakovaně.

3. `ParseParam`vyplní objekt, který je poté předán do [ProcessShellCommand.](#processshellcommand) `CCommandLineInfo`

4. `ProcessShellCommand`zpracovává argumenty a příznaky příkazového řádku.

Všimněte si, že můžete `ParseCommandLine` zavolat přímo podle potřeby.

Popis příznaků příkazového řádku naleznete v tématu [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

##  <a name="pretranslatemessage"></a>CWinApp::P reTranslateMessage

Přepište tuto funkci pro filtrování zpráv oken před odesláním do funkce Windows Functions [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) výchozí implementace provádí překlad akcelerátorového klíče, takže musíte zavolat `CWinApp::PreTranslateMessage`členská funkce v přepsané verzi

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel na strukturu [zprávy](/windows/desktop/api/winuser/ns-winuser-tagmsg) , která obsahuje zprávu ke zpracování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla zpráva plně zpracována `PreTranslateMessage` v a neměla by být zpracována dále. Nula, pokud má být zpráva zpracována normálním způsobem.

##  <a name="processmessagefilter"></a>CWinApp::P rocessMessageFilter

Funkce Hooku rozhraní volá tuto členskou funkci k filtrování a reakci na určité zprávy systému Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*code*<br/>
Určuje kód vidlice. Tato členská funkce používá kód k určení způsobu zpracování *lpMsg.*

*lpMsg*<br/>
Ukazatel na strukturu [zprávy](/windows/desktop/api/winuser/ns-winuser-tagmsg) systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zpráva zpracována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Funkce zavěšení zpracovává události před odesláním do normálního zpracování zprávy aplikace.

Pokud přepíšete tuto rozšířenou funkci, ujistěte se, že jste volali verzi základní třídy, aby se zachovalo zpracování zavěšení rozhraní.

##  <a name="processshellcommand"></a>CWinApp::P rocessShellCommand

Tato členská funkce je volána pomocí [InitInstance](#initinstance) pro přijetí parametrů předaných `CCommandLineInfo` z objektu identifikovaného *rCmdInfo*a provedení uvedené akce.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odkaz na objekt [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je příkaz prostředí úspěšně zpracován. Pokud je 0, vrátí FALSE z [InitInstance](#initinstance).

### <a name="remarks"></a>Poznámky

Při spuštění nového projektu knihovny MFC pomocí Průvodce aplikací vytvoří Průvodce aplikací `CCommandLineInfo`místní instanci a potom v `InitInstance` členské funkci zavolá `ProcessShellCommand` a [ParseCommandLine](#parsecommandline) . Příkazový řádek následuje po trase popsané níže:

1. Po vytvoření `InitInstance` `CCommandLineInfo` je objekt předán do. `ParseCommandLine`

2. `ParseCommandLine`pak volá [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) opakovaně, jednou pro každý parametr.

3. `ParseParam`vyplní `ProcessShellCommand`objekt, který je poté předán do. `CCommandLineInfo`

4. `ProcessShellCommand`zpracovává argumenty a příznaky příkazového řádku.

Datové členy `CCommandLineInfo` objektu, identifikovaný [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), mají následující Výčtový typ, který `CCommandLineInfo` je definován v rámci třídy.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Stručný popis každé z těchto hodnot naleznete v tématu `CCommandLineInfo::m_nShellCommand`.

##  <a name="processwndprocexception"></a>CWinApp::P rocessWndProcException

Rozhraní volá tuto členskou funkci pokaždé, když obslužná rutina nezachytává výjimku vyvolanou v jedné z obslužných rutin zpráv nebo příkazů vaší aplikace.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*e*<br/>
Ukazatel na nezachycenou výjimku.

*pMsg*<br/>
Struktura [](/windows/desktop/api/winuser/ns-winuser-tagmsg) zprávy, která obsahuje informace o zprávě systému Windows, která způsobila, že rozhraní vyvolalo výjimku.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která má být vrácena do systému Windows. Obvykle je to 0L pro zprávy systému Windows, 1L (TRUE) pro zprávy příkazů.

### <a name="remarks"></a>Poznámky

Nevolejte tuto členskou funkci přímo.

Výchozí implementace této členské funkce vytvoří okno se zprávou. Pokud by nezachycená výjimka vznikla s chybou nabídky, panelu nástrojů nebo příkazu akcelerátoru, zobrazí se v okně se zprávou zpráva o neúspěšném provedení příkazu. v opačném případě se zobrazí zpráva "interní chyba aplikace".

Přepište tuto členskou funkci tak, aby poskytovala globální zpracování vašich výjimek. Pouze v případě, že chcete zobrazit okno se zprávou, volejte pouze základní funkce.

##  <a name="register"></a>CWinApp:: Register

Provede všechny registrační úkoly, které `RegisterShellFileTypes`nezpracovává.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové při úspěchu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace jednoduše vrátí hodnotu TRUE. Tuto funkci potlačíte tak, aby poskytovala jakékoli vlastní kroky registrace.

##  <a name="registershellfiletypes"></a>CWinApp:: RegisterShellFileTypes

Zavolejte tuto členskou funkci pro registraci všech typů dokumentů vaší aplikace pomocí Správce souborů systému Windows.

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parametry

*bCompat*<br/>
pro Hodnota TRUE přidá položky registru pro příkazy prostředí tisknout a tisknout do a umožňuje uživateli tisk souborů přímo z prostředí nebo přetažením souboru na objekt tiskárny. Přidá taky DefaultIcon klíč. Ve výchozím nastavení má tento parametr hodnotu FALSE z důvodu zpětné kompatibility.

### <a name="remarks"></a>Poznámky

Uživatel tak může otevřít datový soubor vytvořený aplikací dvojitým kliknutím na něj v rámci správce souborů. Zavolejte `RegisterShellFileTypes` po volání [AddDocTemplate](#adddoctemplate) pro každou šablonu dokumentu ve vaší aplikaci. Při volání `RegisterShellFileTypes`volejte také členskou funkci [EnableShellOpen](#enableshellopen) .

`RegisterShellFileTypes`projde seznam objektů [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md) , které aplikace udržuje, a pro každou šablonu dokumentu přidá položky do registrační databáze, kterou systém Windows udržuje pro přidružení souborů. Správce souborů používá tyto položky k otevření datového souboru, když na něj uživatel dvakrát klikne. Tím se eliminuje nutnost dodávat. Soubor REG s vaší aplikací.

> [!NOTE]
> `RegisterShellFileTypes`funguje pouze v případě, že uživatel spustí program s právy správce. Pokud program nemá oprávnění správce, nemůže změnit klíče registru.

Pokud registrační databáze už přidruží danou příponu názvu souboru k jinému typu souboru, nevytvoří se žádné nové přidružení. Podívejte se `CDocTemplate` na třídu pro formát řetězců potřebných k registraci těchto informací.

##  <a name="registerwithrestartmanager"></a>CWinApp:: RegisterWithRestartManager

Zaregistruje aplikaci pomocí správce restartování.

```
virtual HRESULT RegisterWithRestartManager(
    BOOL bRegisterRecoveryCallback,
    const CString& strRestartIdentifier);

virtual HRESULT RegisterWithRestartManager(
    LPCWSTR pwzCommandLineArgs,
    DWORD dwRestartFlags,
    APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,
    LPVOID lpvParam,
    DWORD dwPingInterval,
    DWORD dwCallbackFlags);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bRegisterRecoveryCallback*|pro Hodnota TRUE označuje, že tato instance aplikace používá funkci zpětného volání pro obnovení. Hodnota FALSE znamená, že není. Rozhraní volá funkci zpětného volání pro obnovení, když dojde k neočekávanému ukončení aplikace. Další informace naleznete v tématu [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*strRestartIdentifier*|pro Jedinečný řetězec, který identifikuje tuto instanci správce restartování. Identifikátor správce restartování je jedinečný pro každou instanci aplikace.|
|*pwzCommandLineArgs*|pro Řetězec, který obsahuje všechny nadbytečné argumenty z příkazového řádku.|
|*dwRestartFlags*|pro Volitelné příznaky pro správce restartování Další informace najdete v části poznámky.|
|*pRecoveryCallback*|pro Funkce zpětného volání pro obnovení. Tato funkce musí jako vstup přijmout parametr LPVOID a vracet hodnotu typu DWORD. Výchozí funkce zpětného volání pro `CWinApp::ApplicationRecoveryCallback`obnovení je.|
|*lpvParam*|pro Vstupní parametr funkce zpětného volání pro obnovení. Další informace naleznete v tématu [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*dwPingInterval*|pro Doba, po kterou správce restartování čeká na vrácení funkce zpětného volání pro obnovení. Tento parametr je v milisekundách.|
|*dwCallbackFlags*|pro Příznaky předané funkci zpětného volání pro obnovení. Vyhrazeno pro budoucí použití.|

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace používá výchozí implementaci knihovny MFC pro automatické ukládání souborů, měli byste použít jednoduchou verzi `RegisterWithRestartManager`. `RegisterWithRestartManager` Pokud chcete přizpůsobit chování aplikace při ukládání do programu, použijte složitou verzi nástroje.

Pokud zavoláte tuto metodu s prázdným řetězcempro strRestartIdentifier `RegisterWithRestartManager` , nástroj vytvoří jedinečný identifikátor řetězce pro tuto instanci správce restartování.

Když dojde k neočekávanému ukončení aplikace, správce restartování spustí aplikaci z příkazového řádku a poskytne jedinečný identifikátor restartování jako nepovinný argument. V tomto scénáři rozhraní volá `RegisterWithRestartManager` dvě časy. První volání pochází z [CWinApp:: InitInstance](#initinstance) s prázdným řetězcem pro identifikátor řetězce. Pak metoda [CWinApp::P rocessshellcommand](#processshellcommand) volání `RegisterWithRestartManager` s jedinečným identifikátorem restartování.

Po registraci aplikace pomocí správce restartování monitoruje aplikace správce restartování. Pokud dojde k neočekávanému ukončení aplikace, správce restartování zavolá funkci zpětného volání pro obnovení během procesu vypnutí. Správce restartování čeká *dwPingInterval* na odpověď z funkce zpětného volání pro obnovení. Pokud funkce zpětného volání pro obnovení nereaguje v této době, aplikace se ukončí bez provedení funkce zpětného volání pro obnovení.

Ve výchozím nastavení nejsou dwRestartFlags podporovány, ale jsou k dispozici pro budoucí použití. Možné hodnoty pro *dwRestartFlags* jsou následující:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="reopenpreviousfilesatrestart"></a>CWinApp:: ReopenPreviousFilesAtRestart

Určuje, zda správce restartování znovu otevře soubory otevřené při neočekávaném ukončení aplikace.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE znamená, že správce restartování znovu otevře dříve otevřené soubory; Hodnota FALSE znamená, že správce restartování není.

##  <a name="restartinstance"></a>CWinApp:: RestartInstance

Zpracovává restart aplikace inicializovaný správcem restartování.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud obslužná rutina obnovení dat otevírá dříve otevřené dokumenty; FALSE, pokud má obslužná rutina obnovy dat chybu, nebo pokud nejsou k dispozici žádné dříve otevřené dokumenty.

### <a name="remarks"></a>Poznámky

Když správce restartu restartuje aplikaci, zavolá rozhraní tuto metodu. Tato metoda načte obslužnou rutinu obnovení dat a obnoví automaticky uložené soubory. Tato metoda volá [CDataRecoveryHandler:: RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) , aby určila, jestli chce uživatel obnovit automaticky uložené soubory.

Tato metoda vrátí hodnotu FALSE, pokud [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) zjistí, že nebyly otevřeny žádné dokumenty. Pokud neexistovaly žádné otevřené dokumenty, aplikace se spustí normálně.

##  <a name="restoreautosavedfilesatrestart"></a>CWinApp:: RestoreAutosavedFilesAtRestart

Určuje, zda správce restartování obnoví automaticky uložené soubory při restartu aplikace.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE označuje, že správce restartování obnoví automaticky uložené soubory; Hodnota FALSE znamená, že správce restartování není.

##  <a name="run"></a>CWinApp:: Run

Poskytuje výchozí smyčku zpráv.

```
virtual int Run();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota typu **int** , kterou vrací `WinMain`.

### <a name="remarks"></a>Poznámky

`Run`Získá a odešle zprávy systému Windows, dokud aplikace neobdrží zprávu WM_QUIT. Pokud fronta zpráv aplikace v současné době neobsahuje žádné zprávy, `Run` volání při nečinnosti zpracovává zpracování nečinného času. [](#onidle) Příchozí zprávy přecházejí do členské funkce [PreTranslateMessage](#pretranslatemessage) pro zvláštní zpracování a pak na funkci `TranslateMessage` Windows pro překlad standardních klávesnic `DispatchMessage` . nakonec se zavolá funkce Windows.

`Run`je zřídka přepsán, ale můžete ji přepsat, aby poskytovala zvláštní chování.

##  <a name="runautomated"></a>CWinApp:: RunAutomated

Voláním této funkce zjistíte, zda je k dispozici možnost " **/Automation.** " nebo " **-Automation**", která označuje, zda byla serverová aplikace spuštěna klientskou aplikací.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla nalezena možnost; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici, možnost je odebrána z příkazového řádku. Další informace o automatizaci OLE naleznete v článku [automatizační servery](../../mfc/automation-servers.md).

##  <a name="runembedded"></a>CWinApp:: RunEmbedded

Voláním této funkce zjistíte, zda je k dispozici možnost " **přepínačem/Embedding**" nebo " **-vkládání**", která označuje, zda byla serverová aplikace spuštěna klientskou aplikací.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla nalezena možnost; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici, možnost je odebrána z příkazového řádku. Další informace o vkládání najdete v článku [servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

##  <a name="saveallmodified"></a>CWinApp:: SaveAllModified

Volá se rozhraním, aby se uložily všechny dokumenty, když se zavře okno hlavního rámce aplikace, nebo prostřednictvím zprávy WM_QUERYENDSESSION.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bezpečné ukončit aplikaci; 0, pokud není bezpečné ukončit aplikaci.

### <a name="remarks"></a>Poznámky

Výchozí implementace této členské funkce volá členskou funkci [objektu CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified) a pak všechny změněné dokumenty v aplikaci.

##  <a name="selectprinter"></a>CWinApp:: SelectPrinter

Zavolejte tuto členskou funkci pro výběr konkrétní tiskárny a uvolněte tiskárnu, která byla dříve vybrána v dialogovém okně Tisk.

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parametry

*hDevNames*<br/>
Popisovač struktury [DEVNAMES –](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) , který identifikuje ovladač, zařízení a výstupní názvy portů konkrétní tiskárny.

*hDevMode*<br/>
Popisovač struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , který určuje informace o inicializaci zařízení a prostředí tiskárny.

*bFreeOld*<br/>
Uvolní dříve vybranou tiskárnu.

### <a name="remarks"></a>Poznámky

Pokud mají hodnoty *hDevMode* i *hDevNames* hodnotu null `SelectPrinter` , používá aktuální výchozí tiskárnu.

##  <a name="sethelpmode"></a>CWinApp:: SetHelpMode

Nastaví typ pomocníka aplikace.

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parametry

*eHelpType*<br/>
Určuje typ, který může být použit. Další informace naleznete v části [CWinApp:: m_eHelpType](#m_ehelptype) .

### <a name="remarks"></a>Poznámky

Nastaví typ pomocníka aplikace.

Chcete-li nastavit typ nápovědě aplikace na HTMLHelp, můžete volat [EnableHTMLHelp](#enablehtmlhelp). Po volání `EnableHTMLHelp`musí vaše aplikace používat HTMLHelp jako svoji aplikaci help. Pokud chcete změnit použití WinHelp, můžete zavolat `SetHelpMode` a nastavit *eHelpType* na. `afxWinHelp`

##  <a name="setregistrykey"></a>CWinApp:: SetRegistryKey

Způsobí, že nastavení aplikace bude uloženo v registru namísto souborů INI.

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistryKey*<br/>
Ukazatel na řetězec obsahující název klíče.

*nIDRegistryKey*<br/>
ID prostředku řetězce obsahujícího název klíče registru.

### <a name="remarks"></a>Poznámky

Tato funkce nastaví *m_pszRegistryKey* `GetProfileInt`, která je poté používána funkcemi `WriteProfileString` `CWinApp`, `GetProfileString`, `WriteProfileInt`a. Pokud byla tato funkce volána, seznam naposledy použitých souborů (MRU) je také uložen v registru. Klíčem registru je obvykle název společnosti. Ukládá se do klíče v následujícím tvaru: Název\\HKEY_CURRENT_USER\Software <\>\>společnosti<název\\aplikace < název oddílu\><název\>hodnoty.\\\\

##  <a name="supportsapplicationrecovery"></a>CWinApp:: SupportsApplicationRecovery

Určuje, zda správce restartování obnoví aplikaci, která byla neočekávaně ukončena.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE znamená, že správce restartování obnoví aplikaci. Hodnota FALSE znamená, že správce restartování není.

##  <a name="supportsautosaveatinterval"></a>CWinApp:: SupportsAutosaveAtInterval

Určuje, zda správce restartování automaticky ukládá otevřené dokumenty v pravidelných intervalech.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE znamená, že správce restartování automaticky ukládá otevřené dokumenty; Hodnota FALSE znamená, že správce restartování není.

##  <a name="supportsautosaveatrestart"></a>CWinApp:: SupportsAutosaveAtRestart

Určuje, zda správce restartování automaticky uloží otevřené dokumenty, když se aplikace restartuje.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE (pravda) znamená, že správce restartování automaticky uloží otevřené dokumenty, když se aplikace restartuje; Hodnota FALSE znamená, že správce restartování není.

##  <a name="supportsrestartmanager"></a>CWinApp:: SupportsRestartManager

Určuje, zda aplikace podporuje správce restartování.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE znamená, že aplikace podporuje správce restartování; Hodnota FALSE znamená, že aplikace není.

##  <a name="unregister"></a>CWinApp:: Unregister

Zruší registraci všech souborů zaregistrovaných objektem aplikace.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové při úspěchu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Funkce zruší registraci prováděnou objektem aplikace a funkcí [Register.](#register) `Unregister` V normálním případě jsou obě funkce volány implicitně pomocí knihovny MFC, a proto se ve vašem kódu nezobrazí.

Přepsáním této funkce proveďte vlastní kroky pro zrušení registrace.

##  <a name="unregistershellfiletypes"></a>CWinApp:: UnregisterShellFileTypes

Voláním této členské funkce zrušíte registraci všech typů dokumentů vaší aplikace pomocí Správce souborů systému Windows.

```
void UnregisterShellFileTypes();
```

##  <a name="winhelp"></a>CWinApp:: WinHelp

Zavolejte tuto členskou funkci pro vyvolání aplikace WinHelp.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parametry

*dwData*<br/>
Určuje další data. Použitá hodnota závisí na hodnotě parametru *nCmd* .

*nCmd*<br/>
Určuje typ požadované aplikace Help. Seznam možných hodnot a jejich vliv na parametr *dwData* naleznete v tématu funkce [WinHelp](/windows/desktop/api/winuser/nf-winuser-winhelpa) Windows.

### <a name="remarks"></a>Poznámky

Rozhraní také volá tuto funkci, aby vyvolala aplikaci WinHelp.

Rozhraní aplikace WinHelp automaticky zavře, jakmile se vaše aplikace ukončí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="writeprofilebinary"></a>CWinApp:: WriteProfileBinary

Tuto členskou funkci volejte pro zápis binárních dat do zadané části registru aplikace nebo. Soubor INI.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud oddíl neexistuje, vytvoří se. Název oddílu nezávisí na velikosti písmen; řetězec může být libovolná kombinace velkých a malých písmen.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, do které se má zapsat hodnota. Pokud položka v zadaném oddílu neexistuje, vytvoří se.

*pData*<br/>
Odkazuje na data, která mají být zapsána.

*nBytes*<br/>
Obsahuje počet bajtů, které mají být zapsány.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

Tento příklad používá `CWinApp* pApp = AfxGetApp();` pro získání na třídu CWinApp ilustrující způsob, `WriteProfileBinary` jak a `GetProfileBinary` lze jej použít z libovolné funkce v aplikaci knihovny MFC.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Další příklad naleznete v příkladu pro [CWinApp:: GetProfileBinary](#getprofilebinary).

##  <a name="writeprofileint"></a>CWinApp:: WriteProfileInt

Zavolejte tuto členskou funkci pro zápis zadané hodnoty do zadané části registru aplikace nebo. Soubor INI.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud oddíl neexistuje, vytvoří se. Název oddílu nezávisí na velikosti písmen; řetězec může být libovolná kombinace velkých a malých písmen.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, do které se má zapsat hodnota. Pokud položka v zadaném oddílu neexistuje, vytvoří se.

*nHodnota*<br/>
Obsahuje hodnotu, která se má zapsat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

Tento příklad používá `CWinApp* pApp = AfxGetApp();` k získání na třídu CWinApp ilustraci `WriteProfileString`způsobu, jak, `WriteProfileInt` `GetProfileString`, a `GetProfileInt` lze použít z libovolné funkce v aplikaci MFC.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Další příklad naleznete v příkladu pro [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="writeprofilestring"></a>CWinApp:: WriteProfileString

Zavolejte tuto členskou funkci pro zápis zadaného řetězce do určené části registru aplikace nebo. Soubor INI.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parametry

*lpszSection*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud oddíl neexistuje, vytvoří se. Název oddílu nezávisí na velikosti písmen; řetězec může být libovolná kombinace velkých a malých písmen.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, do které se má zapsat hodnota. Pokud položka v zadaném oddílu neexistuje, vytvoří se. Pokud má tento parametr hodnotu NULL, odstraní se oddíl určený parametrem *lpszSection* .

*lpszValue*<br/>
Odkazuje na řetězec, který má být zapsán. Pokud má tento parametr hodnotu NULL, položka určená parametrem *lpszEntry* se odstraní.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Další příklad naleznete v příkladu pro [CWinApp:: GetProfileInt](#getprofileint).

##  <a name="setappid"></a>CWinApp:: SetAppID

Explicitně nastaví ID uživatelského modelu aplikace pro aplikaci. Tato metoda by měla být volána před tím, než se uživateli zobrazí jakékoli uživatelské rozhraní (nejlepším místem je konstruktor aplikace).

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parametry

*lpcszAppID*<br/>
Určuje ID modelu uživatele aplikace.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[CWinThread – třída](../../mfc/reference/cwinthread-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md)
