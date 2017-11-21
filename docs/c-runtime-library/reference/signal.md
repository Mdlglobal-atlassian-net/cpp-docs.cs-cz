---
title: "signál | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: signal
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
f1_keywords: signal
dev_langs: C++
helpviewer_keywords: signal function
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 125512ba670c438ff7694b05fa73822273aba664
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="signal"></a>signal
Nastaví přerušení zpracování signál.  
  
> [!IMPORTANT]
>  Nepoužívejte tuto metodu vypnout [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace, kromě testování nebo ladění scénáře. Zavřete způsoby programový nebo uživatelského rozhraní [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace nejsou povolené podle části 3.6 z [požadavky na certifikaci aplikace systému Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Další informace najdete v tématu [životního cyklu aplikací (aplikace pro Windows Store)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### <a name="parameters"></a>Parametry  
 `sig`  
 Hodnota signál.  
  
 `func`  
 Funkce, která má být proveden. První parametr je hodnota signál a druhý parametr je dílčí kód, který lze použít při první parametr je sigfpe –.  
  
## <a name="return-value"></a>Návratová hodnota  
 `signal`Vrátí předchozí hodnotu `func` který je spojen s danou signál. Například pokud předchozí hodnotu `func` byla `SIG_IGN`, vrácená hodnota je také `SIG_IGN`. Vrácená hodnota `SIG_ERR` označuje chybu; v takovém případě `errno` je nastaven na `EINVAL`.  
  
 V tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 `signal` Funkce umožňuje proces vyberte jednu z několik způsobů, jak zpracovat signál přerušení z operačního systému. `sig` Argument je přerušení, ke kterému `signal` reaguje; musí mít jednu z následujících manifestu konstant, které jsou definovány v SIGNÁL. H.  
  
|`sig`Hodnota|Popis|  
|-----------------|-----------------|  
|`SIGABRT`|Abnormální ukončení|  
|`SIGFPE`|Chyba s plovoucí desetinnou čárkou|  
|`SIGILL`|Neplatná instrukce|  
|`SIGINT`|CTRL + C signál|  
|`SIGSEGV`|Přístup k úložišti neplatný|  
|`SIGTERM`|Žádost o ukončení|  
  
 Pokud `sig` není jedním z výše uvedené hodnoty, je vyvolána obslužná rutina neplatný parametr, jak jsou definovány v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `SIG_ERR`.  
  
 Ve výchozím nastavení `signal` ukončí volací program s ukončovacím kódem 3, bez ohledu na hodnotu `sig`.  
  
> [!NOTE]
>  `SIGINT`není podporován pro všechny aplikace typu Win32. Když dojde k přerušení CTRL + C, operační systémy Win32 generovat nové vlákno konkrétně zpracování této přerušení. To může způsobit jedním vláknem aplikaci, například ten, který v systému UNIX se stane s více vlákny a způsobit neočekávané chování.  
  
 `func` Argument je adresu na signál obslužnou rutinu, která můžete psát, nebo na jednu z předdefinovaných konstanty `SIG_DFL` nebo `SIG_IGN`, která je definována v SIGNÁL. H. Pokud `func` je funkce, je nainstalován jako obslužná rutina signál pro danou signál. Obslužná rutina signál prototypu vyžaduje jeden argument formální, `sig`, typu `int`. Operační systém poskytuje skutečné argument prostřednictvím `sig` když dojde k přerušení; argument je signál, která generuje přerušení. Proto můžete šesti manifestu konstanty (uvedené v předchozí tabulce) ve vaší obslužné rutiny signál k určení které přerušení došlo k chybě a proveďte příslušnou akci. Například můžete volat `signal` na dvou různých signály přiřadit stejné obslužné rutiny a otestujte dvakrát `sig` argument v rutině k provádění různých akcí podle signál přijata.  
  
 Pokud testujete výjimky s plovoucí desetinnou čárkou (`SIGFPE`), `func` odkazuje na funkci, která přebírá volitelné druhý argument, který je jedním z několika manifestu konstanty – definované v FLOAT. H – formuláře `FPE_xxx`. Když `SIGFPE` signál dojde, můžete otestovat hodnotu druhý argument, abyste zjistili druh výjimek plovoucí desetinné čárky a proveďte příslušnou akci. Tento argument a jeho možné hodnoty jsou rozšíření Microsoft.  
  
 S plovoucí desetinnou čárkou výjimky, hodnota `func` není resetovat, když je obdržena signál. Obnovit z s plovoucí desetinnou čárkou výjimky, zkuste použít / s výjimkou bodu klauzule k obklopit procedura operace. Je také možné obnovit pomocí [setjmp](../../c-runtime-library/reference/setjmp.md) s [longjmp](../../c-runtime-library/reference/longjmp.md). V obou případech volající proces obnoví spuštění a opustí s plovoucí desetinnou čárkou stav procesu není definovaná.  
  
 Pokud obslužná rutina signál vrátí, volající proces obnoví spuštění hned za bod, ve kterém přijala signál přerušení. To platí bez ohledu na druh signál nebo provozním režimu.  
  
 Před provedením zadaná funkce hodnotu `func` je nastaven na `SIG_DFL`. Další signál přerušení považuje, jak je popsáno pro `SIG_DFL`, pokud uplynulého volat na `signal` neurčí jinak. Tato funkce slouží k resetování signály v volaná funkce.  
  
 Protože rutiny signál – obslužná rutina se obvykle říká asynchronně, když dojde přerušení, může funkce obslužných rutin signál k řízení při spuštění operace nekompletní a v neznámém stavu. Následující seznam shrnuje omezení, které určují, funkcích, které můžete použít v signál rutiny ovladače.  
  
-   To není problém nižší úrovně nebo STDIO. H vstupní a výstupní rutiny (například `printf` nebo `fread`).  
  
-   Nevolejte haldy rutiny nebo všechny rutiny, která používá rutiny haldy (například `malloc`, `_strdup`, nebo `_putenv`). V tématu [malloc –](../../c-runtime-library/reference/malloc.md) Další informace.  
  
-   Nepoužívejte všechny funkce, která generuje volání systému (například `_getcwd` nebo `time`).  
  
-   Nepoužívejte `longjmp` Pokud přerušení je způsobena výjimek plovoucí desetinné čárky (tedy `sig` je `SIGFPE`). V takovém případě nejprve inicializovat balíček s plovoucí desetinnou čárkou s použitím volání `_fpreset`.  
  
-   Nepoužívejte všechny rutiny překrytí.  
  
 Program musí obsahovat s plovoucí desetinnou čárkou kódu, pokud je na depeše `SIGFPE` výjimky pomocí funkce. Pokud program nemá s plovoucí desetinnou čárkou kód a kód pro zpracování signál běhové knihovny vyžaduje, jenom deklarovat volatile dvojitou a provést jeho inicializaci na nulu:  
  
`volatile double d = 0.0f;`  
  
 `SIGILL` a `SIGTERM` signály, které nejsou generované v rámci systému Windows. Jsou zahrnuté pro kompatibilitu ANSI. Proto můžete nastavit signál obslužné rutiny pro tyto signály pomocí `signal`, a také explicitně vygenerovat tyto signály voláním [vyvolat](../../c-runtime-library/reference/raise.md).  
  
 V vytvářený procesy, které jsou vytvořené pomocí volání nejsou zachována nastavení signál `_exec` nebo `_spawn` funkce. Signál nastavení se obnoví na výchozí hodnoty v nový proces.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`signal`|\<Signal.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `signal` přidat některé vlastní chování `SIGABRT` signál. Další informace o chování přerušení najdete v tématu [_set_abort_behavior –](../../c-runtime-library/reference/set-abort-behavior.md).  
  
```cpp  
// crt_signal.c  
// compile with: /EHsc /W4  
// Use signal to attach a signal handler to the abort routine  
#include <stdlib.h>  
#include <signal.h>  
#include <tchar.h>  
  
void SignalHandler(int signal)  
{  
    if (signal == SIGABRT) {  
        // abort signal handler code  
    } else {  
        // ...  
    }  
}  
  
int main()  
{  
    typedef void (*SignalHandlerPointer)(int);  
  
    SignalHandlerPointer previousHandler;  
    previousHandler = signal(SIGABRT, SignalHandler);  
  
    abort();  
}  
```  
  
```Output  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_fpreset –](../../c-runtime-library/reference/fpreset.md)   
 [_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)