---
title: "Třída CAtlServiceModuleT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
dev_langs:
- C++
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2d059a990b9b01cdfc959284d9fe20f3dfd12af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT – třída
Tato třída implementuje služby.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, UINT nServiceNameID>  
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CAtlServiceModuleT`.  
  
 *nServiceNameID*  
 Identifikátor prostředku služby.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlServiceModuleT::Handler](#handler)|Rutina obslužné rutiny pro službu.|  
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|Poskytuje výchozí nastavení zabezpečení pro službu.|  
|[CAtlServiceModuleT::Install](#install)|Nainstaluje a vytvoří službu.|  
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Potvrdí, že byla nainstalována služba.|  
|[CAtlServiceModuleT::LogEvent](#logevent)|Zapíše do protokolu událostí.|  
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Potlačí tuto metodu službu dále používat.|  
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Potlačí tuto metodu za účelem zjistěte službu.|  
|[CAtlServiceModuleT::OnPause](#onpause)|Potlačí tuto metodu za účelem pozastavení služby.|  
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Potlačí tuto metodu vypnout službu|  
|[CAtlServiceModuleT::OnStop](#onstop)|Potlačí tuto metodu k zastavení služby|  
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Potlačí tuto metodu pro zpracování neznámé žádosti o službu|  
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analyzuje příkazového řádku a v případě potřeby provede registrace.|  
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Tato metoda je volána bezprostředně před vstupem smyčce zpráv.|  
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Zaregistruje služby v registru.|  
|[CAtlServiceModuleT::Run](#run)|Spouští službu.|  
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Metoda volána pomocí Správce řízení služeb.|  
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualizuje stav služby.|  
|[CAtlServiceModuleT::Start](#start)|Voláno rozhraním `CAtlServiceModuleT::WinMain` při spuštění služby.|  
|[CAtlServiceModuleT::Uninstall](#uninstall)|Zastaví a odstraní službu.|  
|[CAtlServiceModuleT::Unlock](#unlock)|Snižuje počet služby zámku.|  
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Odebere službu z registru.|  
|[CAtlServiceModuleT::WinMain](#winmain)|Tato metoda implementuje je kód potřebný ke spouštění služby.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlServiceModuleT::m_bService](#m_bservice)|Příznak, což značí, že je program spuštěn jako služba.|  
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Členské proměnné ukládání identifikátor přístup z více vláken.|  
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Členské proměnné ukládání popisovač pro strukturu stavové informace pro službu aktuální.|  
|[CAtlServiceModuleT::m_status](#m_status)|Členské proměnné ukládání strukturu stavové informace pro službu aktuální.|  
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Název služby registrována.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlServiceModuleT`, odvozené od [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementuje modul ATL služby. `CAtlServiceModuleT`poskytuje metody pro zpracování příkazového řádku, instalaci, registraci a odebrání. Pokud je potřeba další funkce, lze přepsat tyto a další metody.  
  
 Nahradí tato třída zastaralá [CComModule – třída](../../atl/reference/ccommodule-class.md) použitého v předchozích verzích ATL. V tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)  
  
 `CAtlServiceModuleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT  
 Konstruktor  
  
```
CAtlServiceModuleT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Datové členy inicializuje a nastaví stav počáteční služby.  
  
##  <a name="handler"></a>CAtlServiceModuleT::Handler  
 Rutina obslužné rutiny pro službu.  
  
