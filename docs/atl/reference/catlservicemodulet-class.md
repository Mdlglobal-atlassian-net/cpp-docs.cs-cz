---
title: CAtlServiceModuleT Class
ms.date: 11/04/2016
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
ms.openlocfilehash: ad682980fbc885d79598b41a5dcc094bb65db8cf
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893532"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT Class

Tato třída implementuje služby.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `CAtlServiceModuleT`.

*nServiceNameID*<br/>
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
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|Potvrdí, že je nainstalovaná služba.|
|[CAtlServiceModuleT::LogEvent](#logevent)|Zapíše do protokolu událostí.|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|Potlačí tuto metodu za účelem pokračování služby.|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|Potlačí tuto metodu k dotazování služby.|
|[CAtlServiceModuleT::OnPause](#onpause)|Potlačí tuto metodu za účelem pozastavení služby.|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|Potlačí tuto metodu za účelem vypnutí služby|
|[CAtlServiceModuleT::OnStop](#onstop)|Potlačí tuto metodu k zastavení služby|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|Potlačí tuto metodu za účelem zpracovat Neznámý požadavky na službu|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|Analyzuje příkazového řádku a provádí registraci v případě potřeby.|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|Tato metoda je volána těsně před zadáním smyčky zpráv.|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|Registruje službu v registru.|
|[CAtlServiceModuleT::Run](#run)|Spouští službu.|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|Metoda ve správci řízení služeb.|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|Aktualizuje stav služby.|
|[CAtlServiceModuleT::Start](#start)|Volané `CAtlServiceModuleT::WinMain` při spuštění služby.|
|[CAtlServiceModuleT::Uninstall](#uninstall)|Zastaví a odebere službu.|
|[CAtlServiceModuleT::Unlock](#unlock)|Dekrementuje počet zámků služby.|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|Odebere službu z registru.|
|[CAtlServiceModuleT::WinMain](#winmain)|Tato metoda implementuje je kód potřebný ke spuštění služby.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|Příznak označující, že je program spuštěn jako služba.|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|Členské proměnné ukládání identifikátor vlákna.|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|Členské proměnné ukládání popisovač struktura informací o stavu pro aktuální službu.|
|[CAtlServiceModuleT::m_status](#m_status)|Členské proměnné ukládání struktura informací o stavu pro aktuální službu.|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|Název služby registrována.|

## <a name="remarks"></a>Poznámky

`CAtlServiceModuleT`, odvozený z [catlexemodulet –](../../atl/reference/catlexemodulet-class.md), implementuje modul knihovny ATL služby. `CAtlServiceModuleT` poskytuje metody pro zpracování příkazového řádku, instalaci, registrace a odebrání. Pokud je potřeba další funkce, lze přepsat tyto a další metody.

Nahradí tato třída zastaralá [ccommodule – třída](../../atl/reference/ccommodule-class.md) použité v dřívějších verzích ATL. Zobrazit [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

Konstruktor

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a nastaví stav počáteční služby.

##  <a name="handler"></a>  Catlservicemodulet::Handler –

Rutina obslužné rutiny pro službu.

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Přepínač, který definuje operaci obslužné rutiny. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Toto je kód, který Pokud chcete načíst stav služby a problém pokyny, jako je zastavení nebo pozastavení volá správce řízení služeb (SCM). SCM předává kód operace, je uvedeno níže, k `Handler` k označení toho, co služba dělat.

|Operační kód|Význam|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|Zastaví službu. Přepsání metody [CAtlServiceModuleT::OnStop](#onstop) v atlbase.h ke změně chování.|
|SERVICE_CONTROL_PAUSE|Uživatel implementována. Přepište metodu prázdný [CAtlServiceModuleT::OnPause](#onpause) v atlbase.h na pozastavení služby.|
|SERVICE_CONTROL_CONTINUE|Uživatel implementována. Přepište metodu prázdný [CAtlServiceModuleT::OnContinue](#oncontinue) v atlbase.h na pokračování služby.|
|SERVICE_CONTROL_INTERROGATE|Uživatel implementována. Přepište metodu prázdný [CAtlServiceModuleT::OnInterrogate](#oninterrogate) v atlbase.h k dotazování služby.|
|SERVICE_CONTROL_SHUTDOWN|Uživatel implementována. Přepište metodu prázdný [CAtlServiceModuleT::OnShutdown](#onshutdown) v atlbase.h na ukončení služby.|

Pokud operační kód není rozpoznána, metoda [CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest) je volána.

Výchozí generovaný ATL služba zpracovává pouze instrukce stop. V případě úspěšného SCM instrukce stop, říká službě SCM, program se chystá ukončit. Pak zavolá služba `PostThreadMessage` pro zprávy o ukončení na sebe sama. To ukončí smyčku zpráv a služby se nakonec zavře.

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

Poskytuje výchozí nastavení zabezpečení pro službu.

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

V aplikaci Visual Studio .NET 2003 tato metoda není implementována v základní třídě. Průvodce projektem Visual Studio obsahuje tuto metodu ve vygenerovaném kódu, ale chybu kompilace dojde, pokud projekt vytvořený v předchozích verzích Visual C++ je zkompilován pomocí knihovny ATL 7.1. Všechny třídy, která je odvozena z `CAtlServiceModuleT` musí tuto metodu implementovat v odvozené třídě.

Použít ověřování úrovni PKT, úroveň zosobnění rpc_c_imp_level_identify a popisovač zabezpečení jinou hodnotu než null při volání funkce `CoInitializeSecurity`.

Pro projekty generované v Průvodci bez atributové služeb to může být v

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

Pro projekty služeb s atributy jde v

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

Nainstaluje a vytvoří službu.

```
BOOL Install() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Nainstaluje službu do databáze nástroje Správce řízení služeb (SCM) a potom vytvoří objekt služby. Pokud službu nebylo možné vytvořit, zobrazí se okno se zprávou a metoda vrátí hodnotu FALSE.

##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled

Potvrdí, že je nainstalovaná služba.

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud služba není nainstalovaná, FALSE, jinak.

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

Zapíše do protokolu událostí.

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězce pro zápis do protokolu událostí.

*...*<br/>
Volitelné další řetězců, které mají být zapsané do protokolu událostí.

### <a name="remarks"></a>Poznámky

Tato metoda zapíše podrobnosti do protokolu událostí, pomocí funkce [ReportEvent](/windows/desktop/api/winbase/nf-winbase-reporteventa). Pokud žádná služba běží, řetězec je odeslána do konzoly.

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

Příznak označující, že je program spuštěn jako služba.

```
BOOL m_bService;
```

### <a name="remarks"></a>Poznámky

Použít k rozlišení EXE služby z aplikace EXE.

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

Členské proměnné ukládání identifikátor služby.

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Poznámky

Tato proměnná ukládá identifikátor aktuálního vlákna.

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

Členské proměnné ukládání popisovač struktura informací o stavu pro aktuální službu.

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Poznámky

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) struktura obsahuje informace o službě.

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

Členské proměnné ukládání struktura informací o stavu pro aktuální službu.

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Poznámky

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status) struktura obsahuje informace o službě.

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

Název služby registrována.

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Poznámky

Řetězec zakončený hodnotou null, která ukládá název služby.

##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue

Potlačí tuto metodu za účelem pokračování služby.

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

Potlačí tuto metodu k dotazování služby.

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

Potlačí tuto metodu za účelem pozastavení služby.

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

Potlačí tuto metodu k vypnutí služby.

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

Potlačí tuto metodu za účelem zastavení služby.

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

Potlačí tuto metodu za účelem zpracovat Neznámý požadavky na službu.

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>Parametry

*dwOpcode*<br/>
Vyhrazená.

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

Analyzuje příkazového řádku a provádí registraci v případě potřeby.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Příkazový řádek.

*pnRetCode*<br/>
Hodnota HRESULT odpovídající registraci (Pokud se uskutečnilo).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true na úspěch, nebo false, pokud nebylo možné zaregistrovat soubor RGS zadané na příkazovém řádku.

### <a name="remarks"></a>Poznámky

Analyzuje příkazového řádku a zaregistruje nebo zruší registraci zadaného souboru RGS v případě potřeby. Tato metoda volá [CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline) ke kontrole **/regserver** a **Unregserver**. Přidání argumentu **– / Service** k registraci služby.

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

Tato metoda je volána těsně před zadáním smyčky zpráv.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Tento parametr je předán [CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přepsáním této metody můžete přidat vlastní inicializační kód pro službu.

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

Registruje službu v registru.

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>Parametry

*bService*<br/>
Musí být pravda, pokud chcete zaregistrovat jako služba.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="run"></a>  Catlservicemodulet::Run –

Spouští službu.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje, jak má být zobrazen v okně. Tento parametr může být jedna z hodnot podrobněji popsána [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) oddílu. Výchozí hodnota je SW_HIDE.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Po volání, `Run` volání [CAtlServiceModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop), a [CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  Catlservicemodulet::servicemain –

Tato metoda je volána pomocí Správce řízení služeb.

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>Parametry

*dwArgc*<br/>
Argc – argument.

*lpszArgv*<br/>
Argv – argument.

### <a name="remarks"></a>Poznámky

Volá správce řízení služeb (SCM) `ServiceMain` při otevření aplikace služby v Ovládacích panelech vyberte službu a klikněte na spustit.

Po SCM volá `ServiceMain`, služba musí poskytnout SCM funkci obslužné rutiny. Tato funkce umožňuje SCM získání stavu služby a předat konkrétní pokyny (jako je například pozastavení nebo ukončení). Následně [catlservicemodulet::Run –](#run) je volána k provedení hlavní služby. `Run` pokračuje v provádění, dokud se tato služba zastavená.

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

Tato metoda aktualizuje stav služby.

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>Parametry

*dwState*<br/>
Nový stav. Zobrazit [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) možných hodnot.

### <a name="remarks"></a>Poznámky

Aktualizuje informace o službě stavu Správce řízení služeb. Je volána metodou [catlservicemodulet::Run –](#run), [catlservicemodulet::servicemain –](#servicemain) a jiné metody obslužné rutiny. Stav je také uložen v proměnné člena [CAtlServiceModuleT::m_status](#m_status).

##  <a name="start"></a>  Catlservicemodulet::Start –

Volané `CAtlServiceModuleT::WinMain` při spuštění služby.

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje, jak má být zobrazen v okně. Tento parametr může být jedna z hodnot podrobněji popsána [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) oddílu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

[CAtlServiceModuleT::WinMain](#winmain) metody se stará o registraci a instalaci, stejně jako úkoly součástí odebrání položky registru a odinstalace modulu. Když je služba spuštěna, `WinMain` volání `Start`.

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

Zastaví a odebere službu.

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Zastaví službu spouštění a odstraní ji z databáze správce řízení služeb.

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

Dekrementuje počet zámků služby.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací počet zámků, což může být užitečné pro diagnostiku a ladění.

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

Odebere službu z registru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

Tato metoda implementuje je kód potřebný ke spuštění služby.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje, jak má být zobrazen v okně. Tento parametr může být jedna z hodnot podrobněji popsána [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain) oddílu.

### <a name="return-value"></a>Návratová hodnota

Vrátí služby návratovou hodnotu.

### <a name="remarks"></a>Poznámky

Tato metoda zpracovává příkazového řádku (s [CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) a pak spustí službu (pomocí [catlservicemodulet::Start –](#start)).

## <a name="see-also"></a>Viz také

[CAtlExeModuleT – třída](../../atl/reference/catlexemodulet-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
