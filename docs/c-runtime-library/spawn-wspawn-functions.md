---
title: _spawn, _wspawn – funkce
ms.date: 11/04/2016
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
ms.openlocfilehash: 044aaee376be02d0d3734ea8982a8c4db47f7d39
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748044"
---
# <a name="spawn-wspawn-functions"></a>_spawn, _wspawn – funkce

Každá z `_spawn` funkcí vytvoří a spustí nový proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Písmen na konci názvu funkce určit variantu.

|Písmeno|Variant|
|-|-|
| `e`  | `envp`, pole ukazatelů do nastavení prostředí, je předán do nového procesu.  |
| `l`  | Argumenty příkazového řádku jsou funkci `_spawn` předány jednotlivě. Tato přípona se obvykle používá, pokud je počet parametrů nového procesu předem známý.  |
| `p`  | Proměnná prostředí `PATH` slouží k vyhledání souboru, který chcete spustit.  |
| `v`  | `argv`, pole ukazatelů do argumentů příkazového řádku je předán `_spawn` funkce. Tato přípona se obvykle používá, když je počet parametrů nového procesu proměnná.  |

## <a name="remarks"></a>Poznámky

`_spawn` Funkce každá vytvoření a spuštění nového procesu. Jsou automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používán. `_wspawn` Funkce jsou širokoznaké verze `_spawn` funkce; že nezpracovávají vícebajtové znakové řetězce. V opačném případě `_wspawn` funkce se chovají stejně jako jejich `_spawn` protějšky.

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

Dostatek paměti musí být k dispozici pro načtení a spuštění nového procesu. `mode` Argument určuje akci provedenou na základě volajícího procesu před a během `_spawn`. Následující hodnoty pro `mode` jsou definovány v Process.h:

|||
|-|-|
| `_P_OVERLAY`  | Překrytí a volání zpracovat nový proces ničení volajícího procesu (stejný vliv jako `_exec` volání).  |
| `_P_WAIT`  | Pozastaví volající vlákno, dokud se nedokončí spuštění nového procesu (synchronní `_spawn`).  |
| `_P_NOWAIT` Nebo `_P_NOWAITO`  | Pokračuje v provádění volající proces současně nový proces (asynchronní `_spawn`).  |
| `_P_DETACH`  | Pokračuje v provádění procesu volání. Nový proces běží na pozadí bez přístupu konzoly nebo klávesnice. Volání `_cwait` proti nový proces selže (asynchronní `_spawn`).  |

`cmdname` Argument určuje soubor, který je spuštěn jako nový proces a můžete zadat úplnou cestu (z kořenového adresáře), část cesty (z aktuálního pracovního adresáře) nebo pouze název souboru. Pokud `cmdname` nemá příponu názvu souboru nebo nekončí tečkou (.), `_spawn` funkce poprvé pokusí příponu názvu souboru .com a poté příponu názvu souboru .exe, .bat příponu názvu souboru a nakonec příponu názvu souboru .cmd.

Pokud `cmdname` má příponu názvu souboru, pouze že se používá rozšíření. Pokud `cmdname` končí tečkou, `_spawn` volání vyhledá `cmdname` bez přípony názvu souboru. `_spawnlp`, `_spawnlpe`, `_spawnvp`, A `_spawnvpe` funkce hledání `cmdname` (s použitím stejné postupy) v adresářích určených `PATH` proměnné prostředí.

Pokud `cmdname` obsahuje specifikátor jednotky nebo jakákoli lomítka (tj. Pokud se jedná o relativní cestu), `_spawn` volání vyhledá pouze zadaný soubor; žádná cesta hledání se provádí.

V minulosti, některé z těchto funkcí sady `errno` na nulovou na úspěšné provedení; aktuální chování je ponechat `errno` zůstanou v případě úspěchu, jak je uvedeno ve standardu C. Pokud potřebujete emulovat staré chování, nastavte `errno` na nulu bezprostředně před volání těchto funkcí.

> [!NOTE]
>  Aby se zajistilo správné překrytí inicializace a ukončování, nepoužívejte `setjmp` nebo `longjmp` funkce a zadejte skript nebo ponechte rutiny překrytí.

## <a name="arguments-for-the-spawned-process"></a>Argumenty pro nové kopie procesu

Předání argumentů do nového procesu, poskytují jednoho nebo víc ukazatelů na řetězce znaků jako argumenty v `_spawn` volání. Tyto řetězce znaků tvoří seznam argumentů pro spuštěný proces. Celková délka řetězce, které tvoří seznamu argumentů nového procesu nesmí překročit 1024 bajtů. Ukončující znak null ('\0') pro každý řetězec není v tomto počtu zahrnut, ale znaky mezery (automaticky vložit do samostatné argumenty) jsou zahrnuty.

> [!NOTE]
>  Mezery vložené do řetězců mohou způsobit neočekávané chování, například výsledkem předání řetězce `_spawn` funkci `"hi there"` bude nový proces, který získá dva argumenty `"hi"` a `"there"`. Proces selže, pokud bylo záměrem, aby nový proces otevřel soubor s názvem "hi there". Tomu lze zabránit citováním řetězce: `"\"hi there\""`.

