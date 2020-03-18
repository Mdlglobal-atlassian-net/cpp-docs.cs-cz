---
title: CAtlServiceModuleT – třída
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
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418032"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT – třída

Tato třída implementuje službu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída je odvozena z `CAtlServiceModuleT`.

*nServiceNameID*<br/>
Identifikátor prostředku služby.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT:: CAtlServiceModuleT](#catlservicemodulet)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT:: Handler](#handler)|Rutina obslužné rutiny pro službu.|
|[CAtlServiceModuleT:: InitializeSecurity](#initializesecurity)|Poskytuje výchozí nastavení zabezpečení pro službu.|
|[CAtlServiceModuleT:: Install](#install)|Nainstaluje a vytvoří službu.|
|[CAtlServiceModuleT:: IsInstalled](#isinstalled)|Potvrdí, že služba je nainstalovaná.|
|[CAtlServiceModuleT:: LogEvent](#logevent)|Zapisuje do protokolu událostí.|
|[CAtlServiceModuleT::-Continue](#oncontinue)|Přepsáním této metody pokračujte v této službě.|
|[CAtlServiceModuleT:: OnInterrogate](#oninterrogate)|Přepsáním této metody dotazování službu.|
|[CAtlServiceModuleT:: pozastaveno](#onpause)|Potlačením této metody pozastavíte službu.|
|[CAtlServiceModuleT:: deshutdown](#onshutdown)|Přepsat tuto metodu pro vypnutí služby|
|[CAtlServiceModuleT:: instop](#onstop)|Přepsáním této metody zastavíte službu.|
|[CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest)|Přepsat tuto metodu pro zpracování neznámých požadavků na službu|
|[CAtlServiceModuleT::P arseCommandLine](#parsecommandline)|Analyzuje příkazový řádek a v případě potřeby provede registraci.|
|[CAtlServiceModuleT::P reMessageLoop](#premessageloop)|Tato metoda se volá bezprostředně před vstupem do smyčky zpráv.|
|[CAtlServiceModuleT:: RegisterAppId](#registerappid)|Zaregistruje službu v registru.|
|[CAtlServiceModuleT:: Run](#run)|Spustí službu.|
|[CAtlServiceModuleT:: ServiceMain](#servicemain)|Metoda, kterou volá správce řízení služeb.|
|[CAtlServiceModuleT:: SetServiceStatus](#setservicestatus)|Aktualizuje stav služby.|
|[CAtlServiceModuleT:: Start](#start)|Volá se při spuštění služby `CAtlServiceModuleT::WinMain`.|
|[CAtlServiceModuleT:: Uninstall](#uninstall)|Zastaví a odebere službu.|
|[CAtlServiceModuleT:: Unlock](#unlock)|Sníží počet zámků služby.|
|[CAtlServiceModuleT:: UnregisterAppId](#unregisterappid)|Odebere službu z registru.|
|[CAtlServiceModuleT:: WinMain](#winmain)|Tato metoda implementuje kód potřebný ke spuštění služby.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT:: m_bService](#m_bservice)|Příznak označující, že program je spuštěný jako služba.|
|[CAtlServiceModuleT:: m_dwThreadID](#m_dwthreadid)|Členský proměnná, která ukládá identifikátor vlákna|
|[CAtlServiceModuleT:: m_hServiceStatus](#m_hservicestatus)|Členská proměnná, která ukládá popisovač do struktury informací o stavu pro aktuální službu.|
|[CAtlServiceModuleT:: m_status](#m_status)|Členská proměnná, která ukládá strukturu stavových informací pro aktuální službu.|
|[CAtlServiceModuleT:: m_szServiceName](#m_szservicename)|Název zaregistrované služby.|

## <a name="remarks"></a>Poznámky

`CAtlServiceModuleT`odvozená z [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)implementuje modul ATL Service. `CAtlServiceModuleT` poskytuje metody pro zpracování, instalaci, registraci a odebrání příkazového řádku. Pokud je potřeba další funkce, můžete tyto a další metody přepsat.

Tato třída nahrazuje zastaralou [třídu CComModule](../../atl/reference/ccommodule-class.md) , která se používá v dřívějších verzích knihovny ATL. Další podrobnosti naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="catlservicemodulet"></a>CAtlServiceModuleT:: CAtlServiceModuleT

Konstruktor

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a nastaví počáteční stav služby.

##  <a name="handler"></a>CAtlServiceModuleT:: Handler

Rutina obslužné rutiny pro službu.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Přepínač, který definuje operaci obslužné rutiny. Podrobnosti najdete v komentářích.

### <a name="remarks"></a>Poznámky

Toto je kód, který zavolá správce řízení služeb (SCM), aby načetl stav služby a pokyny pro vydání, jako je zastavení nebo pozastavení. Správce řízení předává kód operace, který je zobrazen níže, k `Handler` k určení toho, co by měla služba dělat.

|Kód operace|Význam|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Zastaví službu. Chcete-li změnit chování, přepište metodu [CAtlServiceModuleT::-stop](#onstop) v atlbase. h.|
|SERVICE_CONTROL_PAUSE|Implementováno uživatelem. Potlačením prázdné metody [CAtlServiceModuleT:: Pause](#onpause) v atlbase. h službu pozastavíte.|
|SERVICE_CONTROL_CONTINUE|Implementováno uživatelem. Chcete-li pokračovat v této službě, přepište prázdnou metodu [CAtlServiceModuleT::-Continue](#oncontinue) v atlbase. h.|
|SERVICE_CONTROL_INTERROGATE|Implementováno uživatelem. Přepište prázdnou metodu [CAtlServiceModuleT:: OnInterrogate](#oninterrogate) v atlbase. h pro dotazování služby.|
|SERVICE_CONTROL_SHUTDOWN|Implementováno uživatelem. Pro vypnutí služby popište prázdnou metodu [CAtlServiceModuleT:: deshutdown](#onshutdown) v atlbase. h.|

Pokud kód operace není rozpoznán, je volána metoda [CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest) .

Výchozí služba generovaná pomocí ATL zpracovává pouze instrukce stop. Pokud správce řízení předá pokyn k zastavení, služba oznámí službě SCM, že program se chystá zastavit. Služba potom zavolá `PostThreadMessage` pro odeslání zprávy o ukončení do sebe samé. Tím se ukončí smyčka zpráv a služba se nakonec zavře.

##  <a name="initializesecurity"></a>CAtlServiceModuleT:: InitializeSecurity

Poskytuje výchozí nastavení zabezpečení pro službu.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Libovolná třída, která je odvozena z `CAtlServiceModuleT` musí implementovat tuto metodu v odvozené třídě.

Při volání `CoInitializeSecurity`použijte ověřování na úrovni PKT, úroveň zosobnění RPC_C_IMP_LEVEL_IDENTIFY a odpovídající popisovač zabezpečení, který není null.

Pro neatributové projekty generované průvodcem, by to bylo

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Pro projekty s atributem Service by to bylo v

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>CAtlServiceModuleT:: Install

Nainstaluje a vytvoří službu.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Nainstaluje službu do databáze správce řízení služeb (SCM) a pak vytvoří objekt služby. Pokud službu nebylo možné vytvořit, zobrazí se okno se zprávou a metoda vrátí hodnotu FALSE.

##  <a name="isinstalled"></a>CAtlServiceModuleT:: IsInstalled

Potvrdí, že služba je nainstalovaná.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud je služba nainstalována, jinak FALSE.

##  <a name="logevent"></a>CAtlServiceModuleT:: LogEvent

Zapisuje do protokolu událostí.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec, který se má zapsat do protokolu událostí.

*...*<br/>
Volitelné dodatečné řetězce, které mají být zapsány do protokolu událostí.

### <a name="remarks"></a>Poznámky

Tato metoda zapisuje podrobnosti do protokolu událostí pomocí funkce [ReportEvent](/windows/win32/api/winbase/nf-winbase-reporteventw). Pokud žádná služba není spuštěná, pošle se řetězec do konzoly.

##  <a name="m_bservice"></a>CAtlServiceModuleT:: m_bService

Příznak označující, že program je spuštěný jako služba.

```
BOOL m_bService;
```

### <a name="remarks"></a>Poznámky

Slouží k odlišení EXE služby od aplikace EXE.

##  <a name="m_dwthreadid"></a>CAtlServiceModuleT:: m_dwThreadID

Členský proměnná, která ukládá identifikátor vlákna služby.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Poznámky

Tato proměnná ukládá identifikátor vlákna aktuálního vlákna.

##  <a name="m_hservicestatus"></a>CAtlServiceModuleT:: m_hServiceStatus

Členská proměnná, která ukládá popisovač do struktury informací o stavu pro aktuální službu.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Poznámky

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) obsahuje informace o službě.

##  <a name="m_status"></a>CAtlServiceModuleT:: m_status

Členská proměnná, která ukládá strukturu stavových informací pro aktuální službu.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Poznámky

Struktura [SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status) obsahuje informace o službě.

##  <a name="m_szservicename"></a>CAtlServiceModuleT:: m_szServiceName

Název zaregistrované služby.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Poznámky

Řetězec zakončený hodnotou null, který ukládá název služby.

##  <a name="oncontinue"></a>CAtlServiceModuleT::-Continue

Přepsáním této metody pokračujte v této službě.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>CAtlServiceModuleT:: OnInterrogate

Přepsáním této metody dotazování službu.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>CAtlServiceModuleT:: pozastaveno

Potlačením této metody pozastavíte službu.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>CAtlServiceModuleT:: deshutdown

Tuto metodu přepište, pokud chcete službu vypnout.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>CAtlServiceModuleT:: instop

Tuto metodu přepište, pokud chcete zastavit službu.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>CAtlServiceModuleT:: OnUnknownRequest

Přepsat tuto metodu pro zpracování neznámých požadavků na službu.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Rezervovaný.

##  <a name="parsecommandline"></a>CAtlServiceModuleT::P arseCommandLine

Analyzuje příkazový řádek a v případě potřeby provede registraci.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Příkazový řádek.

*pnRetCode*<br/>
Hodnota HRESULT odpovídající registraci (Pokud byla provedena).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true při úspěchu, nebo false, pokud se soubor RGS dodaný do příkazového řádku nepovedlo zaregistrovat.

### <a name="remarks"></a>Poznámky

Analyzuje příkazový řádek a registruje nebo zruší registraci zadaného souboru RGS v případě potřeby. Tato metoda volá [CAtlExeModuleT::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline) pro kontrolu **/regserver** a **přepínačem/Unregserver**. Přidání argumentu **-/Service** provede registraci služby.

##  <a name="premessageloop"></a>CAtlServiceModuleT::P reMessageLoop

Tato metoda se volá bezprostředně před vstupem do smyčky zpráv.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Tento parametr je předán do [CAtlExeModuleT::P remessageloop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete přidat vlastní inicializační kód pro službu.

##  <a name="registerappid"></a>CAtlServiceModuleT:: RegisterAppId

Zaregistruje službu v registru.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parametry

*bService*<br/>
Pro registraci jako službu musí být true.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="run"></a>CAtlServiceModuleT:: Run

Spustí službu.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . Výchozí hodnota je SW_HIDE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Po zavolání `Run` volá [CAtlServiceModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)a [CAtlExeModuleT::P ostmessageloop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>CAtlServiceModuleT:: ServiceMain

Tuto metodu volá správce řízení služeb.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parametry

*dwArgc*<br/>
Argument argc

*lpszArgv*<br/>
Argument argv

### <a name="remarks"></a>Poznámky

Volání správce řízení služeb (SCM) `ServiceMain` při otevření aplikace služby v Ovládacích panelech vyberte službu a klikněte na tlačítko Spustit.

Poté, co správce řízení volání `ServiceMain`, musí poskytovat funkci SCM a obslužné rutiny. Tato funkce umožňuje SCM získat stav služby a předat konkrétní pokyny (například pozastavení nebo zastavení). Následně se volá [CAtlServiceModuleT:: Run](#run) , aby se prováděla hlavní práce služby. `Run` pokračovat, dokud se služba nezastaví.

##  <a name="setservicestatus"></a>CAtlServiceModuleT:: SetServiceStatus

Tato metoda aktualizuje stav služby.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parametry

*dwState*<br/>
Nový stav. Možné hodnoty najdete v tématu [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus) .

### <a name="remarks"></a>Poznámky

Aktualizuje informace o stavu správce řízení služeb pro danou službu. Je volána pomocí [CAtlServiceModuleT:: Run](#run), [CAtlServiceModuleT:: ServiceMain](#servicemain) a dalších metod obslužných rutin. Stav je také uložen v členské proměnné [CAtlServiceModuleT:: m_status](#m_status).

##  <a name="start"></a>CAtlServiceModuleT:: Start

Volá se při spuštění služby `CAtlServiceModuleT::WinMain`.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Metoda [CAtlServiceModuleT:: WinMain](#winmain) zpracovává registraci i instalaci i úlohy, které se týkají odebírání položek registru a odinstalování modulu. Při spuštění služby `WinMain` volání `Start`.

##  <a name="uninstall"></a>CAtlServiceModuleT:: Uninstall

Zastaví a odebere službu.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Zastaví spouštění služby a odebere je z databáze správce řízení služeb.

##  <a name="unlock"></a>CAtlServiceModuleT:: Unlock

Sníží počet zámků služby.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet zámků, který může být užitečný pro diagnostiku a ladění.

##  <a name="unregisterappid"></a>CAtlServiceModuleT:: UnregisterAppId

Odebere službu z registru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="winmain"></a>CAtlServiceModuleT:: WinMain

Tato metoda implementuje kód potřebný ke spuštění služby.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Návratová hodnota

Vrátí návratovou hodnotu služby.

### <a name="remarks"></a>Poznámky

Tato metoda zpracuje příkazový řádek (s [CAtlServiceModuleT::P arsecommandline](#parsecommandline)) a potom službu spustí (pomocí [CAtlServiceModuleT:: Start](#start)).

## <a name="see-also"></a>Viz také

[CAtlExeModuleT – třída](../../atl/reference/catlexemodulet-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
