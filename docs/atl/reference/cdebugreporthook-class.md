---
title: CDebugReportHook – třída
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
ms.openlocfilehash: 7187448b2ba2c9d3ab0399aa3e75ce8d757bfec1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496775"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook – třída

Tato třída slouží k posílání ladicích sestav do pojmenovaného kanálu.

## <a name="syntax"></a>Syntaxe

```
class CDebugReportHook
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Volá [SetPipeName](#setpipename), [setTimeout](#settimeout)a [SetHook](#sethook).|
|[CDebugReportHook::~CDebugReportHook](#dtor)|Volá [CDebugReportHook:: RemoveHook](#removehook).|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|Tras Vlastní funkce vytváření sestav, která je zapojena do procesu generování sestav ladění modulu C Runtime.|
|[CDebugReportHook::RemoveHook](#removehook)|Voláním této metody zastavíte odesílání sestav ladění do pojmenovaného kanálu a obnovíte předchozí zavěšení sestavy.|
|[CDebugReportHook::SetHook](#sethook)|Voláním této metody spustíte odesílání sestav ladění do pojmenovaného kanálu.|
|[CDebugReportHook::SetPipeName](#setpipename)|Voláním této metody nastavte počítač a název kanálu, do kterého budou odesílány sestavy ladění.|
|[CDebugReportHook:: SetTimeout](#settimeout)|Voláním této metody nastavíte dobu v milisekundách, po kterou bude tato třída čekat na zpřístupnění pojmenovaného kanálu.|

## <a name="remarks"></a>Poznámky

Vytvoření instance této třídy v ladicích sestavení vašich služeb nebo aplikací pro odesílání sestav ladění pojmenovanému kanálu. Sestavy ladění jsou generovány voláním [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) nebo pomocí obálky pro tuto funkci, jako jsou například makra [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) a [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) .

Použití této třídy vám umožní interaktivně ladit součásti běžící v neinteraktivních [stanicích okna](/windows/win32/winstation/window-stations).

Všimněte si, že sestavy ladění jsou odesílány pomocí podkladového kontextu zabezpečení vlákna. Zosobnění je dočasně zakázané, aby se sestavy ladění mohly zobrazit v situacích, kdy dochází k zosobnění uživatelů s nízkým oprávněním, jako jsou například webové aplikace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Volá [SetPipeName](#setpipename), [setTimeout](#settimeout)a [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Název počítače, do kterého má být odeslán výstup ladění. Výchozí hodnota je místní počítač.

*szPipeName*<br/>
Název pojmenovaného kanálu, do kterého má být odeslán výstup ladění.

*dwTimeout*<br/>
Čas v milisekundách, který bude tato třída čekat na zpřístupnění pojmenovaného kanálu.

##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook

Volá [CDebugReportHook:: RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

Vlastní funkce vytváření sestav, která je zapojena do procesu generování sestav ladění modulu C Runtime.

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
Řetězec zprávy

*returnValue*<br/>
Hodnota, která má být vrácena funkcí [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu FALSE, pokud zavěšení zprávy zcela zpracuje, takže není nutné provádět žádné další hlášení. Vrátí hodnotu true `_CrtDbgReport` , pokud by měla zpráva vykazovat normálním způsobem.

### <a name="remarks"></a>Poznámky

Funkce vytváření sestav se pokusí otevřít pojmenovaný kanál a komunikovat s procesem na druhém konci. Pokud je kanál zaneprázdněný, funkce generování sestav počká, dokud nebude kanál bezplatný nebo vypršel časový limit. Časový limit lze nastavit pomocí konstruktoru nebo voláním metody [CDebugReportHook:: setTimeout](#settimeout).

Kód v této funkci je spuštěn v podkladovém kontextu zabezpečení volajícího vlákna, to znamená, že zosobnění je zakázáno po dobu trvání této funkce.

##  <a name="removehook"></a>CDebugReportHook::RemoveHook

Voláním této metody zastavíte odesílání sestav ladění do pojmenovaného kanálu a obnovíte předchozí zavěšení sestavy.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Poznámky

Zavolá [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) k obnovení předchozího zavěšení sestavy.

##  <a name="sethook"></a>CDebugReportHook::SetHook

Voláním této metody spustíte odesílání sestav ladění do pojmenovaného kanálu.

```
void SetHook() throw();
```

### <a name="remarks"></a>Poznámky

Volá [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) , aby sestavy ladění byly směrovány prostřednictvím [CDebugReportHookProc](#cdebugreporthookproc) do pojmenovaného kanálu. Tato třída uchovává předchozí zavěšení sestavy, aby bylo možné ho obnovit při volání [RemoveHook](#removehook) .

##  <a name="setpipename"></a>CDebugReportHook::SetPipeName

Voláním této metody nastavte počítač a název kanálu, do kterého budou odesílány sestavy ladění.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parametry

*szMachineName*<br/>
Název počítače, do kterého má být odeslán výstup ladění.

*szPipeName*<br/>
Název pojmenovaného kanálu, do kterého má být odeslán výstup ladění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="settimeout"></a>CDebugReportHook:: SetTimeout

Voláním této metody nastavíte dobu v milisekundách, po kterou bude tato třída čekat na zpřístupnění pojmenovaného kanálu.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Čas v milisekundách, který bude tato třída čekat na zpřístupnění pojmenovaného kanálu.

## <a name="see-also"></a>Viz také:

[Třídy](../../atl/reference/atl-classes.md)
