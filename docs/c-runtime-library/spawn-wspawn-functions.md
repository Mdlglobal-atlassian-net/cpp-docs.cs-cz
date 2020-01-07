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
ms.openlocfilehash: 81f4bf6c60a0c0e4011536e8d3bc104bbc33e04f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301701"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn, _wspawn – funkce

Každá z `_spawn` funkcí vytvoří a spustí nový proces:

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Písmena na konci názvu funkce určují variaci.

|Písmeno|Variantní|
|-|-|
| `e`  | `envp`pole ukazatelů na nastavení prostředí je předáno do nového procesu.  |
| `l`  | Argumenty příkazového řádku jsou funkci `_spawn` předány jednotlivě. Tato přípona se obvykle používá, když je počet parametrů nového procesu předem známý.  |
| `p`  | Proměnná prostředí `PATH` slouží k vyhledání souboru, který chcete spustit.  |
| `v`  | `argv`pole ukazatelů na argumenty příkazového řádku je předáno funkci `_spawn`. Tato přípona se obvykle používá, pokud je počet parametrů nového procesu proměnný.  |

## <a name="remarks"></a>Poznámky

`_spawn` funkce každý vytvoří a spustí nový proces. Automaticky zpracovávají řetězcové argumenty vícebajtových znaků podle potřeby a zjišťují sekvence vícebajtových znaků podle aktuálně používané vícebajtové znakové stránky. Funkce `_wspawn` jsou verze `_spawn`ch funkcí; nezpracovávají řetězce vícebajtových znaků. V opačném případě se funkce `_wspawn` chovají stejně jako jejich `_spawn` protějšky.

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

K dispozici je dostatek paměti pro načtení a spuštění nového procesu. Argument `mode` Určuje akci provedenou volajícím procesem před a během `_spawn`. Následující hodnoty pro `mode` jsou definovány v procesu. h:

|||
|-|-|
| `_P_OVERLAY`  | Překryje volající proces pomocí nového procesu a zničí volající proces (stejný účinek jako volání `_exec`).  |
| `_P_WAIT`  | Pozastavuje volající vlákno, dokud není dokončeno provedení nového procesu (synchronní `_spawn`).  |
| `_P_NOWAIT` Nebo `_P_NOWAITO`  | Pokračuje v souběžném spouštění volajícího procesu pomocí nového procesu (asynchronní `_spawn`).  |
| `_P_DETACH`  | Pokračuje v provádění procesu volání; nový proces se spouští na pozadí bez přístupu ke konzole nebo klávesnici. Volání `_cwait` proti novému procesu selžou (asynchronní `_spawn`).  |

Argument `cmdname` určuje soubor, který je spuštěn jako nový proces, a může určovat úplnou cestu (z kořenu), částečnou cestu (z aktuálního pracovního adresáře) nebo pouze název souboru. Pokud `cmdname` nemá příponu názvu souboru nebo nekončí tečkou (.), funkce `_spawn` nejprve zkusí příponu názvu souboru. com a pak příponu názvu souboru. exe, příponu názvu souboru. bat a nakonec příponu názvu souboru. cmd.

Pokud má `cmdname` příponu názvu souboru, bude použita pouze tato přípona. Pokud `cmdname` končí tečkou, volání `_spawn` vyhledá `cmdname` bez přípony názvu souboru. Funkce `_spawnlp`, `_spawnlpe`, `_spawnvp`a `_spawnvpe` hledají `cmdname` (pomocí stejných postupů) v adresářích určených proměnnou prostředí `PATH`.

Pokud `cmdname` obsahuje specifikátor jednotky nebo jakákoli lomítka (tj. Pokud jde o relativní cestu), volání `_spawn` vyhledá pouze zadaný soubor. není provedeno hledání cesty.

V minulosti některé z těchto funkcí nastavily `errno` na hodnotu nula po úspěchu; aktuální chování je opustit `errno` bez dotykového ovládání, jak je určeno standardem C. Pokud potřebujete emulovat staré chování, nastavte `errno` na nulu těsně před voláním těchto funkcí.

> [!NOTE]
>  Chcete-li zajistit správné překrytí a ukončení, nepoužívejte funkci `setjmp` nebo `longjmp` k zadání nebo opuštění rutiny překryvných operací.

## <a name="arguments-for-the-spawned-process"></a>Argumenty vytvořeného procesu

Chcete-li předat argumenty novému procesu, zadejte jeden nebo více ukazatelů na řetězce znaků jako argumenty ve volání `_spawn`. Tyto řetězce znaků tvoří seznam argumentů vytvořeného procesu. Kombinovaná délka řetězců tvořících seznam argumentů nového procesu nesmí překročit 1024 bajtů. Ukončující znak null (' \ 0 ') pro každý řetězec není zahrnut do počtu, ale jsou zahrnuty znaky mezer (automaticky vložené do samostatných argumentů).

> [!NOTE]
>  Mezery vložené do řetězců mohou způsobit neočekávané chování, například výsledkem předání řetězce `_spawn` funkci `"hi there"` bude nový proces, který získá dva argumenty `"hi"` a `"there"`. Proces selže, pokud bylo záměrem, aby nový proces otevřel soubor s názvem "hi there". Tomu lze zabránit citováním řetězce: `"\"hi there\""`.

