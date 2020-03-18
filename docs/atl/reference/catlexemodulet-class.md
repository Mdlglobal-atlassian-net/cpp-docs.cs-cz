---
title: CAtlExeModuleT – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: d37cc8e97d29cbedfeb4ba79502d44529485399f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418053"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT – třída

Tato třída reprezentuje modul pro aplikaci.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída je odvozena z `CAtlExeModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicializuje model COM.|
|[CAtlExeModuleT::P arseCommandLine](#parsecommandline)|Analyzuje příkazový řádek a v případě potřeby provede registraci.|
|[CAtlExeModuleT::P ostMessageLoop](#postmessageloop)|Tato metoda se volá hned po ukončení smyčky zpráv.|
|[CAtlExeModuleT::P reMessageLoop](#premessageloop)|Tato metoda se volá bezprostředně před vstupem do smyčky zpráv.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Zaregistruje objekt třídy.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odvolá objekt třídy.|
|[CAtlExeModuleT:: Run](#run)|Tato metoda spustí kód v modulu EXE k inicializaci, spuštění smyčky zpráv a vyčištění.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Tato metoda spustí smyčku zpráv.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Zruší inicializaci modelu COM.|
|[CAtlExeModuleT:: Unlock](#unlock)|Sníží počet zámků modulu.|
|[CAtlExeModuleT:: WinMain](#winmain)|Tato metoda implementuje kód potřebný ke spuštění souboru EXE.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown)|Příznak označující, že by mělo být zpoždění vypíná modul.|
|[CAtlExeModuleT:: m_dwPause](#m_dwpause)|Hodnota pozastavení používaná k zajištění uvolnění všech objektů před vypnutím.|
|[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)|Hodnota časového limitu používaná k zpožděné odložení modulu.|

## <a name="remarks"></a>Poznámky

`CAtlExeModuleT` představuje modul pro aplikaci (EXE) a obsahuje kód, který podporuje vytvoření souboru EXE, zpracování příkazového řádku, registraci objektů třídy, spuštění smyčky zpráv a vyčištění při ukončení.

Tato třída je navržena pro zlepšení výkonu při průběžném vytváření a zničení objektů COM v serveru EXE. Po uvolnění posledního objektu COM bude EXE čekat po dobu určenou datovým členem [CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout) . Pokud během této doby neexistují žádné aktivity (to znamená, že se nevytvoří žádné objekty COM), proces vypnutí se iniciuje.

Datový člen [CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown) je příznak sloužící k určení, zda má exe použít výše definovaný mechanismus. Pokud je nastavené na false, modul se okamžitě ukončí.

Další informace o modulech v knihovně ATL naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

Konstruktor

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Pokud nelze modul EXE inicializovat, aplikace WinMain bude okamžitě vrácena bez dalšího zpracování.

##  <a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT

Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="initializecom"></a>CAtlExeModuleT::InitializeCom

Inicializuje model COM.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda je volána z konstruktoru a lze ji přepsat pro inicializaci modelu COM způsobem odlišnou od výchozí implementace. Výchozí implementace buď volá `CoInitializeEx(NULL, COINIT_MULTITHREADED)` nebo `CoInitialize(NULL)` v závislosti na konfiguraci projektu.

Přepsání této metody obvykle vyžaduje přepsání [CAtlExeModuleT:: UninitializeCom](#uninitializecom).

##  <a name="m_bdelayshutdown"></a>CAtlExeModuleT:: m_bDelayShutdown

Příznak označující, že by mělo být zpoždění vypíná modul.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [přehledu CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) .

##  <a name="m_dwpause"></a>CAtlExeModuleT:: m_dwPause

Hodnota pozastavení, která slouží k zajištění, že všechny objekty budou před vypnutím ztraceny.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Poznámky

Po volání metody [CAtlExeModuleT:: InitializeCom](#initializecom) nastavte počet milisekund, které se použijí jako hodnota pozastavení pro vypnutí serveru. Výchozí hodnota je 1000 milisekund.

##  <a name="m_dwtimeout"></a>CAtlExeModuleT:: m_dwTimeOut

Hodnota časového limitu používaná k zpožděné odložení modulu.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu změňte po volání metody [CAtlExeModuleT:: InitializeCom](#initializecom) a definujte počet milisekund používaných jako hodnotu časového limitu pro vypnutí serveru. Výchozí hodnota je 5000 milisekund. Další podrobnosti najdete v tématu [CAtlExeModuleT Overview](../../atl/reference/catlexemodulet-class.md) .

##  <a name="parsecommandline"></a>CAtlExeModuleT::P arseCommandLine

Analyzuje příkazový řádek a v případě potřeby provede registraci.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Příkazový řádek předaný aplikaci.

*pnRetCode*<br/>
Hodnota HRESULT odpovídající registraci (Pokud byla provedena).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud by měla aplikace dál běžet, jinak false.

### <a name="remarks"></a>Poznámky

Tato metoda je volána z [CAtlExeModuleT:: WinMain](#winmain) a lze ji přepsat pro zpracování přepínačů příkazového řádku. Výchozí implementace provádí pro argumenty příkazového řádku **/regserver** a **přepínačem/Unregserver** a provádí registraci nebo zrušení registrace.

##  <a name="postmessageloop"></a>CAtlExeModuleT::P ostMessageLoop

Tato metoda se volá hned po ukončení smyčky zpráv.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, aby se prováděla vlastní vyčištění aplikace. Výchozí implementace volá [CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects).

##  <a name="premessageloop"></a>CAtlExeModuleT::P reMessageLoop

Tato metoda se volá bezprostředně před vstupem do smyčky zpráv.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Hodnota předaná jako parametr *nShowCmd* v metodě WinMain.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete přidat vlastní inicializační kód pro aplikaci. Výchozí implementace registruje objekty třídy.

##  <a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Zaregistruje objekt třídy pomocí technologie OLE, aby se k ní mohli připojit jiné aplikace.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
Určuje kontext, ve kterém má být objekt třídy spuštěn. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu, S_FALSE Pokud nebyly nalezeny žádné třídy k registraci, nebo došlo k chybě HRESULT při selhání.

##  <a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Odebere objekt třídy.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu, S_FALSE Pokud nebyly nalezeny žádné třídy k registraci, nebo došlo k chybě HRESULT při selhání.

##  <a name="run"></a>CAtlExeModuleT:: Run

Tato metoda spustí kód v modulu EXE k inicializaci, spuštění smyčky zpráv a vyčištění.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) . Výchozí hodnota je SW_HIDE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tuto metodu lze přepsat. Nicméně v praxi je lepší přepsat [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT:: RunMessageLoop](#runmessageloop)nebo CAtlExeModuleT: místo toho [:P ostmessageloop](#postmessageloop) .

##  <a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Tato metoda spustí smyčku zpráv.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Poznámky

Tuto metodu lze přepsat, chcete-li změnit chování smyčky zpráv.

##  <a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom

Zruší inicializaci modelu COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda jednoduše volá [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) a je volána z destruktoru. Tuto metodu přepište, pokud přepíšete [CAtlExeModuleT:: InitializeCom](#initializecom).

##  <a name="unlock"></a>CAtlExeModuleT:: Unlock

Sníží počet zámků modulu.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

##  <a name="winmain"></a>CAtlExeModuleT:: WinMain

Tato metoda implementuje kód potřebný ke spuštění souboru EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nShowCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain](/windows/win32/api/winbase/nf-winbase-winmain) .

### <a name="return-value"></a>Návratová hodnota

Vrátí návratovou hodnotu spustitelného souboru.

### <a name="remarks"></a>Poznámky

Tuto metodu lze přepsat. Pokud přepisujete [CAtlExeModuleT::P remessageloop](#premessageloop), [CAtlExeModuleT::P ostmessageloop](#postmessageloop)nebo [CAtlExeModuleT:: RunMessageLoop](#runmessageloop) neposkytuje dostatečnou flexibilitu, je možné přepsat funkci `WinMain` pomocí této metody.

## <a name="see-also"></a>Viz také

[Ukázka ATLDuck](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT – třída](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT – třída](../../atl/reference/catldllmodulet-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
