---
title: _spawn, _wspawn – funkce
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a22f5b0c401dd888bbda451504e644557294544d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322963"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn, _wspawn – funkce

Každá z `_spawn` funkcí vytvoří a spustí nový proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Písmena na konci názvu funkce určují variantu.

|Písmeno|Variantní|
|-|-|
| `e`  | `envp`, pole ukazatelů na nastavení prostředí, je předána novému procesu.  |
| `l`  | Argumenty příkazového řádku jsou funkci `_spawn` předány jednotlivě. Tato přípona se obvykle používá, když je předem znám počet parametrů nového procesu.  |
| `p`  | Proměnná prostředí `PATH` slouží k vyhledání souboru, který chcete spustit.  |
| `v`  | `argv`, pole ukazatelů na argumenty příkazového řádku, je předáno `_spawn` funkci. Tato přípona se obvykle používá, když je proměnný počet parametrů nového procesu.  |

## <a name="remarks"></a>Poznámky

Funkce `_spawn` každý vytvořit a spustit nový proces. Podle potřeby automaticky zpracovávají vícebajtové argumenty řetězce a rozpoznávají vícebajtové sekvence znaků podle aktuálně používáné vícebajtové znakové stránky. Funkce `_wspawn` jsou širokoúhlé verze `_spawn` funkcí; nezpracovávají vícebajtové řetězce znaků. V opačném `_wspawn` případě se funkce `_spawn` chovají stejně jako jejich protějšky.

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

Pro načtení a spuštění nového procesu musí být k dispozici dostatek paměti. Argument `mode` určuje akci přijatou volajícím procesem `_spawn`před a během . V souboru `mode` Process.h jsou definovány následující hodnoty:

|||
|-|-|
| `_P_OVERLAY`  | Překryje volající proces s novým procesem, čímž zničí `_exec` proces volání (stejný efekt jako volání).  |
| `_P_WAIT`  | Pozastaví volající vlákno, dokud nebude dokončeno spuštění `_spawn`nového procesu (synchronní).  |
| `_P_NOWAIT` nebo `_P_NOWAITO`  | Pokračuje v provádění volajícího procesu souběžně s novým `_spawn`procesem (asynchronní).  |
| `_P_DETACH`  | Pokračuje v provádění volajícího procesu; nový proces je spuštěn na pozadí bez přístupu ke konzole nebo klávesnici. Volání `_cwait` proti nový proces nezdaří (asynchronní). `_spawn`  |

Argument `cmdname` určuje soubor, který je spuštěn jako nový proces a může určit úplnou cestu (z kořenového adresáře), částečnou cestu (z aktuálního pracovního adresáře) nebo pouze název souboru. Pokud `cmdname` nemá příponu názvu souboru nebo nekončí tečkou (.), `_spawn` funkce se nejprve pokusí o příponu .com název souboru a potom příponu názvu souboru EXE, příponu .bat název souboru a nakonec příponu .cmd název souboru.

Pokud `cmdname` má příponu název souboru, používá se pouze tato přípona. Pokud `cmdname` končí tečkou, `_spawn` volání vyhledá `cmdname` bez přípony názvu souboru. Funkce `_spawnlp` `_spawnlpe`, `_spawnvp`a `_spawnvpe` funkce `cmdname` vyhledávají (pomocí stejných postupů) v `PATH` adresářích určených proměnnou prostředí.

Pokud `cmdname` obsahuje specifikátor jednotky nebo všechna lomítka (to znamená, pokud se jedná o relativní cestu), `_spawn` volání vyhledá pouze zadaný soubor; neprovádí se žádné hledání cesty.

V minulosti některé z `errno` těchto funkcí nastavena na nulu na úspěch; aktuální chování je `errno` ponechat nedotčené na úspěch, jak je specifikováno standardem C. Pokud potřebujete emulovat staré chování, `errno` nastavte na nulu těsně před voláním těchto funkcí.

> [!NOTE]
> Chcete-li zajistit správnou inicializaci a `setjmp` `longjmp` ukončení překrytí, nepoužívejte funkci nebo k zadání nebo opuštění rutiny překrytí.

## <a name="arguments-for-the-spawned-process"></a>Argumenty pro zplozený proces