> [!IMPORTANT]
>  Nepředávejte funkci `_spawn` vstup uživatele bez explicitní kontroly jeho obsahu. `_spawn` bude mít za následek volání funkce [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) , takže Pamatujte, že nekvalifikované názvy cest by mohly vést k potenciálním ohrožením zabezpečení.

Můžete předat ukazatelům argumentů jako samostatné argumenty (v `_spawnl`, `_spawnle`, `_spawnlp`a `_spawnlpe`) nebo jako pole ukazatelů (v `_spawnv`, `_spawnve`, `_spawnvp`a `_spawnvpe`). Do vytvořeného procesu musíte předat aspoň jeden argument, `arg0` nebo `argv`[0]. Podle konvence je tento argument názvem programu, jak ho zadáte na příkazovém řádku. Jiná hodnota nevytváří chybu.

Volání `_spawnl`, `_spawnle`, `_spawnlp`a `_spawnlpe` se obvykle používají v případech, kdy je počet argumentů znám předem. Argument `arg0` je obvykle ukazatel na `cmdname`. Argumenty `arg1` prostřednictvím `argn` jsou ukazatele na řetězce znaků, které tvoří nový seznam argumentů. Po `argn`musí existovat ukazatel s **hodnotou null** k označení konce seznamu argumentů.

Volání `_spawnv`, `_spawnve`, `_spawnvp`a `_spawnvpe` jsou užitečná v případě, že je k novému procesu variabilní počet argumentů. Ukazatele na argumenty jsou předány jako pole `argv` *.* Argument `argv`[0] je obvykle ukazatel na cestu v reálném režimu nebo v názvu programu v chráněném režimu a `argv`[1] až `argv`[`n`] jsou ukazatelé na řetězce znaků, které tvoří nový seznam argumentů. Argument `argv`[`n` + 1] musí být ukazatel s **hodnotou null** k označení konce seznamu argumentů.

## <a name="environment-of-the-spawned-process"></a>Prostředí vytvořeného procesu

Soubory, které jsou otevřeny, když je prováděno volání `_spawn` zůstane v novém procesu otevřené. V `_spawnl`, `_spawnlp`, `_spawnv`a `_spawnvp` volání, nový proces zdědí prostředí volajícího procesu. Pomocí volání `_spawnle`, `_spawnlpe`, `_spawnve`a `_spawnvpe` můžete změnit prostředí nového procesu tak, že projdete seznam nastavení prostředí pomocí argumentu `envp`. Argument `envp` je pole ukazatelů na znaky, každý prvek (s výjimkou posledního prvku), který odkazuje na řetězec zakončený hodnotou null definující proměnnou prostředí. Takový řetězec má obvykle `NAME`=`value` kde `NAME` je název proměnné prostředí a `value` je hodnota řetězce, na kterou je tato proměnná nastavena. (Všimněte si, že `value` není uzavřen v uvozovkách.) Poslední prvek `envp` pole by měl mít **hodnotu null**. Pokud **je `envp`** sám o sobě, vytvořený proces zdědí nastavení prostředí nadřazeného procesu.

Funkce `_spawn` můžou předat všechny informace o otevřených souborech, včetně režimu překladu, do nového procesu. Tyto informace se předávají v reálném režimu prostřednictvím položky `C_FILE_INFO` v prostředí. Spouštěcí kód obvykle zpracovává tuto položku a pak ji odstraní z prostředí. Pokud však `_spawn` funkce zachová proces, který není v jazyce C, tato položka zůstane v prostředí. Tisk prostředí zobrazuje grafické znaky v řetězci definice pro tuto položku, protože informace o prostředí jsou předány v binárním formátu v reálném režimu. Neměla by mít žádný jiný vliv na běžné operace. V chráněném režimu jsou informace o prostředí předány ve formě textu, a proto neobsahuje žádné grafické znaky.

Musíte explicitně vyprázdnit (pomocí `fflush` nebo `_flushall`) nebo zavřít libovolný datový proud před voláním funkce `_spawn`.

Nové procesy vytvořené voláními rutiny `_spawn` nezachovávají nastavení signálu. Místo toho vytvářený proces obnoví nastavení signálu na výchozí hodnotu.

## <a name="redirecting-output"></a>Přesměrování výstupu

Pokud voláte `_spawn` z knihovny DLL nebo aplikace grafického uživatelského rozhraní a chcete přesměrovat výstup do kanálu, máte dvě možnosti:

- Pomocí Win32 API vytvořte kanál, pak zavolejte [AllocConsole](/windows/console/allocconsole), nastavte hodnoty popisovače ve spouštěcí struktuře a zavolejte metodu [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw).

- Zavolejte [_popen, _wpopen,](../c-runtime-library/reference/popen-wpopen.md) která vytvoří kanál a vyvolá aplikaci pomocí programu **cmd. exe/c** (nebo **příkazu. exe/c**).

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
