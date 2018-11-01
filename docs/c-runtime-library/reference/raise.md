---
title: raise
ms.date: 1/02/2018
apiname:
- raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 68d1cc653b955e607648e4d30562d2b77e3520e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638110"
---
# <a name="raise"></a>raise

Odešle signál k prováděnému programu.

> [!NOTE]
> Nepoužívejte tuto metodu k vypnutí aplikace Microsoft Store, s výjimkou testování nebo ladění scénářů. Zavření aplikace pro Store způsoby programátorské nebo uživatelské rozhraní nejsou povoleny podle [zásady Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Signál, chcete-li být vyvolána.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **vyvolat** vrátí hodnotu 0. V opačném případě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Vyvolat** funkce odešle *sig* prováděnému programu. Pokud předchozí volání **signál** má nainstalovanou funkci pro zpracování signálu pro *sig*, **vyvolat** spustí tuto funkci. Pokud nebyla nainstalována žádná obslužná rutina funkce, výchozí akce přidružené k hodnotě signálu *sig* je převzata, následujícím způsobem.

|Signál|Význam|Výchozí|
|------------|-------------|-------------|
|**SIGABRT**|Abnormální ukončení|Ukončí volající program s ukončovacím kódem 3|
|**SIGFPE**|Chyba plovoucí desetinné čárky|Ukončí volající program|
|**SIGILL**|Neplatná instrukce|Ukončí volající program|
|**SIGINT**|Přerušení CTRL + C|Ukončí volající program|
|**SIGSEGV**|Neplatný přístup k úložišti|Ukončí volající program|
|**SIGTERM**|Žádost o ukončení odeslána programu|Ignoruje signál|

Pokud argument není platný signál, jak je uvedeno výše, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud není zpracována, funkce nastaví **errno** k **EINVAL** a vrátí nenulovou hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**raise**|\<signal.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
