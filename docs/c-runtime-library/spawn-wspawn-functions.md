---
title: "_spawn, _wspawn – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
dev_langs: C++
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0634aeb37d0374f5e6e1dfae0ac004792c279fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="spawn-wspawn-functions"></a>_spawn, _wspawn – funkce
Každý z `_spawn` funkce vytvoří a spustí nový proces:  
  
|||  
|-|-|  
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 Písmen na konci názvu funkce určit variaci.  
  
 `e`  
 `envp`, pole ukazatelů pro nastavení prostředí, je předán nový proces.  
  
 `l`  
 Argumenty příkazového řádku jsou funkci `_spawn` předány jednotlivě. Tato přípona se obvykle používá, když počet parametrů pro nový proces se označuje předem.  
  
 `p`  
 Proměnná prostředí `PATH` slouží k vyhledání souboru, který chcete spustit.  
  
 `v`  
 `argv`, pole ukazatelů pro argumenty příkazového řádku, je předán `_spawn` funkce. Tato přípona se obvykle používá, když počet parametrů pro nový proces je proměnná.  
  
## <a name="remarks"></a>Poznámky  
 `_spawn` Funkce každý vytvoření a provedení nový proces. Budou automaticky zpracovávat argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používán. `_wspawn` Funkce jsou široká charakterová verzích `_spawn` funkce; nezpracuje řetězců vícebajtových znaků. Jinak `_wspawn` funkce chovají stejně jako na jejich `_spawn` svými protějšky.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 Dostatek paměti musí být k dispozici pro načítání a provádění nový proces. `mode` Argument určuje akci provedenou volající proces před a během `_spawn`. Následující hodnoty pro `mode` jsou definovány v Process.h:  
  
 `_P_OVERLAY`  
 Překryvy a volání zpracovat nový proces, zničení volajícího procesu (stejné jako ovlivňuje `_exec` volání).  
  
 `_P_WAIT`  
 Pozastaví volající vlákno až do dokončení provádění nový proces (synchronní `_spawn`).  
  
 `_P_NOWAIT`nebo`_P_NOWAITO`  
 Bude pokračovat v provádění volající proces souběžně nový proces (asynchronní `_spawn`).  
  
 `_P_DETACH`  
 Bude pokračovat v provádění procesu volání. Nový proces běží na pozadí se žádný přístup do konzole nebo klávesnice. Volání `_cwait` proti nový proces nezdaří (asynchronní `_spawn`).  
  
 `cmdname` Argument určuje soubor, který se spustí jako nový proces a můžete určit úplnou cestu (z kořene), část cesty (z aktuálního pracovního adresáře) nebo pouze název souboru. Pokud `cmdname` nemá příponu názvu souboru nebo nekončí tečkou (.), `_spawn` funkce poprvé pokusí .com příponu názvu souboru a pak příponu názvu souboru .exe, .bat příponu názvu souboru a nakonec .cmd příponu názvu souboru.  
  
 Pokud `cmdname` má příponu názvu souboru, pouze zda se používá rozšíření. Pokud `cmdname` končí tečkou, `_spawn` volání hledá `cmdname` s bez přípony názvu souboru. `_spawnlp`, `_spawnlpe`, `_spawnvp`, A `_spawnvpe` funkce Hledat `cmdname` (pomocí stejné postupy) v adresářích určeného `PATH` proměnné prostředí.  
  
 Pokud `cmdname` obsahuje specifikátor jednotky nebo všechny lomítka (tj. Pokud se jedná o relativní cestu), `_spawn` volání vyhledá jenom zadaný soubor; žádná cesta hledání probíhá.  
  
 V minulosti, některé z těchto funkcí sady `errno` na nulové na úspěšné provedení; je ponechat aktuální chování `errno` nezměněné v případě úspěchu podle standardu C. Pokud potřebujete emulují staré chování, nastavte `errno` na nulu bezprostředně před volání těchto funkcí.  
  
