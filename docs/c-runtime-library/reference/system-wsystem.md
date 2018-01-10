---
title: "systém, _wsystem – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- system
- _wsystem
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
- _tsystem
- _wsystem
dev_langs: C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c470717d48836fd405e98f5fccca222e87a9c33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="system-wsystem"></a>system, _wsystem
Spustí příkaz.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int system(  
   const char *command   
);  
int _wsystem(  
   const wchar_t *command   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `command`  
 Příkaz, který má být proveden.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud `command` je `NULL` a překladač příkazů je najít, vrátí nenulovou hodnotu. Pokud překladač příkazů není nalezeno, vrátí hodnotu 0 a nastaví `errno` k `ENOENT`. Pokud `command` není `NULL`, `system` vrátí hodnotu, která vrátí překladač příkazů. Vrátí hodnotu 0 pouze v případě, že překladač příkazů vrátí hodnotu 0. Návratová hodnota - 1 znamená chybu, a `errno` nastaven na jednu z následujících hodnot:  
  
 `E2BIG`  
 Seznam argumentů (což je závislé na systém) je příliš dlouhý.  
  
 `ENOENT`  
 Překladač příkazů nebyl nalezen.  
  
 `ENOEXEC`  
 Překladač příkazů soubor nelze provést, protože formát není platný.  
  
 `ENOMEM`  
 Je k dispozici ke spuštění příkazu; není dostatek paměti nebo dostupné paměti je poškozená; nebo neplatné blok neexistuje, což naznačuje, že proces, který je uskutečněním hovoru nebyla přidělena správně.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pro další informace o těchto návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 `system` Funkce předává `command` k překladač příkazů, které provede řetězec jako příkaz operačního systému. `system`používá `COMSPEC` a `PATH` proměnné prostředí najít překladač příkazů soubor CMD.exe. Pokud `command` je `NULL`, funkce právě ověří, zda existuje překladač příkazů.  
  
 Musíte explicitně flush – pomocí `fflush` nebo `_flushall`– nebo zavřete jakýkoli proud před voláním `system`.  
  
 `_wsystem`široká charakterová verze `system`; `command` argument `_wsystem` je široká charakterová řetězec. Tyto funkce chovají stejně jako jinak.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsystem`|`system`|`system`|`_wsystem`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`system`|\<Process.h > nebo \<stdlib.h >|  
|`_wsystem`|\<Process.h > nebo \<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `system` zadejte do textového souboru.  
  
```  
// crt_system.c  
  
#include <process.h>  
  
int main( void )  
{  
   system( "type crt_system.txt" );  
}  
```  
  
## <a name="input-crtsystemtxt"></a>Vstup: crt_system.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Výstup  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall –](../../c-runtime-library/reference/flushall.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)