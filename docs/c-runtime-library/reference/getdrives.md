---
title: _getdrives
ms.date: 11/04/2016
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
helpviewer_keywords:
- _getdrives function
- getdrives function
- disk drives
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
ms.openlocfilehash: d34b03e307a9c619fab077973e4cc0a4c644de6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597255"
---
# <a name="getdrives"></a>_getdrives

Vrátí bitová maska, která představuje aktuálně k dispozici diskové jednotky.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned long _getdrives( void );
```

## <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je bitová maska, která představuje aktuálně k dispozici diskové jednotky. Bitová pozice 0 (nejméně významných bitů) je jednotce A, bitová pozice 1 je jednotka B, bitová pozice 2 je jednotce C a tak dále. Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, volejte **GetLastError**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdrives**|\<Direct.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
