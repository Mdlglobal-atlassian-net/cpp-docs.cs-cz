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
ms.openlocfilehash: 8ab368378775102b708635b551c046a326adfecb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498911"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn, _wspawn – funkce

Každá z `_spawn` těchto funkcí vytvoří a spustí nový proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Písmena na konci názvu funkce určují variaci.

|Písmeno|Varianty|
|-|-|
| `e`  | `envp`, pole ukazatelů na nastavení prostředí je předáno novému procesu.  |
| `l`  | Argumenty příkazového řádku jsou funkci `_spawn` předány jednotlivě. Tato přípona se obvykle používá, když je počet parametrů nového procesu předem známý.  |
| `p`  | Proměnná prostředí `PATH` slouží k vyhledání souboru, který chcete spustit.  |
| `v`  | `argv`, pole ukazatelů na argumenty příkazového řádku je předáno `_spawn` funkci. Tato přípona se obvykle používá, pokud je počet parametrů nového procesu proměnný.  |

## <a name="remarks"></a>Poznámky

`_spawn` Funkce každý vytvoří a spustí nový proces. Automaticky zpracovávají řetězcové argumenty vícebajtových znaků podle potřeby a zjišťují sekvence vícebajtových znaků podle aktuálně používané vícebajtové znakové stránky. Funkce jsou verze `_spawn` funkcí s velkým znakem, nezpracovávají řetězce vícebajtových znaků. `_wspawn` V opačném `_wspawn` případě se funkce chovají stejně jako jejich `_spawn` protějšky.

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

K dispozici je dostatek paměti pro načtení a spuštění nového procesu. Argument určuje akci provedenou volajícím procesem před a během `_spawn`. `mode` Následující hodnoty pro `mode` jsou definovány v procesu. h:

|||
|-|-|
| `_P_OVERLAY`  | Překrývá volající proces pomocí nového procesu a zničí volající proces (stejný účinek jako `_exec` volání).  |
| `_P_WAIT`  | Pozastaví volající vlákno, dokud není dokončeno provedení nového procesu (synchronní `_spawn`).  |
| `_P_NOWAIT` Nebo `_P_NOWAITO`  | Pokračuje v souběžném spouštění volajícího procesu s novým procesem (asynchronní `_spawn`).  |
| `_P_DETACH`  | Pokračuje v provádění procesu volání; nový proces se spouští na pozadí bez přístupu ke konzole nebo klávesnici. Volání na `_cwait` proti novému procesu selžou (asynchronní `_spawn`).  |

`cmdname` Argument určuje soubor, který je spuštěn jako nový proces, a může určovat úplnou cestu (z kořene), částečnou cestu (z aktuálního pracovního adresáře) nebo pouze název souboru. Pokud `cmdname` nemá příponu názvu souboru nebo nekončí tečkou (.) `_spawn` , funkce nejprve zkusí příponu názvu souboru. com a pak příponu názvu souboru. exe, příponu názvu souboru. bat a nakonec příponu názvu souboru. cmd.

Pokud `cmdname` má přípona názvu souboru, je použita pouze tato přípona. Pokud `cmdname` končí tečkou `_spawn` , volání vyhledá `cmdname` bez přípony názvu souboru. `_spawnlp`Funkce, `_spawnlpe`, avyhledávají`_spawnvpe` (používají stejné postupy) v adresářích určených `PATH` proměnnou prostředí. `cmdname` `_spawnvp`

Pokud `cmdname` obsahuje specifikátor jednotky nebo jakákoli lomítka (tj. Pokud jde o relativní cestu) `_spawn` , volání vyhledá pouze zadaný soubor; není provedeno hledání cesty.

V minulosti některé z těchto funkcí nastaveny `errno` na hodnotu nula při úspěchu; aktuální chování je ponecháno `errno` nezměněno po úspěchu, jak je určeno standardem C. Pokud potřebujete emulovat staré chování, nastavte `errno` na hodnotu nula těsně před voláním těchto funkcí.

> [!NOTE]
>  Chcete-li zajistit správné překrytí a ukončení, `setjmp` Nepoužívejte `longjmp` funkci or k zadání nebo opuštění rutiny překryvných operací.

## <a name="arguments-for-the-spawned-process"></a>Argumenty vytvořeného procesu

Chcete-li předat argumenty novému procesu, zadejte jeden nebo více ukazatelů na řetězce znaků jako argumenty ve `_spawn` volání. Tyto řetězce znaků tvoří seznam argumentů vytvořeného procesu. Kombinovaná délka řetězců tvořících seznam argumentů nového procesu nesmí překročit 1024 bajtů. Ukončující znak null (' \ 0 ') pro každý řetězec není zahrnut do počtu, ale jsou zahrnuty znaky mezer (automaticky vložené do samostatných argumentů).

> [!NOTE]
>  Mezery vložené do řetězců mohou způsobit neočekávané chování, například výsledkem předání řetězce `_spawn` funkci `"hi there"` bude nový proces, který získá dva argumenty `"hi"` a `"there"`. Proces selže, pokud bylo záměrem, aby nový proces otevřel soubor s názvem "hi there". Tomu lze zabránit citováním řetězce: `"\"hi there\""`.

