---
title: Catlexemodulet – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ed6b5f46e20338bdb06c5c04599402dbbefa935e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880047"
---
# <a name="catlexemodulet-class"></a>Catlexemodulet – třída
Tato třída reprezentuje modulu pro aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `CAtlExeModuleT`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|Konstruktor|  
|[Catlexemodulet –:: ~ catlexemodulet –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlExeModuleT::InitializeCom](#initializecom)|Inicializuje model COM.|  
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|Analyzuje příkazového řádku a provádí registraci v případě potřeby.|  
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|Tato metoda je volána ihned po ukončení smyčky zpráv.|  
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|Tato metoda je volána těsně před zadáním smyčky zpráv.|  
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|Zaregistruje objekt třídy.|  
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|Odebere objekt třídy.|  
|[CAtlExeModuleT::Run](#run)|Tato metoda spustí kód v souboru EXE modulu inicializovat, spusťte smyčky zpráv a vyčistit.|  
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|Tato metoda bude spuštěna smyčka zpráv.|  
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|Zruší inicializaci modulu COM.|  
|[CAtlExeModuleT::Unlock](#unlock)|Sníží počet zámků modulů.|  
|[CAtlExeModuleT::WinMain](#winmain)|Tato metoda implementuje je kód potřebný ke spuštění EXE.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|Příznak označující, že by měl být zpoždění vypnutí modulu.|  
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|Pozastavit hodnota používá k zajištění, že všechny objekty jsou vydané před vypnutím.|  
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|Hodnotu časového limitu, používá ke zpoždění uvolnění modulu.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlExeModuleT` představuje modul pro aplikace (EXE) a obsahuje kód, který podporuje vytváření EXE, zpracování příkazového řádku, registrace objekty třídy, spouštění smyčky zpráv a vyčištění při ukončení.  
  
 Tato třída slouží pro zvýšení výkonu při objektů COM v serveru EXE průběžně vytvořen a zničen. Po vydání poslední objekt modelu COM, soubor EXE čeká po dobu určeného [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout) datový člen. Pokud není žádná aktivita během této doby (to znamená, COM nejsou vytvořeny žádné), je zahájeno vypínání.  
  
 [CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown) datový člen je příznak, který umožňuje určit, pokud by měl soubor EXE použijte mechanismus výše. Pokud je nastavena na hodnotu false, se okamžitě ukončí modulu.  
  
 Další informace o modulech v ATL naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [Catlmodule –](../../atl/reference/catlmodule-class.md)  
  
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
 Pokud nebylo možné inicializovat modul EXE, WinMain okamžitě vrátí bez dalšího zpracování.  
  
##  <a name="dtor"></a>  Catlexemodulet –:: ~ catlexemodulet –  
 Destruktor.  
  
```
~CAtlExeModuleT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom  
 Inicializuje model COM.  
  
```
static HRESULT InitializeCom() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána z konstruktoru a může být potlačena za účelem inicializace COM způsobem, který se liší od výchozí implementaci. Výchozí implementace volá buď `CoInitializeEx(NULL, COINIT_MULTITHREADED)` nebo `CoInitialize(NULL)` v závislosti na konfiguraci projektu.  
  
 Potlačení této metody obvykle vyžaduje přepsání [CAtlExeModuleT::UninitializeCom](#uninitializecom).  
  
##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown  
 Příznak označující, že by měl být zpoždění vypnutí modulu.  
  
```
bool m_bDelayShutdown;
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [catlexemodulet – přehled](../../atl/reference/catlexemodulet-class.md) podrobnosti.  
  
##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause  
 Pozastavit hodnota používá k zajištění, že všechny objekty jsou pryč před vypnutím.  
  
```
DWORD m_dwPause;
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu změnit po volání [CAtlExeModuleT::InitializeCom](#initializecom) nastavit počet milisekund, použije jako hodnota pozastavení pro vypnutí serveru. Výchozí hodnota je 1000 milisekund.  
  
##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut  
 Hodnotu časového limitu, používá ke zpoždění uvolnění modulu.  
  
```
DWORD m_dwTimeOut;
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu změnit po volání [CAtlExeModuleT::InitializeCom](#initializecom) definovat dobu v milisekundách použít jako hodnotu časového limitu pro vypnutí serveru. Výchozí hodnota je 5000 MS. Zobrazit [catlexemodulet – přehled](../../atl/reference/catlexemodulet-class.md) další podrobnosti.  
  
##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine  
 Analyzuje příkazového řádku a provádí registraci v případě potřeby.  
  
```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpCmdLine*  
 Příkazového řádku předané do aplikace.  
  
 *pnRetCode*  
 Hodnota HRESULT odpovídající registraci (Pokud se uskutečnilo).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud aplikace by měla pokračovat ke spuštění, v opačném případě false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána z [CAtlExeModuleT::WinMain](#winmain) a může být potlačena za účelem zpracování přepínače příkazového řádku. Výchozí implementace vyhledává **/regserver** a **Unregserver** argumenty příkazového řádku a provádí registraci nebo zrušení registrace.  
  
##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop  
 Tato metoda je volána ihned po ukončení smyčky zpráv.  
  
```
HRESULT PostMessageLoop() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem vyčištění vlastní aplikace. Výchozí implementace volá [CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects).  
  
##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop  
 Tato metoda je volána těsně před zadáním smyčky zpráv.  
  
```
HRESULT PreMessageLoop(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nShowCmd*  
 Hodnotu předanou jako *nShowCmd* parametr WinMain.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Přepsáním této metody můžete přidat vlastní inicializační kód aplikace. Výchozí implementace zaregistruje třídu objektů.  
  
##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects  
 Zaregistruje objekt třídy OLE, můžete k němu připojit další aplikace.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwClsContext*  
 Určuje kontext, ve kterém má být spuštěn objektu třídy. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER.  
  
 *dwFlags*  
 Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK na úspěch, S_FALSE, je-li nebyly žádné třídy k registraci nebo chybu HRESULT při selhání.  
  
##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects  
 Odebere objekt třídy.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK na úspěch, S_FALSE, je-li nebyly žádné třídy k registraci nebo chybu HRESULT při selhání.  
  
##  <a name="run"></a>  CAtlExeModuleT::Run  
 Tato metoda spustí kód v souboru EXE modulu inicializovat, spusťte smyčky zpráv a vyčistit.  
  
```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nShowCmd*  
 Určuje, jak má být zobrazen v okně. Tento parametr může být jedna z hodnot podrobněji popsána [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) oddílu. Výchozí hodnota je SW_HIDE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být přepsána. Ale v praxi je lepší přepsat [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::RunMessageLoop](#runmessageloop), nebo [CAtlExeModuleT::PostMessageLoop](#postmessageloop) Místo toho.  
  
##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop  
 Tato metoda bude spuštěna smyčka zpráv.  
  
```
void RunMessageLoop() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být potlačena za účelem změny chování smyčky zpráv.  
  
##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom  
 Zruší inicializaci modulu COM.  
  
```
static void UninitializeCom() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda provede jednoduché volání [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715) a je volána z destruktoru. Potlačí tuto metodu, pokud přepíšete [CAtlExeModuleT::InitializeCom](#initializecom).  
  
##  <a name="unlock"></a>  CAtlExeModuleT::Unlock  
 Sníží počet zámků modulů.  
  
```
LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, která může být užitečné pro diagnostiku a testování.  
  
##  <a name="winmain"></a>  CAtlExeModuleT::WinMain  
 Tato metoda implementuje je kód potřebný ke spuštění EXE.  
  
```
int WinMain(int nShowCmd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nShowCmd*  
 Určuje, jak má být zobrazen v okně. Tento parametr může být jedna z hodnot podrobněji popsána [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559) oddílu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ke spustitelnému souboru návratovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být přepsána. Pokud přepisuje [CAtlExeModuleT::PreMessageLoop](#premessageloop), [CAtlExeModuleT::PostMessageLoop](#postmessageloop), nebo [CAtlExeModuleT::RunMessageLoop](#runmessageloop) neposkytuje dostatečně flexibilní, , je možné přepsat `WinMain` funkce pomocí této metody.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka ATLDuck](../../visual-cpp-samples.md)   
 [Catlmodulet – třída](../../atl/reference/catlmodulet-class.md)   
 [Catldllmodulet – třída](../../atl/reference/catldllmodulet-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