Chcete-li předat argumenty do nového procesu, dejte jeden nebo `_spawn` více ukazatelů na řetězce znaků jako argumenty ve volání. Tyto řetězce znaků tvoří seznam argumentů pro zplozený proces. Kombinovaná délka řetězců tvořících seznam argumentů pro nový proces nesmí překročit 1024 bajtů. Ukončující znak null (\0') pro každý řetězec není zahrnut v počtu, ale mezery znaky (automaticky vložené do samostatných argumentů) jsou zahrnuty.

> [!NOTE]
> Mezery vložené do řetězců mohou způsobit neočekávané chování, například výsledkem předání řetězce `_spawn` funkci `"hi there"` bude nový proces, který získá dva argumenty `"hi"` a `"there"`. Proces selže, pokud bylo záměrem, aby nový proces otevřel soubor s názvem "hi there". Tomu lze zabránit citováním řetězce: `"\"hi there\""`.

> [!IMPORTANT]
> Nepředávejte funkci `_spawn` vstup uživatele bez explicitní kontroly jeho obsahu. `_spawn`bude mít za následek volání [CreateProcess,](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) takže mějte na paměti, že názvy cest bez výhrad může vést k potenciální ohrožení zabezpečení.

Ukazatele argumentů můžete předat jako samostatné `_spawnl` `_spawnle`argumenty (v `_spawnlp`, , `_spawnlpe`a ) `_spawnv` `_spawnve`nebo `_spawnvp`jako `_spawnvpe`pole ukazatelů (v , , a ). Do procesu zplození musíte předat alespoň jeden argument `arg0` nebo `argv`[0]. Podle konvence je tento argument názvem programu, stejně jako byste jej zadali na příkazovém řádku. Jiná hodnota nevytváří chybu.

Volání `_spawnl` `_spawnle`, `_spawnlp`, `_spawnlpe` a obvykle se používají v případech, kdy je počet argumentů znám předem. Argument `arg0` je obvykle ukazatel `cmdname`na . Argumenty `arg1` prostřednictvím `argn` jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Následující `argn`, musí být **ukazatel NULL** označit konec seznamu argumentů.

Volání `_spawnv` `_spawnve`, `_spawnvp`, `_spawnvpe` a jsou užitečné, pokud existuje proměnný počet argumentů pro nový proces. Ukazatele na argumenty jsou předány `argv`jako pole *.* Argument `argv`[0] je obvykle ukazatel na cestu v reálném režimu nebo `argv`na název `argv`programu`n`v chráněném režimu a [1] přes [ ] jsou ukazatele na řetězce znaků tvořící nový seznam argumentů. Argument `argv`[`n` +1] musí být ukazatelem **NULL,** který označuje konec seznamu argumentů.

## <a name="environment-of-the-spawned-process"></a>Prostředí zplozeného procesu

Soubory, které jsou `_spawn` otevřené při uskutečnění hovoru, zůstávají otevřené v novém procesu. V `_spawnl`, `_spawnlp` `_spawnv`, `_spawnvp` , a volání nový proces dědí prostředí volajícího procesu. Pomocí volání `_spawnle`, `_spawnlpe` `_spawnve`a `_spawnvpe` volání můžete změnit prostředí pro nový proces předáním seznamu `envp` nastavení prostředí prostřednictvím argumentu. Argument `envp` je pole ukazatelů znaků, každý prvek (s výjimkou konečného prvku), který odkazuje na řetězec s ukončeným hodnotou null definující proměnnou prostředí. Takový řetězec má obvykle `NAME` = `value` `NAME` formulář, kde je název `value` proměnné prostředí a je hodnota řetězce, na které je tato proměnná nastavena. (Všimněte `value` si, že není uzavřen a uvozovky.) Poslední prvek `envp` pole by měl být **NULL**. Pokud `envp` **je**null , zplozený proces dědí nastavení prostředí nadřazeného procesu.

Funkce `_spawn` mohou předat do nového procesu všechny informace o otevřených souborech, včetně režimu překladu. Tyto informace jsou předávány `C_FILE_INFO` v reálném režimu prostřednictvím položky v prostředí. Spouštěcí kód obvykle zpracovává tuto položku a poté ji odstraní z prostředí. Pokud však `_spawn` funkce spouští proces bez Jazyka C, zůstane tato položka v prostředí. Tisk prostředí zobrazuje grafické znaky v definičním řetězci pro tuto položku, protože informace o prostředí jsou předávány v binární podobě v reálném režimu. Nemělo by to mít žádný jiný vliv na normální provoz. V chráněném režimu jsou informace o prostředí předávány v textové podobě, a proto neobsahují žádné grafické znaky.

Před voláním `fflush` `_spawn` funkce `_flushall`je nutné explicitně vyprázdnit (pomocí nebo ) nebo zavřít libovolný datový proud.

Nové procesy vytvořené `_spawn` voláním rutin nezachovávají nastavení signálu. Místo toho proces tření obnoví nastavení signálu na výchozí.

## <a name="redirecting-output"></a>Přesměrování výstupu

Pokud voláte `_spawn` z dll nebo gui aplikace a chcete přesměrovat výstup na potrubí, máte dvě možnosti:

- Pomocí rozhraní API win32 vytvořte kanál, pak zavolejte [AllocConsole](/windows/console/allocconsole), nastavte hodnoty popisovače ve struktuře spuštění a volejte [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw).

- Volání [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md) který vytvoří kanál a vyvolá aplikaci pomocí **cmd.exe /c** (nebo **command.exe /c).**

## <a name="example"></a>Příklad

```c
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

[Řízení procesů a prostředí](../c-runtime-library/process-and-environment-control.md)<br/>
[Přerušení](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, _wexec funkce](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
