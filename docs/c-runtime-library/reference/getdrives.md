---
title: _getdrives – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getdrives
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getdrives
- _getdrives
dev_langs:
- C++
helpviewer_keywords:
- _getdrives function
- getdrives function
- disk drives
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec2834e9f755a8039326ea6fb193c4bc591355ac
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399942"
---
# <a name="getdrives"></a>_getdrives

Vrátí bitová maska, která představuje aktuálně k dispozici disky.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned long _getdrives( void );
```

## <a name="return-value"></a>Návratová hodnota

Pokud funkci úspěšné, je vrácenou hodnotu bitová maska, která představuje aktuálně k dispozici disky. Bit pozice 0 (nejmenší významných bitů) jednotce A, je bit pozici 1 jednotka B se bit pozici 2 jednotce C a tak dále. Pokud funkce selže, je vrácenou hodnotu nula. Chcete-li získat rozšířené informace o chybě, volejte **GetLastError**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdrives**|\<Direct.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getdrives.c
// This program retrives and lists out
// all the logical drives that are
// currently mounted on the machine.

#include <windows.h>
#include <direct.h>
#include <stdio.h>
#include <tchar.h>

TCHAR g_szDrvMsg[] = _T("A:\n");

int main(int argc, char* argv[]) {
   ULONG uDriveMask = _getdrives();

   if (uDriveMask == 0)
   {
      printf( "_getdrives() failed with failure code: %d\n",
              GetLastError());
   }
   else
   {
      printf("The following logical drives are being used:\n");

      while (uDriveMask) {
         if (uDriveMask & 1)
            printf(g_szDrvMsg);

         ++g_szDrvMsg[0];
         uDriveMask >>= 1;
      }
   }
}
```

```Output
The following logical drives are being used:
A:
C:
D:
E:
```

## <a name="see-also"></a>Viz také

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