> [!IMPORTANT]
>  Nepředávejte funkci `_spawn` vstup uživatele bez explicitní kontroly jeho obsahu. `_spawn`Výsledkem bude volání funkce [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) , takže Pamatujte, že nekvalifikované názvy cest by mohly vést k potenciálním ohrožením zabezpečení.

`_spawnl`Ukazatele argumentů můžete předat jako samostatné argumenty (v `_spawnvp` `_spawnv` `_spawnle` `_spawnlp`,, a `_spawnlpe`) nebo jako pole ukazatelů (v, `_spawnve`, `_spawnvpe`a). Do vytvořeného procesu musíte předat aspoň jeden `arg0` argument `argv`nebo [0]. Podle konvence je tento argument názvem programu, jak ho zadáte na příkazovém řádku. Jiná hodnota nevytváří chybu.

`_spawnle` Volání,,`_spawnlp`a jsou`_spawnlpe` obvykle používána v případech, kdy je počet argumentů znám předem. `_spawnl` Argument je obvykle ukazatel na `cmdname`. `arg0` Argumenty `arg1` prostřednictvím`argn` jsou ukazatele na znakové řetězce tvořící nový seznam argumentů. Níže `argn`musí být ukazatel s **hodnotou null** k označení konce seznamu argumentů.

Volání `_spawnv`, `_spawnve`, ajsou`_spawnvpe` užitečná v případě, že je k novému procesu variabilní počet argumentů. `_spawnvp` Ukazatele na argumenty jsou předány jako pole, `argv` *.* Argument `argv`[0] je obvykle ukazatel na cestu v reálném režimu nebo v názvu programu v chráněném režimu a `argv`[1] až `argv`[`n`] jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Argument `argv`[`n` + 1] musí být ukazatel s **hodnotou null** k označení konce seznamu argumentů.

## <a name="environment-of-the-spawned-process"></a>Prostředí vytvořeného procesu

Soubory, které jsou otevřeny `_spawn` po provedení volání, zůstanou v novém procesu otevřené. V volání `_spawnlp` ,,`_spawnv` a`_spawnvp` , nový proces zdědí prostředí volajícího procesu. `_spawnl` Pomocí `_spawnle`volání, `_spawnlpe`, `_spawnve`a `envp` můžete změnit prostředí nového procesu předáním seznamu nastavení prostředí pomocí argumentu. `_spawnvpe` Argument `envp` je pole ukazatelů na znaky, každý prvek (s výjimkou posledního prvku), který odkazuje na řetězec zakončený hodnotou null definující proměnnou prostředí. Takový řetězec má obvykle `NAME` formu = `value` , kde `NAME` je název proměnné prostředí a `value` je hodnota řetězce, na kterou je tato proměnná nastavena. (Hodnota `value` není uzavřena v dvojitých uvozovkách.) Poslední prvek `envp` pole by měl mít **hodnotu null**. Pokud `envp` je tato **hodnota null**, vytvořený proces zdědí nastavení prostředí nadřazeného procesu.

`_spawn` Funkce můžou do nového procesu předat všechny informace o otevřených souborech, včetně režimu překladu. Tyto informace se předávají v reálném režimu prostřednictvím `C_FILE_INFO` záznamu v prostředí. Spouštěcí kód obvykle zpracovává tuto položku a pak ji odstraní z prostředí. Pokud však funkce vytvoří `_spawn` proces, který není v jazyce C, tato položka zůstane v prostředí. Tisk prostředí zobrazuje grafické znaky v řetězci definice pro tuto položku, protože informace o prostředí jsou předány v binárním formátu v reálném režimu. Neměla by mít žádný jiný vliv na běžné operace. V chráněném režimu jsou informace o prostředí předány ve formě textu, a proto neobsahuje žádné grafické znaky.

Před voláním `_spawn` funkce musíte explicitně `fflush` vyprázdnit (pomocí nebo `_flushall`) nebo zavřít libovolný datový proud.

Nové procesy vytvořené voláním `_spawn` rutin nezachovávají nastavení signálu. Místo toho vytvářený proces obnoví nastavení signálu na výchozí hodnotu.

## <a name="redirecting-output"></a>Přesměrování výstupu

Pokud voláte `_spawn` z knihovny DLL nebo aplikace grafického uživatelského rozhraní a chcete přesměrovat výstup do kanálu, máte dvě možnosti:

- Pomocí Win32 API vytvořte kanál, pak zavolejte [AllocConsole](/windows/console/allocconsole), nastavte hodnoty popisovače ve spouštěcí struktuře a zavolejte metodu [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw).

- Zavolejte [_popen, _wpopen,](../c-runtime-library/reference/popen-wpopen.md) který vytvoří kanál a vyvolá aplikaci pomocí programu **cmd. exe/c** (nebo **příkazu. exe/c**).

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
