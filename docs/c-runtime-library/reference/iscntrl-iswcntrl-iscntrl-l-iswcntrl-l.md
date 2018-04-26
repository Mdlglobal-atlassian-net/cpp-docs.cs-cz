---
title: iscntrl –, iswcntrl –, _iscntrl_l –, _iswcntrl_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
dev_langs:
- C++
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c0eecee5d33bd9e250e88021556625101202082
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="iscntrl-iswcntrl-iscntrll-iswcntrll"></a>iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l

Určuje, zda celé reprezentuje řídicí znak.

## <a name="syntax"></a>Syntaxe

```C
int iscntrl(
   int c
);
int iswcntrl(
   wint_t c
);
int _iscntrl_l(
   int c,
   _locale_t locale
);
int _iswcntrl_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo pro testování

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Všechny tyto rutiny vrátí nenulové hodnoty, pokud *c* je konkrétní reprezentace řídicí znak. **iscntrl –** vrátí nenulovou hodnotu, pokud *c* je řídicí znak (0x00-0x1F nebo 0x7F). **iswcntrl –** vrátí nenulovou hodnotu, pokud *c* je ovládací prvek celý znak. Všechny tyto rutiny vrátí hodnotu 0, pokud *c* nesplňuje podmínky testu.

Verze tyto funkce, které mají **_l** příponu použijte parametr národního prostředí, je předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Chování **iscntrl –** a **_iscntrl_l –** není definován, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). V případě použití knihovny ladění CRT a *c* není jednou z těchto hodnot, funkce raise kontrolní výrazy.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istcntrl –**|**iscntrl**|**iscntrl**|**iswcntrl –**|
|**_istcntrl_l –**|**_iscntrl_l**|**_iscntrl_l**|**_iswcntrl_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**iscntrl**|\<ctype.h >|
|**iswcntrl –**|\<ctype.h > nebo \<wchar.h >|
|**_iscntrl_l**|\<ctype.h >|
|**_iswcntrl_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
