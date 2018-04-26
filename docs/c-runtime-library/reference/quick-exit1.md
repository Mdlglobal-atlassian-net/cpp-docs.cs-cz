---
title: quick_exit1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs:
- C++
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fde06fc83b27b8bba43e3fa929cc8b97bb68dd06
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="quickexit"></a>quick_exit

Způsobí ukončení normální programu proběhnout.

## <a name="syntax"></a>Syntaxe

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Kód stavu se vraťte do prostředí hostitele.

## <a name="return-value"></a>Návratová hodnota

**Quick_exit** funkce nelze vrátit k jeho volajícího.

## <a name="remarks"></a>Poznámky

**Quick_exit** funkce způsobí ukončení normální programu. Zavolá žádné funkce registrovaných **atexit**, **_onexit –** nebo signál registrovaných obslužné rutiny **signál** funkce. Pokud není definován chování **quick_exit** nazývá více než jednou, nebo pokud **ukončete** je volána funkce.

**Quick_exit** funkce volání v last-in, pořadí ven (LIFO), funkce registrovaných **at_quick_exit**, s výjimkou pro tyto funkce už voláno, když byl zaregistrován funkce.  Pokud není definován chování [longjmp](longjmp.md) přišla v průběhu hovoru registrovaná funkce, která by ukončit volání funkce.

Po zavolání registrovaná funkce **quick_exit** vyvolá **_exit –** pomocí *stav* hodnota vrátit kontrolu hostitelské prostředí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**quick_exit**|\<Process.h > nebo \<stdlib.h >|

Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
