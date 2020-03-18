---
title: Globální funkce ladění a zasílání zpráv o chybách
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7483b7473383958089b0c88d0b3c2645ddc2a4f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417710"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Globální funkce ladění a zasílání zpráv o chybách

Tyto funkce poskytují užitečná zařízení pro ladění a trasování.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Vrátí kód chyby `GetLastError` ve formátu HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Převede kód chyby Win32 na HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Nastaví `IErrorInfo` k poskytnutí podrobností o chybách klientovi.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Vyvolá `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Voláním této funkce signalizujete chybu na základě výsledku funkce Windows `GetLastError`.|

##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

Vrátí hodnotu posledního kódu chyby volajícího vlákna ve formě HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Poznámky

`AtlHresultFromLastError` volá `GetLastError`, aby získal poslední chybu a vrátila chybu po jejím převedení na HRESULT pomocí makra HRESULT_FROM_WIN32.

### <a name="requirements"></a>Požadavky

**Záhlaví:** Atlcomcli. h

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32

Převede kód chyby Win32 na HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parametry

*Chyba*<br/>
Hodnota chyby, která má být převedena.

### <a name="remarks"></a>Poznámky

Převede kód chyby Win32 na HRESULT pomocí HRESULT_FROM_WIN32 makra.

> [!NOTE]
>  Místo použití `HRESULT_FROM_WIN32(GetLastError())`použijte funkci [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Požadavky

**Záhlaví:** Atlcomcli. h

##  <a name="atlreporterror"></a>AtlReportError

Nastaví `IErrorInfo` rozhraní pro poskytování informací o chybách klientům objektu.

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

*CLSID*<br/>
pro Identifikátor CLSID objektu, který hlásí chybu.

*lpszDesc*<br/>
pro Řetězec popisující chybu. Verze Unicode určují, že *lpszDesc* je typu LPCOLESTR; verze ANSI určuje typ LPCSTR.

*identifikátor*<br/>
pro Identifikátor IID rozhraní, který definuje chybu, nebo GUID_NULL, pokud je Chyba definovaná operačním systémem.

*hRes*<br/>
pro Hodnota HRESULT, kterou chcete vrátit volajícímu.

*nID*<br/>
pro Identifikátor prostředku, kde je uložen řetězec s popisem chyby. Tato hodnota by se měla nacházet mezi 0x0200 a 0xFFFF (včetně). V sestavení ladění bude výsledek **vyhodnocení** v případě, že *NID* neindexuje platný řetězec. V sestavení vydaných verzí se řetězec popisu chyby nastaví na "Neznámá chyba".

*dwHelpID*<br/>
pro Identifikátor kontextu nápovědu pro chybu.

*lpszHelpFile*<br/>
pro Cesta a název souboru Help popisujícího chybu.

*hInst*<br/>
pro Popisovač prostředku. Ve výchozím nastavení je tento parametr `__AtlBaseModuleModule::GetResourceInstance`, kde `__AtlBaseModuleModule` je globální instance [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) nebo třída odvozená z něj.

### <a name="return-value"></a>Návratová hodnota

Pokud je parametr *hRes* nenulový, vrátí hodnotu *hRes*. Pokud má *hRes* hodnotu nula, pak DISP_E_EXCEPTION první čtyři verze `AtlReportError` vrátit. Poslední dvě verze vrátí výsledek makra **MAKE_HRESULT (1, FACILITY_ITF** `nID` **)** .

### <a name="remarks"></a>Poznámky

Řetězec *lpszDesc* se používá jako textový popis chyby. Když klient obdrží *hRes* , který vrátíte z `AtlReportError`, může klient získat přístup ke struktuře `IErrorInfo`, kde najdete podrobnosti o chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  Nepoužívejte `AtlReportError` v C++ obslužných rutinách catch. Některá přepsání těchto funkcí používají interně makra převodu řetězce ATL, která zase používají funkci `_alloca` interně. Použití `AtlReportError` v obslužné C++ rutině catch může způsobit výjimky C++ v obslužných rutinách catch.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="atlthrow"></a>AtlThrow

Voláním této funkce signalizujete chybu na základě stavového kódu HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*oddělení*<br/>
Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tuto funkci používá ATL a kód MFC v případě chybové podmínky. Může být také volána z vlastního kódu. Výchozí implementace této funkce závisí na definici symbolu _ATL_NO_EXCEPTIONS a na typu projektu, MFC nebo ATL.

Ve všech případech tato funkce sleduje HRESULT do ladicího programu.

V aplikaci Visual Studio 2015 Update 3 a novějších je tato funkce s atributem __declspec (Return), aby se předešlo upozornění spurious SAL.

Pokud _ATL_NO_EXCEPTIONS není definována v projektu knihovny MFC, tato funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md) na základě hodnoty HRESULT.

Pokud _ATL_NO_EXCEPTIONS není definována v projektu ATL, funkce vyvolá výjimku [CAtlException](../../atl/reference/catlexception-class.md).

Pokud je definována _ATL_NO_EXCEPTIONS, funkce způsobí selhání kontrolního výrazu namísto vyvolání výjimky.

Pro projekty ATL je možné poskytnout vlastní implementaci této funkce, která bude v případě selhání používána knihovnou ATL. Uděláte to tak, že definujete svou vlastní funkci se stejnou signaturou jako `AtlThrow` a #define `AtlThrow` název vaší funkce. To je nutné provést před zahrnutím atlexcept. h (to znamená, že je nutné provést před zahrnutím jakýchkoli hlaviček ATL, protože atlbase. h zahrnuje atlexcept. h). Atribut `__declspec(noreturn)` funkce, aby nedocházelo k upozorněním spurious SAL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef. h

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Voláním této funkce signalizujete chybu na základě výsledku funkce Windows `GetLastError`.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Poznámky

Tato funkce sleduje výsledek `GetLastError` ladicímu programu.

Pokud _ATL_NO_EXCEPTIONS není definována v projektu knihovny MFC, tato funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md) na základě hodnoty vrácené `GetLastError`.

Pokud _ATL_NO_EXCEPTIONS není definována v projektu ATL, funkce vyvolá výjimku [CAtlException](../../atl/reference/catlexception-class.md).

Pokud je definována _ATL_NO_EXCEPTIONS, funkce způsobí selhání kontrolního výrazu namísto vyvolání výjimky.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef. h

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)<br/>
[Makra ladění a hlášení chyb](../../atl/reference/debugging-and-error-reporting-macros.md)
