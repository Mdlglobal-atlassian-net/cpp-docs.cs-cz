---
title: Ladění a globální funkce zpráv o chybách | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs:
- C++
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8af4a1b2ee763dfc28288058d27b1b08721fd97
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756061"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Ladění a globální funkce hlášení chyb

Tyto funkce poskytují užitečné funkce ladění a trasování.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Vrátí `GetLastError` chyba kódu ve formě HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Převede kód chyby Win32 na HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Nastaví `IErrorInfo` poskytovat podrobnosti o chybě klienta.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Vyvolá výjimku `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Voláním této funkce signalizujete chybu na základě výsledku funkce Windows `GetLastError`.|

##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError

Vrátí hodnotu posledního kódu chyby volajícího vlákna ve formě HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Poznámky

`AtlHresultFromLastError` volání `GetLastError` získat poslední chyby a vrátí chybu po převedení na použití makra HRESULT_FROM_WIN32 HRESULT.  

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32

Převede kód chyby Win32 na HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parametry

*Chyba*  
Hodnota chyby pro převod.

### <a name="remarks"></a>Poznámky

Převede kód chyby Win32 na HRESULT, makro HRESULT_FROM_WIN32.

> [!NOTE]
>  Namísto použití `HRESULT_FROM_WIN32(GetLastError())`, použijte funkci [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).  

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h  

##  <a name="atlreporterror"></a>  AtlReportError

Nastaví `IErrorInfo` rozhraní k poskytování informací o chybách klientům objektu.

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

*identifikátor CLSID*  
[in] Identifikátor CLSID objektu oznámena tato chyba.

*lpszDesc*  
[in] Řetězec popisující chybu. Verze Unicode určit, že *lpszDesc* je typ LPCOLESTR; verze ANSI Určuje typ LPCSTR.

*identifikátor IID*  
[in] Identifikátor IID rozhraní definování chyb nebo GUID_NULL Pokud chyba není definován v operačním systému.

*hRes*  
[in] Hodnota HRESULT, který chcete vrátit zpět volajícímu.

*nID*  
[in] Identifikátor prostředku řetězce popisu chyby se mají ukládat. Tato hodnota by měla být mezi hodnotu 0x0200 a 0xFFFF (včetně). V sestavení ladění **ASSERT** dojde-li *nID* index není platný řetězec. V sestaveních pro vydání řetězce popisu chyby bude nastavena na "Neznámá chyba".

*dwHelpID*  
[in] Identifikátor kontextu pomoc pro chybu.

*lpszHelpFile*  
[in] Cesta a název souboru nápovědy popisující chybu.

*hInst*  
[in] Popisovač pro prostředek. Ve výchozím nastavení, je tento parametr `__AtlBaseModuleModule::GetResourceInstance`, kde `__AtlBaseModuleModule` je globální instanci [catlbasemodule –](../../atl/reference/catlbasemodule-class.md) nebo z něj odvozenou třídu.

### <a name="return-value"></a>Návratová hodnota

Pokud *hRes* parametr je nenulovou hodnotu, vrátí hodnotu *hRes*. Pokud *hRes* je nula, pak první čtyři verzích `AtlReportError` vrátí DISP_E_EXCEPTION. Poslední dvě verze vrácení výsledku makra **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.

### <a name="remarks"></a>Poznámky

Řetězec *lpszDesc* slouží jako textový popis chyby. Když klient obdrží *hRes* vrátit z `AtlReportError`, klient může získat `IErrorInfo` strukturu pro podrobnosti o chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  Nepoužívejte `AtlReportError` obslužné rutiny zachytávání v jazyce C++. Některé přepsání těchto funkcí používat převodních maker knihovny ATL řetězec interně, která pak může použít `_alloca` fungovat interně. Pomocí `AtlReportError` v bloku catch C++ může způsobit obslužná rutina výjimky v obslužné rutiny catch C++.  

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="atlthrow"></a>  AtlThrow

Voláním této funkce signalizujete chybu na základě kódu stavu HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*hr*  
Standardní hodnotu HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce používá kódu ATL a MFC v případě chybového stavu. Také může být volána z vlastního kódu. Výchozí implementace této funkce závisí na definici symbolu _ATL_NO_EXCEPTIONS a na typu projektu knihovny MFC ani ATL.

Ve všech případech se tato funkce sleduje HRESULT v ladicím programu.

V sadě Visual Studio 2015 Update 3 nebo novější tato funkce je s atributy __declspec(noreturn), aby se zabránilo detekováno falešné upozornění SAL.

Pokud _ATL_NO_EXCEPTIONS není definovaný v projektu knihovny MFC, tato funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md) na základě hodnoty HRESULT.

Pokud _ATL_NO_EXCEPTIONS není definovaný v projektu knihovny ATL, funkce vyvolá [catlexception –](../../atl/reference/catlexception-class.md).

Pokud je definován _ATL_NO_EXCEPTIONS, funkce způsobí selhání kontrolního výrazu namísto vyvolání výjimky.

Pro projekty ATL je možné poskytnout vlastní implementaci této funkce ATL používané v případě selhání. K tomuto účelu definovat vlastní funkce se stejným podpisem jako `AtlThrow` a #define `AtlThrow` bude název vaší funkce. To je nutné provést před zahrnutím atlexcept.h (to znamená, že je třeba provést před včetně záhlaví knihovny ATL, protože obsahuje atlbase.h atlexcept.h). Atribut funkce `__declspec(noreturn)` , aby detekováno falešné upozornění SAL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef.h  

##  <a name="atlthrowlastwin32"></a>  AtlThrowLastWin32

Voláním této funkce signalizujete chybu na základě výsledku funkce Windows `GetLastError`.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Poznámky

Tato funkce sleduje výsledek `GetLastError` ladicímu programu.

Pokud _ATL_NO_EXCEPTIONS není definovaný v projektu knihovny MFC, tato funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) nebo [coleexception –](../../mfc/reference/coleexception-class.md) podle hodnoty vrácené `GetLastError`.

Pokud _ATL_NO_EXCEPTIONS není definovaný v projektu knihovny ATL, funkce vyvolá [catlexception –](../../atl/reference/catlexception-class.md).

Pokud je definován _ATL_NO_EXCEPTIONS, funkce způsobí selhání kontrolního výrazu namísto vyvolání výjimky.  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef.h

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)   
[Makra ladění a hlášení chyb](../../atl/reference/debugging-and-error-reporting-macros.md)