```
void Handler(DWORD dwOpcode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwOpcode*  
 Přepínač, který definuje operaci obslužné rutiny. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Toto je kód, který volá správce řízení služeb (SCM), aby se načíst stav služby a problém pokynů například zastavit nebo pozastavit. SCM předá kód operace, viz následující obrázek, na `Handler` označující, co má provést službu.  
  
|Kód operace|Význam|  
|--------------------|-------------|  
|SERVICE_CONTROL_STOP|Zastaví službu. Přepsání metody [CAtlServiceModuleT::OnStop](#onstop) v atlbase.h můžete změnit chování.|  
|SERVICE_CONTROL_PAUSE|Uživatel implementována. Přepsat metodu prázdný [CAtlServiceModuleT::OnPause](#onpause) v atlbase.h pozastavit službu.|  
|SERVICE_CONTROL_CONTINUE|Uživatel implementována. Přepsat metodu prázdný [CAtlServiceModuleT::OnContinue](#oncontinue) v atlbase.h službu dále používat.|  
|SERVICE_CONTROL_INTERROGATE|Uživatel implementována. Přepsat metodu prázdný [CAtlServiceModuleT::OnInterrogate](#oninterrogate) v atlbase.h k dotazování služby.|  
|SERVICE_CONTROL_SHUTDOWN|Uživatel implementována. Přepsat metodu prázdný [CAtlServiceModuleT::OnShutdown](#onshutdown) v atlbase.h vypnutí služby.|  
  
 Pokud není rozpoznán kód operace, metody [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) je volána.  
  
 Výchozí generovaný ATL služba zpracovává jenom pokyn zastavit. Pokud správce SCM úspěšně projde zastavení pokyn, službu informuje správce SCM, program se chystá ukončit. Pak zavolá službu `PostThreadMessage` ukončete zprávu na sebe sama. To ukončí smyčce zpráv a služby se nakonec zavřete.  
  
##  <a name="initializesecurity"></a>CAtlServiceModuleT::InitializeSecurity  
 Poskytuje výchozí nastavení zabezpečení pro službu.  
  
```
HRESULT InitializeSecurity() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V aplikaci Visual Studio .NET 2003 tato metoda není implementována v základní třídě. Průvodce projektem Visual Studio zahrnuje tato metoda v generovaný kód, ale k chybě kompilace dojde v případě kompiluje projekt vytvořený v dřívější verzi Visual C++ pomocí knihovny ATL 7.1. Všechny třídy odvozené od `CAtlServiceModuleT` musí implementovat tuto metodu v odvozené třídě.  
  
 Použít PKT úroveň ověřování, úroveň zosobnění RPC_C_IMP_LEVEL_IDENTIFY a příslušný nesmí být nulová popisovač zabezpečení ve volání **u funkce CoInitializeSecurity**.  
  
 Pro projekty generované v Průvodci neoznačené atributy služeb bude v  
  
 [!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]  
  
 Pro projekty s atributy služeb bude v  
  
 [!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]  
  
##  <a name="install"></a>CAtlServiceModuleT::Install  
 Nainstaluje a vytvoří službu.  
  
```
BOOL Install() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nainstaluje službu do databáze nástroje Správce řízení služeb (SCM) a potom vytvoří objekt služby. Pokud službu nelze vytvořit, zobrazí se okno se zprávou a metoda vrátí hodnotu FALSE.  
  
##  <a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled  
 Potvrdí, že byla nainstalována služba.  
  
```
BOOL IsInstalled() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud služba je nainstalovaná, FALSE, jinak hodnota.  
  
##  <a name="logevent"></a>CAtlServiceModuleT::LogEvent  
 Zapíše do protokolu událostí.  
  
```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Řetězec k zápisu do protokolu událostí.  
  
 ...  
 Volitelné další řetězce k zápisu do protokolu událostí.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda podrobnosti zapíše do protokolu událostí, pomocí funkce [ReportEvent](http://msdn.microsoft.com/library/windows/desktop/aa363679). Pokud žádná služba běží, se budou odesílat řetězec do konzoly.  
  
##  <a name="m_bservice"></a>CAtlServiceModuleT::m_bService  
 Příznak, což značí, že je program spuštěn jako služba.  
  
```
BOOL m_bService;
```  
  
### <a name="remarks"></a>Poznámky  
 Používá k rozlišení EXE služby z EXE aplikace.  
  
##  <a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID  
 Členské proměnné ukládání identifikátor vlákna služby.  
  
```
DWORD m_dwThreadID;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná ukládá identifikátor aktuálního vlákna.  
  
##  <a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus  
 Členské proměnné ukládání popisovač pro strukturu stavové informace pro službu aktuální.  
  
```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```  
  
### <a name="remarks"></a>Poznámky  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996) struktura obsahuje informace o službě.  
  
##  <a name="m_status"></a>CAtlServiceModuleT::m_status  
 Členské proměnné ukládání strukturu stavové informace pro službu aktuální.  
  
```
SERVICE_STATUS m_status;
```  
  
