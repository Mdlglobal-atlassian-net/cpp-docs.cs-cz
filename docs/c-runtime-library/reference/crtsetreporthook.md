---
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 77c1e499c66a76027e872783e256754ef72e465d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938516"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

Nainstaluje funkci vytváření sestav definovanou klientem tak, že ji připojíte k procesu generování sestav ladění C za běhu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parametry

*reportHook*<br/>
Nová funkce vytváření sestav definovaná klientem, která se připojí k procesu generování sestav ladění jazyka C za běhu.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí funkci generování sestav definovanou klientem.

## <a name="remarks"></a>Poznámky

**_CrtSetReportHook** umožňuje aplikaci používat vlastní funkci vytváření sestav v procesu generování sestav běhové knihovny jazyka C. V důsledku toho je volána funkce vytváření sestav aplikace, kdykoli je volána [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) k vygenerování sestavy ladění. Tato funkce umožňuje aplikaci provádět operace, jako je filtrování sestav ladění, takže se může soustředit na konkrétní typy přidělení nebo odeslat sestavu do cílových umístění, která nejsou k dispozici pomocí **_CrtDbgReport**. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetReportHook** se během předběžného zpracování odeberou.

Pro robustnější verzi **_CrtSetReportHook**naleznete v tématu [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md).

Funkce **_CrtSetReportHook** nainstaluje novou funkci vytváření sestav definovanou v *reportHook* a vrátí předchozí zavěšení definované klientem. Následující příklad ukazuje, jak by měl být objekt pro zavěšení sestav definovaný klientem prototyp:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

kde *ReportType* je typ sestavy ladění ( **_CRT_WARN**, **_CRT_ERROR**nebo **_CRT_ASSERT**), *zpráva* je plně sestavená zpráva pro ladění uživatele, která bude obsažena v sestavě, a je hodnota **ReturnValue** zadáno funkcí vytváření sestav definovaných klientem, které by měly být vráceny pomocí **_CrtDbgReport**. Úplný popis dostupných typů sestav naleznete v tématu funkce [_CrtSetReportMode](crtsetreportmode.md) .

Pokud funkce generování sestav definovaná klientem zcela zpracuje zprávu ladění tak, že není nutné provádět žádné další hlášení, funkce by měla vrátit **hodnotu true**. Pokud funkce vrátí **hodnotu false**, je volána metoda **_CrtDbgReport** pro vygenerování sestavy ladění pomocí aktuálního nastavení pro typ sestavy, režim a soubor. Kromě toho zadáním návratové hodnoty **_CrtDbgReport** v parametru **ReturnValue**může aplikace také určit, zda dojde k přerušení ladění. Úplný popis způsobu konfigurace a generování sestavy ladění naleznete v tématech **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md)a **_CrtDbgReport**.

Další informace o používání dalších funkcí běhu s podporou zavěšení a psaní vlastních funkcí zavěšení definovaných klientem naleznete v tématu [ladění funkce vidlice](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Pokud je vaše aplikace kompilována s možností **/CLR** a funkce vytváření sestav je volána poté, co aplikace ukončila hlavní, modul CLR vyvolá výjimku, pokud funkce vytváření sestav volá jakékoli funkce CRT.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
