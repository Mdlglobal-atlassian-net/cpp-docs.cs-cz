---
title: Třída CDebugReportHook
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 621d32a14618327873e6e0cce856c5792e1f8c46
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327115"
---
# <a name="cdebugreporthook-class"></a>Třída CDebugReportHook

Tato třída slouží k odeslání ladicí sestavy do pojmenovaného kanálu.

## <a name="syntax"></a>Syntaxe

```
class CDebugReportHook
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Volání [SetPipeName](#setpipename), [SetTimeout](#settimeout)a [SetHook](#sethook).|
|[CDebugReportHook::~CDebugReportHook](#dtor)|Volání [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statické) Vlastní funkce vykazování, která je připojena k procesu vytváření ladicích procesů c run-time.|
|[CDebugReportHook::RemoveHook](#removehook)|Volání této metody zastavit odesílání ladicí sestavy do pojmenované kanálu a obnovit předchozí zavěšení sestavy.|
|[CDebugReportHook::SetHook](#sethook)|Volání této metody začít odesílat ladicí sestavy do pojmenované kanálu.|
|[CDebugReportHook::SetPipeName](#setpipename)|Volání této metody nastavit počítač a název kanálu, do kterého budou odeslány zprávy ladění.|
|[CDebugReportHook::SetTimeout](#settimeout)|Volání této metody nastavit čas v milisekundách, že tato třída bude čekat na pojmenované kanálu k dispozici.|

## <a name="remarks"></a>Poznámky

Vytvořte instanci této třídy v ladění sestavení služeb nebo aplikací pro odesílání ladicích sestav do pojmenovaného kanálu. Ladicí sestavy jsou generovány voláním [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) nebo pomocí obálky pro tuto funkci, jako jsou například makra [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) a [ATLASSERT.](debugging-and-error-reporting-macros.md#atlassert)

Použití této třídy umožňuje interaktivně ladit součásti běžící v [neinteraktivních stanicích oken](/windows/win32/winstation/window-stations).

Všimněte si, že ladicí sestavy jsou odesílány pomocí základního kontextu zabezpečení vlákna. Zosobnění je dočasně zakázáno, takže ladicí sestavy lze zobrazit v situacích, kdy dochází k zosobnění uživatelů s nízkými oprávněními, například ve webových aplikacích.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Volání [SetPipeName](#setpipename), [SetTimeout](#settimeout)a [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Název počítače, do kterého by měl být odeslán ladicí výstup. Výchozí je místní počítač.

*szPipeName*<br/>
Název pojmenovaného kanálu, do kterého by měl být odeslán ladicí výstup.

*dwTimeout*<br/>
Čas v milisekundách, že tato třída bude čekat na pojmenované kanálu k dispozici.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>CDebugReportHook::~CDebugReportHook

Volání [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

Vlastní funkce vykazování, která je připojena k procesu vytváření ladicích procesů c run-time.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parametry

*type sestavy*<br/>
Typ sestavy (_CRT_WARN, _CRT_ERROR nebo _CRT_ASSERT).

*Zprávu*<br/>
Řetězec zprávy.

*Returnvalue*<br/>
Hodnota, která by měla být vrácena [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu NEPRAVDA, pokud háček zpracovává dotyčnou zprávu zcela tak, aby nebylo vyžadováno žádné další hlášení. Vrátí hodnotu PRAVDA, pokud `_CrtDbgReport` má zprávu nahlásit normálním způsobem.

### <a name="remarks"></a>Poznámky

Funkce vykazování se pokusí otevřít pojmenovaný kanál a komunikovat s procesem na druhém konci. Pokud je kanál zaneprázdněn, funkce vykazování počká, dokud nebude kanál volný nebo dokud vyprší časový limit. Časový čas lze nastavit konstruktorem nebo [voláníc CDebugReportHook::SetTimeout](#settimeout).

Kód v této funkci je spuštěn v kontextu zabezpečení podkladového vlákna volajícího, to znamená, že zosobnění je zakázáno po dobu trvání této funkce.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebugReportHook::RemoveHook

Volání této metody zastavit odesílání ladicí sestavy do pojmenované kanálu a obnovit předchozí zavěšení sestavy.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Poznámky

Volání [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) k obnovení předchozího zavěšení sestavy.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebugReportHook::SetHook

Volání této metody začít odesílat ladicí sestavy do pojmenované kanálu.

```
void SetHook() throw();
```

### <a name="remarks"></a>Poznámky

Volání [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) mít ladicí sestavy směrovány prostřednictvím [CDebugReportHookProc](#cdebugreporthookproc) do pojmenovaného kanálu. Tato třída udržuje informace o předchozí zavěšení sestavy tak, aby jej lze obnovit při [RemoveHook](#removehook) je volána.

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebugReportHook::SetPipeName

Volání této metody nastavit počítač a název kanálu, do kterého budou odeslány zprávy ladění.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Název počítače, do kterého by měl být odeslán ladicí výstup.

*szPipeName*<br/>
Název pojmenovaného kanálu, do kterého by měl být odeslán ladicí výstup.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebugReportHook::SetTimeout

Volání této metody nastavit čas v milisekundách, že tato třída bude čekat na pojmenované kanálu k dispozici.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Čas v milisekundách, že tato třída bude čekat na pojmenované kanálu k dispozici.

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)
