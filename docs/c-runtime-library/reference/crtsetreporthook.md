---
title: _Crtsetreporthook – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ef76fe0b7befb99b5bf0e8bb69fa1a1229782de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

Nainstaluje klienta definované funkce vytváření sestav tak, že zapojování do procesu vytváření sestav běhové ladění C (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parametry

*reportHook*<br/>
Nový klient definované generování sestav funkce připojí do běhu C ladění procesu generování sestav.

## <a name="return-value"></a>Návratová hodnota

Vrátí předchozí klientský definované funkce vytváření sestav.

## <a name="remarks"></a>Poznámky

**_Crtsetreporthook –** umožňuje aplikaci používat vlastní reporting funkce do ladicí běhové knihovny jazyka C reporting procesu. Výsledkem je, vždy, když [_crtdbgreport –](crtdbgreport-crtdbgreportw.md) je volána k vygenerování sestavy ladění, je reporting funkce je volána nejprve aplikace. Tato funkce umožňuje aplikaci k provedení operací, jako je například filtrování sestavy ladění tak, aby se zaměřit na konkrétní přidělení typy nebo poslat zprávu cíle není k dispozici pomocí **_crtdbgreport –**. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtsetreporthook –** jsou odebrány při předběžném zpracování.

Robustnější verzi **_crtsetreporthook –**, najdete v části [_crtsetreporthook2 –](crtsetreporthook2-crtsetreporthookw2.md).

**_Crtsetreporthook –** funkce nainstaluje nový klient definované reporting zadanou ve funkci *reportHook* a vrátí hák předchozí definované klienta. Následující příklad ukazuje, jak by měla být deklaraci háku klient definované sestavy:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

kde *reportType* je typ sestavy ladění (**_CRT_WARN**, **_CRT_ERROR**, nebo **_CRT_ASSERT**), *zpráva* je zpráva již sestavených ladění uživatele mají být obsažena v sestavě, a **returnValue** je hodnotu zadanou pomocí klienta definované generování sestav funkce, která má být vrácen podle **_ Crtdbgreport –**. Úplný popis typů sestav k dispozici, najdete v článku [_crtsetreportmode –](crtsetreportmode.md) funkce.

Pokud funkci generování sestav definované klienta úplně zpracovává zprávy ladění tak, aby další vykazování se nevyžaduje, pak by měla vrátit funkce **TRUE**. Když funkce vrátí hodnotu **FALSE**, **_crtdbgreport –** je volána při generování sestav o ladění pomocí aktuální nastavení pro typ sestavy, režimu a souboru. Kromě toho zadáním **_crtdbgreport –** vrátit hodnotu v **returnValue**, aplikace můžete taky řídit, jestli zalomení ladění. Úplný popis jak nakonfigurovaný a vygenerovat sestavu ladění, najdete v části **_crtsetreportmode –**, [_crtsetreportfile –](crtsetreportfile.md), a **_crtdbgreport –**.

Další informace o použití jiných podporující háku běhové funkce a psaní vlastního klienta definované funkce háku najdete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Pokud vaše aplikace je kompilovat s **/CLR** a vytváření sestav funkce je volána po aplikaci byl ukončen hlavní, modul CLR bude vyvolána výjimka, pokud žádné funkce CRT volá funkci generování sestav.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
