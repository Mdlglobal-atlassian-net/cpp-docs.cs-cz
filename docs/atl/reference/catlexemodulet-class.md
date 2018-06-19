---
title: Třída CAtlExeModuleT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d22510da8c1377411b289b940e1b8e196533c93a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364960"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT – třída
Tato třída reprezentuje modul pro aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CAtlExeModuleT`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor|  
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicializuje COM.|  
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analyzuje příkazového řádku a v případě potřeby provede registrace.|  
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Tato metoda je volána hned po ukončení smyčky zpráv.|  
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Tato metoda je volána bezprostředně před vstupem smyčce zpráv.|  
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Zaregistruje třídu objektu.|  
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odvolá objektu třídy.|  
|[CAtlExeModuleT::Run](#run)|Tato metoda spustí kód v modulu EXE inicializovat, spusťte zpráva smyčky a vyčistit.|  
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Tato metoda provede smyčce zpráv.|  
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Uninitializes COM.|  
|[CAtlExeModuleT::Unlock](#unlock)|Snižuje počet modulu zámku.|  
|[CAtlExeModuleT::WinMain](#winmain)|Tato metoda implementuje je kód potřebný ke spuštění EXE.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Příznak označující, že by měl být zpoždění vypínání modulu.|  
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Pozastavení hodnota používá k zajištění, že všechny objekty, které jsou vydané dřív než vypnutí.|  
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Hodnota časového limitu, používá ke zpoždění uvolnění modulu.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlExeModuleT` představuje modul pro aplikaci (EXE) a obsahuje kód, který podporuje vytváření EXE, zpracování příkazového řádku, registrace objekty tříd, systémem zpráva smyčky a čištění po ukončení.  
  
 Tato třída slouží ke zlepšení výkonu při objekty modelu COM v serveru EXE průběžně vytvořen a zničen. Po vydání poslední objektu COM, EXE se čeká na dobu trvání určeného [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) – datový člen. Pokud během této doby nebude žádná aktivita (tedy COM nejsou vytvořeny žádné), vypnutí proces je zahájen.  
  
 [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) – datový člen je příznak lze zjistit, zda EXE by měl používat mechanismus definované výše. Pokud je nastavené na hodnotu false, se okamžitě ukončí modul.  
  
 Další informace o modulech v ATL najdete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlExeModuleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT  
 Konstruktor  
  
```
CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud modul EXE nelze inicializovat, WinMain vrátí okamžitě bez dalšího zpracování.  
  
##  <a name="dtor"></a>  CAtlExeModuleT:: ~ CAtlExeModuleT  
 Destruktor.  
  
```
~CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom  
 Inicializuje COM.  
  
