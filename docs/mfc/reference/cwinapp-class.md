---
title: CWinApp – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aab01b0f55d19ef3c9d39fed38b42471f559ba8d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123198"
---
# <a name="cwinapp-class"></a>CWinApp – třída
Základní třída, ze kterého odvodíte objekt aplikace systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWinApp : public CWinThread  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinApp::CWinApp](#cwinapp)|Vytvoří `CWinApp` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinApp::AddDocTemplate](#adddoctemplate)|Přidá šablonu dokumentu aplikace seznam šablon dokumentu k dispozici.|  
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|Přidá do seznamu naposledy použitých souborů (naposledy použitých) název souboru.|  
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Voláno rámcem, pokud neočekávaně ukončí aplikaci.|  
|[CWinApp::CloseAllDocuments](#closealldocuments)|Zavře všechny otevřené dokumenty.|  
|[CWinApp::CreatePrinterDC](#createprinterdc)|Vytvoří kontextu zařízení tiskárny.|  
|[CWinApp::DelRegTree](#delregtree)|Odstraní zadaný klíč a všechny jeho podklíče.|  
|[CWinApp::DoMessageBox](#domessagebox)|Implementuje [AfxMessageBox –](cstring-formatting-and-message-box-display.md#afxmessagebox) pro aplikaci.|  
|[CWinApp::DoWaitCursor](#dowaitcursor)|Kurzor čekání vypíná a zapíná.|  
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|Umožňuje podporu D2D aplikace. Tuto metodu volejte před inicializací hlavní okno.|  
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementuje HTMLHelp aplikace, nikoli WinHelp.|  
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Umožňuje interakci panelu.|  
|[CWinApp::ExitInstance](#exitinstance)|Přepsání nastavení za účelem vyčištění při ukončení aplikace.|  
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Načte vstupního parametru pro metodu obnovení aplikace.|  
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Vrátí dobu, kterou správce restartování čeká funkce zpětného volání obnovení vrátit.|  
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Vrátí příznaků pro správce restartování.|  
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Vrátí klíč pro HKEY_CURRENT_USER\\\RegistryKey\ProfileName "Software".|  
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Získá obslužnou rutinu obnovení dat pro tuto instanci aplikace.|  
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Načte pozici první šablona dokumentu.|  
|[CWinApp::GetHelpMode](#gethelpmode)|Načte typ nápovědy používá aplikace.|  
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Načte pozici šablony dokumentu. Lze použít rekurzivně.|  
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Načte výchozí nastavení zařízení tiskárny.|  
|[CWinApp::GetProfileBinary](#getprofilebinary)|Načte binární data z položku do aplikace. Soubor INI.|  
|[CWinApp::GetProfileInt](#getprofileint)|Načte celé číslo z položku do aplikace. Soubor INI.|  
|[CWinApp::GetProfileString](#getprofilestring)|Načte řetězec z položku do aplikace. Soubor INI.|  
|[CWinApp::GetSectionKey](#getsectionkey)|Vrátí klíč pro HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection "Software".|  
|[CWinApp::HideApplication](#hideapplication)|Skryje aplikace před jeho zavřením všechny dokumenty.|  
|[CWinApp::HtmlHelp](#htmlhelp)|Volání `HTMLHelp` funkce systému Windows.|  
|[CWinApp::InitInstance](#initinstance)|Přepsání nastavení za účelem provést inicializaci instance Windows, jako je například vytváření vašeho objekty oken.|  
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Určuje, zda je povoleno interakce na hlavním panelu Windows 7.|  
|[CWinApp::LoadCursor](#loadcursor)|Načte prostředek kurzoru.|  
|[CWinApp::LoadIcon](#loadicon)|Načte prostředek s ikonou.|  
|[CWinApp::LoadOEMCursor](#loadoemcursor)|Načítání Windows OEM předdefinované kurzoru, **OCR_** konstanty zadejte ve WINDOWS. H.|  
|[CWinApp::LoadOEMIcon](#loadoemicon)|Načte předdefinované ikonou Windows OEM, **OIC_** konstanty zadejte ve WINDOWS. H.|  
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Načítání Windows předdefinované kurzoru, **IDC_** konstanty zadejte ve WINDOWS. H.|  
|[CWinApp::LoadStandardIcon](#loadstandardicon)|Načte předdefinované ikona systému Windows, **IDI_** konstanty zadejte ve WINDOWS. H.|  
|[CWinApp::OnDDECommand](#onddecommand)|Voláno rámcem v reakci na dynamická data systému exchange (DDE) možné provést příkaz.|  
|[CWinApp::OnIdle](#onidle)|Přepsání nastavení za účelem provedení zpracování doby nečinnosti specifické pro aplikaci.|  
|[CWinApp::OpenDocumentFile](#opendocumentfile)|Voláno rámcem k otevření dokumentu ze souboru.|  
|[CWinApp::ParseCommandLine](#parsecommandline)|Analyzuje jednotlivé parametry a příznaky v příkazovém řádku.|  
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|Filtry zpráv předtím, než jsou odeslány do funkce Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Zachytí některé zprávy předtím, než nedostanou aplikace.|  
|[CWinApp::ProcessShellCommand](#processshellcommand)|Zpracovává argumenty příkazového řádku a značky.|  
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Zachycuje všechny neošetřené výjimky vyvolané aplikace zprávu a obslužné rutiny příkazů.|  
|[CWinApp::Register](#register)|Provede vlastní registrace.|  
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Registruje správce restartování aplikace.|  
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Určuje, zda správce restartování neotevře soubory, které byly otevřené, pokud aplikace byl neočekávaně ukončen.|  
|[CWinApp::RestartInstance](#restartinstance)|Zpracuje restartování aplikace iniciovaná správce restartování.|  
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Určuje, zda správce restartování obnoví soubory automaticky uloženo po restartování aplikace.|  
|[CWinApp::Run](#run)|Spustí výchozí zpráva smyčky. Přepsání nastavení za účelem přizpůsobení smyčce zpráv.|  
|[CWinApp::RunAutomated](#runautomated)|Aplikace příkazového řádku pro testy **/Automation** možnost. Zastaralé. Místo toho používat hodnotu v [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) po volání [ParseCommandLine](#parsecommandline).|  
|[CWinApp::RunEmbedded](#runembedded)|Aplikace příkazového řádku pro testy **/vložení** možnost. Zastaralé. Místo toho používat hodnotu v [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) po volání [ParseCommandLine](#parsecommandline).|  
|[CWinApp::SaveAllModified](#saveallmodified)|Zobrazí výzvu pro uložení všech upravené dokumenty.|  
|[CWinApp::SelectPrinter](#selectprinter)|Vybere tiskárnu předtím indikovali uživatelem prostřednictvím dialogové okno tisku.|  
|[CWinApp::SetHelpMode](#sethelpmode)|Nastaví a inicializuje typ nápovědy používá aplikace.|  
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|Určuje, zda správce restartování obnoví aplikaci, která byl neočekávaně ukončen.|  
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Určuje, zda autosaves správce restartování otevřít dokumenty v pravidelných intervalech.|  
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Určuje, zda autosaves správce restartování žádné otevřít dokumenty, když se aplikace restartuje.|  
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|Určuje, jestli aplikace podporuje správce restartování.|  
|[CWinApp::Unregister](#unregister)|Zruší registraci všechno, co ví, že jej zaregistrovat `CWinApp` objektu.|  
|[CWinApp::WinHelp](#winhelp)|Volání `WinHelp` funkce systému Windows.|  
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Binární data zapíše položku do aplikace. Soubor INI.|  
|[CWinApp::WriteProfileInt](#writeprofileint)|Zapíše položku v aplikačním celé číslo. Soubor INI.|  
|[CWinApp::WriteProfileString](#writeprofilestring)|Zapíše řetězec položku do aplikace. Soubor INI.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinApp::EnableShellOpen](#enableshellopen)|Umožňuje uživateli otevřít datových souborů ze Správce souborů systému Windows.|  
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Načítání standard. Nastavení souboru INI a umožňuje naposledy použitých souborů funkce seznamu.|  
|[CWinApp::OnContextHelp](#oncontexthelp)|Zpracovává SHIFT + F1 – Nápověda v aplikaci.|  
|[CWinApp::OnFileNew](#onfilenew)|Implementuje id_file_new – příkaz.|  
|[CWinApp::OnFileOpen](#onfileopen)|Implementuje id_file_open – příkaz.|  
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementuje id_file_print_setup – příkaz.|  
|[CWinApp::OnHelp](#onhelp)|Zpracovává nápovědy F1 v rámci aplikace (pomocí aktuálního kontextu).|  
|[CWinApp::OnHelpFinder](#onhelpfinder)|Zpracovává příkazy ID_HELP_FINDER a id_default_help –.|  
|[CWinApp::OnHelpIndex](#onhelpindex)|Zpracuje id_help_index – příkaz a poskytuje výchozí téma nápovědy.|  
|[CWinApp::OnHelpUsing](#onhelpusing)|Zpracovává id_help_using – příkaz.|  
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|Zaregistruje typů dokumentů. všechny aplikace s Správce souborů systému Windows.|  
|[CWinApp::SetAppID](#setappid)|Nastaví explicitně Application User Model ID aplikace. Tato metoda by měla být volána, než bude zobrazeno žádné uživatelské rozhraní pro uživatele (nejlepší místo je konstruktor aplikace).|  
|[CWinApp::SetRegistryKey](#setregistrykey)|Způsobí, že nastavení aplikace má být uložen v registru místo. Soubory INI.|  
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Zruší registraci typů dokumentů všechny aplikace s Správce souborů systému Windows.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Určuje, zda uživatel je v režimu kontextové nápovědy (obvykle volat pomocí klávesy SHIFT + F1).|  
|[CWinApp::m_eHelpType](#m_ehelptype)|Určuje typ nápovědy používá aplikace.|  
|[CWinApp::m_hInstance](#m_hinstance)|Určuje aktuální instanci aplikace.|  
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Odkazuje na řetězec ukončené hodnotou null, který určuje příkazový řádek pro aplikaci.|  
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Určuje, jak má být zobrazen původně okna.|  
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Ukazatel na hlavní okno aplikace kontejneru, pokud je na místě aktivní server služby OLE.|  
|[CWinApp::m_pszAppID](#m_pszappid)|ID aplikace uživatele modelu.|  
|[CWinApp::m_pszAppName](#m_pszappname)|Určuje název aplikace.|  
|[CWinApp::m_pszExeName](#m_pszexename)|Název modulu aplikace.|  
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|Cesta k souboru nápovědy aplikace.|  
|[CWinApp::m_pszProfileName](#m_pszprofilename)|Aplikace. Název souboru INI.|  
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Použít k určení klíč úplné registru pro ukládání nastavení profilu aplikace.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Příznaky, které určují, jak se chová správce restartování.|  
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|Délka doby v milisekundách mezi autosaves.|  
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Ukazatel na obslužnou rutinu obnovení dat pro aplikaci.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt aplikace obsahuje členské funkce inicializace aplikace (a každou instanci) a pro spuštění aplikace.  
  
 Všech aplikací, které používá Microsoft Foundation třídy může obsahovat pouze jeden objekt odvozený od `CWinApp`. Tento objekt je vytvořený, když se vytvářejí další globální objekty C++ a je již k dispozici, když Windows zavolá `WinMain` funkce, které poskytl knihovny Microsoft Foundation Class. Deklarovat vaší odvozené `CWinApp` objektu na globální úrovni.  
  
 Pokud odvodíte třídu aplikace z `CWinApp`, přepsat [InitInstance](#initinstance) – členská funkce k vytvoření objektu hlavní okno vaší aplikace.  
  
 Kromě `CWinApp` členské funkce knihovny Microsoft Foundation Class poskytuje následující globální funkce pro přístup k vaší `CWinApp` objektu a další globální informace:  
  
- [AfxGetApp –](application-information-and-management.md#afxgetapp) získá ukazatel `CWinApp` objektu.  
  
- [Afxgetinstancehandle –](application-information-and-management.md#afxgetinstancehandle) získá popisovač pro aktuální instanci aplikace.  
  
- [AfxGetResourceHandle –](application-information-and-management.md#afxgetresourcehandle) získá popisovač pro prostředky aplikace.  
  
- [Afxgetappname –](application-information-and-management.md#afxgetappname) získá ukazatel na řetězec, který obsahuje název aplikace. Případně pokud máte ukazatel na `CWinApp` objektu, použijte `m_pszExeName` získat název aplikace.  
  
 V tématu [CWinApp: The třídy aplikace](../../mfc/cwinapp-the-application-class.md) Další informace o `CWinApp` třída, včetně přehledu následující:  
  
- `CWinApp`– odvozené kód napsaný pomocí Průvodce aplikací.  
  
- `CWinApp`pro roli v pořadí spouštění vaší aplikace.  
  
- `CWinApp`je výchozí implementace členských funkcí.  
  
- `CWinApp`pro klíče k přepisovatelným.  
  
 `m_hPrevInstance` – Datový člen již existuje. Informace o zjišťování předchozí instance `CWinApp`, najdete v článku znalostní báze "Jak k identifikaci předchozí instanci z aplikace" (KB106385) na [ http://support.microsoft.com/default.aspxscid=kb; en-us; 106385](http://support.microsoft.com/default.aspxscid=kb;en-us;106385).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="adddoctemplate"></a>  CWinApp::AddDocTemplate  
 Volání této funkce člen o přidání šablony dokumentu do seznamu šablony dostupné dokumentů, které udržuje aplikace.  
  
```  
void AddDocTemplate(CDocTemplate* pTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *pTemplate*  
 Ukazatel `CDocTemplate` má být přidán.  
  
### <a name="remarks"></a>Poznámky  
 Měli byste přidat všechny dokumentů šablony aplikace před voláním [registershellfiletypes –](#registershellfiletypes).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]  
  
##  <a name="addtorecentfilelist"></a>  CWinApp::AddToRecentFileList  
 Volání této funkce člen přidat *lpszPathName* do seznamu naposledy použitých souborů.  
  
```  
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPathName*  
 Cesta k souboru.  
  
### <a name="remarks"></a>Poznámky  
 Měli byste zavolat [loadstdprofilesettings –](#loadstdprofilesettings) – členská funkce načíst aktuální seznam naposledy použitých souborů před použitím této funkce člen.  
  
 Rozhraní framework volá funkci tento člen, pokud ho otevře soubor nebo provede příkazu Uložit jako uložte soubor pod novým názvem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]  
  
##  <a name="applicationrecoverycallback"></a>  CWinApp::ApplicationRecoveryCallback  
 Voláno rámcem, pokud neočekávaně ukončí aplikaci.  
  
```  
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpvParam*  
 Vyhrazeno pro budoucí použití.  
  
### <a name="return-value"></a>Návratová hodnota  
 0, pokud tato metoda je úspěšná. nenulové hodnoty, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace podporuje správce restartování, volá rozhraní tuto funkci, pokud neočekávaně ukončí aplikaci.  
  
 Výchozí implementaci `ApplicationRecoveryCallback` používá `CDataRecoveryHandler` uložení seznamu nyní otevřené dokumenty do registru. Tato metoda nepodporuje automaticky ukládat všechny soubory.  
  
 Chcete-li přizpůsobit chování, přepište tuto funkci v odvozené [CWinApp – třída](../../mfc/reference/cwinapp-class.md) nebo předejte vlastní metodu obnovení aplikace jako parametr pro [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).  
  
##  <a name="closealldocuments"></a>  CWinApp::CloseAllDocuments  
 Volání této funkce člen zavřete všechny otevřené dokumenty před ukončením.  
  
```  
void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parametry  
 *bEndSession*  
 Určuje, zda se skončí relace Windows. Hodnotu TRUE, pokud relace skončí; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání [HideApplication](#hideapplication) před voláním `CloseAllDocuments`.  
  
##  <a name="createprinterdc"></a>  CWinApp::CreatePrinterDC  
 Volání této funkce člen vytvoření kontextu zařízení tiskárny (DC) z vybrané tiskárny.  
  
```  
BOOL CreatePrinterDC(CDC& dc);
```  
  
### <a name="parameters"></a>Parametry  
 *řadič domény*  
 Odkaz na kontextu zařízení tiskárny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v kontextu zařízení tiskárny vytvořeném úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `CreatePrinterDC` Inicializuje kontext zařízení, kterou předáte odkazem, takže ho můžete použít k vytištění.  
  
 Pokud funkci úspěšné, po dokončení tisku, musíte zničit kontextu zařízení. Můžete je nechat destruktoru objektu [CDC](../../mfc/reference/cdc-class.md) objektu provést, nebo můžete provést explicitně voláním [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc).  
  
##  <a name="cwinapp"></a>  CWinApp::CWinApp  
 Vytvoří `CWinApp` objekt a předává *lpszAppName* ukládaly jako název aplikace.  
  
```  
CWinApp(LPCTSTR lpszAppName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszAppName*  
 Řetězec ukončené hodnotou null, který obsahuje název aplikace, které používá systém Windows. Pokud tento argument není zadaný nebo má hodnotu NULL, `CWinApp` používá řetězec prostředku AFX_IDS_APP_TITLE nebo název spustitelného souboru.  
  
### <a name="remarks"></a>Poznámky  
 Je potřeba vytvořit jeden globální objekt vaší `CWinApp`-odvozené třídy. Může mít jen jeden `CWinApp` objektu ve vaší aplikaci. Konstruktor ukládá ukazatel `CWinApp` objektu tak, aby `WinMain` můžete volat objektu členské funkce k inicializaci a spuštění aplikace.  
  
##  <a name="delregtree"></a>  CWinApp::DelRegTree  
 Odstraní klíč konkrétní registru a všechny jeho podklíče.  
  
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
 *hParentKey*  
 Zpracování ke klíči registru.  
  
 *strKeyName*  
 Název klíče registru pro odstranění.  
  
 *Druh*  
 Ukazatel na CAtlTransactionManager objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se odstranit zadaný klíč a jeho podklíčích.  
  
##  <a name="domessagebox"></a>  CWinApp::DoMessageBox  
 Tento člen funkce implementovat okno se zprávou pro globální funkce volá framework [AfxMessageBox –](cstring-formatting-and-message-box-display.md#afxmessagebox).  
  
```  
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,  
    UINT nType,  
    UINT nIDPrompt);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPrompt*  
 Adresa text do pole zpráva.  
  
 *Noznámení*  
 Do pole zpráva [styl](../../mfc/reference/styles-used-by-mfc.md#message-box-styles).  
  
 *nIDPrompt*  
 Index pro řetězec kontextové nápovědy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí stejné hodnoty jako `AfxMessageBox`.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte tuto funkci člen otevřete okno se zprávou; použít `AfxMessageBox` místo.  
  
 Člen funkci k přizpůsobení vaší celou aplikaci zpracování přepsat `AfxMessageBox` volání.  
  
##  <a name="dowaitcursor"></a>  CWinApp::DoWaitCursor  
 Tato funkce člen je voláno rámcem implementovat [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor), a [ CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
```  
virtual void DoWaitCursor(int nCode);
```  
  
### <a name="parameters"></a>Parametry  
 *nCode*  
 Pokud tento parametr je 1, zobrazí se kurzoru čekání. Pokud je 0, počkejte kurzor je obnoven bez zvyšování počet odkazů. Pokud-1, ukončí kurzor čekání.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota implementuje přesýpacích hodin kurzoru. `DoWaitCursor` zaznamenává počet odkaz. Když kladné, zobrazí se přesýpacích hodin kurzor.  
  
 Zatímco by za normálních okolností volání `DoWaitCursor` přímo, může člen funkci změnit kurzor čekání nebo provádět další zpracovávání, když se zobrazí ukazatel čekání přepsat.  
  
 Pro snadnější a zefektivnění způsob implementace čekání kurzoru, použijte `CWaitCursor`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]  
  
##  <a name="enabled2dsupport"></a>  CWinApp::EnableD2DSupport  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Umožňuje podporu D2D aplikace. Tuto metodu volejte před inicializací hlavní okno.  
  
```  
BOOL EnableD2DSupport(
D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parametry  
 *d2dFactoryType*  
 Model vláken D2D tovární nastavení a prostředky vytvoří.  
  
 *writeFactoryType*  
 Hodnotu, která určuje, zda se objekt factory zápisu sdílené nebo izolované  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud D2D podpora bylo povoleno, FALSE - jinak  
  
##  <a name="enablehtmlhelp"></a>  CWinApp::EnableHtmlHelp  
 Volání této funkce člena z v konstruktoru vaší `CWinApp`-odvozené třídy používat HTMLHelp nápovědu k vaší aplikace.  
  
```  
void EnableHtmlHelp();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enableshellopen"></a>  CWinApp::EnableShellOpen  
 Volání této funkce, které jsou obvykle z vaší `InitInstance` přepsat, aby mohli uživatelé vaší aplikace k otevření datových souborů, když klikněte dvakrát na soubory z v rámci Správce souborů systému Windows.  
  
```  
void EnableShellOpen();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání `RegisterShellFileTypes` členské funkce ve spojení pomocí této funkce nebo zadejte. Soubor REG s vaší aplikací pro ruční registraci typů dokumentů.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]  
  
##  <a name="enabletaskbarinteraction"></a>  CWinApp::EnableTaskbarInteraction  
 Umožňuje interakci panelu.  
  
```  
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnable*  
 Určuje, zda by měla být povolená (TRUE) interakci s hlavním systému Windows 7, nebo zakázána (FALSE).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud interakce panelu můžete povolit nebo zakázat.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda musí být volána před vytvořením hlavní okno, v opačném případě se vyhodnotí a vrátí hodnotu FALSE.  
  
##  <a name="exitinstance"></a>  CWinApp::ExitInstance  
 Voláno rámcem uvnitř `Run` – členská funkce ukončíte tuto instanci aplikace.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukončovací kód aplikace; 0 znamená žádné chyby a hodnoty, které jsou větší než 0 indikují chybu. Tato hodnota se používá jako návratová hodnota z `WinMain`.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte tuto funkci člena z libovolného místa ale uvnitř `Run` – členská funkce.  
  
 Výchozí implementace této funkce zapíše framework možnosti do aplikace. Soubor INI. Funkci odstranit při ukončí aplikaci přepište.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]  
  
##  <a name="getapplicationrecoveryparameter"></a>  CWinApp::GetApplicationRecoveryParameter  
 Načte vstupního parametru pro metodu obnovení aplikace.  
  
```  
virtual LPVOID GetApplicationRecoveryParameter();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí vstupní parametr pro metodu obnovení aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování této funkce vrátí hodnotu NULL.  
  
 Další informace najdete v tématu [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).  
  
##  <a name="getapplicationrecoverypinginterval"></a>  CWinApp::GetApplicationRecoveryPingInterval  
 Vrátí dobu, kterou správce restartování čeká funkce zpětného volání obnovení vrátit.  
  
```  
virtual DWORD GetApplicationRecoveryPingInterval();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka doby v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Když aplikaci, která je zaregistrovaná u ukončí správce restartování neočekávaně, aplikace se pokusí uložit otevřené dokumenty a volá funkci zpětného volání pro obnovení. Výchozí funkce zpětného volání pro obnovení je [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).  
  
 Doba, kterou rozhraní framework čeká funkce zpětného volání obnovení vrátit je interval příkazu ping. Pomocí přepsání můžete upravit ping interval `CWinApp::GetApplicationRecoveryPingInterval` nebo tím, že poskytuje vlastní hodnota `RegisterWithRestartManager`.  
  
##  <a name="getapplicationrestartflags"></a>  CWinApp::GetApplicationRestartFlags  
 Vrátí příznaků pro správce restartování.  
  
```  
virtual DWORD GetApplicationRestartFlags();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Příznaky pro správce restartování. Výchozí implementace vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Pro správce restartování příznaky nemají vliv s výchozí implementace. Jsou k dispozici pro budoucí použití.  
  
 Nastavte příznaky při registraci aplikace s správce restartování pomocí [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).  
  
 Možné hodnoty pro příznaky správce restartování jsou následující:  
  
- RESTART_NO_CRASH  
  
- RESTART_NO_HANG  
  
- RESTART_NO_PATCH  
  
- RESTART_NO_REBOOT  
  
##  <a name="getappregistrykey"></a>  CWinApp::GetAppRegistryKey  
 Vrátí klíč pro HKEY_CURRENT_USER\\\RegistryKey\ProfileName "Software".  
  
```  
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *Druh*  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Klíč aplikace, pokud funkci úspěšně. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdatarecoveryhandler"></a>  CWinApp::GetDataRecoveryHandler  
 Získá obslužnou rutinu obnovení dat pro tuto instanci aplikace.  
  
```  
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Data obnovení obslužná rutina pro tuto instanci aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Každou aplikaci, která používá správce restartování musí mít jednu instanci [CDataRecoveryHandler třída](../../mfc/reference/cdatarecoveryhandler-class.md). Tato třída je odpovědná za monitorování otevřené dokumenty a automatické ukládání souborů. Chování `CDataRecoveryHandler` závisí na konfiguraci správce restartování. Další informace najdete v tématu [CDataRecoveryHandler třída](../../mfc/reference/cdatarecoveryhandler-class.md).  
  
 Tato metoda vrátí hodnotu NULL v operačních systémech starších než Windows Vista. Správce restartování není podporováno v operačních systémech starších než Windows Vista.  
  
 Pokud aplikace nemá aktuálně obslužnou rutinu obnovení dat, tato metoda vytvoří jednu a vrátí ukazatel na ni.  
  
##  <a name="getfirstdoctemplateposition"></a>  CWinApp::GetFirstDocTemplatePosition  
 Získá pozici prvního šablony dokumentu v aplikaci.  
  
```  
POSITION GetFirstDocTemplatePosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota pozice, který lze použít pro iteraci nebo načtení objektu ukazatel; Hodnota NULL, pokud je seznam prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Použití vrácena hodnota pozice v volání [GetNextDocTemplate](#getnextdoctemplate) získat první [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objektu.  
  
##  <a name="gethelpmode"></a>  CWinApp::GetHelpMode  
 Načte typ nápovědy používá aplikace.  
  
```  
AFX_HELP_TYPE GetHelpMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ nápovědy používá aplikace. V tématu [CWinApp::m_eHelpType](#m_ehelptype) Další informace.  
  
##  <a name="getnextdoctemplate"></a>  CWinApp::GetNextDocTemplate  
 Získá šablonu dokumentu identifikovaný *pos*, pak nastaví *pos* na POZICI hodnotu.  
  
```  
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Odkaz na hodnotu pozice vrácené z předchozího volání `GetNextDocTemplate` nebo [GetFirstDocTemplatePosition](#getfirstdoctemplateposition). Hodnota se aktualizuje na další pozici toto volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetNextDocTemplate` ve smyčce dopředného iterace Pokud vytvořit počáteční pozice pomocí volání `GetFirstDocTemplatePosition`.  
  
 Je nutné zajistit, že vaše pozice hodnota je platná. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud šablona načtená dokumentu je poslední, k dispozici, pak nová hodnota *pos* je nastaven na hodnotu NULL.  
  
##  <a name="getprinterdevicedefaults"></a>  CWinApp::GetPrinterDeviceDefaults  
 Volání této funkce člen Příprava kontextu zařízení tiskárny pro tisk.  
  
```  
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```  
  
### <a name="parameters"></a>Parametry  
 *pPrintDlg*  
 Ukazatel [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Načte aktuální výchozí nastavení tiskárny ze systému Windows. Soubor INI jako nezbytné, nebo používá poslední konfigurace tiskárny nastavený uživatelem v nastavení tisku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]  
  
##  <a name="getprofilebinary"></a>  CWinApp::GetProfileBinary  
 Volání této funkce člen načíst binární data z položky v rámci zadaný oddíl registru aplikace nebo. Soubor INI.  
  
```  
BOOL GetProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.  
  
 *lpszEntry*  
 Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž hodnota má být načtena.  
  
 *ppData*  
 Odkazuje na ukazatel, která bude přijímat adresu data.  
  
 *pBytes*  
 Odkazuje na UINT, která bude přijímat velikost dat (v bajtech).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen není rozlišuje velká a malá písmena, takže řetězců v *lpszSection* a *lpszEntry* parametry se můžou lišit v případě.  
  
> [!NOTE]
> `GetProfileBinary` přidělení vyrovnávací paměti a vrátí jeho adresy v \* *ppData*. Volající zodpovídá za uvolnění vyrovnávací paměti pomocí **odstranit []**.  
  
> [!IMPORTANT]
>  Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]  
  
 Další příklad najdete v tématu [CWinApp::WriteProfileBinary](#writeprofilebinary).  
  
##  <a name="getprofileint"></a>  CWinApp::GetProfileInt  
 Voláním této členské funkce lze získat hodnotu celého čísla z položky v určitém oddíle registru aplikace nebo souboru .INI.  
  
```  
UINT GetProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.  
  
 *lpszEntry*  
 Odkazuje na řetězec zakončený hodnotou null, který obsahuje položku, jejíž hodnota má být načtena.  
  
 *nDefault*  
 Určuje výchozí vrácenou hodnotu, pokud rozhraní položku nemůže najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselná hodnota řetězce, který následuje zadanou položku, pokud je funkce úspěšná. Vrácená hodnota je hodnota *nDefault* parametr, pokud funkci nelze nalézt položku. Vrácená hodnota je 0, pokud hodnota, která odpovídá zadané položce, není celé číslo.  
  
 Tato členská funkce podporuje šestnáctkovou notaci hodnot v souboru .INI. Pokud načítáte znaménkem, by měl přetypovat hodnotu do **int**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen není rozlišuje velká a malá písmena, takže řetězců v *lpszSection* a *lpszEntry* parametry se můžou lišit v případě.  
  
> [!IMPORTANT]
>  Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]  
  
 Další příklad najdete v tématu [CWinApp::WriteProfileInt](#writeprofileint).  
  
##  <a name="getprofilestring"></a>  CWinApp::GetProfileString  
 Volání této funkce člen načíst řetězce spojeného s položky v rámci zadaný oddíl v registru aplikace nebo. Soubor INI.  
  
```  
CString GetProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku.  
  
 *lpszEntry*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje položku, na nichž je řetězec mají být načteny. Tato hodnota nesmí být NULL.  
  
 *lpszDefault*  
 Odkazuje na výchozí hodnotu řetězce pro danou položku, pokud položka nebyla nalezena v inicializační soubor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je řetězec z aplikace. Soubor INI nebo *lpszDefault* Pokud řetězec nelze nalézt. Maximální délka řetězce nepodporuje rozhraní je _max_path –. Pokud *lpszDefault* má hodnotu NULL, vrácená hodnota je prázdný řetězec.  
  
### <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Data vrácená touto funkcí nemusí být nutně ukončena hodnotou null a volající musí provést ověření. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 Další příklad, podívejte se na příklad pro [CWinApp::GetProfileInt](#getprofileint).  
  
##  <a name="getsectionkey"></a>  CWinApp::GetSectionKey  
 Vrátí klíč pro HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection "Software".  
  
```  
HKEY GetSectionKey(
LPCTSTR lpszSection,  
CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Název klíče, který se získat.  
  
 *Druh*  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Oddíl klíč, pokud funkci úspěšně. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hideapplication"></a>  CWinApp::HideApplication  
 Volání této funkce člen ke skrytí aplikace před jeho zavřením otevřené dokumenty.  
  
```  
void HideApplication();
```  
  
##  <a name="htmlhelp"></a>  CWinApp::HtmlHelp  
 Volání této funkce člen má být vyvolán HTMLHelp aplikace.  
  
```  
virtual void HtmlHelp(
    DWORD_PTR dwData,  
    UINT nCmd = 0x000F);
```  
  
### <a name="parameters"></a>Parametry  
 *dwData*  
 Určuje další data. Hodnota použitá závisí na hodnotu *nCmd* parametr.  
  
 *nCmd*  
 Určuje typ nápovědy požadovaný. Seznam možných hodnot a jejich vliv *dwData* parametr, najdete v článku *uCommand* parametr popsané v o the HTMLHelp funkce rozhraní API ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce má být vyvolán HTMLHelp aplikace také volá framework.  
  
 Rozhraní se automaticky zavře HTMLHelp aplikace při ukončení aplikace.  
  
##  <a name="initinstance"></a>  CWinApp::InitInstance  
 Windows umožňuje několik kopií stejný program ke spuštění ve stejnou dobu.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného; inicializace jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Inicializace aplikace je koncepčně rozdělené na dvě části: Inicializace jednorázové aplikace, které se provádí první čas program se spustí a inicializaci instance, který spouští každou čas kopii program se spustí, včetně poprvé. Implementace rozhraní framework `WinMain` volání této funkce.  
  
 Přepsání `InitInstance` k chybě při inicializaci každou novou instanci třídy vaši aplikaci běžící v systému Windows. Obvykle přepsat `InitInstance` k sestavení objektu sady hlavní okno a nastavení `CWinThread::m_pMainWnd` – datový člen tak, aby odkazoval na toto okno. Další informace o přepsání této – členská funkce najdete v tématu [CWinApp: třídy aplikace](../../mfc/cwinapp-the-application-class.md).  
  
> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Když zavoláte [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ve vaší `InitInstance` přepsat, zadejte COINIT_APARTMENTTHREADED (nikoli COINIT_MULTITHREADED). Další informace najdete v tématu PRB: MFC aplikace přestane reagovat při inicializaci aplikace jako a více vláken typu Apartment (828643) v [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]  
  
##  <a name="istaskbarinteractionenabled"></a>  CWinApp::IsTaskbarInteractionEnabled  
 Určuje, zda je povoleno interakce na hlavním panelu Windows 7.  
  
```  
virtual BOOL IsTaskbarInteractionEnabled();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud `EnableTaskbarInteraction` byla volána a je operační systém Windows 7 nebo vyšší.  
  
### <a name="remarks"></a>Poznámky  
 Interakce panelu znamená, že aplikace MDI zobrazuje obsah MDI, děti v samostatných záložkách miniatur, které se zobrazují, když ukazatel myši nad tlačítka panelu aplikace.  
  
##  <a name="loadcursor"></a>  CWinApp::LoadCursor  
 Načte prostředek kurzor s názvem podle *lpszResourceName* nebo specifikace *nIDResource* z aktuální spustitelný soubor.  
  
```  
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpszResourceName*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje název prostředku kurzoru. Můžete použít `CString` pro tento argument.  
  
 *nIDResource*  
 ID prostředku kurzoru. Seznam prostředků najdete v tématu [LoadCursor](http://msdn.microsoft.com/library/windows/desktop/ms648391) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro kurzor v případě úspěšného; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 `LoadCursor` načte kurzor do paměti pouze v případě, že nebyla dříve načíst; jinak načte popisovač existující prostředek.  
  
 Použití [LoadStandardCursor](#loadstandardcursor) nebo [LoadOEMCursor](#loadoemcursor) – členská funkce pro přístup k předdefinované kurzory systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]  
  
##  <a name="loadicon"></a>  CWinApp::LoadIcon  
 Načte ikonu prostředek s názvem podle *lpszResourceName* nebo specifikace *nIDResource* ze spustitelného souboru.  
  
```  
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpszResourceName*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje název prostředku ikonu. Můžete použít také `CString` pro tento argument.  
  
 *nIDResource*  
 Číslo ID prostředku ikonu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu v případě úspěšného; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 `LoadIcon` načte ikonu pouze v případě, že nebyla dříve načíst; jinak načte popisovač existující prostředek.  
  
 Můžete použít [LoadStandardIcon](#loadstandardicon) nebo [LoadOEMIcon](#loadoemicon) – členská funkce pro přístup k předdefinované ikony systému Windows.  
  
> [!NOTE]
>  Tato funkce člen volá funkce rozhraní API Win32 [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), který načtěte jenom na ikonu, jehož velikost odpovídá hodnoty metriky systému SM_CXICON a SM_CYICON.  
  
##  <a name="loadoemcursor"></a>  CWinApp::LoadOEMCursor  
 Načítání Windows předdefinované kurzoru prostředku zadaného parametrem *nIDCursor*.  
  
```  
HCURSOR LoadOEMCursor(UINT nIDCursor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIDCursor*  
 **OCR_** manifest konstantní identifikátor, který určuje předdefinované Windows kurzoru. Musíte mít `#define OEMRESOURCE` před `#include \<afxwin.h>` k získání přístupu k **OCR_** konstanty v systému WINDOWS. H.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro kurzor v případě úspěšného; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Použití `LoadOEMCursor` nebo [LoadStandardCursor](#loadstandardcursor) – členská funkce pro přístup k předdefinované kurzory systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]  
  
 [!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]  
  
##  <a name="loadoemicon"></a>  CWinApp::LoadOEMIcon  
 Načítání Windows předdefinované ikonu prostředku zadaného parametrem *nIDIcon*.  
  
```  
HICON LoadOEMIcon(UINT nIDIcon) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIDIcon*  
 **OIC_** manifest konstantní identifikátor, který určuje předdefinované ikonu systému Windows. Musíte mít `#define OEMRESOURCE` před `#include \<afxwin.h>` k přístupu **OIC_** konstanty v systému WINDOWS. H.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu v případě úspěšného; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Použití `LoadOEMIcon` nebo [LoadStandardIcon](#loadstandardicon) – členská funkce pro přístup k předdefinované ikony systému Windows.  
  
##  <a name="loadstandardcursor"></a>  CWinApp::LoadStandardCursor  
 Načítání Windows předdefinované prostředků kurzoru, *lpszCursorName* určuje.  
  
```  
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpszCursorName*  
 **IDC_** manifest konstantní identifikátor, který určuje předdefinované Windows kurzoru. Tyto identifikátory jsou definovány v systému WINDOWS. H. V následujícím seznamu jsou možné předem definovaných hodnot a význam pro *lpszCursorName*:  
  
- Standardní IDC_ARROW šipku kurzoru  
  
- Standardní IDC_IBEAM kurzoru vkládání textu  
  
- Přesýpací hodiny IDC_WAIT kurzor používá, když Windows provede časově náročný úkol  
  
- IDC_CROSS kříž kurzor pro výběr  
  
- Šipka IDC_UPARROW, který odkazuje nahoru  
  
- IDC_SIZE zastaralé a nepodporované; použít IDC_SIZEALL  
  
- IDC_SIZEALL A čtyřmi odkazoval šipku. Kurzor sloužící k změnit velikost okna.  
  
- IDC_ICON zastaralé a nepodporované. Použijte IDC_ARROW.  
  
- Dvojitá šipka IDC_SIZENWSE s končí v levé horní a dolní pravá  
  
- Dvojitá šipka IDC_SIZENESW s končí v levé horní vpravo a nižší  
  
- IDC_SIZEWE vodorovné dvojitá šipka  
  
- IDC_SIZENS svislé dvojitá šipka  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro kurzor v případě úspěšného; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Použití `LoadStandardCursor` nebo [LoadOEMCursor](#loadoemcursor) – členská funkce pro přístup k předdefinované kurzory systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]  
  
##  <a name="loadstandardicon"></a>  CWinApp::LoadStandardIcon  
 Ikona prostředků předdefinované zatížení systému Windows, *lpszIconName* určuje.  
  
```  
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpszIconName*  
 Manifestu konstantní identifikátor, který určuje předdefinované ikonu systému Windows. Tyto identifikátory jsou definovány v systému WINDOWS. H. Seznam možných předem definovaných hodnot a jejich popisy najdete v tématu *lpIconName* parametr v [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu v případě úspěšného; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Použití `LoadStandardIcon` nebo [LoadOEMIcon](#loadoemicon) – členská funkce pro přístup k předdefinované ikony systému Windows.  
  
##  <a name="loadstdprofilesettings"></a>  CWinApp::LoadStdProfileSettings  
 Volání této funkce člen uvnitř [InitInstance](#initinstance) – členská funkce povolit a načíst seznam naposledy použitých souborů (naposledy použitých) a poslední náhled stavu.  
  
```  
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```  
  
### <a name="parameters"></a>Parametry  
 *nMaxMRU*  
 Počet naposledy použitých souborů ke sledování.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *nMaxMRU* je 0, žádný seznam naposledy použitých se zachová.  
  
##  <a name="m_bhelpmode"></a>  CWinApp::m_bHelpMode  
 Hodnota TRUE, pokud je aplikace v režimu kontextové nápovědy (obvykle volat pomocí klávesy SHIFT + F1); jinak hodnota FALSE.  
  
```  
BOOL m_bHelpMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 V režimu kontextové nápovědy kurzoru změní na otazník a uživatele můžete přesunout o na obrazovce. Zkontrolujte tento příznak, pokud chcete implementovat zvláštní zpracování v režimu nápovědy. `m_bHelpMode` je veřejné proměnné typu BOOL.  
  
##  <a name="m_dwrestartmanagersupportflags"></a>  CWinApp::m_dwRestartManagerSupportFlags  
 Příznaky, které určují, jak se chová správce restartování.  
  
```  
DWORD m_dwRestartManagerSupportFlags;  
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li povolit správce restartování, nastavte `m_dwRestartManagerSupportFlags` chování, které chcete. V následující tabulce jsou uvedeny příznaky, které jsou k dispozici.  
  
|||  
|-|-|  
|Příznak|Popis|  
|AFX_RESTART_MANAGER_SUPPORT_RESTART|Aplikace je registrován pomocí [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager). Správce restartování je zodpovědná za restartování aplikace, pokud neočekávaně ukončí se.|  
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|Aplikace není zaregistrována správce restartování a správce restartování volání funkce zpětného volání pro zotavení po restartování aplikace. Výchozí funkce zpětného volání pro obnovení je [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|  
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Je povoleno automatické ukládání a autosaves správce restartování žádné otevřít dokumenty, když se aplikace restartuje.|  
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Je povoleno automatické ukládání a autosaves správce restartování žádné otevřít dokumenty v pravidelných intervalech. Interval je definována [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval).|  
|-AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|Správce restartování otevře dříve otevřené dokumenty po restartování aplikace z neočekávané ukončení. [CDataRecoveryHandler třída](../../mfc/reference/cdatarecoveryhandler-class.md) zpracovává ukládání seznam otevřené dokumenty a jejich obnovení.|  
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|Správce restartování vyzývá uživatele k obnovení souborů automaticky uloženo po restartování aplikace. `CDataRecoveryHandler` Třída dotazuje uživatele.|  
|-AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|Sjednocení AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER a AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|  
|-AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|Sjednocení AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|  
|-AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|Sjednocení AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|  
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Union ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES a AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|  
  
##  <a name="m_ehelptype"></a>  CWinApp::m_eHelpType  
 Typ této – datový člen je výčtového typu AFX_HELP_TYPE, která je definována v rámci `CWinApp` třídy.  
  
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
  
-   Chcete-li nastavit aplikace Nápověda HTML – Nápověda, volejte [SetHelpMode](#sethelpmode) a zadejte `afxHTMLHelp`.  
  
-   Chcete-li nastavit aplikace Nápověda WinHelp, volejte `SetHelpMode` a zadejte `afxWinHelp`.  
  
##  <a name="m_hinstance"></a>  CWinApp::m_hInstance  
 Odpovídá *hInstance* parametr předaná Windows `WinMain`.  
  
```  
HINSTANCE m_hInstance;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hInstance` – Datový člen je popisovač pro aktuální instanci aplikace běžící v systému Windows. To je vrácené funkcí globální [afxgetinstancehandle –](application-information-and-management.md#afxgetinstancehandle). `m_hInstance` je veřejné proměnné typu HINSTANCE.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]  
  
##  <a name="m_lpcmdline"></a>  CWinApp::m_lpCmdLine  
 Odpovídá *lpCmdLine* parametr předaná Windows `WinMain`.  
  
```  
LPTSTR m_lpCmdLine;  
```  
  
### <a name="remarks"></a>Poznámky  
 Odkazuje na řetězec ukončené hodnotou null, který určuje příkazový řádek pro aplikaci. Použití `m_lpCmdLine` pro přístup k žádných argumentů příkazového řádku zadané uživatelem při spuštění aplikace. `m_lpCmdLine` je veřejné proměnné typu LPTSTR.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="m_nautosaveinterval"></a>  CWinApp::m_nAutosaveInterval  
 Délka doby v milisekundách mezi autosaves.  
  
```  
int m_nAutosaveInterval;  
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete nakonfigurovat správce restartování pro automatické ukládání otevřené dokumenty ve stanovených intervalech. Pokud aplikace nemá automaticky ukládat soubory, tento parametr nemá žádný vliv.  
  
##  <a name="m_ncmdshow"></a>  CWinApp::m_nCmdShow  
 Odpovídá *nCmdShow* parametr předaná Windows `WinMain`.  
  
```  
int m_nCmdShow;  
```  
  
### <a name="remarks"></a>Poznámky  
 By měla předávat `m_nCmdShow` jako argument při volání [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) pro hlavní okno vaší aplikace. `m_nCmdShow` je veřejné proměnné typu **int**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]  
  
##  <a name="m_pactivewnd"></a>  CWinApp::m_pActiveWnd  
 Tento člen data použijte k ukládání ukazatel na hlavní okno aplikace OLE kontejneru, který má váš server aplikace na místě OLE aktivován.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tento člen dat mají hodnotu NULL, není aktivní místní aplikace.  
  
 Rozhraní framework nastaví tento členské proměnné po okně s rámečkem na místě aktivován aplikace kontejneru OLE.  
  
##  <a name="m_pdatarecoveryhandler"></a>  CWinApp::m_pDataRecoveryHandler  
 Ukazatel na obslužnou rutinu obnovení dat pro aplikaci.  
  
```  
CDataRecoveryHandler* m_pDataRecoveryHandler;  
```  
  
### <a name="remarks"></a>Poznámky  
 Obslužná rutina obnovení dat aplikace monitoruje otevřené dokumenty a autosaves je. Rozhraní používá obslužná rutina obnovení dat automaticky uloženo soubory obnovit, když se aplikace restartuje po neočekávaně ukončí. Další informace najdete v tématu [CDataRecoveryHandler třída](../../mfc/reference/cdatarecoveryhandler-class.md).  
  
##  <a name="m_pszappname"></a>  CWinApp::m_pszAppName  
 Určuje název aplikace.  
  
```  
LPCTSTR m_pszAppName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Název aplikace mohou pocházet z parametr předaný [CWinApp](#cwinapp) konstruktoru, nebo pokud není zadaný, na řetězec prostředku s ID AFX_IDS_APP_TITLE. Pokud název aplikace nebyl nalezen v prostředku, pochází z tohoto programu. Název souboru EXE.  
  
 Globální funkce [afxgetappname –](application-information-and-management.md#afxgetappname). `m_pszAppName` je veřejné proměnné typu **const char\***.  
  
> [!NOTE]
>  Chcete-li přiřadit hodnotu na `m_pszAppName`, musí být dynamicky přiřazovány v haldě. `CWinApp` Volání destruktoru **volné**() s Tento ukazatel. Mnoho chcete použít `_tcsdup`funkce běhové knihovny () uděláte přidělení. Navíc uvolnění paměti spojené s aktuální ukazatele před přiřazením novou hodnotu. Příklad:  
  
 [!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]  
  
##  <a name="m_pszexename"></a>  CWinApp::m_pszExeName  
 Obsahuje název spustitelného souboru aplikace bez přípony.  
  
```  
LPCTSTR m_pszExeName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [m_pszAppName](#m_pszappname), tento název nesmí obsahovat prázdné znaky. `m_pszExeName` je veřejné proměnné typu **const char\***.  
  
> [!NOTE]
>  Chcete-li přiřadit hodnotu na `m_pszExeName`, musí být dynamicky přiřazovány v haldě. `CWinApp` Volání destruktoru **volné**() s Tento ukazatel. Mnoho chcete použít `_tcsdup`funkce běhové knihovny () uděláte přidělení. Navíc uvolnění paměti spojené s aktuální ukazatele před přiřazením novou hodnotu. Příklad:  
  
 [!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]  
  
##  <a name="m_pszhelpfilepath"></a>  CWinApp::m_pszHelpFilePath  
 Obsahuje cestu k souboru nápovědy aplikace.  
  
```  
LPCTSTR m_pszHelpFilePath;  
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, inicializuje rozhraní `m_pszHelpFilePath` na název aplikace s ". HLP"připojí. Chcete-li změnit název souboru nápovědy, nastavte `m_pszHelpFilePath` tak, aby odkazoval na řetězec, který obsahuje úplný název souboru požadovaného nápovědy. Vhodné místo k tomu je do aplikace [InitInstance](#initinstance) funkce. `m_pszHelpFilePath` je veřejné proměnné typu **const char\***.  
  
> [!NOTE]
>  Chcete-li přiřadit hodnotu na `m_pszHelpFilePath`, musí být dynamicky přiřazovány v haldě. `CWinApp` Volání destruktoru **volné**() s Tento ukazatel. Mnoho chcete použít `_tcsdup`funkce běhové knihovny () uděláte přidělení. Navíc uvolnění paměti spojené s aktuální ukazatele před přiřazením novou hodnotu. Příklad:  
  
 [!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]  
  
##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName  
 Obsahuje název aplikace. Soubor INI.  
  
```  
LPCTSTR m_pszProfileName;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_pszProfileName` je veřejné proměnné typu **const char\***.  
  
> [!NOTE]
>  Chcete-li přiřadit hodnotu na `m_pszProfileName`, musí být dynamicky přiřazovány v haldě. `CWinApp` Volání destruktoru **volné**() s Tento ukazatel. Mnoho chcete použít `_tcsdup`funkce běhové knihovny () uděláte přidělení. Navíc uvolnění paměti spojené s aktuální ukazatele před přiřazením novou hodnotu. Příklad:  
  
 [!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]  
  
##  <a name="m_pszregistrykey"></a>  CWinApp::m_pszRegistryKey  
 Použít k určení, kde v registru nebo soubor INI, jsou uloženy nastavení profilu aplikace.  
  
```  
LPCTSTR m_pszRegistryKey;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen data za normálních okolností považuje jen pro čtení.  
  
-   Hodnota je uložena do klíče registru. Název pro nastavení profilu aplikace je připojen k následující klíč registru: HKEY_CURRENT_USER/Software/LocalAppWizard-generovaný /.  
  
 Chcete-li přiřadit hodnotu na `m_pszRegistryKey`, musí být dynamicky přiřazovány v haldě. `CWinApp` Volání destruktoru **volné**() s Tento ukazatel. Mnoho chcete použít `_tcsdup`funkce běhové knihovny () uděláte přidělení. Navíc uvolnění paměti spojené s aktuální ukazatele před přiřazením novou hodnotu. Příklad:  
  
 [!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]  
  
##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID  
 ID aplikace uživatele modelu.  
  
```  
LPCTSTR m_pszAppID;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncontexthelp"></a>  CWinApp::OnContextHelp  
 Zpracovává SHIFT + F1 – Nápověda v aplikaci.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` příkaz, který má vaše `CWinApp` třídy mapy zpráv a taky k přidání položky tabulky akcelerátorů, obvykle SHIFT + F1, chcete-li povolit tuto funkci člen.  
  
 `OnContextHelp` vloží aplikace do režimu nápovědy. Změní na šipka a otazník a uživatele můžete přesunutí ukazatele myši a stiskněte klávesu levé tlačítko myši a vyberte dialogové okno, oken, nabídek nebo příkazového tlačítka. Tato funkce člen načte kontextu nápovědy objekt pod kurzor a volání funkce systému Windows WinHelp s kontextem této nápovědy.  
  
##  <a name="onddecommand"></a>  CWinApp::OnDDECommand  
 Voláno rámcem přijetí DDE v hlavním okně rámce spustit zprávu.  
  
```  
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszCommand*  
 Odkazuje na řetězec příkaz DDE přijatých aplikací.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se zpracovává příkaz; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace ověří, zda příkaz je požadavku na otevření dokumentu a pokud ano, otevře zadaný dokument. Správce souborů systému Windows obvykle odešle takové DDE příkazového řetězce při poklepání datový soubor. Přepsat tuto funkci pro zpracování jiných DDE spustit příkazy, jako je například příkaz k vytištění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]  
  
##  <a name="onfilenew"></a>  CWinApp::OnFileNew  
 Implementuje id_file_new – příkaz.  
  
```  
afx_msg void OnFileNew();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_FILE_NEW, OnFileNew )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud je povoleno, tato funkce zpracovává provedení příkazu nový soubor.  
  
 V tématu [Technická poznámka 22](../../mfc/tn022-standard-commands-implementation.md) informace o výchozí chování a pokyny o tom, jak funkci člena přepsat.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="onfileopen"></a>  CWinApp::OnFileOpen  
 Implementuje id_file_open – příkaz.  
  
```  
afx_msg void OnFileOpen();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud je povoleno, tato funkce zpracovává provádění příkazu Otevřít soubor.  
  
 Informace o výchozí chování a pokyny o tom, jak funkci člena přepsat, najdete v části [Technická poznámka 22](../../mfc/tn022-standard-commands-implementation.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="onfileprintsetup"></a>  CWinApp::OnFilePrintSetup  
 Implementuje id_file_print_setup – příkaz.  
  
```  
afx_msg void OnFilePrintSetup();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud je povoleno, tato funkce zpracovává provedení příkazu tisku souboru.  
  
 Informace o výchozí chování a pokyny o tom, jak funkci člena přepsat, najdete v části [Technická poznámka 22](../../mfc/tn022-standard-commands-implementation.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="onhelp"></a>  CWinApp::OnHelp  
 Zpracovává nápovědy F1 v rámci aplikace (pomocí aktuálního kontextu).  
  
```  
afx_msg void OnHelp();
```  
  
### <a name="remarks"></a>Poznámky  
 Obvykle se také přidat položku klávesa akcelerátoru pro klávesy F1. Povolení klávesy F1 je pouze konvence, která nevyžaduje.  
  
 Je nutné přidat `ON_COMMAND( ID_HELP, OnHelp )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud je povoleno, voláno rámcem po stisknutí klávesy F1.  
  
 Výchozí implementace této funkce obslužné rutiny zpráv určuje nápovědy kontext, který odpovídá aktuálního okna, dialogové okno nebo položku nabídky a pak zavolá WINHELP. SOUBOR EXE. Pokud není aktuálně k dispozici žádný kontext, funkce používá výchozí kontext.  
  
 Člen funkci nastavit kontext nápovědy na jinou hodnotu než okna, dialogové okno, položku nabídky nebo tlačítka panelu nástrojů, který je aktuálně aktivní přepište. Volání `WinHelp` s požadovanou pomůže ID kontextu.  
  
##  <a name="onhelpfinder"></a>  CWinApp::OnHelpFinder  
 Zpracovává příkazy ID_HELP_FINDER a id_default_help –.  
  
```  
afx_msg void OnHelpFinder();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud je povoleno, rozhraní volá funkci tento popisovač zpráv, pokud uživatel aplikace vybere příkaz pomůže vyhledávací k vyvolání `WinHelp` se standardem **HELP_FINDER** tématu.  
  
##  <a name="onhelpindex"></a>  CWinApp::OnHelpIndex  
 Zpracuje id_help_index – příkaz a poskytuje výchozí téma nápovědy.  
  
```  
afx_msg void OnHelpIndex();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud je povoleno, rozhraní volá funkci tento popisovač zpráv, pokud uživatel aplikace vybere příkaz nápovědě k vyvolání `WinHelp` se standardem **HELP_INDEX** tématu.  
  
##  <a name="onhelpusing"></a>  CWinApp::OnHelpUsing  
 Zpracovává id_help_using – příkaz.  
  
```  
afx_msg void OnHelpUsing();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přidat `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` příkaz, který má vaše `CWinApp` třída mapy zpráv pro povolení této funkce člen. Pokud uživatel aplikace vybere pomůže pomocí příkazu k vyvolání volá rámec této funkce obslužné rutiny zpráv `WinHelp` aplikace s standardní **HELP_HELPONHELP** tématu.  
  
##  <a name="onidle"></a>  CWinApp::OnIdle  
 Člen funkci k provedení zpracování doby nečinnosti přepište.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Parametry  
 *lCount*  
 Čítač zvýší pokaždé, když `OnIdle` je volána, když se fronta zpráv aplikace je prázdný. Toto je čítač nastaven na 0 pokaždé, když je novou zprávu zpracovat. Můžete použít *lCount* parametr k určení relativních doba běhu aplikace bylo nečinné bez zpracování zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty pro příjem více zpracování doby nečinnosti; 0, pokud není nutná žádná další doby nečinnosti.  
  
### <a name="remarks"></a>Poznámky  
 `OnIdle` ve smyčce zpráv výchozí je volána, když fronta zpráv aplikace je prázdný. Pomocí přepsání volání vlastní pozadí úlohy nečinnosti obslužné rutiny.  
  
 `OnIdle` by měl vrátit 0 k označení, že není vyžadováno žádné nečinnosti doba zpracování. *LCount* parametr se zvýší pokaždé, když `OnIdle` je volána, když je prázdný fronty zpráv a resetuje na hodnotu 0 pokaždé, když je novou zprávu zpracovat. Vaše různých nečinnosti rutiny založené na tento počet můžete volat.  
  
 Zde je souhrn zpracování nečinné smyčky:  
  
1.  Pokud zpráva smyčky v knihovny Microsoft Foundation Class zkontroluje fronty zpráv a ne zjistí čekajících zpráv, zavolá `OnIdle` pro objekt aplikace a zdroje 0 jako *lCount* argument.  
  
2. `OnIdle` provádí některé zpracování a vrátí nenulovou hodnotu indikující ho by měla být volána znovu udělat další zpracování.  
  
3.  Zpráva smyčky znovu kontroluje fronty zpráv. Pokud žádné zprávy čekají na vyřízení, zavolá `OnIdle` znovu zvyšování *lCount* argument.  
  
4.  Nakonec `OnIdle` dokončí zpracování její nečinnosti úkoly a vrátí hodnotu 0. Tato hodnota informuje zpráva smyčky zastavit volání `OnIdle` dokud přijetí další zprávy z fronty zpráv v tomto okamžiku nečinnosti cyklus restartuje s argumentem nastaven na hodnotu 0.  
  
 Neprovádějte zdlouhavé úlohy během `OnIdle` vzhledem k tomu, že aplikace nemůže zpracovat vstup uživatele, dokud `OnIdle` vrátí.  
  
> [!NOTE]
>  Výchozí implementaci `OnIdle` příkaz aktualizace objektů uživatelského rozhraní, jako je například položek nabídky a tlačítka panelu nástrojů a provede interních datových struktura čištění. Proto pokud přepíšete `OnIdle`, musí volat `CWinApp::OnIdle` s `lCount` ve vaší verzi přepsané. Nejdřív voláním zpracování při nečinnosti všechny základní třídy (to znamená, dokud základní třídy `OnIdle` vrátí hodnotu 0). Pokud potřebujete k práci, než dokončí zpracování základní třídy, přečtěte si základní třída implementace a vyberte správnou *lCount* během které k práci.  
  
 Pokud nechcete, aby `OnIdle` volá se vždy, když se načte zprávu z fronty zpráv, můžete přepsat [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Pokud aplikace má nastavit velmi krátké časovač, nebo pokud systému odesílá zprávy WM_SYSTIMER pak `OnIdle` bude volána opakovaně a snížit výkon.  
  
### <a name="example"></a>Příklad  
 Následující dva příklady ukazují, jak používat `OnIdle`. V prvním příkladu zpracovává dvě nečinnosti úlohy pomocí *lCount* argument k určení priority úlohy. První úlohou je s vysokou prioritou a měli byste udělat, je to možné. V druhé úloze je méně důležité a by měl být v době, kdy je dlouhá pozastavení vstup uživatele. Všimněte si volání základní třídy verzi `OnIdle`. V druhém příkladu spravuje skupinu nečinnosti úlohy s různými prioritami.  
  
 [!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]  
  
##  <a name="opendocumentfile"></a>  CWinApp::OpenDocumentFile  
 Architektura volá tuto metodu za účelem otevřete pojmenované [CDocument](../../mfc/reference/cdocument-class.md) soubor pro aplikaci.  
  
```  
virtual CDocument* OpenDocumentFile(
LPCTSTR lpszFileName  
BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *lpszFileName*  
 Název souboru, který se otevřít.  
  
 [v] *bAddToMRU*  
 Pravda označuje, že dokument je jednou z nejnovější soubory; NEPRAVDA označuje, že dokument není jedním z nejnovější soubory.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CDocument` Pokud úspěšná, jinak hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dokument, který má tento název je již otevřeno, bude první okno rámce, který obsahuje tento dokument získat fokus. Pokud aplikace podporuje více šablon dokumentů, rozhraní používá k nalezení šablony příslušný dokument k pokusu o načtení dokumentu příponu názvu souboru. Pokud bylo úspěšné, vytvoří šablona dokumentu pak oken s rámečkem a zobrazení pro dokument.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="parsecommandline"></a>  CWinApp::ParseCommandLine  
 Volání této funkce člen k analýze příkazového řádku a odeslat parametry, jeden po druhém, na [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).  
  
```  
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *rCmdInfo*  
 Odkaz na [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Při spuštění nového projektu knihovny MFC pomocí Průvodce aplikací v Průvodce vytvořením aplikace vytvoří místní instanci `CCommandLineInfo`a pak zavolají `ProcessShellCommand` a `ParseCommandLine` v [InitInstance](#initinstance) – členská funkce. Příkazový řádek odpovídá trasy popsané dál:  
  
1.  Po vytváření v `InitInstance`, `CCommandLineInfo` je předán objekt `ParseCommandLine`.  
  
2. `ParseCommandLine` pak zavolá `CCommandLineInfo::ParseParam` opakovaně, jednou pro každý parametr.  
  
3. `ParseParam` vyplní celé `CCommandLineInfo` objekt, který se potom předá do [ProcessShellCommand](#processshellcommand).  
  
4. `ProcessShellCommand` zpracovává argumenty příkazového řádku a značky.  
  
 Všimněte si, že můžete volat `ParseCommandLine` přímo podle potřeby.  
  
 Popis příznaky příkazového řádku najdete v tématu [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).  
  
##  <a name="pretranslatemessage"></a>  CWinApp::PreTranslateMessage  
 Přepsání této funkci můžete filtrovat okno zprávy předtím, než jsou odeslány do funkce Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) výchozí implementace provede klávesa akcelerátoru překlad, aby musí zavolat `CWinApp::PreTranslateMessage` členské funkce ve vaší verzi přepsané.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *pMsg*  
 Ukazatel [MSG](../../mfc/reference/msg-structure1.md) struktura, která obsahuje zprávu zpracovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zpráva byla plně zpracovány v `PreTranslateMessage` a nesmí být další zpracování. Nula, pokud by měl být zpráva zpracována běžným způsobem.  
  
##  <a name="processmessagefilter"></a>  CWinApp::ProcessMessageFilter  
 Funkce háku rozhraní framework volá tuto funkci člen filtrovat a reagovat na určité zpráv systému Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *Kód*  
 Určuje kód háku. Tato funkce člen kód používá určit, jak zpracovat *lpMsg.*  
  
 *lpMsg*  
 Ukazatel na Windows [MSG](../../mfc/reference/msg-structure1.md) struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je zpráva zpracována; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce háku zpracovává události před jejich odesláním do aplikace normální zpráva zpracování.  
  
 Pokud přepíšete tato pokročilé funkce, je nutné volat základní třídy verze Udržovat rozhraní framework napojit zpracování.  
  
##  <a name="processshellcommand"></a>  CWinApp::ProcessShellCommand  
 Tento člen funkce volá [InitInstance –](#initinstance) tak, aby přijímal parametrů předaných z `CCommandLineInfo` objekt identifikovaný *rCmdInfo*a provádět uvedené akce.  
  
```  
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *rCmdInfo*  
 Odkaz na [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je úspěšně zpracovat příkaz prostředí. Pokud 0, vrátí hodnotu FALSE z [InitInstance](#initinstance).  
  
### <a name="remarks"></a>Poznámky  
 Při spuštění nového projektu knihovny MFC pomocí Průvodce aplikací v Průvodce vytvořením aplikace vytvoří místní instanci `CCommandLineInfo`a pak zavolají `ProcessShellCommand` a [ParseCommandLine](#parsecommandline) v `InitInstance` – členská funkce. Příkazový řádek odpovídá trasy popsané dál:  
  
1.  Po vytváření v `InitInstance`, `CCommandLineInfo` je předán objekt `ParseCommandLine`.  
  
2. `ParseCommandLine` pak zavolá [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) opakovaně, jednou pro každý parametr.  
  
3. `ParseParam` vyplní celé `CCommandLineInfo` objekt, který se potom předá do `ProcessShellCommand`.  
  
4. `ProcessShellCommand` zpracovává argumenty příkazového řádku a značky.  
  
 Datové členy `CCommandLineInfo` objekt, identifikovaný [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), jsou následující výčtového typu, který je definován v rámci `CCommandLineInfo` třídy.  
  
```  
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };  
```
  
 Stručný popis každého z těchto hodnot najdete v tématu `CCommandLineInfo::m_nShellCommand`.  
  
##  <a name="processwndprocexception"></a>  CWinApp::ProcessWndProcException  
 Tento člen funkce volá framework vždy, když obslužná rutina nezachytí výjimka vyvolána v jednom z vaší aplikace zpráva nebo obslužné rutiny příkazů.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *e*  
 Ukazatel na nezachycenou výjimku.  
  
 *pMsg*  
 A [MSG](../../mfc/reference/msg-structure1.md) struktura, která obsahuje informace o zprávě systému windows, která způsobila, že rozhraní framework má být vyvolána výjimka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která má být vrácen do systému Windows. Obvykle je to 0L pro zpráv systému windows, 1L (TRUE) pro příkaz zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte tuto funkci člen přímo.  
  
 Výchozí implementace této funkce člen vytvoří okno se zprávou. Pokud pomocí nabídky, panelu nástrojů nebo selhání příkazu akcelerátoru vznikl nezachycenou výjimku, zobrazí se v zprávu "Příkazu se nezdařilo"; jinak zobrazí zprávu "Chyba interní aplikace".  
  
 Člen funkci zajistit globální zpracování vaše výjimek přepište. Volejte pouze základní funkce, pokud chcete, aby pole zpráv, který se má zobrazit.  
  
##  <a name="register"></a>  CWinApp::Register  
 Provádí úlohy všechny registrace není zpracována `RegisterShellFileTypes`.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace jednoduše vrátí hodnotu TRUE. Přepsání této funkce můžete poskytnout všechny přizpůsobené registrace kroky.  
  
##  <a name="registershellfiletypes"></a>  CWinApp::RegisterShellFileTypes  
 Volání této funkce člen na registraci všech typů dokumentů aplikace pomocí Správce souborů systému Windows.  
  
```  
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bCompat*  
 Hodnota TRUE přidá položky registrace pro příkazy prostředí tiskových a tisku na, umožňuje uživatelům tisknout soubory přímo z prostředí nebo přetažením souboru na objekt tiskárny. Také přidá DefaultIcon klíč. Ve výchozím nastavení je tento parametr hodnotu FALSE pro zpětnou kompatibilitu.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje uživateli otevřít datový soubor vytvořené aplikace dvojitým kliknutím na soubor z v rámci Správce souborů. Volání `RegisterShellFileTypes` po zavolání metody [AddDocTemplate](#adddoctemplate) pro každou z šablony dokumentů v aplikaci. Také zavolat [enableshellopen –](#enableshellopen) – členská funkce při volání `RegisterShellFileTypes`.  
  
 `RegisterShellFileTypes` prochází seznam [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objekty, že aplikace udržuje a ke každé šabloně dokumentu přidá položky do databáze registrace, která udržuje Windows pro přidružení typu souboru. Správce souborů používá tyto položky při poklepání ho otevřít datový soubor. Tím se eliminuje potřeba pro odeslání. Soubor REG s vaší aplikací.  
  
> [!NOTE]
> `RegisterShellFileTypes` funguje jenom v případě, že program spustí uživatel s právy správce. Pokud program nemá oprávnění správce, nelze změnit klíče registru.  
  
 Pokud databázi registrace již přidruží zadané přípony souboru jiný typ souboru, vytvoří se žádné nové přidružení. Najdete v článku `CDocTemplate` třídu pro formát řetězce, které jsou potřebné k registraci tyto informace.  
  
##  <a name="registerwithrestartmanager"></a>  CWinApp::RegisterWithRestartManager  
 Registruje správce restartování aplikace.  
  
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
|[v] *bRegisterRecoveryCallback*|Pravda označuje, že tuto instanci aplikace používá funkci zpětného volání obnovení; NEPRAVDA označuje, že je nepoužívá. Při ukončení aplikace neočekávaně volá framework funkce zpětného volání pro obnovení. Další informace najdete v tématu [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|  
|[v] *strRestartIdentifier*|Jedinečného řetězce, který identifikuje tuto instanci správce restartování. Restartování manager identifikátor je jedinečný pro každou instanci aplikace.|  
|[v] *pwzCommandLineArgs*|Řetězec, který obsahuje všechny další argumenty z příkazového řádku.|  
|[v] *dwRestartFlags*|Volitelné příznaky pro správce restartování. Další informace najdete v části poznámky.|  
|[v] *pRecoveryCallback*|Funkce zpětného volání pro obnovení. Tato funkce musí přijmout parametr LPVOID jako vstup a vrátit typu DWORD. Výchozí funkce zpětného volání pro obnovení je `CWinApp::ApplicationRecoveryCallback`.|  
|[v] *lpvParam*|Vstupní parametr pro zpětné volání funkce obnovení. Další informace najdete v tématu [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|  
|[v] *dwPingInterval*|Časový interval, který správce restartování čeká funkce zpětného volání obnovení vrátit. Tento parametr je v milisekundách.|  
|[v] *dwCallbackFlags*|Příznaky předaný funkci zpětného volání pro obnovení. Vyhrazeno pro budoucí použití.|  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná. v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace používá výchozí implementace MFC automatické ukládání souborů, používejte jednoduché verzi `RegisterWithRestartManager`. Použijte komplexní verzi `RegisterWithRestartManager` Pokud chcete přizpůsobit automatické ukládání chování vaší aplikace.  
  
 Pokud tuto metodu lze volat s prázdný řetězec pro *strRestartIdentifier*, `RegisterWithRestartManager` vytvoří řetězec jedinečný identifikátor pro tuto instanci restartování správce.  
  
 Při ukončení aplikace, neočekávaně, správce restartování restartuje aplikace z příkazového řádku a zajišťuje, že že jedinečný identifikátor jako volitelný argument restartovat. V tomto scénáři volá framework `RegisterWithRestartManager` dvakrát. První volání pochází z [CWinApp::InitInstance](#initinstance) s prázdný řetězec pro identifikátor řetězce. Potom metoda [CWinApp::ProcessShellCommand](#processshellcommand) volání `RegisterWithRestartManager` s identifikátorem jedinečný restartování.  
  
 Po registraci aplikace pomocí Správce restartování, monitoruje správce restartování aplikace. Pokud aplikace neočekávaně ukončí, správce restartování volání funkce zpětného volání obnovení během procesu vypnutí dolů. Manager čeká restartování *dwPingInterval* na odpověď od obnovení funkce zpětného volání. Pokud funkce zpětného volání obnovení neodpoví během této doby, aplikace se ukončí bez provádění obnovení funkce zpětného volání.  
  
 Ve výchozím nastavení dwRestartFlags nejsou podporovány, ale jsou k dispozici pro budoucí použití. Možné hodnoty *dwRestartFlags* jsou následující:  
  
- RESTART_NO_CRASH  
  
- RESTART_NO_HANG  
  
- RESTART_NO_PATCH  
  
- RESTART_NO_REBOOT  
  
##  <a name="reopenpreviousfilesatrestart"></a>  CWinApp::ReopenPreviousFilesAtRestart  
 Určuje, zda správce restartování neotevře soubory, které byly otevřené, pokud aplikace byl neočekávaně ukončen.  
  
```  
virtual BOOL ReopenPreviousFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravda označuje, že správce restartování neotevře dříve otevřených souborů; NEPRAVDA označuje, že správce restartování neexistuje.  
  
##  <a name="restartinstance"></a>  CWinApp::RestartInstance  
 Zpracuje restartování aplikace iniciovaná správce restartování.  
  
```  
virtual BOOL CWinApp::RestartInstance();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud obslužná rutina dat obnovení otevře dříve otevřené dokumenty; FALSE, pokud obslužná rutina obnovení dat došlo k chybě, nebo pokud nejsou žádné dříve otevřené dokumenty.  
  
### <a name="remarks"></a>Poznámky  
 Po restartování aplikace Správce restartování rozhraní volá tuto metodu. Tato metoda načítá obslužná rutina obnovení dat a obnoví soubory automaticky uloženo. Tato metoda volá [CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) k určení, jestli uživatel chce obnovit soubory automaticky uloženo.  
  
 Tato metoda vrátí hodnotu FALSE, pokud [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) Určuje, že neexistují žádné otevřené dokumenty. Pokud nebyly žádné otevřené dokumenty, aplikace se spustí normálně.  
  
##  <a name="restoreautosavedfilesatrestart"></a>  CWinApp::RestoreAutosavedFilesAtRestart  
 Určuje, zda správce restartování obnoví soubory automaticky uloženo po restartování aplikace.  
  
```  
virtual BOOL RestoreAutosavedFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravda označuje, že správce restartování obnoví soubory automaticky uloženo; NEPRAVDA označuje, že správce restartování neexistuje.  
  
##  <a name="run"></a>  CWinApp::Run  
 Poskytuje výchozí zprávu smyčku.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Int** hodnotu, která vrátí `WinMain`.  
  
### <a name="remarks"></a>Poznámky  
 `Run` odeslání zpráv systému Windows, dokud aplikace přijme zprávu o WM_QUIT a operace čtení. Pokud aplikace zprávu fronty aktuálně obsahuje žádné zprávy `Run` volání [OnIdle](#onidle) k provedení zpracování doby nečinnosti. Příchozí zprávy přejít na [PreTranslateMessage –](#pretranslatemessage) – členská funkce pro zvláštní zpracování a pak na funkce systému Windows `TranslateMessage` pro překlad standardní klávesnice; nakonec `DispatchMessage` je volána funkce systému Windows.  
  
 `Run` zřídka přepsána, ale ji, aby poskytovala zvláštní chování můžete přepsat.  
  
##  <a name="runautomated"></a>  CWinApp::RunAutomated  
 Volání této funkce můžete určit, zda " **/Automation**"nebo" **-automatizace**" možnost je přítomen, což naznačuje, zda aplikace server byl spuštěn klientské aplikace.  
  
```  
BOOL RunAutomated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla nalezena možnost; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici, je možnost odebrat z příkazového řádku. Další informace o automatizace OLE, najdete v článku [automatizační servery](../../mfc/automation-servers.md).  
  
##  <a name="runembedded"></a>  CWinApp::RunEmbedded  
 Volání této funkce můžete určit, zda " **/vložení**"nebo" **-vkládání objektů**" možnost je přítomen, což naznačuje, zda aplikace server byl spuštěn klientské aplikace.  
  
```  
BOOL RunEmbedded();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla nalezena možnost; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici, je možnost odebrat z příkazového řádku. Další informace o vložení, najdete v článku [servery: implementace serveru](../../mfc/servers-implementing-a-server.md).  
  
##  <a name="saveallmodified"></a>  CWinApp::SaveAllModified  
 Voláno rámcem uložit všechny dokumenty, pokud je okno hlavního rámce aplikace bude uzavřen, nebo prostřednictvím WM_QUERYENDSESSION zprávu.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je to bezpečné ukončit aplikaci; 0, pokud je to není bezpečné ukončit aplikaci.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce člen volá [CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified) – členská funkce zase pro všechny upravené dokumenty v aplikaci.  
  
##  <a name="selectprinter"></a>  CWinApp::SelectPrinter  
 Volání této funkce člen vybrat konkrétní tiskárnu a verzí tiskárny, který byl předtím vybrali v dialogovém okně tisku.  
  
```  
void SelectPrinter(
    HANDLE hDevNames,  
    HANDLE hDevMode,  
    BOOL bFreeOld = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *hDevNames je*  
 Popisovač pro [DEVNAMES](../../mfc/reference/devnames-structure.md) struktura, která identifikuje ovladače, zařízení a názvy port výstupu dané tiskárny.  
  
 *hDevMode*  
 Popisovač pro [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktura, která určuje informace o prostředí tiskárny a inicializace zařízení.  
  
 *bFreeOld*  
 Uvolní dříve vybrané tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Pokud oba *hDevMode* a *hDevNames je* má hodnotu NULL, `SelectPrinter` používá výchozí tiskárnu.  
  
##  <a name="sethelpmode"></a>  CWinApp::SetHelpMode  
 Nastaví typ nápovědy aplikace.  
  
```  
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```  
  
### <a name="parameters"></a>Parametry  
 *eHelpType*  
 Určuje typ nápovědy k použití. V tématu [CWinApp::m_eHelpType](#m_ehelptype) Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví typ nápovědy aplikace.  
  
 Postup nastavení typu nápovědy aplikace HTMLHelp, můžete volat [EnableHTMLHelp](#enablehtmlhelp). Jakmile zavoláte `EnableHTMLHelp`, aplikace musí používat HTMLHelp jako jeho aplikace nápovědy. Pokud chcete změnit použití WinHelp, můžete zavolat `SetHelpMode` a nastavte *eHelpType* k `afxWinHelp`.  
  
##  <a name="setregistrykey"></a>  CWinApp::SetRegistryKey  
 Způsobí, že nastavení aplikace má být uložen v registru místo soubory INI.  
  
```  
void SetRegistryKey(LPCTSTR lpszRegistryKey);  
void SetRegistryKey(UINT nIDRegistryKey);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRegistryKey*  
 Ukazatel na řetězec, který obsahuje název klíče.  
  
 *nIDRegistryKey*  
 ID prostředku řetězec obsahující název klíče registru.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nastaví *m_pszRegistryKey*, který je pak používány `GetProfileInt`, `GetProfileString`, `WriteProfileInt`, a `WriteProfileString` členské funkce `CWinApp`. Pokud je tato funkce je volána, seznam nejvíce naposledy použitých souborů (naposledy použitých) také uložen v registru. Klíč registru je obvykle název společnosti. Je uložený v klíč v následujícím formátu: HKEY_CURRENT_USER\Software\\< název společnosti\>\\< název aplikace\>\\< název oddílu\>\\< hodnota název\>.  
  
##  <a name="supportsapplicationrecovery"></a>  CWinApp::SupportsApplicationRecovery  
 Určuje, zda správce restartování obnoví aplikaci, která byl neočekávaně ukončen.  
  
```  
virtual BOOL SupportsApplicationRecovery() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravda označuje, že správce restartování obnoví aplikaci; NEPRAVDA označuje, že správce restartování neexistuje.  
  
##  <a name="supportsautosaveatinterval"></a>  CWinApp::SupportsAutosaveAtInterval  
 Určuje, zda autosaves správce restartování otevřít dokumenty v pravidelných intervalech.  
  
```  
virtual BOOL SupportsAutosaveAtInterval() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravda označuje, že autosaves správce restartování otevřít dokumenty; NEPRAVDA označuje, že správce restartování neexistuje.  
  
##  <a name="supportsautosaveatrestart"></a>  CWinApp::SupportsAutosaveAtRestart  
 Určuje, zda autosaves správce restartování žádné otevřít dokumenty, když se aplikace restartuje.  
  
```  
virtual BOOL SupportsAutosaveAtRestart() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravda označuje, že autosaves správce restartování otevřít dokumenty, když se aplikace restartuje; NEPRAVDA označuje, že správce restartování neexistuje.  
  
##  <a name="supportsrestartmanager"></a>  CWinApp::SupportsRestartManager  
 Určuje, jestli aplikace podporuje správce restartování.  
  
```  
virtual BOOL SupportsRestartManager() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pravda označuje, že aplikace podporuje správce restartování; NEPRAVDA označuje, že aplikace neexistuje.  
  
##  <a name="unregister"></a>  CWinApp::Unregister  
 Zruší registraci všechny soubory, zaregistrovaný objekt aplikace.  
  
```  
virtual BOOL Unregister();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Unregister` Funkce vrátí zpět registraci provádí objekt aplikace a [zaregistrovat](#register) funkce. Za normálních okolností obě funkce se nazývají implicitně v prostředí MFC a proto se nezobrazí v kódu.  
  
 Přepsání této funkci můžete provést kroky vlastní zrušení registrace.  
  
##  <a name="unregistershellfiletypes"></a>  CWinApp::UnregisterShellFileTypes  
 Volání této funkce člen se zrušit registraci všech typů dokumentů aplikace pomocí Správce souborů systému Windows.  
  
```  
void UnregisterShellFileTypes();
```  
  
##  <a name="winhelp"></a>  CWinApp::WinHelp  
 Volání této funkce člen má být vyvolán WinHelp aplikace.  
  
```  
virtual void WinHelp(
    DWORD_PTR dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>Parametry  
 *dwData*  
 Určuje další data. Hodnota použitá závisí na hodnotu *nCmd* parametr.  
  
 *nCmd*  
 Určuje typ nápovědy požadovaný. Seznam možných hodnot a jejich vlivu *dwData* parametr, najdete v článku [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) funkce systému Windows.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce má být vyvolán WinHelp aplikace také volá framework.  
  
 Rozhraní se automaticky zavře WinHelp aplikace při ukončení aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]  
  
##  <a name="writeprofilebinary"></a>  CWinApp::WriteProfileBinary  
 Volání této funkce členů k zápisu binární data do zadaný oddíl registru aplikace nebo. Soubor INI.  
  
```  
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud v části neexistuje, vytvoří se. Název oddílu, je případ nezávislé; řetězec může být libovolnou kombinaci velkých a velkých písmen.  
  
 *lpszEntry*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje položku, do kterého je hodnota má být proveden zápis. Pokud položka v zadaný oddíl neexistuje, vytvoří se.  
  
 *pData*  
 Odkazuje na data, která mají být zapsána.  
  
 *nBytes*  
 Obsahuje počet bajtů, které mají být zapsána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 Tento příklad používá `CWinApp* pApp = AfxGetApp();` v CWinApp – třída ilustrující způsob, jak získat, `WriteProfileBinary` a `GetProfileBinary` lze z jakékoli funkce v aplikaci MFC.  
  
 [!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]  
  
 Další příklad, podívejte se na příklad pro [CWinApp::GetProfileBinary](#getprofilebinary).  
  
##  <a name="writeprofileint"></a>  CWinApp::WriteProfileInt  
 Volání této funkce členů k zápisu do zadaný oddíl registru aplikace zadaná hodnota nebo. Soubor INI.  
  
```  
BOOL WriteProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud v části neexistuje, vytvoří se. Název oddílu, je případ nezávislé; řetězec může být libovolnou kombinaci velkých a velkých písmen.  
  
 *lpszEntry*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje položku, do kterého je hodnota má být proveden zápis. Pokud položka v zadaný oddíl neexistuje, vytvoří se.  
  
 *nHodnota*  
 Obsahuje hodnotu, která má být proveden zápis.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 Tento příklad používá `CWinApp* pApp = AfxGetApp();` v CWinApp – třída ilustrující způsob, jak získat, `WriteProfileString`, `WriteProfileInt`, `GetProfileString`, a `GetProfileInt` lze z jakékoli funkce v aplikaci MFC.  
  
 [!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 Další příklad, podívejte se na příklad pro [CWinApp::GetProfileInt](#getprofileint).  
  
##  <a name="writeprofilestring"></a>  CWinApp::WriteProfileString  
 Volání této funkce členů k zápisu zadaný řetězec do zadaný oddíl registru aplikace nebo. Soubor INI.  
  
```  
BOOL WriteProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSection*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje oddíl obsahující položku. Pokud v části neexistuje, vytvoří se. Název oddílu, je případ nezávislé; řetězec může být libovolnou kombinaci velkých a velkých písmen.  
  
 *lpszEntry*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje položku, do kterého je hodnota má být proveden zápis. Pokud položka v zadaný oddíl neexistuje, vytvoří se. Pokud tento parametr hodnotu NULL, v části určeného *lpszSection* se odstraní.  
  
 *lpszValue*  
 Odkazuje na řetězec, který má být zapsána. Pokud tento parametr hodnotu NULL, položka určeného *lpszEntry* parametr se odstraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 Další příklad, podívejte se na příklad pro [CWinApp::GetProfileInt](#getprofileint).  
  
##  <a name="setappid"></a>  CWinApp::SetAppID  
 Nastaví explicitně Application User Model ID aplikace. Tato metoda by měla být volána před žádné uživatelské rozhraní se zobrazí uživatelům (nejlepší místo je konstruktor aplikace).  
  
```  
void SetAppID(LPCTSTR lpcszAppID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpcszAppID*  
 Určuje ID aplikace uživatele modelu.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [CWinThread – třída](../../mfc/reference/cwinthread-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md)



