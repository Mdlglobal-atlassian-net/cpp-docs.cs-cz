---
title: "Ladění a globální funkce zpráv o chybách | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs: C++
helpviewer_keywords: functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b3383efcc78a022fc5131984957d94aa4b47838
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-global-functions"></a>Ladění a chybách globální funkce
Tyto funkce poskytují užitečné ladění a trasování zařízení.  
  
|||  
|-|-|  
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Vrátí `GetLastError` kód chyby ve formě HRESULT.|  
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Převede kód chyby Win32 na HRESULT.|  
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Nastaví **IErrorInfo** poskytnout podrobné informace o chybě pro klienta.|  
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Vyvolá `CAtlException`.|  
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Volání této funkce signál chybu na základě výsledku funkce systému Windows `GetLastError`.|  
  
##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError  
 Vrátí hodnotu posledního kódu chyby volajícího vlákna ve formě HRESULT.  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>Poznámky  
 `AtlHresultFromLastError`volání `GetLastError` získat poslední chyby a vrátí chybu po převodu k HRESULT pomocí **HRESULT_FROM_WIN32** makro.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32  
 Převede kód chyby Win32 na HRESULT.  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>Parametry  
 *Chyba*  
 Hodnota chyby pro převod.  
  
### <a name="remarks"></a>Poznámky  
 Převede kód chyby Win32 HRESULT, pomocí makro **HRESULT_FROM_WIN32**.  
  
> [!NOTE]
>  Místo použití **HRESULT_FROM_WIN32(GetLastError())**, použijte funkci [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcomcli.h  

##  <a name="atlreporterror"></a>AtlReportError  
 Nastaví `IErrorInfo` rozhraní a poskytuje informace o chybě klientům objektu.  
  
```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] CLSID objekt oznámena tato chyba.  
  
 `lpszDesc`  
 [v] Řetězec popisující chybu. Unicode verze určit, že `lpszDesc` je typu **LPCOLESTR**; verze ANSI Určuje typ `LPCSTR`.  
  
 `iid`  
 [v] Identifikátory IID rozhraní definování chyba nebo `GUID_NULL` Pokud chyba je definována v operačním systému.  
  
 `hRes`  
 [v] `HRESULT` Chcete vrácen volajícímu.  
  
 `nID`  
 [v] Identifikátor prostředku, uloží řetězec popis chyby. Tato hodnota by měla být mezi hodnotu 0x0200 a 0xFFFF, (včetně). V sestavení pro ladění **ASSERT** dojde, pokud `nID` index není platný řetězec. V sestavení pro vydání řetězec popis chyby. bude nastavena na "Neznámá chyba."  
  
 `dwHelpID`  
 [v] Identifikátor nápovědy Kontext chyby.  
  
 `lpszHelpFile`  
 [v] Cesta a název souboru nápovědy popisující chybu.  
  
 `hInst`  
 [v] Popisovač pro prostředek. Ve výchozím nastavení je tento parametr **__AtlBaseModuleModule::GetResourceInstance**, kde **__AtlBaseModuleModule** je globální instance [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) nebo třída z něj odvozenou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `hRes` parametr je nenulové hodnoty, vrátí hodnotu `hRes`. Pokud `hRes` nula, pak je první čtyři verze `AtlReportError` vrátit `DISP_E_EXCEPTION`. Poslední dvě verze vrátit výsledek makro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec *lpszDesc* slouží jako textový popis chyby. Když klient obdrží `hRes` vrátíte z `AtlReportError`, klient může získat **IErrorInfo** struktura podrobnosti o této chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  Nepoužívejte `AtlReportError` v jazyce C++ obslužné rutiny zachytávání. Některé přepsání tyto funkce používají makra převodů řetězec ATL interně, což následně použít `_alloca` funkce interně. Pomocí `AtlReportError` v C++ catch může způsobit obslužná rutina výjimky v C++ catch obslužné rutiny.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
    
##  <a name="atlthrow"></a>AtlThrow  
 Volání této funkce signál chybu na základě `HRESULT` stavový kód.  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>Parametry  
 `hr`  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce používá kódu ATL a MFC v případě chybový stav. Také může být volána z vlastního kódu. Výchozí implementace této funkce závisí na definici symbolu **_ATL_NO_EXCEPTIONS** a na typu projektu knihovny MFC nebo ATL.  
  
 Ve všech případech tato funkce sleduje HRESULT k ladicího programu.  
  
 V sadě Visual Studio 2015 Update 3 nebo novější je tato funkce s atributy __declspec(noreturn), aby se zabránilo nesprávné upozornění SAL.  
  
 Pokud **_ATL_NO_EXCEPTIONS** není definován v projektu knihovny MFC, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md) na základě hodnoty hodnota HRESULT.  
  
 Pokud **_ATL_NO_EXCEPTIONS** není definován v projektu knihovny ATL, vrátí funkce [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Pokud **_ATL_NO_EXCEPTIONS** je definován, funkce způsobí chybu assertion místo došlo k výjimce.  
  
 Pro projekty knihovny ATL je možné poskytnout vlastní implementaci této funkci můžete používat knihovny ATL v případě selhání. K tomuto účelu definovat vlastní funkce se stejným podpisem jako `AtlThrow` a #define `AtlThrow` jako název funkce. To je třeba provést před zahrnutím atlexcept.h (což znamená, že je třeba provést před včetně všechny hlavičky ATL vzhledem k tomu, že atlbase.h zahrnuje atlexcept.h). Atribut funkce `__declspec(noreturn)` předejdete nesprávné upozornění SAL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldef.h  

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32  
 Volání této funkce signál chybu na základě výsledku funkce systému Windows `GetLastError`.  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce sleduje výsledek `GetLastError` do ladicího programu.  
  
 Pokud **_ATL_NO_EXCEPTIONS** není definován v projektu knihovny MFC, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md) na základě hodnoty vrácené `GetLastError`.  
  
 Pokud **_ATL_NO_EXCEPTIONS** není definován v projektu knihovny ATL, vrátí funkce [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Pokud **_ATL_NO_EXCEPTIONS** je definován, funkce způsobí chybu assertion místo došlo k výjimce.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldef.h  
   
     
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)   
 [Makra ladění a hlášení chyb](../../atl/reference/debugging-and-error-reporting-macros.md)