### <a name="remarks"></a>Poznámky  
 [SERVICE_STATUS](http://msdn.microsoft.com/library/windows/desktop/ms685996) struktura obsahuje informace o službě.  
  
##  <a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName  
 Název služby registrována.  
  
```
TCHAR [256] m_szServiceName;
```  
  
### <a name="remarks"></a>Poznámky  
 Řetězce ukončené hodnotou null, který ukládá název služby.  
  
##  <a name="oncontinue"></a>CAtlServiceModuleT::OnContinue  
 Potlačí tuto metodu službu dále používat.  
  
```
void OnContinue() throw();
```  
  
##  <a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate  
 Potlačí tuto metodu za účelem zjistěte službu.  
  
```
void OnInterrogate() throw();
```  
  
##  <a name="onpause"></a>CAtlServiceModuleT::OnPause  
 Potlačí tuto metodu za účelem pozastavení služby.  
  
```
void OnPause() throw();
```  
  
##  <a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown  
 Potlačí tuto metodu vypnutí služby.  
  
```
void OnShutdown() throw();
```  
  
##  <a name="onstop"></a>CAtlServiceModuleT::OnStop  
 Potlačí tuto metodu k zastavení služby.  
  
```
void OnStop() throw();
```  
  
##  <a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest  
 Potlačí tuto metodu za účelem zpracování neznámé žádosti o službu.  
  
```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```  
  
### <a name="parameters"></a>Parametry  
 */\*dwOpcode\*/*  
 Vyhrazena.  
  
##  <a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine  
 Analyzuje příkazového řádku a v případě potřeby provede registrace.  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpCmdLine`  
 Příkazový řádek.  
  
 `pnRetCode`  
 HRESULT odpovídající registrace (Pokud trvalo místní).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA na úspěch, nebo hodnotu NEPRAVDA, pokud RGS soubor zadaný v příkazovém řádku se nepodařilo zaregistrovat.  
  
### <a name="remarks"></a>Poznámky  
 Analyzuje příkazového řádku a zaregistruje nebo zrušení registrace zadaný soubor RGS v případě potřeby. Tato metoda volá [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) zkontrolujte **/regserver** a **/Unregserver**. Přidání argument **- / Service** se zaregistrovat službu.  
  
##  <a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop  
 Tato metoda je volána bezprostředně před vstupem smyčce zpráv.  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Tento parametr se předává do [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu přidejte vlastní inicializaci kód pro službu.  
  
##  <a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId  
 Zaregistruje služby v registru.  
  
```
inline HRESULT RegisterAppId(bool bService = false) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *bService*  
 Musí být hodnota true, má-li zaregistrovat jako služba.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="run"></a>CAtlServiceModuleT::Run  
 Spouští službu.  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Určuje, jak se nezobrazí okno. Tento parametr může být jedna z hodnot zabývá [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) části. Výchozí hodnota je SW_HIDE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Po volání, **spustit** volání [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop), a [CAtlExeModuleT:: PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).  
  
##  <a name="servicemain"></a>CAtlServiceModuleT::ServiceMain  
 Tato metoda je volána pomocí Správce řízení služeb.  
  
```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwArgc*  
 Argc – argument.  
  
 *lpszArgv*  
 Argv – argument.  
  
### <a name="remarks"></a>Poznámky  
 Správce řízení služeb (SCM) volání `ServiceMain` při otevření aplikace služby v Ovládacích panelech, vyberte službu a klikněte na příkaz spustit.  
  
 Po SCM volá `ServiceMain`, služba musí dát SCM funkce obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (například pozastavení nebo ukončení). Následně [CAtlServiceModuleT::Run](#run) je volána pro práci hlavní služby. **Spustit** bude pokračovat v provádění, dokud služba je zastavena.  
  
##  <a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus  
 Tato metoda aktualizuje stav služby.  
  
```
void SetServiceStatus(DWORD dwState) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwState`  
 Nový stav. V tématu [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241) pro možné hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje informace o službě stavu Správce řízení služeb. Je volána metodou [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) a další metody obslužné rutiny. Stav je také uložené v proměnné člena [CAtlServiceModuleT::m_status](#m_status).  
  
##  <a name="start"></a>CAtlServiceModuleT::Start  
 Voláno rozhraním `CAtlServiceModuleT::WinMain` při spuštění služby.  
  
```
HRESULT Start(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Určuje, jak se nezobrazí okno. Tento parametr může být jedna z hodnot zabývá [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) části.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 [CAtlServiceModuleT::WinMain](#winmain) metoda zpracovává registrace a instalace, a také úlohy součástí odstranění položek registru a odinstalace modulu. Při spuštění služby `WinMain` volání **spustit**.  
  
##  <a name="uninstall"></a>CAtlServiceModuleT::Uninstall  
 Zastaví a odstraní službu.  
  
```
BOOL Uninstall() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Zastaví službu spuštění a odstraní ji z databáze správce řízení služeb.  
  
##  <a name="unlock"></a>CAtlServiceModuleT::Unlock  
 Snižuje počet služby zámku.  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet zámků, což může být užitečné pro diagnostiku a ladění.  
  
##  <a name="unregisterappid"></a>CAtlServiceModuleT::UnregisterAppId  
 Odebere službu z registru.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="winmain"></a>CAtlServiceModuleT::WinMain  
 Tato metoda implementuje kód nezbytné ke spuštění služby.  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Určuje, jak se nezobrazí okno. Tento parametr může být jedna z hodnot zabývá [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) části.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí služby návratovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává příkazového řádku (s [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) a pak spustí službu (pomocí [CAtlServiceModuleT::Start](#start)).  
  
## <a name="see-also"></a>Viz také  
 [CAtlExeModuleT – třída](../../atl/reference/catlexemodulet-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