```
static HRESULT InitializeCom() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána z konstruktoru a může být potlačena za účelem inicializace COM způsobem, který se liší od výchozí implementace. Výchozí implementace volá buď **CoInitializeEx (hodnotu NULL, COINIT_MULTITHREADED)** nebo **CoInitialize(NULL)** v závislosti na konfiguraci projektu.  
  
 Přepíše tuto metodu obvykle vyžaduje přepsání [CAtlExeModuleT::UninitializeCom](#uninitializecom).  
  
##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown  
 Příznak označující, že by měl být zpoždění vypínání modulu.  
  
```
bool m_bDelayShutdown;
```  
  
### <a name="remarks"></a>Poznámky  
 Najdete v článku [CAtlExeModuleT přehled](../../atl/reference/catlexemodulet-class.md) podrobnosti.  
  
##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause  
 Pozastavení hodnota používá k zajištění, že jsou všechny objekty zmizel před vypnutí.  
  
```
DWORD m_dwPause;
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu změnit po volání [CAtlExeModuleT::InitializeCom](#initializecom) nastavit počet milisekund, po použít jako hodnotu pozastavení pro vypnutí serveru. Výchozí hodnota je 1000 milisekund.  
  
##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut  
 Hodnota časového limitu, používá ke zpoždění uvolnění modulu.  
  
```
DWORD m_dwTimeOut;
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu změnit po volání [CAtlExeModuleT::InitializeCom](#initializecom) zadat počet milisekund, po použít jako hodnotu časového limitu pro vypnutí serveru. Výchozí hodnota je 5000 milisekund. Najdete v článku [CAtlExeModuleT přehled](../../atl/reference/catlexemodulet-class.md) další podrobnosti.  
  
##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine  
 Analyzuje příkazového řádku a v případě potřeby provede registrace.  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpCmdLine`  
 Příkazový řádek předána do aplikace.  
  
 `pnRetCode`  
 HRESULT odpovídající registrace (Pokud trvalo místní).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud aplikace by měly být nadále spouštět, jinak hodnota false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána z [CAtlExeModuleT::WinMain](#winmain) a může být potlačena za účelem zpracování přepínače příkazového řádku. Výchozí implementace zkontroluje **/regserver** a **/Unregserver** argumenty příkazového řádku a provádí registraci nebo zrušení registrace.  
  
##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop  
 Tato metoda je volána hned po ukončení smyčky zpráv.  
  
```
HRESULT PostMessageLoop() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu provést čištění vlastní aplikaci. Výchozí implementace volá [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).  
  
##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop  
 Tato metoda je volána bezprostředně před vstupem smyčce zpráv.  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Hodnota zadaná jako `nShowCmd` parametr v WinMain.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem přidání vlastní inicializaci kód aplikace. Výchozí implementace zaregistruje objekty tříd.  
  
##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects  
 Zaregistruje objektu třídy se OLE, takže k nim mohla připojit jiné aplikace.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwClsContext*  
 Určuje kontext, ve kterém má být spuštěna objektu třídy. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER.  
  
 `dwFlags`  
 Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch, S_FALSE kdyby žádné třídy k registraci nebo chybu HRESULT při selhání.  
  
##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects  
 Odebere objekt třídy.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch, S_FALSE kdyby žádné třídy k registraci nebo chybu HRESULT při selhání.  
  
##  <a name="run"></a>  CAtlExeModuleT::Run  
 Tato metoda spustí kód v modulu EXE inicializovat, spusťte zpráva smyčky a vyčistit.  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Určuje, jak se nezobrazí okno. Tento parametr může být jedna z hodnot zabývá [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) části. Výchozí hodnota je SW_HIDE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být přepsána. Nicméně, v praxi je lepší přepsat [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), nebo [CAtlExeModuleT::PostMessageLoop](#postmessageloop) Místo toho.  
  
##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop  
 Tato metoda provede smyčce zpráv.  
  
```
void RunMessageLoop() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být potlačena za účelem změnit chování smyčce zpráv.  
  
##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom  
 Uninitializes COM.  
  
```
static void UninitializeCom() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda jednoduše volá [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715) a je volána z destruktoru. Potlačí tuto metodu, pokud přepíšete [CAtlExeModuleT::InitializeCom](#initializecom).  
  
##  <a name="unlock"></a>  CAtlExeModuleT::Unlock  
 Snižuje počet modulu zámku.  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování.  
  
##  <a name="winmain"></a>  CAtlExeModuleT::WinMain  
 Tato metoda implementuje je kód potřebný ke spuštění EXE.  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nShowCmd`  
 Určuje, jak se nezobrazí okno. Tento parametr může být jedna z hodnot zabývá [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) části.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ke spustitelnému souboru návratovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být přepsána. Pokud přepsání [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), nebo [CAtlExeModuleT::RunMessageLoop](#runmessageloop) neposkytuje dost flexibilitu , je možné přepsat `WinMain` funkce pomocí této metody.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka ATLDuck](../../visual-cpp-samples.md)   
 [CAtlModuleT – třída](../../atl/reference/catlmodulet-class.md)   
 [CAtlDllModuleT – třída](../../atl/reference/catldllmodulet-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