> [!NOTE]
>  Chcete-li zajistit správné překrytí inicializace a ukončování, nepoužívejte `setjmp` nebo `longjmp` funkce zadejte nebo tyto rutiny překrytí.  
  
## <a name="arguments-for-the-spawned-process"></a>Argumenty pro proces spuštěný  
 Předání argumentů do nový proces, předáte jednoho nebo víc ukazatelů řetězce znaků jako argumentů `_spawn` volání. Tyto řetězce znaků představují seznam argumentů pro proces spuštěný. Celková délka řetězce, které tvoří seznam argumentů pro nový proces nesmí překročit 1024 bajtů. Ukončovací znak hodnoty null (\0) pro každý řetězec není zahrnutí do počtu, ale místo znaků (automaticky vložit do samostatné argumenty) jsou zahrnuty.  
  
> [!NOTE]
>  Mezery vložené do řetězců mohou způsobit neočekávané chování, například výsledkem předání řetězce `_spawn` funkci `"hi there"` bude nový proces, který získá dva argumenty `"hi"` a `"there"`. Proces selže, pokud bylo záměrem, aby nový proces otevřel soubor s názvem "hi there". Tomu lze zabránit citováním řetězce: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  Nepředávejte funkci `_spawn` vstup uživatele bez explicitní kontroly jeho obsahu. `_spawn`bude mít za následek volání [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) , mějte na paměti tato nekvalifikované cesta názvy může vést k potenciální ohrožení zabezpečení.  
  
 Argument ukazatele můžete předat jako samostatné argumenty (v `_spawnl`, `_spawnle`, `_spawnlp`, a `_spawnlpe`) nebo jako pole ukazatele (v `_spawnv`, `_spawnve`, `_spawnvp`, a `_spawnvpe`). Musíte zadat alespoň jeden argument, `arg0` nebo `argv`[0], k proces spuštěný. Podle konvence tento argument je název aplikace, jako by ji zadejte na příkazovém řádku. Jinou hodnotu nevytváří k chybě.  
  
 `_spawnl`, `_spawnle`, `_spawnlp`, A `_spawnlpe` volání jsou obvykle používány v případech, kde je předem známo počet argumentů. `arg0` Argument je obvykle ukazatel na `cmdname`. Argumenty `arg1` prostřednictvím `argn` jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Následující `argn`, musí existovat `NULL` ukazatel na konec seznamu argumentů.  
  
 `_spawnv`, `_spawnve`, `_spawnvp`, A `_spawnvpe` volání jsou užitečné, když je proměnný počet argumentů pro nový proces. Ukazatelé na argumenty jsou předány jako pole, `argv` *.* Argument `argv`[0] je obvykle ukazatel na cestu v reálném režimu nebo název programu v chráněném režimu, a `argv`[1] prostřednictvím `argv`[`n`] jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Argument `argv`[`n` + 1] musí být `NULL` ukazatel na konec seznamu argumentů.  
  
