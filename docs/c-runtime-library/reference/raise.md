---
title: vyvolat | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3a41f88bc6883af1db4bbde8729a3638ded64a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="raise"></a>raise

Odešle signál k provádění programu.

> [!NOTE]
> Vypnout aplikaci pomocí Microsoft Store, s výjimkou testování nebo ladění scénáře nepoužívejte tuto metodu. Zavřete aplikaci ve Store způsoby programový nebo uživatelského rozhraní nejsou povolené podle požadavků [Microsoft Store zásady](http://go.microsoft.com/fwlink/?LinkId=865936). Další informace najdete v tématu [životní cyklus aplikace UWP](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Syntaxe

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Signál má být aktivována.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného **vyvolat** vrátí hodnotu 0. Jinak vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Vyvolat** funkce zasílá *sig* provádění programu. Pokud předchozí volání **signál** má nainstalovanou funkci pro zpracování signál *sig*, **vyvolat** spustí této funkce. Pokud byla nainstalována žádná funkce obslužných rutin, výchozí akce asociovaná s hodnotou signál *sig* se provede následujícím způsobem.

|Signál|Význam|Výchozí|
|------------|-------------|-------------|
|**SIGABRT –**|Abnormální ukončení|Ukončí volací program s ukončovacím kódem 3|
|**SIGFPE –**|Chyba s plovoucí desetinnou čárkou|Ukončí volací program|
|**SIGILL –**|Neplatná instrukce|Ukončí volací program|
|**SIGINT –**|CTRL + C přerušení|Ukončí volací program|
|**SIGSEGV –**|Přístup k úložišti neplatný|Ukončí volací program|
|**SIGTERM –**|Ukončení požadavek odeslaný programu|Ignoruje signál|

Pokud argument není platný signál, jak je uvedeno výše, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud nebyla zpracována, nastaví funkci **errno** k **einval –** a vrátí nenulovou hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**raise**|\<signal.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
