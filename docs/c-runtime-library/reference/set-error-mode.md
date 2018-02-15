---
title: "_set_error_mode – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
dev_langs:
- C++
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bae0e413e46776d9d0df0508a30905b9fdb09062
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="seterrormode"></a>_set_error_mode
Upraví `__error_mode` určit jiné než výchozí umístění, kde C runtime zapíše chybovou zprávu pro chybu, která může ukončení programu.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `modeval`  
 Cíl chybové zprávy.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí staré nastavení nebo -1, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvky výstupní jímku chyba nastavením hodnotu `__error_mode`. Můžete například přesměrujte výstup do standardní chyba nebo použít `MessageBox` rozhraní API.  
  
 `modeval` Parametr můžete nastavit na jedno z následujících hodnot.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_OUT_TO_DEFAULT`|Chyba podřízený je dáno `__app_type`.|  
|`_OUT_TO_STDERR`|Chyba podřízený je standardní chyba.|  
|`_OUT_TO_MSGBOX`|Podřízený chyba se zprávou.|  
|`_REPORT_ERRMODE`|Sestavy aktuální `__error_mode` hodnota.|  
  
 Pokud je předaná hodnota nejsou uvedeny, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_set_error_mode` nastaví `errno` k `EINVAL` a vrátí hodnotu -1.  
  
 Pokud se používá s [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md), `_set_error_mode` v dialogovém okně zobrazí příkaz neúspěšné a vám zvolit `Ignore` tlačítko, aby mohl pokračovat ke spuštění programu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_error_mode`|\<stdlib.h>|  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
```Output  
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>Viz také  
 [assert Macro, _assert, _wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)