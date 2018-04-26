---
title: _swab – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab841400bd002595508806797a9a204415b5f15
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="swab"></a>_swab

Záměna bajtů.

## <a name="syntax"></a>Syntaxe

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Parametry

*src* dat zkopírovat a vzájemně zaměněny.

*cíle* umístění úložiště pro prohodil data.

*n* počet bajtů, které mají být zkopírovány a vzájemně zaměněny.

## <a name="return-value"></a>Návratová hodnota

**Swab –** funkce nevrací hodnotu. Funkce sady **errno** k **einval –** Pokud buď *src* nebo *cíle* ukazatel má hodnotu null nebo *n* je menší než nula a neplatný parametr je volána obslužná rutina, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a ostatní návratové kódy.

## <a name="remarks"></a>Poznámky

Pokud *n* i, je **_swab –** funkce kopie *n* bajtů z *src*prohození každý pár přiléhající bajtů a ukládá výsledek v *cíle*. Pokud *n* je liché, **_swab –** zkopíruje a prohození první *n*-1 bajtů *src*, a není zkopírovaný poslední bajt. **_Swab –** funkce se obvykle používá k přípravě binární data pro přenos do počítače, které používají různé bajtů pořadí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h > C++: \<cstdlib – > nebo \<stdlib.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>Viz také

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