## <a name="environment-of-the-spawned-process"></a>Prostředí proces spuštěný  
 Soubory, které jsou při otevření `_spawn` volání zůstaly otevřené v novém procesu. V `_spawnl`, `_spawnlp`, `_spawnv`, a `_spawnvp` volání, nový proces dědí prostředí volajícího procesu. Můžete použít `_spawnle`, `_spawnlpe`, `_spawnve`, a `_spawnvpe` volání změnit prostředí pro nový proces předávání seznam nastavení prostředí prostřednictvím `envp` argument. Argument `envp` je pole znak ukazatele každý prvek (s výjimkou poslední element), které odkazuje na řetězec ukončené hodnotou null definování proměnné prostředí. Takové řetězec obvykle má tento formulář `NAME` = `value` kde `NAME` je název proměnné prostředí a `value` je řetězcovou hodnotu, na kterou je nastavena tuto proměnnou. (Hodnota `value` není uzavřena v dvojitých uvozovkách.) Poslední prvek pole `envp` by měl být `NULL`. Když `envp` sám o sobě představuje `NULL`, proces spuštěný dědí nastavení prostředí nadřazeného procesu.  
  
 `_spawn` Funkce můžete předat všechny informace o otevřených souborů, včetně překladu režim, nový proces. Tyto informace je předán v reálném režimu prostřednictvím `C_FILE_INFO` položky v prostředí. Kód spuštění normálně zpracuje tuto položku a odstraní ji z prostředí. Ale pokud `_spawn` funkce vytvoří proces jiný C, tato položka zůstane v prostředí. Tisk v prostředí zobrazí grafiky znaků v řetězci definice pro tuto položku, protože informace o prostředí, je předaná binárního formátu v reálném režimu. By neměl mít žádný vliv na běžný provoz. V chráněném režimu informace o prostředí je předán v textové podobě a proto nejsou žádné grafické znaky.  
  
 Musíte explicitně flush (pomocí `fflush` nebo `_flushall`) nebo zavřete jakýkoli proud před voláním `_spawn` funkce.  
  
 Nové procesů vytvořených službou volání `_spawn` rutiny nezachováte signál nastavení. Místo toho proces spuštěný obnoví na výchozí nastavení signál.  
  
## <a name="redirecting-output"></a>Přesměrování výstupu  
 Při volání `_spawn` z knihovny DLL nebo aplikace pro grafické uživatelské rozhraní a chcete přesměrujte výstup do kanálu, máte dvě možnosti:  
  
-   Použít rozhraní API Win32 k vytvoření kanálu, pak zavolají [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944), nastavte hodnoty popisovač ve struktuře spuštění a volání [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425).  
  
-   Volání [_popen –, _wpopen –](../c-runtime-library/reference/popen-wpopen.md) kterého bude kanál a vyvolání aplikace pomocí **cmd.exe /c** (nebo **command.exe /c**).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_spawn.c  
// This program accepts a number in the range  
// 1-8 from the command line. Based on the number it receives,  
// it executes one of the eight different procedures that  
// spawn the process named child. For some of these procedures,  
// the CHILD.EXE file must be in the same directory; for  
// others, it only has to be in the same path.  
//  
  
#include <stdio.h>  
#include <process.h>  
  
char *my_env[] =  
{  
   "THIS=environment will be",  
   "PASSED=to child.exe by the",  
   "_SPAWNLE=and",  
   "_SPAWNLPE=and",  
   "_SPAWNVE=and",  
   "_SPAWNVPE=functions",  
   NULL  
};  
  
int main( int argc, char *argv[] )  
{  
   char *args[4];  
  
   // Set up parameters to be sent:   
   args[0] = "child";  
   args[1] = "spawn??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   if (argc <= 2)  
   {  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
  
   switch (argv[1][0])   // Based on first letter of argument   
   {  
   case '1':  
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );  
      break;  
   case '2':  
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",   
               NULL, my_env );  
      break;  
   case '3':  
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );  
      break;  
   case '4':  
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",   
                NULL, my_env );  
      break;  
   case '5':  
      _spawnv( _P_OVERLAY, argv[2], args );  
      break;  
   case '6':  
      _spawnve( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   case '7':  
      _spawnvp( _P_OVERLAY, argv[2], args );  
      break;  
   case '8':  
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   default:  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
   printf( "from SPAWN!\n" );  
}  
```  
  
```Output  
child process output  
from SPAWN!  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../c-runtime-library/reference/abort.md)   
 [AtExit](../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec – funkce](../c-runtime-library/exec-wexec-functions.md)   
 [ukončení, _exit –, _exit –](../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall –](../c-runtime-library/reference/flushall.md)   
 [_getmbcp –](../c-runtime-library/reference/getmbcp.md)   
 [_onexit –, _onexit_m –](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp –](../c-runtime-library/reference/setmbcp.md)   
 [system, _wsystem](../c-runtime-library/reference/system-wsystem.md)