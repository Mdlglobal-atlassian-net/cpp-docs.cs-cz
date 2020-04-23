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
ms.openlocfilehash: 4bb1ade4182424cbdcbf0d7ba69af88bbb88abe6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750668"
---
# <a name="cwinapp-class"></a>CWinApp – třída

Základní třída, ze které odvozujete aplikační objekt systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWinApp::CWinApp](#cwinapp)|Vytvoří `CWinApp` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinApp::AddDocTemplate](#adddoctemplate)|Přidá šablonu dokumentu do seznamu dostupných šablon dokumentů aplikace.|
|[Cwinapp::AddtoRecentFileList](#addtorecentfilelist)|Přidá název souboru do seznamu naposledy použitých souborů (MRU).|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Volat rámci při neočekávaně ukončí aplikace.|
|[CWinApp::Zavřít všechny dokumenty](#closealldocuments)|Zavře všechny otevřené dokumenty.|
|[CWinApp::VytvořitprinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny.|
|[CWinApp::DelRegTree](#delregtree)|Odstraní zadaný klíč a všechny jeho podklíče.|
|[CWinApp::DoMessageBox](#domessagebox)|[Implementuje AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) pro aplikaci.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Zapíná a vypíná kurzor čekání.|
|[CWinApp::Povolena podpora D2D](#enabled2dsupport)|Umožňuje podporu aplikace D2D. Volání této metody před inicializování hlavního okna.|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementuje HTMLHelp pro aplikaci, spíše než WinHelp.|
|[CWinApp::EnableTaskbarInterakce](#enabletaskbarinteraction)|Povolí interakci na hlavním panelu.|
|[Cwinapp::Instance výstupu](#exitinstance)|Přepište vyčistit, když vaše aplikace ukončí.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Načte vstupní parametr pro metodu obnovení aplikace.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Vrátí dobu, po kterou bude správce restartování čekat na návrat funkce zpětného volání obnovení.|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Vrátí příznaky pro správce restartování.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Vrátí klíč\\pro HKEY_CURRENT_USER "Software"\RegistryKey\ProfileName.|
|[CWinApp::GetDataRecoveryHandler CWinApp::GetDataRecoveryHandler CWinApp::GetDataRecoveryHandler CWin](#getdatarecoveryhandler)|Získá obslužnou rutinu obnovení dat pro tuto instanci aplikace.|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Načte pozici první šablony dokumentu.|
|[CWinApp::GetHelpMode](#gethelpmode)|Načte typ nápovědy používané aplikací.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Načte pozici šablony dokumentu. Lze použít rekurzivně.|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Načte výchozí hodnoty zařízení tiskárny.|
|[CWinApp::GetProfileBinary](#getprofilebinary)|Načte binární data ze záznamu v aplikaci . INI.|
|[CWinApp::GetProfileInt](#getprofileint)|Načte celé číslo ze položky v aplikaci . INI.|
|[CWinApp::GetProfileString](#getprofilestring)|Načte řetězec z položky v aplikaci . INI.|
|[CWinApp::GetSectionKey](#getsectionkey)|Vrátí klíč\\pro HKEY_CURRENT_USER "Software"\RegistryKey\AppName\lpszSection.|
|[CWinApp::Skrýtaplikaci](#hideapplication)|Před zavřením všech dokumentů skryje aplikaci.|
|[CWinApp::HtmlNápověda](#htmlhelp)|Volá `HTMLHelp` funkci systému Windows.|
|[Cwinapp::initinstance](#initinstance)|Přepište, chcete-li provést inicializaci instance systému Windows, například vytvoření objektů okna.|
|[CWinApp::IsTaskbarInterakcePovolená](#istaskbarinteractionenabled)|Určuje, zda je povolena interakce na hlavním panelu systému Windows 7.|
|[CWinApp::LoadCursor](#loadcursor)|Načte prostředek kurzoru.|
|[CWinApp::Ikona načítání](#loadicon)|Načte prostředek ikony.|
|[Cwinapp::Kurzor zatížení](#loadoemcursor)|Načte předdefinovaný kurzor o výrobci OEM systému Windows, který **OCR_** konstanty určí v systému WINDOWS. H.|
|[Cwinapp::LoadOEMIcon](#loadoemicon)|Načte předdefinovanou ikonu oem systému Windows, kterou **OIC_** konstanty určí v systému WINDOWS. H.|
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Načte předdefinovaný kurzor systému Windows, který **určí konstanty IDC_** v systému WINDOWS. H.|
|[CWinApp::LoadStandardIcon](#loadstandardicon)|Načte předdefinovanou ikonu systému Windows, kterou **IDI_** konstanty určí v systému WINDOWS. H.|
|[CWinApp::OnDDECommand](#onddecommand)|Volat rámci v reakci na dynamickou výměnu dat (DDE) spustit příkaz.|
|[Cwinapp::OnIdle](#onidle)|Přepsat provádět zpracování nečinnosti specifické pro aplikaci.|
|[CWinApp::Soubor OpenDocumentFile](#opendocumentfile)|Volat rámci otevřít dokument ze souboru.|
|[CWinApp::ParseCommandLine](#parsecommandline)|Analyzuje jednotlivé parametry a příznaky v příkazovém řádku.|
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|Filtruje zprávy před jejich odesláním do funkcí systému Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Zachytí určité zprávy dříve, než se dostanou do aplikace.|
|[CWinApp::ProcessShellCommand](#processshellcommand)|Zpracovává argumenty a příznaky příkazového řádku.|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Zachytí všechny neošetřené výjimky vyzývané obslužnými rutinami zpráv a příkazů aplikace.|
|[CWinApp::Registrovat](#register)|Provádí vlastní registraci.|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Zaregistruje aplikaci se správcem restartování.|
|[CWinApp::ZnovuotevřítPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Určuje, zda správce restartování znovu otevře soubory, které byly otevřeny při neočekávaném ukončení aplikace.|
|[Cwinapp::Restartinstance](#restartinstance)|Zpracovává restartování aplikace iniciované správcem restartování.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Určuje, zda správce restartování obnoví automaticky uložené soubory při restartování aplikace.|
|[CWinApp::Spustit](#run)|Spustí výchozí smyčku zpráv. Přepsáním můžete přizpůsobit smyčku zpráv.|
|[CWinApp::Spustit automatické](#runautomated)|Testuje příkazový řádek aplikace pro možnost **/Automation.** Zastaralé. Místo toho použijte hodnotu v [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) po volání [ParseCommandLine](#parsecommandline).|
|[CWinApp::RunEmbedded](#runembedded)|Testuje příkazový řádek aplikace pro **/Embedding** možnost. Zastaralé. Místo toho použijte hodnotu v [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) po volání [ParseCommandLine](#parsecommandline).|
|[CWinApp::UložitAllModified](#saveallmodified)|Vyzve uživatele k uložení všech změněných dokumentů.|
|[CWinApp::SelectPrinter](#selectprinter)|Vybere tiskárnu, která byla dříve indikována uživatelem prostřednictvím tiskového dialogového okna.|
|[CWinApp::Nastavitrežim nápovědy](#sethelpmode)|Nastaví a inicializuje typ nápovědy používané aplikací.|
|[CWinApp::Podporuje obnovení aplikace](#supportsapplicationrecovery)|Určuje, zda správce restartování obnoví aplikaci, která byla neočekávaně ukončena.|
|[CWinApp::Podporujeautomatické ukládáníinterval](#supportsautosaveatinterval)|Určuje, zda správce restartování automaticky ukládá otevřené dokumenty v pravidelných intervalech.|
|[CWinApp::PodporujeAutosaveAtRestart](#supportsautosaveatrestart)|Určuje, zda správce restartování automaticky uloží všechny otevřené dokumenty při restartování aplikace.|
|[CWinApp::PodporujeRestartManager](#supportsrestartmanager)|Určuje, zda aplikace podporuje správce restartování.|
|[CWinApp::Zrušit registraci](#unregister)|Zruší registrace všeho, o co `CWinApp` je známo, že je zaregistrováno objektem.|
|[CWinApp::WinHelp](#winhelp)|Volá `WinHelp` funkci systému Windows.|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Zapisuje binární data do položky v aplikaci . INI.|
|[CWinApp::WriteProfileInt](#writeprofileint)|Zapíše celé číslo do položky v aplikaci . INI.|
|[CWinApp::WriteProfileString](#writeprofilestring)|Zapíše řetězec do položky v aplikaci . INI.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|Umožňuje uživateli otevírat datové soubory ze Správce souborů systému Windows.|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Zatížení standardní . INI nastavení souboru a umožňuje funkci seznamu souborů MRU.|
|[CWinApp::OnContextHelp](#oncontexthelp)|Zpracovává nápovědu SHIFT+F1 v rámci aplikace.|
|[CWinApp::OnFileNew](#onfilenew)|Implementuje příkaz ID_FILE_NEW.|
|[CWinApp::OnFileOpen](#onfileopen)|Implementuje příkaz ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementuje příkaz ID_FILE_PRINT_SETUP.|
|[CWinApp::OnHelp](#onhelp)|Zpracovává Nápovědu F1 v rámci aplikace (pomocí aktuálního kontextu).|
|[CWinApp::OnHelpFinder](#onhelpfinder)|Zpracovává příkazy ID_HELP_FINDER a ID_DEFAULT_HELP.|
|[CWinApp::OnHelpIndex](#onhelpindex)|Zpracovává příkaz ID_HELP_INDEX a poskytuje výchozí téma nápovědy.|
|[Cwinapp::OnHelpUsing CWinApp::OnHelpUsing CWinApp::OnHelpUsing CWin](#onhelpusing)|Zpracovává příkaz ID_HELP_USING.|
|[CWinApp::RegisterShellTypy souborů](#registershellfiletypes)|Zaregistruje všechny typy dokumentů aplikace pomocí Správce souborů systému Windows.|
|[CWinApp::SetAppID](#setappid)|Explicitně nastaví ID modelu uživatele aplikace pro aplikaci. Tato metoda by měla být volána před jakékoli uživatelské rozhraní je předloženuživateli (nejlepší místo je konstruktor aplikace).|
|[CWinApp::Nastavit klíč registru](#setregistrykey)|Způsobí, že nastavení aplikace, které mají být uloženy v registru namísto . INI soubory.|
|[CWinApp::UnregisterShellFileTypes CWinApp::UnregisterShellFileTypes CWinApp::UnregisterShellFileTypes CWin](#unregistershellfiletypes)|Zruší registraci všech typů dokumentů aplikace pomocí Správce souborů systému Windows.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Označuje, zda je uživatel v režimu kontextu nápovědy (obvykle vyvolána s SHIFT + F1).|
|[CWinApp::m_eHelpType](#m_ehelptype)|Určuje typ nápovědy používané aplikací.|
|[CWinApp::m_hInstance](#m_hinstance)|Identifikuje aktuální instanci aplikace.|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Odkazuje na řetězec s nulovým ukončením, který určuje příkazový řádek aplikace.|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Určuje, jak má být okno zpočátku zobrazeno.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace kontejneru, když je server OLE aktivní.|
|[CWinApp::m_pszAppID](#m_pszappid)|ID modelu uživatele aplikace.|
|[CWinApp::m_pszAppName](#m_pszappname)|Určuje název aplikace.|
|[CWinApp::m_pszExeName](#m_pszexename)|Název modulu aplikace.|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|Cesta k souboru nápovědy aplikace.|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|Aplikace . NÁZEV SOUBORU INI.|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Slouží k určení úplného klíče registru pro ukládání nastavení profilu aplikace.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Příznaky, které určují, jak se chová správce restartování.|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|Doba v milisekundách mezi automatickým ukládáním.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Ukazatel na obslužnou rutinu obnovení dat pro aplikaci.|

## <a name="remarks"></a>Poznámky

Objekt aplikace poskytuje členské funkce pro inicializaci aplikace (a každou její instanci) a pro spuštění aplikace.

Každá aplikace, která používá třídy Microsoft Foundation, `CWinApp`může obsahovat pouze jeden objekt odvozený z aplikace . Tento objekt je vytvořen při vytvoření jiných globálních objektů jazyka C++ a je již k dispozici, když systém Windows volá `WinMain` funkci, která je dodávána knihovnou tříd Microsoft Foundation. Deklarujte `CWinApp` odvozený objekt na globální úrovni.

Když odvodíte `CWinApp`třídu aplikace z , přepište člennou funkci [InitInstance](#initinstance) a vytvořte objekt hlavního okna aplikace.

Kromě `CWinApp` členských funkcí poskytuje knihovna tříd Microsoft Foundation následující globální `CWinApp` funkce pro přístup k objektu a dalším globálním informacím:

- [Aplikace AfxGet](application-information-and-management.md#afxgetapp) Získá ukazatel na `CWinApp` objekt.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Získá popisovač aktuální instance aplikace.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Získá popisovač prostředků aplikace.

- [Název aplikace AfxGetApp](application-information-and-management.md#afxgetappname) Získá ukazatel na řetězec obsahující název aplikace. Alternativně pokud máte ukazatel na `CWinApp` objekt, `m_pszExeName` použijte k získání názvu aplikace.

Viz [CWinApp: Třída aplikace](../../mfc/cwinapp-the-application-class.md) pro `CWinApp` více informací o třídě, včetně přehledu následujících:

- `CWinApp`-odvozený kód napsaný Průvodcem aplikací.

- `CWinApp`Role v pořadí provádění vaší aplikace.

- `CWinApp`Výchozí implementace členské funkce .

- `CWinApp`'s klíčem overridables.

Datový `m_hPrevInstance` člen již neexistuje. Chcete-li zjistit, zda je spuštěna jiná instance aplikace, použijte pojmenovaný objekt mutex. Pokud otevření objektu mutex se nezdaří, pak neexistují žádné další instance aplikace spuštěna.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwinthread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp::AddDocTemplate

Voláním této členské funkce přidáte šablonu dokumentu do seznamu dostupných šablon dokumentů, které aplikace spravuje.

```cpp
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parametry

*pŠablona*<br/>
Ukazatel na `CDocTemplate` přidání.

### <a name="remarks"></a>Poznámky

Před voláním [RegisterShellFileTypes](#registershellfiletypes)byste měli do aplikace přidat všechny šablony dokumentů .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

## <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>Cwinapp::AddtoRecentFileList

Volánítéto členské funkce pro přidání *lpszPathName* do seznamu souborů MRU.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Cesta k souboru.

### <a name="remarks"></a>Poznámky

Před použitím této členské funkce byste měli zavolat člennou funkci [LoadStdProfileSettings,](#loadstdprofilesettings) abyste načetli aktuální seznam souborů MRU.

Rozhraní Framework volá tuto členskou funkci při otevření souboru nebo provede příkaz Uložit jako pro uložení souboru s novým názvem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

## <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp::ApplicationRecoveryCallback

Volat rámci při neočekávaně ukončí aplikace.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parametry

*lpvParam*<br/>
[v] Vyhrazeno pro budoucí použití.

### <a name="return-value"></a>Návratová hodnota

0 Pokud je tato metoda úspěšná; nenulová, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace podporuje správce restartování, rozhraní framework volá tuto funkci při neočekávaně ukončí aplikace.

Výchozí implementace `ApplicationRecoveryCallback` používá `CDataRecoveryHandler` k uložení seznamu aktuálně otevřených dokumentů do registru. Tato metoda neukládá automaticky žádné soubory.

Chcete-li přizpůsobit chování, přepište tuto funkci v odvozené [třídě CWinApp](../../mfc/reference/cwinapp-class.md) nebo předejte vlastní metodu obnovení aplikace jako parametr [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

## <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp::Zavřít všechny dokumenty

Volání této členské funkce zavřít všechny otevřené dokumenty před ukončením.

```cpp
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Určuje, zda je relace systému Windows ukončena. Je pravda, pokud je relace ukončena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání [HideApplication](#hideapplication) `CloseAllDocuments`před voláním .

## <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp::VytvořitprinterDC

Volánítéto členské funkce k vytvoření kontextu zařízení tiskárny (DC) z vybrané tiskárny.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Odkaz na kontext zařízení tiskárny.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je kontext zařízení tiskárny úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

`CreatePrinterDC`inicializuje kontext zařízení, který předáte odkazem, takže jej můžete použít k tisku.

Pokud je funkce úspěšná, po dokončení tisku je nutné zničit kontext zařízení. Můžete nechat destruktor objektu [CDC](../../mfc/reference/cdc-class.md) to udělat, nebo můžete to udělat explicitně voláním [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc).

## <a name="cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp::CWinApp

Vytvoří `CWinApp` objekt a předá *lpszAppName,* které mají být uloženy jako název aplikace.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszAppName*<br/>
Řetězec s nulovým ukončením obsahující název aplikace, který používá systém Windows. Pokud tento argument není zadán `CWinApp` nebo je null, použije řetězec prostředků AFX_IDS_APP_TITLE nebo název souboru spustitelného souboru.

### <a name="remarks"></a>Poznámky

Měli byste vytvořit jeden `CWinApp`globální objekt vaší odvozené třídy. V aplikaci `CWinApp` můžete mít pouze jeden objekt. Konstruktor ukládá ukazatel na `CWinApp` objekt `WinMain` tak, aby volání členské funkce objektu inicializovat a spustit aplikaci.

## <a name="cwinappdelregtree"></a><a name="delregtree"></a>CWinApp::DelRegTree

Odstraní určitý klíč registru a všechny jeho podklíče.

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
Název klíče registru, který má být odstraněn.

*Ptm*<br/>
Ukazatel na catltransactionmanager objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="remarks"></a>Poznámky

Voláním této funkce odstraňte zadaný klíč a jeho podklíče.

## <a name="cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp::DoMessageBox

Framework volá tuto člennou funkci k implementaci okna se zprávou pro globální funkci [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parametry

*lpszPrompt*<br/>
Adresa textu v poli se zprávou.

*nTyp*<br/>
[Styl](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)okna se zprávou .

*nIDPrompt*<br/>
Index řetězce kontextu nápovědy.

### <a name="return-value"></a>Návratová hodnota

Vrátí stejné hodnoty `AfxMessageBox`jako .

### <a name="remarks"></a>Poznámky

Nevolejte tuto člennou funkci otevřít okno se zprávou; místo `AfxMessageBox` toho použít.

Přepište tuto člennou funkci a přizpůsobte zpracování `AfxMessageBox` volání v celé aplikaci.

## <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp::DoWaitCursor

Tato členská funkce je volána rámci implementovat [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor), a [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parametry

*nKód*<br/>
Pokud je tento parametr 1, zobrazí se kurzor čekání. Pokud 0, kurzor čekání je obnovena bez zvýšení počtu odkazů. Pokud -1, kurzor čekání končí.

### <a name="remarks"></a>Poznámky

Výchozí implementuje kurzor přesýpacích hodin. `DoWaitCursor`udržuje referenční počet. Pokud je pozitivní, zobrazí se kurzor přesýpacích hodin.

I když by `DoWaitCursor` normálně volat přímo, můžete přepsat tuto členská funkce změnit kurzor čekání nebo provést další zpracování při zobrazení kurzoru čekání.

Pro jednodušší a efektivnější způsob implementace kurzoru `CWaitCursor`čekání použijte .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

## <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp::Povolena podpora D2D

Je požadována sada Visual Studio 2010 SP1.

Umožňuje podporu aplikace D2D. Volání této metody před inicializování hlavního okna.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFactoryType*<br/>
Model zřetězení továrny D2D a prostředky, které vytvoří.

*writeFactoryType*<br/>
Hodnota, která určuje, zda bude objekt factory zápisu sdílen nebo izolován

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byla povolena podpora D2D, NEPRAVDA - jinak

## <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp::EnableHtmlHelp

Volání této členské funkce z v `CWinApp`rámci konstruktoru vaší odvozené třídy použít HTMLHelp pro pomoc vaší aplikace.

```cpp
void EnableHtmlHelp();
```

### <a name="remarks"></a>Poznámky

## <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp::EnableShellOpen

Volání této funkce, obvykle `InitInstance` z přepsání, aby uživatelé aplikace mohli otevřít datové soubory při poklepání na soubory ze Správce souborů systému Windows.

```cpp
void EnableShellOpen();
```

### <a name="remarks"></a>Poznámky

Volání `RegisterShellFileTypes` členské funkce ve spojení s touto funkcí nebo zadejte . REG soubor s vaší žádostí o ruční registraci typů dokumentů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

## <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp::EnableTaskbarInterakce

Povolí interakci na hlavním panelu.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda má být interakce s hlavním panelem systému Windows 7 povolena (TRUE) nebo zakázána (NEPRAVDA).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud lze povolit nebo zakázat interakci na hlavním panelu.

### <a name="remarks"></a>Poznámky

Tato metoda musí být volána před vytvořením hlavního okna, jinak se uplatní a vrátí HODNOTU FALSE.

## <a name="cwinappexitinstance"></a><a name="exitinstance"></a>Cwinapp::Instance výstupu

Volat rámci z v `Run` rámci členské funkce k ukončení této instance aplikace.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Ukončovací kód aplikace; 0 označuje žádné chyby a hodnoty větší než 0 označují chybu. Tato hodnota se používá jako `WinMain`vrácená hodnota z .

### <a name="remarks"></a>Poznámky

Nevolejte tuto člennou funkci odkudkoliv, ale v rámci `Run` členské funkce.

Výchozí implementace této funkce zapisuje možnosti architektury do aplikace . INI. Přepsat tuto funkci vyčistit při ukončení aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

## <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp::GetApplicationRecoveryParameter

Načte vstupní parametr pro metodu obnovení aplikace.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí vstupní parametr pro metodu obnovení aplikace.

### <a name="remarks"></a>Poznámky

Výchozí chování této funkce vrátí hodnotu NULL.

Další informace naleznete v tématu [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

## <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp::GetApplicationRecoveryPingInterval

Vrátí dobu, po kterou bude správce restartování čekat na návrat funkce zpětného volání obnovení.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Návratová hodnota

Doba v milisekundách.

### <a name="remarks"></a>Poznámky

Když aplikace, která je registrována u správce restartování ukončí neočekávaně, aplikace se pokusí uložit otevřené dokumenty a volá funkci zpětného volání obnovení. Výchozí funkce zpětného volání obnovení je [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

Doba, po kterou framework čeká na návrat funkce zpětného volání obnovení, je interval ping. Interval příkazu ping můžete `CWinApp::GetApplicationRecoveryPingInterval` přizpůsobit přepsáním `RegisterWithRestartManager`nebo poskytnutím vlastní hodnoty aplikace .

## <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp::GetApplicationRestartFlags

Vrátí příznaky pro správce restartování.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Návratová hodnota

Příznaky pro správce restartování. Výchozí implementace vrátí 0.

### <a name="remarks"></a>Poznámky

Příznaky pro správce restartování nemají žádný vliv na výchozí implementaci. Jsou k dispozici pro budoucí použití.

Příznaky nastavíte při registraci aplikace pomocí správce restartování pomocí [cwinapp::RegisterWithRestartManager](#registerwithrestartmanager).

Možné hodnoty pro příznaky správce restartování jsou následující:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp::GetAppRegistryKey

Vrátí klíč pro\\HKEY_CURRENT_USER "Software"\RegistryKey\ProfileName.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, je to tak. jinak NULL.

### <a name="remarks"></a>Poznámky

## <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp::GetDataRecoveryHandler CWinApp::GetDataRecoveryHandler CWinApp::GetDataRecoveryHandler CWin

Získá obslužnou rutinu obnovení dat pro tuto instanci aplikace.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Návratová hodnota

Obslužná rutina obnovení dat pro tuto instanci aplikace.

### <a name="remarks"></a>Poznámky

Každá aplikace, která používá správce restartování, musí mít jednu instanci [třídy CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Tato třída je zodpovědná za sledování otevřených dokumentů a automatického ukládání souborů. Chování `CDataRecoveryHandler` závisí na konfiguraci správce restartování. Další informace naleznete v tématu [CDataRecoveryHandler Class](../../mfc/reference/cdatarecoveryhandler-class.md).

Tato metoda vrátí hodnotu NULL v operačních systémech starších než Windows Vista. Správce restartování není podporován v operačních systémech starších než Windows Vista.

Pokud aplikace aktuálně nemá obslužnou rutinu pro obnovení dat, tato metoda ji vytvoří a vrátí na něj ukazatel.

## <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp::GetFirstDocTemplatePosition

Získá pozici první šablony dokumentu v aplikaci.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci nebo načtení ukazatele objektu; Null, pokud je seznam prázdný.

### <a name="remarks"></a>Poznámky

Použijte hodnotu POSITION vrácenou při volání [GetNextDocTemplate](#getnextdoctemplate) k získání prvního objektu [CDocTemplate.](../../mfc/reference/cdoctemplate-class.md)

## <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp::GetHelpMode

Načte typ nápovědy používané aplikací.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Návratová hodnota

Typ nápovědy používaný aplikací. Další informace naleznete v tématu [CWinApp::m_eHelpType.](#m_ehelptype)

## <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp::GetNextDocTemplate

Získá šablonu dokumentu identifikovanou *pos*, pak nastaví *pos* na hodnotu POSITION.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Odkaz na hodnotu POSITION vrácenou `GetNextDocTemplate` předchozím voláním nebo [GetFirstDocTemplatePosition](#getfirstdoctemplateposition). Hodnota je aktualizována na další pozici tímto voláním.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CDocTemplate.](../../mfc/reference/cdoctemplate-class.md)

### <a name="remarks"></a>Poznámky

Můžete použít `GetNextDocTemplate` ve smyčce iterace vpřed, pokud `GetFirstDocTemplatePosition`navážete počáteční pozici s voláním .

Musíte se ujistit, že vaše hodnota POZICE je platná. Pokud je neplatný, pak ladicí verze Knihovny tříd Microsoft Foundation uplatňuje.

Pokud je načtená šablona dokumentu poslední dostupná, je nová hodnota *pos* nastavena na hodnotu NULL.

## <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp::GetPrinterDeviceDefaults

Volání této členské funkce připravit kontext zařízení tiskárny pro tisk.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parametry

*pPrintDlg*<br/>
Ukazatel na strukturu [PRINTDLG.](/windows/win32/api/commdlg/ns-commdlg-printdlga)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Načte aktuální výchozí hodnoty tiskárny ze systému Windows . INI podle potřeby nebo používá poslední konfiguraci tiskárny nastavenou uživatelem v nastavení tisku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

## <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp::GetProfileBinary

Volání této členské funkce k načtení binárních dat ze záznamu v zadané části registru aplikace nebo . INI.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž hodnota má být načtena.

*ppData*<br/>
Odkazuje na ukazatel, který obdrží adresu dat.

*pBytes*<br/>
Odkazuje na UINT, který obdrží velikost dat (v bajtů).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce nerozlišuje malá a velká písmena, takže řetězce v *parametrech lpszSection* a *lpszEntry* se mohou lišit v případě.

> [!NOTE]
> `GetProfileBinary`přiděluje vyrovnávací paměť \* a vrací svou adresu v *ppData*. Volající je zodpovědný za uvolnění vyrovnávací paměti pomocí **delete []**.

> [!IMPORTANT]
> Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Další příklad naleznete v tématu [CWinApp::WriteProfileBinary](#writeprofilebinary).

## <a name="cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp::GetProfileInt

Voláním této členské funkce lze získat hodnotu celého čísla z položky v určitém oddíle registru aplikace nebo souboru .INI.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.

*lpszEntry*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž hodnota má být načtena.

*nVýchozí*<br/>
Určuje výchozí vrácenou hodnotu, pokud rozhraní položku nemůže najít.

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota řetězce, který následuje zadanou položku, pokud je funkce úspěšná. Vrácená hodnota je hodnota parametru *nDefault,* pokud funkce položku nenalezne. Vrácená hodnota je 0, pokud hodnota, která odpovídá zadané položce, není celé číslo.

Tato členská funkce podporuje šestnáctkovou notaci hodnot v souboru .INI. Při načtení podepsané holčičí číslo, měli byste přetypovat hodnotu **do int**.

### <a name="remarks"></a>Poznámky

Tato členská funkce nerozlišuje malá a velká písmena, takže řetězce v *parametrech lpszSection* a *lpszEntry* se mohou lišit v případě.

> [!IMPORTANT]
> Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Další příklad naleznete v tématu [CWinApp::WriteProfileInt](#writeprofileint).

## <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp::GetProfileString

Volání této členské funkce načíst řetězec přidružený k položce v rámci zadané části v registru aplikace nebo . INI.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.

*lpszEntry*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje položku, jejíž řetězec má být načten. Tato hodnota nesmí být null.

*lpszVýchozí*<br/>
Odkazuje na výchozí hodnotu řetězce pro danou položku, pokud položku nelze najít v inicializačním souboru.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je řetězec z aplikace . INI soubor nebo *lpszDefault,* pokud řetězec nelze najít. Maximální délka řetězce podporovaná rozhraním framework je _MAX_PATH. Pokud *je hodnota LPSZDefault* null, vrácená hodnota je prázdný řetězec.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Další příklad naleznete v příkladu [cwinapp::GetProfileInt](#getprofileint).

## <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp::GetSectionKey

Vrátí klíč pro\\HKEY_CURRENT_USER "Software"\RegistryKey\AppName\lpszSection.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Název klíče, který má být získán.

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

klávesa section, pokud je funkce úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

## <a name="cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp::Skrýtaplikaci

Volánítéto členské funkce skrýt aplikaci před zavřením otevřené dokumenty.

```cpp
void HideApplication();
```

## <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp::HtmlNápověda

Volání této členské funkce k vyvolání aplikace HTMLHelp.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parametry

*dwData*<br/>
Určuje další data. Použitá hodnota závisí na hodnotě parametru *nCmd.* Výchozí hodnoty, `0x000F` které znamená [HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command).

*nCmd*<br/>
Určuje typ požadované nápovědy. Seznam možných hodnot a jejich vliv na parametr *dwData* naleznete v parametru *uCommand* popsaném ve funkcích Rozhraní API [HtmlHelpW](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) nebo [HtmlHelpA](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Rozhraní Framework také volá tuto funkci k vyvolání aplikace HTMLHelp.

Rozhraní framework automaticky ukončí aplikaci HTMLHelp při ukončení aplikace.

## <a name="cwinappinitinstance"></a><a name="initinstance"></a>Cwinapp::initinstance

Systém Windows umožňuje spuštění několika kopií stejného programu současně.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Inicializace aplikace je koncepčně rozdělena do dvou částí: jednorázová inicializace aplikace, která se provádí při prvním spuštění programu, a inicializace instance, která se spustí při každém spuštění kopie programu, včetně prvního spuštění. Provádění rámce `WinMain` volání této funkce.

Přepište `InitInstance` inicializaci každé nové instance aplikace spuštěné v systému Windows. Obvykle přepíšete, `InitInstance` abyste vytvořili objekt hlavního okna a nastavili `CWinThread::m_pMainWnd` datový člen tak, aby ukazoval na toto okno. Další informace o přepsání této členské funkce naleznete v tématu [CWinApp: Třída aplikace](../../mfc/cwinapp-the-application-class.md).

> [!NOTE]
> Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Pokud zavoláte [CoInitializeExV](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) v `InitInstance` přepsání, zadejte COINIT_APARTMENTTHREADED (spíše než COINIT_MULTITHREADED).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

## <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp::IsTaskbarInterakcePovolená

Určuje, zda je povolena interakce na hlavním panelu systému Windows 7.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud `EnableTaskbarInteraction` byla volána a operační systém je Windows 7 nebo vyšší.

### <a name="remarks"></a>Poznámky

Interakce na hlavním panelu znamená, že aplikace MDI zobrazuje obsah podřízených mdi v samostatných miniaturách s kartami, které se zobrazí, když je ukazatel myši nad tlačítkem hlavního panelu aplikace.

## <a name="cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp::LoadCursor

Načte prostředek kurzoru pojmenovaný *lpszResourceName* nebo určený *nIDResource* z aktuálního spustitelného souboru.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název prostředku kurzoru. Pro tento `CString` argument můžete použít.

*nIDZdroj*<br/>
ID prostředku kurzoru. Seznam prostředků naleznete v tématu [LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

`LoadCursor`načte kurzor do paměti pouze v případě, že nebyl dříve načten; v opačném případě načte popisovač existujícího prostředku.

Pomocí členské funkce [LoadStandardCursor](#loadstandardcursor) nebo [LoadOEMCursor](#loadoemcursor) pro přístup k předdefinovaným kurzorům systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

## <a name="cwinapploadicon"></a><a name="loadicon"></a>CWinApp::Ikona načítání

Načte prostředek ikony pojmenovaný *lpszResourceName* nebo určený *nIDResource* ze spustitelného souboru.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje název prostředku ikony. Můžete také použít `CString` pro tento argument.

*nIDZdroj*<br/>
ID číslo prostředku ikony.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

`LoadIcon`načte ikonu pouze v případě, že nebyla dříve načtena; v opačném případě načte popisovač existujícího prostředku.

Pro přístup k předdefinovaným ikonám systému Windows můžete použít členská funkci [LoadStandardIcon](#loadstandardicon) nebo [LoadOEMIcon.](#loadoemicon)

> [!NOTE]
> Tato členská funkce volá funkci Rozhraní API Win32 [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw), která může načíst pouze ikonu, jejíž velikost odpovídá hodnotám SM_CXICON a SM_CYICON systémových metrik.

## <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a>Cwinapp::Kurzor zatížení

Načte předdefinovaný prostředek kurzoru systému Windows určený *společností nIDCursor*.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parametry

*nIDKurz*<br/>
OCR_ **OCR_** identifikátor konstanty manifestu, který určuje předdefinovaný kurzor systému Windows. Musíte mít `#define OEMRESOURCE` `#include \<afxwin.h>` před získat přístup k **OCR_** konstanty v systému WINDOWS. H.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí `LoadOEMCursor` členské funkce [nebo LoadStandardCursor](#loadstandardcursor) pro přístup k předdefinovaným kurzorům systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

## <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a>Cwinapp::LoadOEMIcon

Načte prostředek ikony systému Windows určený *službou nIDIcon*.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parametry

*nIDIcon*<br/>
OIC_ **OIC_** konstantní identifikátor manifestu, který určuje předdefinovanou ikonu systému Windows. Musíte mít `#define OEMRESOURCE` `#include \<afxwin.h>` před přístupem **k OIC_** konstanty v systému WINDOWS. H.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí `LoadOEMIcon` členské funkce [nebo LoadStandardIcon](#loadstandardicon) můžete přistupovat k předdefinovaným ikonám systému Windows.

## <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp::LoadStandardCursor

Načte předdefinovaný prostředek kurzoru systému Windows, který určuje *lpszCursorName.*

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parametry

*lpszCursorName*<br/>
IDC_ **IDC_** konstantní identifikátor manifestu, který určuje předdefinovaný kurzor systému Windows. Tyto identifikátory jsou definovány v systému WINDOWS. H. V následujícím seznamu jsou uvedeny možné předdefinované hodnoty a významy pro *lpszCursorName*:

- IDC_ARROW Kurzor standardní šipky

- IDC_IBEAM Standardní kurzor pro vložení textu

- IDC_WAIT kurzor přesýpacích hodin používaný při provádění časově náročné úlohy systémem Windows

- IDC_CROSS Cross-hair kurzor pro výběr

- IDC_UPARROW Arrow, který ukazuje přímo nahoru

- IDC_SIZE zastaralé a nepodporované; používat IDC_SIZEALL

- IDC_SIZEALL Čtyřcípá šipka. Kurzor, který se má použít ke změně velikosti okna.

- IDC_ICON Zastaralé a nepodporované. Použijte IDC_ARROW.

- IDC_SIZENWSE Dvouhlavá šipka s konci vlevo nahoře a vpravo dole

- IDC_SIZENESW Dvouhlavá šipka s konci v pravém horním a levém dolním rohu

- IDC_SIZEWE Vodorovná dvousměrná šipka

- IDC_SIZENS Svislá dvousměrná šipka

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí `LoadStandardCursor` členské funkce [nebo LoadOEMCursor](#loadoemcursor) pro přístup k předdefinovaným kurzorům systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

## <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp::LoadStandardIcon

Načte předdefinovaný prostředek ikony systému Windows, který určuje *lpszIconName.*

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parametry

*lpszIconName*<br/>
Identifikátor konstanty manifestu, který určuje předdefinovanou ikonu systému Windows. Tyto identifikátory jsou definovány v systému WINDOWS. H. Seznam možných předdefinovaných hodnot a jejich popisy naleznete v parametru *lpIconName* v [aplikaci LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí `LoadStandardIcon` členské funkce [nebo LoadOEMIcon](#loadoemicon) můžete přistupovat k předdefinovaným ikonám systému Windows.

## <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp::LoadStdProfileSettings

Volání této členské funkce z členské funkce [InitInstance](#initinstance) povolit a načíst seznam naposledy použitých souborů (MRU) a poslední stav náhledu.

```cpp
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parametry

*nMaxMRU*<br/>
Počet naposledy použitých souborů ke sledování.

### <a name="remarks"></a>Poznámky

Pokud *nMaxMRU* je 0, žádný seznam MRU bude zachována.

## <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a>CWinApp::m_bHelpMode

TRUE, pokud je aplikace v režimu kontextu nápovědy (obvykle vyvolána s SHIFT + F1); jinak FALSE.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Poznámky

V kontextovém režimu nápovědy se kurzor stane otazníkem a uživatel jej může přesunout po obrazovce. Zkontrolujte tento příznak, pokud chcete implementovat zvláštní zpracování v režimu nápovědy. `m_bHelpMode`je veřejná proměnná typu BOOL.

## <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp::m_dwRestartManagerSupportFlags

Příznaky, které určují, jak se chová správce restartování.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit `m_dwRestartManagerSupportFlags` správce restartování, nastavte požadované chování. V následující tabulce jsou uvedeny příznaky, které jsou k dispozici.

|||
|-|-|
|Příznak|Popis|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Aplikace je registrována pomocí [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager). Správce restartování je zodpovědný za restartování aplikace, pokud se neočekávaně ukončí.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Aplikace je registrována u správce restartování a správce restartování volá funkci zpětného volání obnovení při restartování aplikace. Výchozí funkce zpětného volání obnovení je [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Automatické ukládání je povoleno a správce restartování automaticky uloží všechny otevřené dokumenty při restartování aplikace.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Automatické ukládání je povoleno a správce restartování automaticky ukládá všechny otevřené dokumenty v pravidelných intervalech. Interval je definován [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval).|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Správce restartování otevře dříve otevřené dokumenty po restartování aplikace z neočekávaného ukončení. [Třída CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) zpracovává ukládání seznamu otevřených dokumentů a jejich obnovení.|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Správce restartování vyzve uživatele k obnovení automaticky uložených souborů po restartování aplikace. Třída `CDataRecoveryHandler` dotazuje uživatele.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Spojení AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER a AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Spojení AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Spojení AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Odbory ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

## <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a>CWinApp::m_eHelpType

Typ tohoto datového člena je ve výčtu typu AFX_HELP_TYPE, který je definován v rámci třídy. `CWinApp`

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Poznámky

Výčet AFX_HELP_TYPE je definován takto:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Chcete-li nastavit nápovědu aplikace na nápovědu HTML, zavolejte [SetHelpMode](#sethelpmode) a zadejte `afxHTMLHelp`.

- Chcete-li nastavit nápovědu aplikace na `SetHelpMode` winhelp, zavolejte a zadejte `afxWinHelp`.

## <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a>CWinApp::m_hInstance

Odpovídá parametru *hInstance* předaný `WinMain`systému Windows společnosti .

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Poznámky

Datový `m_hInstance` člen je popisovač aktuální instance aplikace spuštěné v systému Windows. To je vrácena globální funkce [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance`je veřejná proměnná typu HINSTANCE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

## <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a>CWinApp::m_lpCmdLine

Odpovídá parametru *lpCmdLine* předaný `WinMain`systémem Windows společnosti .

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Poznámky

Odkazuje na řetězec s nulovým ukončením, který určuje příkazový řádek aplikace. Slouží `m_lpCmdLine` k přístupu k všem argumentům příkazového řádku, které uživatel zadal při spuštění aplikace. `m_lpCmdLine`je veřejná proměnná typu LPTSTR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp::m_nAutosaveInterval

Doba v milisekundách mezi automatickým ukládáním.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Poznámky

Správce restartování můžete nakonfigurovat tak, aby automaticky ukláněl otevřené dokumenty v nastavených intervalech. Pokud aplikace neukládá soubory automaticky, nemá tento parametr žádný vliv.

## <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a>CWinApp::m_nCmdShow

Odpovídá parametru *nCmdShow* předaný `WinMain`systému Windows společnosti .

```
int m_nCmdShow;
```

### <a name="remarks"></a>Poznámky

Měli byste `m_nCmdShow` předat jako argument při volání [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) pro hlavní okno aplikace. `m_nCmdShow`je veřejná proměnná typu **int**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

## <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinApp::m_pActiveWnd

Tento datový člen slouží k uložení ukazatele do hlavního okna aplikace kontejneru OLE, ve které je aktivována aplikace serveru OLE.

### <a name="remarks"></a>Poznámky

Pokud je tento datový člen NULL, aplikace není aktivní na místě.

Rozhraní Framework nastaví tuto členskou proměnnou, když je okno rámce na místě aktivované aplikací kontejneru OLE.

## <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp::m_pDataRecoveryHandler

Ukazatel na obslužnou rutinu obnovení dat pro aplikaci.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Poznámky

Obslužná rutina obnovení dat aplikace monitoruje otevřené dokumenty a automaticky je ukládá. Rozhraní framework používá obslužnou rutinu pro obnovení dat k obnovení automaticky uložených souborů při neočekávaném restartování aplikace. Další informace naleznete v tématu [CDataRecoveryHandler Class](../../mfc/reference/cdatarecoveryhandler-class.md).

## <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a>CWinApp::m_pszAppName

Určuje název aplikace.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Poznámky

Název aplikace může pocházet z parametru předaného konstruktoru [CWinApp](#cwinapp) nebo, pokud není zadán, do řetězce prostředku s ID AFX_IDS_APP_TITLE. Pokud název aplikace není nalezen v prostředku, pochází z programu . EXE název souboru.

Vráceno globální funkcí [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName`je veřejná proměnná typu **const char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte `m_pszAppName`hodnotu , musí být dynamicky přidělena na haldě. Destruktor `CWinApp` volá **zdarma**( ) s tímto ukazatelem. Mnoho z nich `_tcsdup`chcete použít funkci knihovny ( ) za běhu k alokace. Také uvolněte paměť přidruženou k aktuálnímu ukazateli před přiřazením nové hodnoty. Příklad:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

## <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a>CWinApp::m_pszExeName

Obsahuje název spustitelného souboru aplikace bez přípony.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Poznámky

Na rozdíl [od m_pszAppName](#m_pszappname)tento název nemůže obsahovat prázdná místa. `m_pszExeName`je veřejná proměnná typu **const char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte `m_pszExeName`hodnotu , musí být dynamicky přidělena na haldě. Destruktor `CWinApp` volá **zdarma**( ) s tímto ukazatelem. Mnoho z nich `_tcsdup`chcete použít funkci knihovny ( ) za běhu k alokace. Také uvolněte paměť přidruženou k aktuálnímu ukazateli před přiřazením nové hodnoty. Příklad:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

## <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp::m_pszHelpFilePath

Obsahuje cestu k souboru nápovědy aplikace.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se rozhraní `m_pszHelpFilePath` inicializuje na název aplikace pomocí ". HLP" připojen. Chcete-li změnit název souboru `m_pszHelpFilePath` nápovědy, nastavte na odkaz na řetězec, který obsahuje úplný název požadovaného souboru nápovědy. Vhodné místo k tomu je ve funkci [InitInstance](#initinstance) aplikace. `m_pszHelpFilePath`je veřejná proměnná typu **const char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte `m_pszHelpFilePath`hodnotu , musí být dynamicky přidělena na haldě. Destruktor `CWinApp` volá **zdarma**( ) s tímto ukazatelem. Mnoho z nich `_tcsdup`chcete použít funkci knihovny ( ) za běhu k alokace. Také uvolněte paměť přidruženou k aktuálnímu ukazateli před přiřazením nové hodnoty. Příklad:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

## <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a>CWinApp::m_pszProfileName

Obsahuje název aplikace . INI.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Poznámky

`m_pszProfileName`je veřejná proměnná typu **const char**<strong>\*</strong>.

> [!NOTE]
> Pokud přiřadíte `m_pszProfileName`hodnotu , musí být dynamicky přidělena na haldě. Destruktor `CWinApp` volá **zdarma**( ) s tímto ukazatelem. Mnoho z nich `_tcsdup`chcete použít funkci knihovny ( ) za běhu k alokace. Také uvolněte paměť přidruženou k aktuálnímu ukazateli před přiřazením nové hodnoty. Příklad:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

## <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp::m_pszRegistryKey

Slouží k určení, kde jsou uložena nastavení profilu aplikace v registru nebo souboru INI.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Poznámky

Obvykle je tento datový člen považován za jen pro čtení.

- Hodnota je uložena v klíči registru. Název nastavení profilu aplikace je připojen k následujícímu klíči registru: HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/.

Pokud přiřadíte `m_pszRegistryKey`hodnotu , musí být dynamicky přidělena na haldě. Destruktor `CWinApp` volá **zdarma**( ) s tímto ukazatelem. Mnoho z nich `_tcsdup`chcete použít funkci knihovny ( ) za běhu k alokace. Také uvolněte paměť přidruženou k aktuálnímu ukazateli před přiřazením nové hodnoty. Příklad:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

## <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a>CWinApp::m_pszAppID

ID modelu uživatele aplikace.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Poznámky

## <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp::OnContextHelp

Zpracovává nápovědu SHIFT+F1 v rámci aplikace.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` tuto `CWinApp` členskou funkci povolit, je nutné přidat příkaz do mapy zpráv třídy a také přidat položku tabulky akcelerátoru, obvykle SHIFT+F1.

`OnContextHelp`přepne aplikaci do režimu nápovědy. Kurzor se změní na šipku a otazník a uživatel pak může pohybovat ukazatelem myši a stisknutím levého tlačítka myši vybrat dialogové okno, okno, nabídku nebo příkazové tlačítko. Tato členská funkce načte kontext nápovědy objektu pod kurzorem a zavolá funkci Systému Windows WinHelp s tímto kontextem nápovědy.

## <a name="cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp::OnDDECommand

Volat rámci při okno hlavního rámce obdrží zprávu spuštění DDE.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parametry

*lpszCommand*<br/>
Odkazuje na příkazový řetězec DDE přijatý aplikací.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je příkaz zpracován; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace zkontroluje, zda je příkaz požadavkem na otevření dokumentu, a pokud ano, otevře zadaný dokument. Správce souborů systému Windows obvykle odesílá takové řetězce příkazů DDE, když uživatel poklepe na datový soubor. Přepsat tuto funkci pro zpracování jiných příkazů spuštění DDE, jako je například příkaz k tisku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

## <a name="cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp::OnFileNew

Implementuje příkaz ID_FILE_NEW.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_FILE_NEW, OnFileNew )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Pokud je tato funkce povolena, zpracovává spuštění příkazu File New.

Informace o výchozím chování a pokyny k přepsání této členské funkce naleznete v [technické poznámce 22.](../../mfc/tn022-standard-commands-implementation.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp::OnFileOpen

Implementuje příkaz ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Pokud je tato funkce povolena, zpracovává spuštění příkazu Otevřít soubor.

Informace o výchozím chování a pokyny k přepsání této členské funkce naleznete [v technické poznámce 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp::OnFilePrintSetup

Implementuje příkaz ID_FILE_PRINT_SETUP.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Pokud je tato funkce povolena, zpracovává spuštění příkazu Tisk souborů.

Informace o výchozím chování a pokyny k přepsání této členské funkce naleznete [v technické poznámce 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponhelp"></a><a name="onhelp"></a>CWinApp::OnHelp

Zpracovává Nápovědu F1 v rámci aplikace (pomocí aktuálního kontextu).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Poznámky

Obvykle přidáte také položku klávesy akcelerátoru pro klávesu F1. Povolení klávesy F1 je pouze konvence, nikoli požadavek.

Chcete-li `ON_COMMAND( ID_HELP, OnHelp )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Pokud je tato možnost povolena, volána v rámci, když uživatel stiskne klávesu F1.

Výchozí implementace této funkce obslužné rutiny zpráv určuje kontext nápovědy, který odpovídá aktuálnímu oknu, dialogovému oknu nebo položce nabídky, a pak volá winhelp. Exe. Pokud není aktuálně k dispozici žádný kontext, funkce používá výchozí kontext.

Přepsáním této členské funkce nastavte kontext nápovědy na něco jiného než na okno, dialogové okno, položku nabídky nebo tlačítko panelu nástrojů, které má aktuálně fokus. Volání `WinHelp` s požadovaným ID kontextu nápovědy.

## <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp::OnHelpFinder

Zpracovává příkazy ID_HELP_FINDER a ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Pokud je tato možnost povolena, rozhraní framework zavolá tuto funkci obslužné rutiny zpráv, když uživatel aplikace vybere příkaz Hledání nápovědy, který vyvolá `WinHelp` se standardním **HELP_FINDER** tématem.

## <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp::OnHelpIndex

Zpracovává příkaz ID_HELP_INDEX a poskytuje výchozí téma nápovědy.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Pokud je tato možnost povolena, rozhraní framework zavolá tuto funkci obslužné rutiny zpráv, když uživatel aplikace vybere příkaz Index nápovědy, který vyvolá `WinHelp` se standardním **HELP_INDEX** tématem.

## <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a>Cwinapp::OnHelpUsing CWinApp::OnHelpUsing CWinApp::OnHelpUsing CWin

Zpracovává příkaz ID_HELP_USING.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Poznámky

Chcete-li `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` povolit `CWinApp` tuto člennou funkci, musíte do mapy zpráv třídy přidat příkaz. Rozhraní Framework volá tuto funkci obslužné rutiny zpráv, když `WinHelp` uživatel aplikace vybere příkaz Použití nápovědy k vyvolání aplikace se standardním **HELP_HELPONHELP** tématem.

## <a name="cwinapponidle"></a><a name="onidle"></a>Cwinapp::OnIdle

Přepsat tuto člennou funkci provádět zpracování nečinnosti.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parametry

*lPočet*<br/>
Čítač se pokaždé, když `OnIdle` je volána, když je fronta zpráv aplikace prázdná. Tento počet se při každém zpracování nové zprávy resetuje na 0. Parametr *lCount* můžete použít k určení relativní doby, po kterou byla aplikace nečinná bez zpracování zprávy.

### <a name="return-value"></a>Návratová hodnota

Nenulová pro příjem více času zpracování nečinnosti; 0, pokud není potřeba žádná další doba nečinnosti.

### <a name="remarks"></a>Poznámky

`OnIdle`je volána ve smyčku výchozí zprávy, když je fronta zpráv aplikace prázdná. Pomocí přepsání můžete volat vlastní úlohy obslužné rutiny na pozadí.

`OnIdle`by měl vrátit 0 označuje, že není vyžadována žádná doba zpracování nečinnosti. Parametr *lCount* se zpřísňuje pokaždé, když `OnIdle` je volána fronta zpráv prázdná a při každém zpracování nové zprávy se obnoví na hodnotu 0. Můžete volat různé nečinné rutiny na základě tohoto počtu.

Následující shrnuje zpracování nečinnosti smyčky:

1. Pokud smyčka zpráv v knihovně tříd Microsoft Foundation zkontroluje frontu `OnIdle` zpráv a nenajde žádné čekající zprávy, zavolá objekt aplikace a poskytne 0 jako argument *lCount.*

2. `OnIdle`provede některé zpracování a vrátí nenulovou hodnotu označující, že by měla být volána znovu provést další zpracování.

3. Smyčka zpráv znovu zkontroluje frontu zpráv. Pokud žádné zprávy čekají `OnIdle` na vyřízení, volání znovu, zvýšení *argument lCount.*

4. Nakonec `OnIdle` dokončí zpracování všech jeho nečinnosti úkoly a vrátí 0. To říká smyčky zprávy `OnIdle` zastavit volání, dokud další zpráva je přijata z fronty zpráv, v tomto okamžiku cyklu nečinnosti restartuje s argumentem nastavenna 0.

Během provádění zdlouhavých `OnIdle` úloh neprovádějte `OnIdle` zdlouhavé úlohy, protože aplikace nemůže zpracovat vstup uživatele, dokud se nevrátí.

> [!NOTE]
> Výchozí implementace `OnIdle` objektů uživatelského rozhraní příkazu aktualizace, jako jsou položky nabídky a tlačítka panelu nástrojů, a provádí vyčištění vnitřní struktury dat. Proto pokud přepsat `OnIdle`, musíte `CWinApp::OnIdle` volat `lCount` s v přepsané verzi. Nejprve volání všech nečinnosti základní třídy zpracování `OnIdle` (to znamená, dokud základní třída vrátí 0). Pokud potřebujete provést práci před dokončením zpracování základní třídy, zkontrolujte implementaci základní třídy a vyberte správné *lCount,* během kterého chcete provést svou práci.

Pokud nechcete `OnIdle` být volána vždy, když je zpráva načtena z fronty zpráv, můžete přepsat [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Pokud aplikace nastavila velmi krátký časovač nebo pokud systém odesílá `OnIdle` zprávu WM_SYSTIMER, bude volána opakovaně a snižuje výkon.

### <a name="example"></a>Příklad

Následující dva příklady ukazují, `OnIdle`jak používat . První příklad zpracuje dva nečinné úlohy pomocí argumentu *lCount* k určení priority úloh. První úkol má vysokou prioritu a měli byste to udělat, kdykoli je to možné. Druhý úkol je méně důležité a by mělo být provedeno pouze v případě, že je dlouhá pauza v vstupu uživatele. Poznámka: volání verze základní třídy `OnIdle`. Druhý příklad spravuje skupinu nečinných úloh s různými prioritami.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

## <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp::Soubor OpenDocumentFile

Rozhraní Framework volá tuto metodu k otevření pojmenovaného souboru [CDocument](../../mfc/reference/cdocument-class.md) pro aplikaci.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*název souboru lpsz*<br/>
[v] Název souboru, který má být otevřen.

*bAddToMRU*<br/>
[v] PRAVDA označuje, že dokument je jedním z nejnovějších souborů; NEPRAVDA označuje, že dokument není jedním z nejnovějších souborů.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CDocument` a pokud úspěšné; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud je dokument, který má tento název již otevřen, první okno rámce, který obsahuje tento dokument, získá fokus. Pokud aplikace podporuje více šablon dokumentů, rozhraní framework používá příponu názvu souboru k vyhledání příslušné šablony dokumentu a pokusu o načtení dokumentu. Pokud je úspěšná, šablona dokumentu pak vytvoří okno rámce a zobrazení dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp::ParseCommandLine

Volání této členské funkce analyzovat příkazový řádek a odeslat parametry, jeden po druhém, [cCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).

```cpp
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odkaz na objekt [CCommandLineInfo.](../../mfc/reference/ccommandlineinfo-class.md)

### <a name="remarks"></a>Poznámky

Při `CCommandLineInfo`spuštění nového projektu knihovny MFC pomocí Průvodce aplikací vytvoří Průvodce aplikací `ProcessShellCommand` `ParseCommandLine` místní instanci aplikace a potom zavolá a v členské funkci [InitInstance.](#initinstance) Příkazový řádek sleduje níže popsanou trasu:

1. Po vytvoření `InitInstance`v `CCommandLineInfo` aplikaci je `ParseCommandLine`objekt předán .

2. `ParseCommandLine`pak `CCommandLineInfo::ParseParam` volá opakovaně, jednou pro každý parametr.

3. `ParseParam`vyplní `CCommandLineInfo` objekt, který je pak předán [ProcessShellCommand](#processshellcommand).

4. `ProcessShellCommand`zpracovává argumenty a příznaky příkazového řádku.

Všimněte si, `ParseCommandLine` že můžete volat přímo podle potřeby.

Popis příznaků příkazového řádku naleznete v tématu [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

## <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp::PreTranslateMessage

Přepsat tuto funkci filtrovat okno zprávy před jejich odesláním do funkcí systému Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) `CWinApp::PreTranslateMessage` Výchozí implementace provádí překlad klíče akcelerátoru, takže je nutné volat členské funkce v přepsané verzi.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel na strukturu [MSG,](/windows/win32/api/winuser/ns-winuser-msg) která obsahuje zprávu ke zpracování.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zpráva `PreTranslateMessage` plně zpracována a neměla by být dále zpracována. Nula, pokud by zpráva měla být zpracována normálním způsobem.

## <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp::ProcessMessageFilter

Funkce zavěšení rozhraní volá tuto členská funkci k filtrování a odpovědi na určité zprávy systému Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*Kód*<br/>
Určuje kód háku. Tato členská funkce používá kód k určení způsobu zpracování *lpMsg.*

*lpMsg*<br/>
Ukazatel na tructure Windows [MSG.](/windows/win32/api/winuser/ns-winuser-msg)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zpráva zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Háček funkce zpracovává události před jejich odesláním do aplikace normální zpracování zpráv.

Pokud přepíšete tuto pokročilou funkci, nezapomeňte volat verzi základní třídy pro zachování zpracování zavěšení rozhraní.

## <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp::ProcessShellCommand

Tato členská funkce je volána [InitInstance](#initinstance) přijmout `CCommandLineInfo` parametry předané z objektu *určeného rCmdInfo*a provést uvedenou akci.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parametry

*rCmdInfo*<br/>
Odkaz na objekt [CCommandLineInfo.](../../mfc/reference/ccommandlineinfo-class.md)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je příkaz prostředí úspěšně zpracován. Pokud 0, vrátí FALSE z [InitInstance](#initinstance).

### <a name="remarks"></a>Poznámky

Při spuštění nového projektu `CCommandLineInfo`knihovny MFC pomocí Průvodce aplikací vytvoří Průvodce aplikací `ProcessShellCommand` místní instanci aplikace a potom zavolá a [ParseCommandLine](#parsecommandline) v `InitInstance` členské funkci. Příkazový řádek sleduje níže popsanou trasu:

1. Po vytvoření `InitInstance`v `CCommandLineInfo` aplikaci je `ParseCommandLine`objekt předán .

2. `ParseCommandLine`pak volá [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) opakovaně, jednou pro každý parametr.

3. `ParseParam`vyplní `CCommandLineInfo` objekt, který je `ProcessShellCommand`pak předán .

4. `ProcessShellCommand`zpracovává argumenty a příznaky příkazového řádku.

Datové členy objektu, `CCommandLineInfo` identifikované [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), jsou následujícího typu s výčtu, který je definován v rámci `CCommandLineInfo` třídy.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Stručný popis každé z těchto hodnot `CCommandLineInfo::m_nShellCommand`naleznete v tématu .

## <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp::ProcessWndProcException

Rozhraní Framework volá tuto členskou funkci vždy, když obslužná rutina nezachytí výjimku vyženou v jedné z obslužných rutin zprávy nebo příkazu vaší aplikace.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*E*<br/>
Ukazatel na nezachycenou výjimku.

*pMsg*<br/>
Tructure [MSG,](/windows/win32/api/winuser/ns-winuser-msg)který obsahuje informace o zprávě systému Windows, která způsobila, že rozhraní pro vyvolání výjimky.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která by měla být vrácena systému Windows. Za normálních okolností se jedná o 0L pro zprávy systému Windows, 1L ( TRUE) pro příkazové zprávy.

### <a name="remarks"></a>Poznámky

Nevolejte tuto člennou funkci přímo.

Výchozí implementace této členské funkce vytvoří okno se zprávou. Pokud nezachycená výjimka pochází z nabídky, panelu nástrojů nebo selhání příkazu akcelerátoru, zobrazí se v poli se zprávou zpráva "Příkaz se nezdařil"; v opačném případě se zobrazí zpráva "Vnitřní chyba aplikace".

Přepsat tuto členská funkci poskytnout globální zpracování výjimek. Základní funkce zavolejte pouze v případě, že chcete zobrazit okno se zprávou.

## <a name="cwinappregister"></a><a name="register"></a>CWinApp::Registrovat

Provádí všechny úlohy `RegisterShellFileTypes`registrace, které nejsou zpracovány .

```
virtual BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace jednoduše vrátí hodnotu TRUE. Přepište tuto funkci a poskytněte všechny přizpůsobené kroky registrace.

## <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp::RegisterShellTypy souborů

Volání této členské funkce zaregistrovat všechny typy dokumentů aplikace ve Správci souborů systému Windows.

```cpp
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parametry

*bCompat*<br/>
[v] TRUE přidává registrační položky pro příkazy prostředí Tisk a Tisk na, což umožňuje uživateli tisknout soubory přímo z prostředí nebo přetažením souboru do objektu tiskárny. Přidá také klíč DefaultIcon. Ve výchozím nastavení je tento parametr nepravda z důvodu zpětné kompatibility.

### <a name="remarks"></a>Poznámky

To umožňuje uživateli otevřít datový soubor vytvořený vaší aplikací poklepáním z v rámci Správce souborů. Volání `RegisterShellFileTypes` po volání [AddDocTemplate](#adddoctemplate) pro každou šablonu dokumentu v aplikaci. Při volání `RegisterShellFileTypes`také volejte členská funkci [EnableShellOpen](#enableshellopen) .

`RegisterShellFileTypes`iterates prostřednictvím seznamu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objekty, které aplikace udržuje a pro každou šablonu dokumentu přidá položky do registrační databáze, které systém Windows udržuje pro přidružení souborů. Správce souborů používá tyto položky k otevření datového souboru, když na něj uživatel poklepe. To eliminuje potřebu doručovat . REG s vaší aplikací.

> [!NOTE]
> `RegisterShellFileTypes`Funguje pouze v případě, že uživatel spustí program s právy správce. Pokud program nemá práva správce, nemůže změnit klíče registru.

Pokud registrační databáze již přidruží danou příponu názvu souboru k jinému typu souboru, nebude vytvořeno žádné nové přidružení. Viz `CDocTemplate` třídy pro formát řetězců potřebných k registraci těchto informací.

## <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp::RegisterWithRestartManager

Zaregistruje aplikaci se správcem restartování.

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
|*bRegisterRecoveryCallback*|[v] True označuje, že tato instance aplikace používá funkci zpětného volání obnovení; FALSE označuje, že tomu tak není. Rozhraní framework volá funkci zpětného volání obnovení při neočekávaně ukončí aplikace. Další informace naleznete v tématu [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*strRestartIdentifier*|[v] Jedinečný řetězec, který identifikuje tuto instanci správce restartování. Identifikátor správce restartování je jedinečný pro každou instanci aplikace.|
|*pwzCommandLineArgs*|[v] Řetězec, který obsahuje všechny další argumenty z příkazového řádku.|
|*dwRestartFlags*|[v] Volitelné příznaky pro správce restartování. Další informace naleznete v části Poznámky.|
|*pRecoveryCallback*|[v] Funkce zpětného volání obnovení. Tato funkce musí trvat LPVOID parametr jako vstup a vrátit DWORD. Výchozí funkce zpětného `CWinApp::ApplicationRecoveryCallback`volání obnovení je .|
|*lpvParam*|[v] Vstupní parametr pro funkci zpětného volání obnovení. Další informace naleznete v tématu [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*dwPingInterval*|[v] Doba, po kterou správce restartování čeká na návrat funkce zpětného volání obnovení. Tento parametr je v milisekundách.|
|*dwCallbackFlags*|[v] Příznaky předané funkci zpětného volání obnovení. Vyhrazeno pro budoucí použití.|

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace používá výchozí implementaci knihovny MFC pro automatické `RegisterWithRestartManager`ukládání souborů, měli byste použít jednoduchou verzi aplikace . Použijte komplexní `RegisterWithRestartManager` verzi, pokud chcete přizpůsobit chování automatického ukládání vaší aplikace.

Pokud tuto metodu zavoláte s prázdným `RegisterWithRestartManager` řetězcem pro *strRestartIdentifier*, vytvoří jedinečný řetězec identifikátoru pro tuto instanci správce restartování.

Při neočekávaném ukončení aplikace restartuje správce restartování aplikace z příkazového řádku a poskytuje jedinečný identifikátor restartování jako volitelný argument. V tomto scénáři `RegisterWithRestartManager` volání rozhraní dvakrát. První volání pochází z [CWinApp::InitInstance](#initinstance) s prázdným řetězcem pro identifikátor řetězce. Potom metoda [CWinApp::ProcessShellCommand](#processshellcommand) `RegisterWithRestartManager` volání s jedinečným identifikátorem restart.

Po registraci aplikace u správce restartování program správce restartování aplikaci monitoruje. Pokud aplikace neočekávaně ukončí, správce restartování volá funkci zpětného volání obnovení během procesu vypnutí. Správce restartování čeká *dwPingInterval* na odpověď z funkce zpětného volání obnovení. Pokud funkce zpětného volání obnovení nereaguje během této doby, aplikace ukončí bez spuštění funkce zpětného volání obnovení.

Ve výchozím nastavení dwRestartFlags nejsou podporovány, ale jsou k dispozici pro budoucí použití. Možné hodnoty pro *dwRestartFlags* jsou následující:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp::ZnovuotevřítPreviousFilesAtRestart

Určuje, zda správce restartování znovu otevře soubory, které byly otevřeny při neočekávaném ukončení aplikace.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že správce restartování znovu otevře dříve otevřené soubory. NEPRAVDA označuje, že správce restartování nikoli.

## <a name="cwinapprestartinstance"></a><a name="restartinstance"></a>Cwinapp::Restartinstance

Zpracovává restartování aplikace iniciované správcem restartování.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud obslužná rutina obnovení dat otevře dříve otevřené dokumenty; FALSE, pokud má obslužná rutina obnovení dat chybu nebo pokud neexistují žádné dříve otevřené dokumenty.

### <a name="remarks"></a>Poznámky

Když správce restartování restartuje aplikaci, rozhraní framework volá tuto metodu. Tato metoda načte obslužnou rutinu obnovení dat a obnoví automaticky uložené soubory. Tato metoda volá [CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) k určení, zda uživatel chce obnovit automaticky uložené soubory.

Tato metoda vrátí hodnotu FALSE, pokud [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) zjistí, že nebyly k dispozici žádné otevřené dokumenty. Pokud nebyly k dispozici žádné otevřené dokumenty, aplikace se spustí obvykle.

## <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp::RestoreAutosavedFilesAtRestart

Určuje, zda správce restartování obnoví automaticky uložené soubory při restartování aplikace.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že správce restartování obnoví automaticky uložené soubory; NEPRAVDA označuje, že správce restartování nikoli.

## <a name="cwinapprun"></a><a name="run"></a>CWinApp::Spustit

Poskytuje výchozí smyčku zpráv.

```
virtual int Run();
```

### <a name="return-value"></a>Návratová hodnota

**Int** hodnota, která `WinMain`je vrácena .

### <a name="remarks"></a>Poznámky

`Run`získává a odesílá zprávy systému Windows, dokud aplikace neobdrží zprávu WM_QUIT. Pokud fronta zpráv aplikace aktuálně neobsahuje `Run` žádné zprávy, volá [OnIdle](#onidle) provést zpracování nečinnosti. Příchozí zprávy přejdou na členskou funkci [PreTranslateMessage](#pretranslatemessage) pro `TranslateMessage` speciální zpracování a poté na funkci systému Windows pro standardní překlad klávesnice; nakonec je `DispatchMessage` volána funkce systému Windows.

`Run`je zřídka přepsána, ale můžete přepsat poskytnout zvláštní chování.

## <a name="cwinapprunautomated"></a><a name="runautomated"></a>CWinApp::Spustit automatické

Volání této funkce k určení, zda je k dispozici možnost " **/Automation**" nebo " **-Automation**", která označuje, zda byla serverová aplikace spuštěna klientskou aplikací.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla nalezena možnost; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici, je tato možnost odebrána z příkazového řádku. Další informace o automatizaci OLE naleznete v článku [Automatizační servery](../../mfc/automation-servers.md).

## <a name="cwinapprunembedded"></a><a name="runembedded"></a>CWinApp::RunEmbedded

Volání této funkce k určení, zda je k dispozici možnost " **/Embedding**" nebo **"-Embedding**", která označuje, zda byla serverová aplikace spuštěna klientskou aplikací.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla nalezena možnost; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici, je tato možnost odebrána z příkazového řádku. Další informace o vkládání naleznete v článku [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp::UložitAllModified

Volat rámci uložit všechny dokumenty, když má být uzavřena hlavní okno rámce aplikace nebo prostřednictvím WM_QUERYENDSESSION zprávy.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je bezpečná ukončit aplikaci; 0, pokud není bezpečné ukončit aplikaci.

### <a name="remarks"></a>Poznámky

Výchozí implementace této členské funkce volá členská funkce [CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified) pro všechny upravené dokumenty v rámci aplikace.

## <a name="cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp::SelectPrinter

Voláním této členské funkce vyberte určitou tiskárnu a uvolněte tiskárnu, která byla dříve vybrána v tiskovém dialogovém okně.

```cpp
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parametry

*hDevNames*<br/>
Popisovač tructure [DEVNAMES,](/windows/win32/api/commdlg/ns-commdlg-devnames)který identifikuje názvy ovladačů, zařízení a výstupního portu konkrétní tiskárny.

*hDevMode*<br/>
Popisovač struktury [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) která určuje informace o inicializaci zařízení a prostředí tiskárny.

*bFreeOld*<br/>
Uvolní dříve vybranou tiskárnu.

### <a name="remarks"></a>Poznámky

Pokud jsou *hodnoty hDevMode* i *hDevNames* null, `SelectPrinter` použije aktuální výchozí tiskárnu.

## <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp::Nastavitrežim nápovědy

Nastaví typ nápovědy aplikace.

```cpp
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parametry

*eHelpType*<br/>
Určuje typ nápovědy, která má být používána. Další informace naleznete v tématu [CWinApp::m_eHelpType.](#m_ehelptype)

### <a name="remarks"></a>Poznámky

Nastaví typ nápovědy aplikace.

Chcete-li nastavit typ nápovědy aplikace na nápovědu HTMLHelp, můžete volat [EnableHTMLHelp](#enablehtmlhelp). Po volání `EnableHTMLHelp`aplikace musí používat HTMLHelp jako jeho nápovědu. Pokud chcete změnit používat WinHelp, můžete `SetHelpMode` volat a nastavit `afxWinHelp` *eHelpType* na .

## <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp::Nastavit klíč registru

Způsobí, že nastavení aplikace, které mají být uloženy v registru namísto souborů INI.

```cpp
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistryKey*<br/>
Ukazatel na řetězec obsahující název klíče.

*nIDRegistryKey*<br/>
ID prostředku řetězce obsahujícího název klíče registru.

### <a name="remarks"></a>Poznámky

Tato funkce nastaví *m_pszRegistryKey*, `GetProfileInt`která `GetProfileString` `WriteProfileInt`je `WriteProfileString` pak používána , , a členské funkce `CWinApp`. Pokud byla tato funkce volána, seznam naposledy použitých souborů (MRU) je také uložen v registru. Klíč registru je obvykle název společnosti. Je uložen v klíči následujícího formuláře:\\ HKEY_CURRENT_USER\Software<\> \\ název společnosti\> \\<název aplikace<název\> \\ oddílu<název\>hodnoty .

## <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp::Podporuje obnovení aplikace

Určuje, zda správce restartování obnoví aplikaci, která byla neočekávaně ukončena.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že správce restartování obnoví aplikaci; NEPRAVDA označuje, že správce restartování nikoli.

## <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp::Podporujeautomatické ukládáníinterval

Určuje, zda správce restartování automaticky ukládá otevřené dokumenty v pravidelných intervalech.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že správce restartování automaticky ukládá otevřené dokumenty. NEPRAVDA označuje, že správce restartování nikoli.

## <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp::PodporujeAutosaveAtRestart

Určuje, zda správce restartování automaticky uloží všechny otevřené dokumenty při restartování aplikace.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že správce restartování automaticky uloží otevřené dokumenty při restartování aplikace. NEPRAVDA označuje, že správce restartování nikoli.

## <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp::PodporujeRestartManager

Určuje, zda aplikace podporuje správce restartování.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že aplikace podporuje správce restartování; FALSE označuje, že aplikace není.

## <a name="cwinappunregister"></a><a name="unregister"></a>CWinApp::Zrušit registraci

Zruší registrace všech souborů registrovaných aplikačním objektem.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Funkce `Unregister` zruší registraci provedenou objektem aplikace a funkcí [Register.](#register) Za normálních okolností jsou obě funkce volány implicitně knihovnou MFC a proto se nezobrazí v kódu.

Přepište tuto funkci a proveďte vlastní kroky zrušení registrace.

## <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp::UnregisterShellFileTypes CWinApp::UnregisterShellFileTypes CWinApp::UnregisterShellFileTypes CWin

Volánítéto členské funkce zrušit registraci všech typů dokumentů aplikace pomocí Správce souborů systému Windows.

```cpp
void UnregisterShellFileTypes();
```

## <a name="cwinappwinhelp"></a><a name="winhelp"></a>CWinApp::WinHelp

Volání této členské funkce k vyvolání aplikace WinHelp.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parametry

*dwData*<br/>
Určuje další data. Použitá hodnota závisí na hodnotě parametru *nCmd.*

*nCmd*<br/>
Určuje typ požadované nápovědy. Seznam možných hodnot a jejich vliv na parametr *dwData* naleznete ve funkci [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows.

### <a name="remarks"></a>Poznámky

Rozhraní Framework také volá tuto funkci k vyvolání aplikace WinHelp.

Rozhraní Framework automaticky ukončí aplikaci WinHelp při ukončení aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

## <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp::WriteProfileBinary

Volání této členské funkce pro zápis binárních dat do zadané části registru aplikace nebo . INI.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud oddíl neexistuje, je vytvořen. Název oddílu je nezávislý na případu; řetězec může být libovolná kombinace velkých a malých písmen.

*lpszEntry*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje položku, do které má být hodnota zapsána. Pokud položka v zadaném oddílu neexistuje, je vytvořena.

*Pdata*<br/>
Odkazuje na data, která mají být zapsána.

*nBajtu bajtů*<br/>
Obsahuje počet bajtů, které mají být zapsány.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

Tento příklad `CWinApp* pApp = AfxGetApp();` slouží k získání na CWinApp třídy ilustrující způsobem, který `WriteProfileBinary` a `GetProfileBinary` lze použít z libovolné funkce v aplikaci knihovny MFC.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Další příklad naleznete v příkladu [cwinapp::GetProfileBinary](#getprofilebinary).

## <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp::WriteProfileInt

Volání této členské funkce zapsat zadanou hodnotu do zadané části registru aplikace nebo . INI.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud oddíl neexistuje, je vytvořen. Název oddílu je nezávislý na případu; řetězec může být libovolná kombinace velkých a malých písmen.

*lpszEntry*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje položku, do které má být hodnota zapsána. Pokud položka v zadaném oddílu neexistuje, je vytvořena.

*nHodnota*<br/>
Obsahuje hodnotu, která má být zapsána.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

Tento příklad `CWinApp* pApp = AfxGetApp();` slouží k získání třídy CWinApp `WriteProfileString`ilustrující způsob, jakým , `WriteProfileInt`, `GetProfileString`, a `GetProfileInt` lze použít z libovolné funkce v aplikaci knihovny MFC.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Další příklad naleznete v příkladu [cwinapp::GetProfileInt](#getprofileint).

## <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp::WriteProfileString

Volání této členské funkce zapsat zadaný řetězec do zadané části registru aplikace nebo . INI.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parametry

*lpszSekce*<br/>
Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud oddíl neexistuje, je vytvořen. Název oddílu je nezávislý na případu; řetězec může být libovolná kombinace velkých a malých písmen.

*lpszEntry*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje položku, do které má být hodnota zapsána. Pokud položka v zadaném oddílu neexistuje, je vytvořena. Pokud je tento parametr NULL, oddíl určený *lpszSection* je odstraněn.

*lpszValue*<br/>
Odkazuje na řetězec, který má být zapsán. Pokud je tento parametr NULL, položka určená parametrem *lpszEntry* bude odstraněna.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Další příklad naleznete v příkladu [cwinapp::GetProfileInt](#getprofileint).

## <a name="cwinappsetappid"></a><a name="setappid"></a>CWinApp::SetAppID

Explicitně nastaví ID modelu uživatele aplikace pro aplikaci. Tato metoda by měla být volána před jakékoli uživatelské rozhraní je předloženuživateli (nejlepší místo je konstruktor aplikace).

```cpp
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parametry

*lpcszAppID*<br/>
Určuje ID modelu uživatele aplikace.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Třída CWinThread](../../mfc/reference/cwinthread-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md)
