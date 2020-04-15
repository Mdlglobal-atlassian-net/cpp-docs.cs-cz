---
title: Třída CAtlExeModuleT
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
ms.openlocfilehash: a20a02a467d74a89e3cda176a6a15961be4ffd61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318990"
---
# <a name="catlexemodulet-class"></a>Třída CAtlExeModuleT

Tato třída představuje modul pro aplikaci.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozená z `CAtlExeModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor|
|[CAtlExeModuleT::~CAtlExeModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicializuje kom.|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analyzuje příkazový řádek a v případě potřeby provede registraci.|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Tato metoda je volána bezprostředně po ukončení smyčky zpráv.|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Tato metoda je volána bezprostředně před vstupem do smyčky zpráv.|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Registruje objekt třídy.|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odvolá objekt třídy.|
|[CAtlExeModuleT::Spustit](#run)|Tato metoda spustí kód v modulu EXE pro inicializaci, spuštění smyčky zpráv a vyčištění.|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Tato metoda spustí smyčku zpráv.|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Uninitializes COM.|
|[CAtlExeModuleT::Odemknout](#unlock)|Sníží počet zámků modulu.|
|[CAtlExeModuleT::WinMain](#winmain)|Tato metoda implementuje kód potřebný ke spuštění EXE.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Příznak označující, že by mělo dojít ke zpoždění vypnutí modulu.|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Hodnota pozastavení slouží k zajištění všech objektů jsou uvolněny před vypnutím.|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Hodnota časového času slouží ke zpoždění uvolnění modulu.|

## <a name="remarks"></a>Poznámky

`CAtlExeModuleT`představuje modul pro aplikaci (EXE) a obsahuje kód, který podporuje vytváření EXE, zpracování příkazového řádku, registraci objektů třídy, spuštění smyčky zpráv a vyčištění při ukončení.

Tato třída je navržena tak, aby zlepšila výkon při vytváření a zničení objektů MODELU COM na serveru EXE. Po uvolnění posledního objektu COM exe čeká na dobu určenou datovým členem [CAtlExeModuleT::m_dwTimeOut.](#m_dwtimeout) Pokud během tohoto období neexistuje žádná aktivita (to znamená, že nejsou vytvořeny žádné objekty COM), je zahájen proces vypnutí.

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) datový člen je příznak používaný k určení, pokud EXE by měl používat mechanismus definovaný výše. Pokud je nastavena na false, modul bude okamžitě ukončen.

Další informace o modulech v atl naleznete v tématu [ATL Module Classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Modul CAtl](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlexemoduletcatlexemodulet"></a><a name="catlexemodulet"></a>CAtlExeModuleT::CAtlExeModuleT

Konstruktor

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Pokud modul EXE nelze inicializovat, WinMain se okamžitě vrátí bez dalšího zpracování.

## <a name="catlexemoduletcatlexemodulet"></a><a name="dtor"></a>CAtlExeModuleT::~CAtlExeModuleT

Destruktor.

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="catlexemoduletinitializecom"></a><a name="initializecom"></a>CAtlExeModuleT::InitializeCom

Inicializuje kom.

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda je volána z konstruktoru a může být přepsána k inicializaci com způsobem odlišným od výchozí implementace. Výchozí implementace volání `CoInitializeEx(NULL, COINIT_MULTITHREADED)` `CoInitialize(NULL)` nebo v závislosti na konfiguraci projektu.

Přepsání této metody obvykle vyžaduje přepsání [CAtlExeModuleT::UninitializeCom](#uninitializecom).

## <a name="catlexemoduletm_bdelayshutdown"></a><a name="m_bdelayshutdown"></a>CAtlExeModuleT::m_bDelayShutdown

Příznak označující, že by mělo dojít ke zpoždění vypnutí modulu.

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v [přehledu CAtlExeModuleT.](../../atl/reference/catlexemodulet-class.md)

## <a name="catlexemoduletm_dwpause"></a><a name="m_dwpause"></a>CAtlExeModuleT::m_dwPause

Hodnota pozastavení slouží k zajištění všech objektů jsou pryč před vypnutím.

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Poznámky

Změňte tuto hodnotu po volání [CAtlExeModuleT::InitializeCom](#initializecom) nastavit počet milisekund použít jako hodnotu pauza pro vypnutí serveru. Výchozí hodnota je 1000 milisekund.

## <a name="catlexemoduletm_dwtimeout"></a><a name="m_dwtimeout"></a>CAtlExeModuleT::m_dwTimeOut

Hodnota časového času slouží ke zpoždění uvolnění modulu.

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Poznámky

Změňte tuto hodnotu po volání [CAtlExeModuleT::InitializeCom](#initializecom) definovat počet milisekund používaných jako hodnota časového výpadku pro vypnutí serveru. Výchozí hodnota je 5000 milisekund. Další podrobnosti najdete v [přehledu CAtlExeModuleT.](../../atl/reference/catlexemodulet-class.md)

## <a name="catlexemoduletparsecommandline"></a><a name="parsecommandline"></a>CAtlExeModuleT::ParseCommandLine

Analyzuje příkazový řádek a v případě potřeby provede registraci.

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>Parametry

*lpCmdLine*<br/>
Příkazový řádek předán do aplikace.

*pnRetCode*<br/>
HRESULT odpovídající registraci (pokud k ní došlo).

### <a name="return-value"></a>Návratová hodnota

Vrátit true, pokud aplikace by měla pokračovat v běhu, jinak false.

### <a name="remarks"></a>Poznámky

Tato metoda je volána z [CAtlExeModuleT::WinMain](#winmain) a může být přepsána pro zpracování přepínačů příkazového řádku. Výchozí implementace kontroluje argumenty příkazového řádku **/RegServer** a **/UnRegServer** a provádí registraci nebo zrušení registrace.

## <a name="catlexemoduletpostmessageloop"></a><a name="postmessageloop"></a>CAtlExeModuleT::PostMessageLoop

Tato metoda je volána bezprostředně po ukončení smyčky zpráv.

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu provést vlastní vyčištění aplikace. Výchozí implementace volá [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).

## <a name="catlexemoduletpremessageloop"></a><a name="premessageloop"></a>CAtlExeModuleT::PreMessageLoop

Tato metoda je volána bezprostředně před vstupem do smyčky zpráv.

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Hodnota předaná jako parametr *nShowCmd* ve WinMain.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a přidejte vlastní inicializační kód pro aplikaci. Výchozí implementace registruje objekty třídy.

## <a name="catlexemoduletregisterclassobjects"></a><a name="registerclassobjects"></a>CAtlExeModuleT::RegisterClassObjects

Zaregistruje objekt třídy pomocí technologie OLE, aby se k němu mohly připojit jiné aplikace.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsKontext*<br/>
Určuje kontext, ve kterém má být objekt třídy spuštěn. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER.

*dwFlags*<br/>
Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch, S_FALSE pokud nebyly žádné třídy k registraci nebo chyba HRESULT při selhání.

## <a name="catlexemoduletrevokeclassobjects"></a><a name="revokeclassobjects"></a>CAtlExeModuleT::RevokeClassObjects

Odebere objekt třídy.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch, S_FALSE pokud nebyly žádné třídy k registraci nebo chyba HRESULT při selhání.

## <a name="catlexemoduletrun"></a><a name="run"></a>CAtlExeModuleT::Spustit

Tato metoda spustí kód v modulu EXE pro inicializaci, spuštění smyčky zpráv a vyčištění.

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain) Výchozí hodnota je SW_HIDE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda může být přepsána. V praxi je však lepší přepsat [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop)nebo [CAtlExeModuleT::PostMessageLoop.](#postmessageloop)

## <a name="catlexemoduletrunmessageloop"></a><a name="runmessageloop"></a>CAtlExeModuleT::RunMessageLoop

Tato metoda spustí smyčku zpráv.

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda může být přepsána změnit chování smyčky zpráv.

## <a name="catlexemoduletuninitializecom"></a><a name="uninitializecom"></a>CAtlExeModuleT::UninitializeCom

Uninitializes COM.

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda jednoduše volá [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize) a je volána z destruktoru. Přepsat tuto metodu, pokud přepsat [CAtlExeModuleT::InitializeCom](#initializecom).

## <a name="catlexemoduletunlock"></a><a name="unlock"></a>CAtlExeModuleT::Odemknout

Sníží počet zámků modulu.

```
LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

## <a name="catlexemoduletwinmain"></a><a name="winmain"></a>CAtlExeModuleT::WinMain

Tato metoda implementuje kód potřebný ke spuštění EXE.

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>Parametry

*nZobrazitCmd*<br/>
Určuje způsob zobrazení okna. Tento parametr může být jednou z hodnot popsaných v části [WinMain.](/windows/win32/api/winbase/nf-winbase-winmain)

### <a name="return-value"></a>Návratová hodnota

Vrátí vrácenou hodnotu spustitelného souboru.

### <a name="remarks"></a>Poznámky

Tato metoda může být přepsána. Pokud přepsání [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop)nebo [CAtlExeModuleT::RunMessageLoop](#runmessageloop) neposkytuje dostatečnou flexibilitu, `WinMain` je možné přepsat funkci pomocí této metody.

## <a name="see-also"></a>Viz také

[Atlduck vzorek](../../overview/visual-cpp-samples.md)<br/>
[Třída CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Třída CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
