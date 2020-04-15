---
title: raise
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: b38a3430274b2324e345be30ce9e38f0c2749fa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338267"
---
# <a name="raise"></a>raise

Odešle signál do spuštěného programu.

> [!NOTE]
> Tuto metodu nepoužívejte k vypnutí aplikace pro Microsoft Store, s výjimkou scénářů testování nebo ladění. Programové nebo způsoby, jak zavřít aplikaci store, nejsou povoleny v souladu se [zásadami Microsoft Storu](/legal/windows/agreements/store-policies). Další informace naleznete v [tématu Životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*Sig*<br/>
Signál má být zvednut.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, **raise** vrátí 0. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **raise** odešle *sig* do spuštěného programu. Pokud předchozí volání **signálu** nainstaloval funkci zpracování signálu pro *sig*, **raise** provede tuto funkci. Pokud nebyla nainstalována žádná funkce obslužné rutiny, je provedena výchozí akce spojená s hodnotou signálu *sig* následujícím způsobem.

|Signál|Význam|Výchozí|
|------------|-------------|-------------|
|**SIGABRT**|Abnormální ukončení|Ukončí volající program s ukončovacím kódem 3|
|**SIGFPE**|Chyba s plovoucí desetinnou desetinnou desetinnou tí|Ukončí volající program.|
|**SIGILL (SIGILL)**|Nelegální výuka|Ukončí volající program.|
|**SIGINT**|Přerušení CTRL+C|Ukončí volající program.|
|**SIGSEGV**|Neplatný přístup k úložišti|Ukončí volající program.|
|**SIGTERM**|Žádost o ukončení odeslaná do programu|Ignoruje signál|

Pokud argument není platný signál, jak je uvedeno výše, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud není zpracována, funkce nastaví **errno** na **EINVAL** a vrátí nenulovou hodnotu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**raise**|\<signal.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Přerušení](abort.md)<br/>
[signal](signal.md)<br/>
