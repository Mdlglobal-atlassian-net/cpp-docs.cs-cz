---
title: Třída CAtlServiceModuleT
ms.date: 05/06/2019
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
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 6d1985384c2d9a324abac548f27be6be5f0cacf5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748588"
---
# <a name="catlservicemodulet-class"></a>Třída CAtlServiceModuleT

Tato třída implementuje službu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozená z `CAtlServiceModuleT`.

*nID___*<br/>
Identifikátor prostředku služby.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT::Obslužná rutina](#handler)|Rutina obslužné rutiny pro službu.|
|[CAtlServiceModuleT::Inicializovatzabezpečení](#initializesecurity)|Poskytuje výchozí nastavení zabezpečení služby.|
|[CAtlServiceModuleT::Instalace](#install)|Nainstaluje a vytvoří službu.|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Potvrzuje, že služba byla nainstalována.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Zapíše do protokolu událostí.|
|[CAtlServiceModuleT::Pokračování](#oncontinue)|Přepsat tuto metodu pokračovat ve službě.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Přepsat tuto metodu k dotazování služby.|
|[CAtlServiceModuleT::OnPause](#onpause)|Přepsat tuto metodu pozastavit službu.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Přepsat tuto metodu k vypnutí služby|
|[CAtlServiceModuleT::OnStop](#onstop)|Přepsat tuto metodu zastavit službu|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Přepsat tuto metodu pro zpracování neznámých požadavků na službu|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analyzuje příkazový řádek a v případě potřeby provede registraci.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Tato metoda je volána bezprostředně před vstupem do smyčky zpráv.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Zaregistruje službu v registru.|
|[CAtlServiceModuleT::Spustit](#run)|Spustí službu.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Metoda volaná správcem řízení služeb.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualizuje stav služby.|
|[CAtlServiceModuleT::Start](#start)|Volána `CAtlServiceModuleT::WinMain` při spuštění služby.|
|[CAtlServiceModuleT::Odinstalace](#uninstall)|Zastaví a odebere službu.|
|[CAtlServiceModuleT::Odemknout](#unlock)|Sníží počet zámků služby.|
|[CAtlServiceModuleT::Zrušení registrace Id](#unregisterappid)|Odebere službu z registru.|
|[CAtlServiceModuleT::WinMain](#winmain)|Tato metoda implementuje kód potřebný ke spuštění služby.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Příznak označující, že program je spuštěn jako služba.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Proměnná člena ukládající identifikátor vlákna.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Proměnná člena ukládající popisovač do struktury informací o stavu pro aktuální službu.|
|[CAtlServiceModuleT::m_status](#m_status)|Proměnná člena ukládající strukturu informací o stavu pro aktuální službu.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Název registrované služby.|

## <a name="remarks"></a>Poznámky

`CAtlServiceModuleT`, odvozený z [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), implementuje modul služby ATL. `CAtlServiceModuleT`poskytuje metody pro zpracování, instalaci, registraci a odebrání příkazového řádku. Pokud je požadována další funkce, tyto a další metody mohou být přepsány.

Tato třída nahrazuje zastaralou [třídu CComModule používanou](../../atl/reference/ccommodule-class.md) v dřívějších verzích atl. Další podrobnosti naleznete [v části Třídy modulů ATL.](../../atl/atl-module-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Modul CAtl](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModulT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlservicemoduletcatlservicemodulet"></a><a name="catlservicemodulet"></a>CAtlServiceModuleT::CAtlServiceModuleT

Konstruktor

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a nastaví stav počáteční služby.

## <a name="catlservicemodulethandler"></a><a name="handler"></a>CAtlServiceModuleT::Obslužná rutina

Rutina obslužné rutiny pro službu.

```cpp
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Přepínač, který definuje operaci obslužné rutiny. Podrobnosti naleznete v poznámkách.

### <a name="remarks"></a>Poznámky

Toto je kód, který správce řízení služeb (SCM) volá k načtení stavu služby a vydat pokyny, jako je například zastavit nebo pozastavit. SCM předá kód operace, je `Handler` uvedeno níže, chcete-li označit, co by měla služba dělat.

|Kód operace|Význam|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Zastaví službu. Přepište metodu [CAtlServiceModuleT::OnStop](#onstop) v atlbase.h změnit chování.|
|SERVICE_CONTROL_PAUSE|Uživatel implementován. Přepište prázdnou metodu [CAtlServiceModuleT::OnPause](#onpause) v atlbase.h pozastavit službu.|
|SERVICE_CONTROL_CONTINUE|Uživatel implementován. Přepsat prázdnou metodu [CAtlServiceModuleT::OnPokračovat](#oncontinue) v atlbase.h pokračovat ve službě.|
|SERVICE_CONTROL_INTERROGATE|Uživatel implementován. Přepište prázdnou metodu [CAtlServiceModuleT::OnInterrogate](#oninterrogate) in atlbase.h k dotazování služby.|
|SERVICE_CONTROL_SHUTDOWN|Uživatel implementován. Přepište prázdnou metodu [CAtlServiceModuleT::OnShutdown](#onshutdown) v souboru atlbase.h a vypněte službu.|

Pokud kód operace není rozpoznán, je volána metoda [CAtlServiceModuleT::OnUnknownRequest.](#onunknownrequest)

Výchozí služba generovaná atl zpracovává pouze stop instrukce. Pokud SCM předá stop instrukce, služba sdělí SCM, že program se chystá zastavit. Služba pak `PostThreadMessage` volá k odeslání ukončovací zprávy sám sobě. Tím se ukončí smyčka zpráv a služba bude nakonec ukončena.

## <a name="catlservicemoduletinitializesecurity"></a><a name="initializesecurity"></a>CAtlServiceModuleT::Inicializovatzabezpečení

Poskytuje výchozí nastavení zabezpečení služby.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Všechny třídy, `CAtlServiceModuleT` která pochází z musí implementovat tuto metodu v odvozené třídě.

Použijte ověřování na úrovni PKT, úroveň zosobnění RPC_C_IMP_LEVEL_IDENTIFY a odpovídající popisovač `CoInitializeSecurity`zabezpečení, který není null, při volání .

U nepřiřazených projektů služeb generovaných průvodcem by to bylo

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

U připsaných projektů služeb by to bylo

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

## <a name="catlservicemoduletinstall"></a><a name="install"></a>CAtlServiceModuleT::Instalace

Nainstaluje a vytvoří službu.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Nainstaluje službu do databáze Správce řízení služeb (SCM) a potom vytvoří objekt služby. Pokud službu nelze vytvořit, zobrazí se okno se zprávou a metoda vrátí hodnotu NEPRAVDA.

## <a name="catlservicemoduletisinstalled"></a><a name="isinstalled"></a>CAtlServiceModuleT::IsInstalled

Potvrzuje, že služba byla nainstalována.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je služba nainstalována, jinak NEPRAVDA.

## <a name="catlservicemoduletlogevent"></a><a name="logevent"></a>CAtlServiceModuleT::LogEvent

Zapíše do protokolu událostí.

```cpp
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec pro zápis do protokolu událostí.

*...*<br/>
Volitelné další řetězce, které mají být zapsány do protokolu událostí.

### <a name="remarks"></a>Poznámky

Tato metoda zapíše podrobnosti do protokolu událostí pomocí funkce [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Pokud není spuštěna žádná služba, řetězec je odeslán do konzoly.

## <a name="catlservicemoduletm_bservice"></a><a name="m_bservice"></a>CAtlServiceModuleT::m_bService

Příznak označující, že program je spuštěn jako služba.

```
BOOL m_bService;
```

### <a name="remarks"></a>Poznámky

Slouží k rozlišení EXE služby od exe aplikace.

## <a name="catlservicemoduletm_dwthreadid"></a><a name="m_dwthreadid"></a>CAtlServiceModuleT::m_dwThreadID

Proměnná člena ukládající identifikátor vlákna služby.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Poznámky

Tato proměnná ukládá identifikátor vlákna aktuálního vlákna.

## <a name="catlservicemoduletm_hservicestatus"></a><a name="m_hservicestatus"></a>CAtlServiceModuleT::m_hServiceStatus

Proměnná člena ukládající popisovač do struktury informací o stavu pro aktuální službu.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Poznámky

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) obsahuje informace o službě.

## <a name="catlservicemoduletm_status"></a><a name="m_status"></a>CAtlServiceModuleT::m_status

Proměnná člena ukládající strukturu informací o stavu pro aktuální službu.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Poznámky

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) obsahuje informace o službě.

## <a name="catlservicemoduletm_szservicename"></a><a name="m_szservicename"></a>CAtlServiceModuleT::m_szServiceName

Název registrované služby.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Poznámky

Řetězec s ukončeným hodnotou null, ve kterém je uložen název služby.

## <a name="catlservicemoduletoncontinue"></a><a name="oncontinue"></a>CAtlServiceModuleT::Pokračování

Přepsat tuto metodu pokračovat ve službě.

```cpp
void OnContinue() throw();
```

## <a name="catlservicemoduletoninterrogate"></a><a name="oninterrogate"></a>CAtlServiceModuleT::OnInterrogate

Přepsat tuto metodu k dotazování služby.

```cpp
void OnInterrogate() throw();
```

## <a name="catlservicemoduletonpause"></a><a name="onpause"></a>CAtlServiceModuleT::OnPause

Přepsat tuto metodu pozastavit službu.

```cpp
void OnPause() throw();
```

## <a name="catlservicemoduletonshutdown"></a><a name="onshutdown"></a>CAtlServiceModuleT::OnShutdown

Přepsat tuto metodu vypnout službu.

```cpp
void OnShutdown() throw();
```

## <a name="catlservicemoduletonstop"></a><a name="onstop"></a>CAtlServiceModuleT::OnStop

Přepsat tuto metodu zastavit službu.

```cpp
void OnStop() throw();
```

## <a name="catlservicemoduletonunknownrequest"></a><a name="onunknownrequest"></a>CAtlServiceModuleT::OnUnknownRequest

Přepsat tuto metodu pro zpracování neznámých požadavků na službu.

```cpp
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Vyhrazeno.

## <a name="catlservicemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlServiceModuleT::ParseCommandLine

Analyzuje příkazový řádek a v případě potřeby provede registraci.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Příkazový řádek.

*pnRetCode*<br/>
HRESULT odpovídající registraci (pokud k ní došlo).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true na úspěch nebo false, pokud nelze zaregistrovat soubor RGS zadaný v příkazovém řádku.

### <a name="remarks"></a>Poznámky

Analyzuje příkazový řádek a v případě potřeby zaregistruje nebo zruší registraci zadaného souboru RGS. Tato metoda volá [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) ke kontrole **/RegServer** a **/UnregServer**. Přidání **argumentu -/Service** zaregistruje službu.

## <a name="catlservicemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlServiceModuleT::PreMessageLoop

Tato metoda je volána bezprostředně před vstupem do smyčky zpráv.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Tento parametr je předán [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a přidejte vlastní inicializační kód pro službu.

## <a name="catlservicemoduletregisterappid"></a><a name="registerappid"></a>CAtlServiceModuleT::RegisterAppId

Zaregistruje službu v registru.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parametry

*bSlužba*<br/>
Musí být pravda, zaregistrovat se jako služba.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlservicemoduletrun"></a><a name="run"></a>CAtlServiceModuleT::Spustit

Spustí službu.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) Výchozí hodnota je SW_HIDE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Po volání `Run` volání [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)a [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

## <a name="catlservicemoduletservicemain"></a><a name="servicemain"></a>CAtlServiceModuleT::ServiceMain

Tato metoda je volána správcem řízení služeb.

```cpp
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parametry

*dwArgc řekl:*<br/>
Argc argument.

*lpszArgv*<br/>
Argv argument.

### <a name="remarks"></a>Poznámky

Správce řízení služeb (SCM) volá `ServiceMain` při otevření aplikace Služby v Ovládacích panelech, vyberte službu a klepněte na tlačítko Start.

Po volání `ServiceMain`SCM musí služba poskytnout funkci obslužné rutiny SCM. Tato funkce umožňuje SCM získat stav služby a předat konkrétní pokyny (například pozastavení nebo zastavení). Následně [CAtlServiceModuleT::Run](#run) je volána k provedení hlavní práce služby. `Run`pokračuje v provádění, dokud není služba zastavena.

## <a name="catlservicemoduletsetservicestatus"></a><a name="setservicestatus"></a>CAtlServiceModuleT::SetServiceStatus

Tato metoda aktualizuje stav služby.

```cpp
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parametry

*dwState*<br/>
Nový stav. Možné hodnoty naleznete v [tématu SetServiceStatus.](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)

### <a name="remarks"></a>Poznámky

Aktualizuje informace o stavu správce řízení služeb pro službu. Nazývá se [CAtlServiceModuleT::Run](#run), [CAtlServiceModuleT::ServiceMain](#servicemain) a další mislovací metody. Stav je také uložen v členské proměnné [CAtlServiceModuleT::m_status](#m_status).

## <a name="catlservicemoduletstart"></a><a name="start"></a>CAtlServiceModuleT::Start

Volána `CAtlServiceModuleT::WinMain` při spuštění služby.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[Metoda CAtlServiceModuleT::WinMain](#winmain) zpracovává registraci i instalaci, stejně jako úkoly spojené s odebráním položek registru a odinstalací modulu. Při spuštění služby `WinMain` `Start`volání .

## <a name="catlservicemoduletuninstall"></a><a name="uninstall"></a>CAtlServiceModuleT::Odinstalace

Zastaví a odebere službu.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Zastaví spuštění služby a odebere ji z databáze Správce řízení služeb.

## <a name="catlservicemoduletunlock"></a><a name="unlock"></a>CAtlServiceModuleT::Odemknout

Sníží počet zámků služby.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet zámků, což může být užitečné pro diagnostiku a ladění.

## <a name="catlservicemoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlServiceModuleT::Zrušení registrace Id

Odebere službu z registru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlservicemoduletwinmain"></a><a name="winmain"></a>CAtlServiceModuleT::WinMain

Tato metoda implementuje kód potřebný ke spuštění služby.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Návratová hodnota

Vrátí vrácenou hodnotu služby.

### <a name="remarks"></a>Poznámky

Tato metoda zpracuje příkazový řádek (s [CAtlServiceModuleT::ParseCommandLine)](#parsecommandline)a poté spustí službu (pomocí [CAtlServiceModuleT::Start).](#start)

## <a name="see-also"></a>Viz také

[Třída CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
