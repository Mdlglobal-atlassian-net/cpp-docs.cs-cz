---
title: Cdebugreporthook – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb0bf24657a47cbe1cf1129f0202d120fb1d017e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039059"
---
# <a name="cdebugreporthook-class"></a>Cdebugreporthook – třída

Tato třída slouží k odesílání sestav ladění k pojmenovanému kanálu.

## <a name="syntax"></a>Syntaxe

```
class CDebugReportHook
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Volání [SetPipeName](#setpipename), [SetTimeout](#settimeout), a [SetHook](#sethook).|
|[Cdebugreporthook –:: ~ cdebugreporthook –](#dtor)|Volání [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statické) Vlastní vytváření sestav funkce, která je připojit vykazování procesu ladění za běhu C.|
|[CDebugReportHook::RemoveHook](#removehook)|Voláním této metody lze zastavit odesílání sestav ladění k pojmenovanému kanálu a obnovit předchozí háku sestavy.|
|[CDebugReportHook::SetHook](#sethook)|Voláním této metody lze zahájit odesílání sestav ladění k pojmenovanému kanálu.|
|[CDebugReportHook::SetPipeName](#setpipename)|Voláním této metody nastavte počítač a název kanálu, do které se pošlou sestav ladění.|
|[CDebugReportHook::SetTimeout](#settimeout)|Voláním této metody lze nastavit čas v milisekundách, že tato třída bude čekat pojmenovaný kanál k dispozici.|

## <a name="remarks"></a>Poznámky

Vytvoření instance této třídy v sestavení ladění, služby nebo aplikace zasílání zpráv o ladění k pojmenovanému kanálu. Ladění sestavy jsou generovány pomocí volání [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) nebo pomocí obálku pro tuto funkci, jako [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) a [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) makra.

Použití této třídy můžete interaktivně ladění součástí, které běží neinteraktivním přístupu [okno stanice](/windows/desktop/winstation/window-stations).

Všimněte si, že se odesílají zprávy ladění pomocí základního kontextu zabezpečení vlákna. Zosobnění je dočasně zakázat, aby ladění sestavy můžete zobrazit v situacích, kde zosobnění uživatelů s nízkým oprávněním probíhat, například ve webových aplikacích.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook

Volání [SetPipeName](#setpipename), [SetTimeout](#settimeout), a [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Název počítače, na které mají být odesílána výstupu ladění. Výchozí hodnota je v místním počítači.

*szPipeName*<br/>
Název pojmenovaného kanálu, které mají posílat výstup ladění.

*dwTimeout*<br/>
Doba v milisekundách, že tato třída bude čekat pojmenovaný kanál k dispozici.

##  <a name="dtor"></a>  Cdebugreporthook –:: ~ cdebugreporthook –

Volání [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc

Vlastní vytváření sestav funkce, která je připojit vykazování procesu ladění za běhu C.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy (_CRT_WARN, _CRT_ERROR nebo _CRT_ASSERT).

*message*<br/>
Řetězec zprávy.

*returnValue*<br/>
Hodnota, která má být vrácen podle [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu FALSE, pokud háku zpracovává zprávu dotyčný zcela tak, aby další vykazování se nevyžaduje. Vrátí TRUE, pokud `_CrtDbgReport` ohlaste zprávy běžným způsobem.

### <a name="remarks"></a>Poznámky

Vytváření sestav funkce se pokusí otevřít pojmenovaného kanálu a komunikaci s procesem na druhém konci. Pokud kanál je zaneprázdněný, vytváření sestav funkce počká, až do kanálu je zdarma nebo vyprší časový limit. Časový limit lze nastavit pomocí konstruktoru nebo volání [CDebugReportHook::SetTimeout](#settimeout).

Kód této funkce se spustí v kontextu základního zabezpečení volajícího vlákna, to znamená, je po dobu trvání této funkce zakázaná zosobnění.

##  <a name="removehook"></a>  CDebugReportHook::RemoveHook

Voláním této metody lze zastavit odesílání sestav ladění k pojmenovanému kanálu a obnovit předchozí háku sestavy.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Poznámky

Volání [_crtsetreporthook2 –](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) obnovit předchozí háku sestavy.

##  <a name="sethook"></a>  CDebugReportHook::SetHook

Voláním této metody lze zahájit odesílání sestav ladění k pojmenovanému kanálu.

```
void SetHook() throw();
```

### <a name="remarks"></a>Poznámky

Volání [_crtsetreporthook2 –](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) přehledné sestavy ladění směrován přes [CDebugReportHookProc](#cdebugreporthookproc) k pojmenovanému kanálu. Tato třída uchovává informace o předchozích háku sestavy tak, aby ji bylo možné obnovit, kdy [RemoveHook](#removehook) je volána.

##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName

Voláním této metody nastavte počítač a název kanálu, do které se pošlou sestav ladění.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Název počítače, na které mají být odesílána výstupu ladění.

*szPipeName*<br/>
Název pojmenovaného kanálu, které mají posílat výstup ladění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout

Voláním této metody lze nastavit čas v milisekundách, že tato třída bude čekat pojmenovaný kanál k dispozici.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Doba v milisekundách, že tato třída bude čekat pojmenovaný kanál k dispozici.

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)
