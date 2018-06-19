---
title: _exec, _wexec – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
dev_langs:
- C++
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 728c4878736d2e0cafc94660db3d9a709f87715f
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451521"
---
# <a name="exec-wexec-functions"></a>_exec, _wexec – funkce
Každá funkce této rodiny načte a spustí nový proces:  
  
|||  
|-|-|  
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|  
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|  
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|  
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|  
  
 Písmeno na konci názvu funkce určuje variantu.  
  
|přípona funkce _exec|Popis|  
|----------------------------|-----------------|  
|`e`|`envp`, pole ukazatelů nastavení prostředí, je předáno novému procesu.|  
|`l`|Argumenty příkazového řádku jsou funkci `_exec` předány jednotlivě. Obvykle se používají, pokud je počet parametrů nového procesu předem známý.|  
|`p`|Proměnná prostředí `PATH` slouží k vyhledání souboru, který chcete spustit.|  
|`v`|`argv`, pole ukazatelů na argumenty příkazového řádku, je předáno funkci `_exec`. Obvykle se používá, pokud je počet parametrů nového procesu proměnný.|  
  
## <a name="remarks"></a>Poznámky  
 Každá funkce `_exec` načte a spustí nový proces. Všechny `_exec` funkce pomocí stejné funkce operačního systému ([CreateProcess –](http://msdn.microsoft.com/library/windows/desktop/ms682425.aspx)). Funkce `_exec` automaticky zpracují argumenty vícebajtových řetězců znaků podle potřeby a rozpoznají vícebajtové sekvence znaků podle aktuálně použité vícebajtové znakové stránky. Funkce `_wexec` jsou širokoznaké verze funkcí `_exec`. Funkce `_wexec` se chovají stejně jako jejich protějšky rodiny `_exec` s tím rozdílem, že nezpracovávají vícebajtové řetězce znaků.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_texecl`|`_execl`|`_execl`|`_wexecl`|  
|`_texecle`|`_execle`|`_execle`|`_wexecle`|  
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|  
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|  
|`_texecv`|`_execv`|`_execv`|`_wexecv`|  
|`_texecve`|`_execve`|`_execve`|`_wexecve`|  
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|  
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|  
  
 Parametr `cmdname` určuje soubor, který má být spuštěn jako nový proces. Lze zadat úplnou cestu (z kořenového adresáře), část cesty (z aktuálního pracovního adresáře) nebo název souboru. Pokud parametr `cmdname` nemá příponu názvu souboru nebo nekončí tečkou (.), funkce `_exec` vyhledá soubor s tímto názvem. Pokud je hledání neúspěšné, pokusí se vyhledat stejný základní název s příponou názvu souboru .com a poté .exe, .bat a .cmd. Pokud má parametr `cmdname` příponu názvu souboru, je pro hledání použita pouze tato přípona. Pokud parametr `cmdname` končí tečkou, vyhledá funkce `_exec` parametr `cmdname` bez přípony názvu souboru. Funkce `_execlp`, `_execlpe`, `_execvp` a `_execvpe` hledají parametr `cmdname` (stejným způsobem) v adresářích určených proměnnou prostředí `PATH`. Pokud parametr `cmdname` obsahuje specifikátor jednotky nebo jakákoli lomítka (pokud se jedná o relativní cestu), volání funkce `_exec` vyhledá pouze zadaný soubor. Cesta není prohledána.  
  
 Parametry jsou novému procesu předány jedním nebo více ukazateli na řetězce znaků jako parametry volání funkce `_exec`. Tyto řetězce znaků tvoří seznam parametrů nového procesu. Celková délka zděděného nastavení prostředí a řetězců tvořících seznam parametrů nového procesu nesmí překročit 32 kB. Ukončující znak null ('\0') každého řetězce není v tomto počtu zahrnut, ale znaky mezery (automaticky vložené pro oddělení parametrů) se počítají.  
  
> [!NOTE]
>  Mezery vložené do řetězců mohou způsobit neočekávané chování, například výsledkem předání řetězce `_exec` funkci `"hi there"` bude nový proces, který získá dva argumenty `"hi"` a `"there"`. Proces selže, pokud bylo záměrem, aby nový proces otevřel soubor s názvem "hi there". Tomu lze zabránit citováním řetězce: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  Nepředávejte funkci `_exec` vstup uživatele bez explicitní kontroly jeho obsahu. `_exec` bude mít za následek volání [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425.aspx) , mějte na paměti tato nekvalifikované cesta názvy může vést k potenciální ohrožení zabezpečení.  
  
 `_exec` Funkcí ověření jejich parametrů. Pokud očekávaný parametry jsou ukazatelé s hodnotou null, prázdné řetězce, nebo tento parametr vynechán, `_exec` funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1. Je proveden žádný nový proces.  
  
 Ukazatelé na argumenty mohou být předány jako oddělené parametry (ve funkcích `_execl`, `_execle`, `_execlp` a `_execlpe`) nebo jako pole ukazatelů (ve funkcích `_execv`, `_execve`, `_execvp` a `_execvpe`). Nejméně jeden parametr, `arg0`, musí být předán novému procesu. Tento parametr je `argv`[0] nového procesu. Tento parametr je obvykle kopií parametru `cmdname`. (Jiná hodnota nevyvolá chybu.)  
  
 Volání funkcí `_execl`, `_execle`, `_execlp` a `_execlpe` se obvykle používají, pokud je počet parametrů předem známý. Parametr `arg0` je obvykle ukazatel na parametr `cmdname`. Parametry `arg1` až `argn` odkazují na řetězce znaků, které tvoří nový seznam parametrů. Nulový ukazatel musí následovat parametr `argn`, což označuje konec seznamu parametrů.  
  
 Volání funkcí `_execv`, `_execve`, `_execvp` a `_execvpe` jsou užitečná, když je počet parametrů nového procesu proměnný. Odkazy na parametry jsou předány jako pole `argv`. Parametr `argv`[0] je obvykle ukazatel na parametr `cmdname`. Parametry `argv`[1] až `argv`[`n`] odkazují na řetězce znaků, které tvoří nový seznam parametrů. Parametr `argv`[`n`+ 1] musí být **NULL** ukazatel na konec seznamu parametrů.  
  
 Soubory, které jsou při volání funkce `_exec` otevřeny, zůstanou v novém procesu otevřeny. Při volání funkcí `_execl`, `_execlp`, `_execv` a `_execvp` nový proces zdědí prostředí volajícího procesu. Volání funkcí `_execle`, `_execlpe`, `_execve` a `_execvpe` změní prostředí nového procesu tím, že předají seznam nastavení prostředí pomocí parametru `envp`. Parametr `envp` je pole ukazatelů na znaky, kde každý prvek (s výjimkou posledního prvku) odkazuje na hodnotu null ukončující řetězec definující proměnnou prostředí. Takové řetězec obvykle má tento formulář `NAME` = `value` kde `NAME` je název proměnné prostředí a `value` je řetězcovou hodnotu, na kterou je nastavena tuto proměnnou. (Hodnota `value` není uzavřena v dvojitých uvozovkách.) Poslední elementu `envp` pole by měla být **NULL**. Když `envp` sám o sobě představuje **NULL**, nový proces dědí nastavení prostředí volajícího procesu.  
  
 Program spuštěný pomocí jedné z funkcí `_exec` je vždy načten do paměti, jako by bylo pole maximálního přidělení v záhlaví souboru programu .exe nastaveno na výchozí hodnotu 0xFFFFH.  
  
 Volání funkce `_exec` nezachovávají režimy překladu otevřených souborů. Pokud nový proces musí použít soubory zděděno z volající proces, použijte [_setmode –](../c-runtime-library/reference/setmode.md) rutiny nastavení režimu překlad těchto souborů na požadovaný režim. Je nutné provést explicitní vyprázdnění (pomocí funkce `fflush` nebo `_flushall`) nebo všechny proudy zavřít před voláním funkce `_exec`. Nastavení signálu není zachováno v nových procesech, které byly vytvořeny voláním rutin `_exec`. Nastavení signálu je v novém procesu obnoveno na výchozí hodnotu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_args.c  
// Illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
// This program will be executed by crt_exec which follows.  
  
#include <stdio.h>  
  
int main( int argc,  // Number of strings in array argv  
 char *argv[],       // Array of command-line argument strings  
 char **envp )       // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.   
    printf( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
 Pro spuštění programu Crt_args.exe spusťte následující program:  
  
```  
// crt_exec.c  
// Illustrates the different versions of exec, including  
//      _execl          _execle          _execlp          _execlpe  
//      _execv          _execve          _execvp          _execvpe  
//  
// Although CRT_EXEC.C can exec any program, you can verify how   
// different versions handle arguments and environment by   
// compiling and specifying the sample program CRT_ARGS.C. See   
// "_spawn, _wspawn Functions" for examples of the similar spawn   
// functions.  
  
#include <stdio.h>  
#include <conio.h>  
#include <process.h>  
  
char *my_env[] =     // Environment for exec?e  
{  
   "THIS=environment will be",  
   "PASSED=to new process by",  
   "the EXEC=functions",  
   NULL  
};  
  
int main( int ac, char* av[] )  
{  
   char *args[4];  
   int ch;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );  
      return;  
   }  
  
   // Arguments for _execv?   
   args[0] = av[1];  
   args[1] = "exec??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   switch( atoi( av[2] ) )  
   {  
   case 1:  
      _execl( av[1], av[1], "_execl", "two", NULL );  
      break;  
   case 2:  
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );  
      break;  
   case 3:  
      _execlp( av[1], av[1], "_execlp", "two", NULL );  
      break;  
   case 4:  
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );  
      break;  
   case 5:  
      _execv( av[1], args );  
      break;  
   case 6:  
      _execve( av[1], args, my_env );  
      break;  
   case 7:  
      _execvp( av[1], args );  
      break;  
   case 8:  
      _execvpe( av[1], args, my_env );  
      break;  
   default:  
      break;  
   }  
  
   // This point is reached only if exec fails.   
   printf( "\nProcess was not execed." );  
   exit( 0 );  
}  
```  
  
## <a name="requirements"></a>Požadavky  
  
 **Záhlaví:** process.h  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../c-runtime-library/process-and-environment-control.md)   
 [Přerušení](../c-runtime-library/reference/abort.md)   
 [AtExit](../c-runtime-library/reference/atexit.md)   
 [ukončení, _exit –, _exit –](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn – funkce](../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../c-runtime-library/reference/system-wsystem.md)