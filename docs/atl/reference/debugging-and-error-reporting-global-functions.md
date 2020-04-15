---
title: Ladění a zasílání zpráv o chybách globální funkce
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330197"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Ladění a zasílání zpráv o chybách globální funkce

Tyto funkce poskytují užitečné ladění a trasování zařízení.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Vrátí `GetLastError` kód chyby ve formě HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Převede kód chyby Win32 na HRESULT.|
|[Chyba AtlReport](debugging-and-error-reporting-global-functions.md#atlreporterror)|Nastaví `IErrorInfo` poskytnutí podrobností o chybě klientovi.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Hodí `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Volání této funkce signalizuje chybu na základě `GetLastError`výsledku funkce systému Windows .|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

Vrátí hodnotu posledního kódu chyby volajícího vlákna ve formě HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Poznámky

`AtlHresultFromLastError`volá `GetLastError` k získání poslední chyby a vrátí chybu po převodu na HRESULT pomocí HRESULT_FROM_WIN32 makro.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultFromWin32

Převede kód chyby Win32 na HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parametry

*error*<br/>
Chybová hodnota, kterou chcete převést.

### <a name="remarks"></a>Poznámky

Převede kód chyby Win32 na HRESULT pomocí HRESULT_FROM_WIN32 makra.

> [!NOTE]
> Místo použití `HRESULT_FROM_WIN32(GetLastError())`použijte funkci [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>Chyba AtlReport

Nastaví `IErrorInfo` rozhraní tak, aby klientům objektu poskytovalo informace o chybě.

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

*Identifikátor clsid*<br/>
[v] IDENTIFIKÁTOR CLSID objektu, který chybu hlásí.

*lpszDesc*<br/>
[v] Řetězec popisující chybu. Verze Unicode určují, že *lpszDesc* je typu LPCOLESTR; verze ANSI určuje typ LPCSTR.

*Iid*<br/>
[v] IID rozhraní definující chybu nebo GUID_NULL pokud je chyba definována operačním systémem.

*hRes*<br/>
[v] HRESULT, které chcete vrátit volajícímu.

*Nid*<br/>
[v] Identifikátor prostředku, kde je uložen řetězec popisu chyby. Tato hodnota by měla ležet mezi 0x0200 a 0xFFFF, včetně. V sestavení chodu dojde k výsledku **ASSERT,** pokud *nID* neindexuje platný řetězec. V sestaveních verzí bude řetězec popisu chyby nastaven na "Neznámá chyba".

*dwHelpID*<br/>
[v] Identifikátor kontextu nápovědy pro chybu.

*soubor lpszHelpFile*<br/>
[v] Cesta a název souboru nápovědy popisující chybu.

*hInst*<br/>
[v] Popisovač prostředku. Ve výchozím nastavení `__AtlBaseModuleModule::GetResourceInstance`je `__AtlBaseModuleModule` tento parametr , kde je globální instance [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) nebo třídy odvozené z něj.

### <a name="return-value"></a>Návratová hodnota

Pokud je parametr *hRes* nenulový, vrátí hodnotu *hRes*. Pokud *hRes* je nula, pak `AtlReportError` první čtyři verze vrácení DISP_E_EXCEPTION. Poslední dvě verze vrátí výsledek MAKE_HRESULT makra( **1, FACILITY_ITF,** `nID` **)**.

### <a name="remarks"></a>Poznámky

Řetězec *lpszDesc* se používá jako textový popis chyby. Když klient obdrží *hRes* vrátíte `AtlReportError`z , klient `IErrorInfo` může získat přístup ke struktuře pro podrobnosti o chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> Nepoužívejte `AtlReportError` v c++ obslužné rutiny catch. Některé přepsání těchto funkcí používají makra převodu řetězce ATL interně, které zase používají `_alloca` funkci interně. Použití `AtlReportError` v c++ catch obslužné rutiny může způsobit výjimky v C++ catch obslužné rutiny.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow

Volání této funkce signalizuje chybu na základě stavového kódu HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je používána kódem KNIHOVNY ATL a knihovny MFC v případě chybového stavu. Může být také volána z vlastního kódu. Výchozí implementace této funkce závisí na definici symbolu _ATL_NO_EXCEPTIONS a na typu projektu, knihovny MFC nebo KNIHOVNY ATL.

Ve všech případech tato funkce sleduje HRESULT do ladicího programu.

V aktualizaci Visual Studio 2015 Update 3 a novější je tato funkce přiřazena __declspec(noreturn), aby se zabránilo falešné SAL upozornění.

Pokud _ATL_NO_EXCEPTIONS není definován v projektu knihovny MFC, tato funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo [COleException](../../mfc/reference/coleexception-class.md) na základě hodnoty HRESULT.

Pokud _ATL_NO_EXCEPTIONS není definován v projektu ATL, funkce vyvolá [CAtlException](../../atl/reference/catlexception-class.md).

Pokud je definován_ATL_NO_EXCEPTIONS funkce způsobí selhání kontrolního výrazu namísto vyvolání výjimky.

Pro projekty ATL je možné poskytnout vlastní implementaci této funkce, která má být použita atl v případě selhání. Chcete-li to provést, definujte vlastní `AtlThrow` funkci `AtlThrow` se stejným podpisem jako a #define být název funkce. To musí být provedeno před zahrnutím atlexcept.h (což znamená, že musí být provedeno před včetně všech hlavičky ATL, protože atlbase.h zahrnuje atlexcept.h). Atribut vaše `__declspec(noreturn)` funkce, aby se zabránilo falešné SAL varování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Volání této funkce signalizuje chybu na základě `GetLastError`výsledku funkce systému Windows .

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Poznámky

Tato funkce sleduje výsledek `GetLastError` ladicího programu.

Pokud _ATL_NO_EXCEPTIONS není definován v projektu knihovny MFC, tato funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) nebo `GetLastError` [COleException](../../mfc/reference/coleexception-class.md) na základě hodnoty vrácené .

Pokud _ATL_NO_EXCEPTIONS není definován v projektu ATL, funkce vyvolá [CAtlException](../../atl/reference/catlexception-class.md).

Pokud je definován_ATL_NO_EXCEPTIONS funkce způsobí selhání kontrolního výrazu namísto vyvolání výjimky.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef.h

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)<br/>
[Ladění a zasílání zpráv o chybách makra](../../atl/reference/debugging-and-error-reporting-macros.md)
