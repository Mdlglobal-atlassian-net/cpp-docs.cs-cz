---
title: _CrtSetReportHook
ms.date: 11/04/2016
apiname:
- _CrtSetReportHook
apilocation:
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
apitype: DLLExport
f1_keywords:
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 7dcb916ea920751618ffa6a4afbcde8df5e35cba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343038"
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

Nainstaluje klienta definované funkce vytváření sestav tak, že zapojení do procesu vytváření sestav ladění za běhu jazyka C (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parametry

*reportHook*<br/>
Nový klient definované generování sestav funkce k připojení do C run-time ladění procesu vytváření sestav.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí klienta definované funkce vytváření sestav.

## <a name="remarks"></a>Poznámky

**_CrtSetReportHook** umožňuje aplikaci používat vlastní vytváření sestav funkce do knihovny ladění za běhu C proces vytváření sestav. V důsledku, vždy, když [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) nazývá Pokud chcete vygenerovat sestavu ladění, je aplikace reporting nejdříve volána. Tato funkce umožňuje aplikaci k provedení operace, jako je filtrování sestavy ladění, tak můžete zaměřit na konkrétní přidělení typy nebo odeslání hlášení o cíle není k dispozici pomocí **_CrtDbgReport**. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetReportHook** odstraněna během předběžného zpracování.

Robustnější verzi **_CrtSetReportHook**, naleznete v tématu [_crtsetreporthook2 –](crtsetreporthook2-crtsetreporthookw2.md).

**_CrtSetReportHook** funkce nainstaluje nový klient definovaný podle funkce vytváření sestav *reportHook* a vrátí předchozí volání definované klienta. Následující příklad ukazuje, jak by měla být prototypem háku sestavy definované klienta:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

kde *reportType* je typ sestavy ladění (**_CRT_WARN**, **_CRT_ERROR**, nebo **_CRT_ASSERT**), *zpráva* sestaveném ladění zpráva uživateli mají být obsažena v sestavě, a **returnValue** je hodnotu zadanou pomocí klienta definované funkce vytváření sestav, který by měl být vrácen **_ Crtdbgreport –**. Úplný popis typů sestav k dispozici, najdete v článku [_CrtSetReportMode](crtsetreportmode.md) funkce.

Pokud klient uživatelsky definovaná funkce generování sestav zcela zpracovává zprávy ladění tak, aby další vykazování se nevyžaduje, pak by měl vrátit funkci **TRUE**. Pokud funkce vrátí **FALSE**, **_CrtDbgReport** je volána k vygenerují sestavu ladění pomocí aktuální nastavení pro typ sestavy, režimu a soubor. Kromě toho, že zadáte **_CrtDbgReport** návratová hodnota v **returnValue**, aplikace můžete také určit, zda dojde k přerušení ladění. Úplný popis fungování nakonfigurovaný a vygeneruje sestavu ladění, naleznete v tématu **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md), a **_CrtDbgReport**.

Další informace o použití jiné funkce háku podporující za běhu a psaní vlastních klienta definované funkce háku naleznete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Pokud vaše aplikace je kompilována s **/CLR** a vytváření sestav funkce se volá, když má aplikace se ukončila hlavní, modul CLR vyvolá výjimku, pokud žádné funkce CRT volá funkci generování sestav.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
