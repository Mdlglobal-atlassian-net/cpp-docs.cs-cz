---
title: raise
ms.date: 01/02/2018
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
ms.openlocfilehash: 1354c76207d6cd59249f6c06df88ae23fe69b1e0
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927419"
---
# <a name="raise"></a>raise

Pošle signál vykonávajícímu programu.

> [!NOTE]
> Nepoužívejte tuto metodu k ukončení aplikace Microsoft Store, s výjimkou scénářů testování nebo ladění. Programové a uživatelské možnosti pro zavření aplikace ze Storu nejsou povolené podle [zásad Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Signál, který má být vyvolán.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu **vyvolá** příkaz Turn hodnotu 0. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **vyvolání** pošle do spuštěného programu *SIG* . Pokud předchozí volání **signálu** nainstalovalo funkci pro zpracování signálu pro *SIG*, **vyvolá** rutinu tuto funkci. Pokud není nainstalována žádná funkce obslužné rutiny, je použita výchozí akce přidružená k hodnotě signálu *SIG* , a to následujícím způsobem.

|Nyní|Význam|Výchozí|
|------------|-------------|-------------|
|**SIGABRT**|Abnormální ukončení|Ukončí volající program s ukončovacím kódem 3.|
|**SIGFPE**|Chyba s plovoucí desetinnou čárkou|Ukončí volající program.|
|**SIGILL**|Neplatná instrukce|Ukončí volající program.|
|**SIGINT**|Přerušení CTRL + C|Ukončí volající program.|
|**SIGSEGV**|Neplatný přístup k úložišti|Ukončí volající program.|
|**SIGTERM**|Žádost o ukončení odeslána programu|Ignoruje signál.|

Pokud argument není platný signál, jak je uvedeno výše, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud není zpracován, funkce nastaví **errno** na **EINVAL** a vrátí nenulovou hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**raise**|\<signal.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