> [!IMPORTANT]
>  Nepředávejte funkci `_spawn` vstup uživatele bez explicitní kontroly jeho obsahu. `_spawn` Výsledkem bude volání [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) myslete že neúplné názvy cest mohou vést k potenciálním zranitelnostem zabezpečení.

Můžete předat argument ukazatele jako samostatné argumenty (v `_spawnl`, `_spawnle`, `_spawnlp`, a `_spawnlpe`) nebo jako pole ukazatelů (v `_spawnv`, `_spawnve`, `_spawnvp`, a `_spawnvpe`). Je nutné předat aspoň jeden argument, `arg0` nebo `argv`[0], do nové kopie procesu. Podle konvence tento argument je název aplikace, jako by ji zadejte na příkazovém řádku. Různé hodnota nevyvolá chybu.

`_spawnl`, `_spawnle`, `_spawnlp`, A `_spawnlpe` volání se obvykle používají v případech, kde je počet argumentů, které předem známý. `arg0` Argument je obvykle ukazatel na `cmdname`. Argumenty `arg1` prostřednictvím `argn` jsou ukazatele na znakové řetězce tvořící nový seznam argumentů. Následující `argn`, musí existovat **NULL** ukazatel k označení konce seznamu argumentů.

`_spawnv`, `_spawnve`, `_spawnvp`, A `_spawnvpe` volání jsou užitečné, když je proměnný počet argumentů novému procesu. Ukazatelé na argumenty jsou předány jako pole, `argv` *.* Argument `argv`[0] je obvykle ukazatel na cestu v reálném režimu nebo na název programu v chráněném režimu, a `argv`[1] až `argv`[`n`] jsou ukazatele na znakové řetězce tvořící nový seznam argumentů. Argument `argv`[`n` + 1] musí být **NULL** ukazatel k označení konce seznamu argumentů.

## <a name="environment-of-the-spawned-process"></a>Prostředí vytvořeném podřízeném procesu

Při otevření souborů, které jsou `_spawn` je uskutečněn hovor, zůstanou otevřené v novém procesu. V `_spawnl`, `_spawnlp`, `_spawnv`, a `_spawnvp` volání, nový proces zdědí prostředí volajícího procesu. Můžete použít `_spawnle`, `_spawnlpe`, `_spawnve`, a `_spawnvpe` změní prostředí nového procesu tím, že předáte seznam nastavení prostředí prostřednictvím volání `envp` argument. Argument `envp` je pole ukazatelů na znaky, kde každý prvek (s výjimkou posledního prvku) odkazuje na null ukončující řetězec definující proměnnou prostředí. Takový řetězec má obvykle tvar `NAME` = `value` kde `NAME` je název proměnné prostředí a `value` je hodnota řetězce, do které tato proměnná nastavena. (Hodnota `value` není uzavřena v dvojitých uvozovkách.) Poslední prvek `envp` pole by měla být **NULL**. Když `envp` sám o sobě **NULL**, spuštěný proces zdědí nastavení prostředí z nadřazeného procesu.

`_spawn` Funkce můžete předat všechny informace o otevřených souborů, včetně režimu překladu novému procesu. Tyto informace je předána v reálném režimu prostřednictvím `C_FILE_INFO` položky v prostředí. Spouštěcí kód obvykle zpracovává tuto položku a odstraní ji z prostředí. Nicméně pokud `_spawn` funkce vytvoří proces jazyka C, tato položka zůstane v prostředí. Tisk prostředí zobrazí grafické znaky v řetězci definice pro tuto položku, protože informace o prostředí v reálném režimu předána v binárním formátu. By neměl mít žádný vliv na běžný provoz. Informace o prostředí v chráněném režimu, se předává v textové podobě a proto neobsahuje žádné grafické znaky.

Je nutné provést explicitní vyprázdnění (pomocí `fflush` nebo `_flushall`) nebo všechny proudy zavřít před voláním `_spawn` funkce.

Nových procesů vytvořených pomocí volání `_spawn` rutiny Nezachovávat hodnotu nastavení signálu. Místo toho spuštěný proces resetuje na výchozí hodnotu nastavení signálu.

## <a name="redirecting-output"></a>Přesměrovat výstup

Pokud voláte `_spawn` z knihovny DLL nebo aplikace s grafickým uživatelským rozhraním a chcete přesměrovat výstup do kanálu, máte dvě možnosti:

- Použít rozhraní API systému Win32 k vytvoření kanálu, potom zavolejte [AllocConsole](/windows/console/allocconsole), nastavte popisovač hodnoty ve struktuře spuštění a volání [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa).

- Volání [_popen – _wpopen –](../c-runtime-library/reference/popen-wpopen.md) který vytvoří kanál a vyvolání aplikace pomocí **cmd.exe /c** (nebo **command.exe /c**).

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

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, _wexec – funkce](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
