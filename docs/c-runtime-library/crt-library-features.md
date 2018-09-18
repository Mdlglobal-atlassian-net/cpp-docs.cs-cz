---
title: Funkce knihovny CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0864c87b33937fe18c3e4c3083e63bde23ac06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092232"
---
# <a name="crt-library-features"></a>Funkce knihovny CRT

Toto téma popisuje různé soubory LIB, které tvoří běhové knihovny jazyka C i jejich kompilátoru přidružené možností a direktivy preprocesoru.

## <a name="c-run-time-libraries-crt"></a>Běhové knihovny jazyka C (CRT)

Knihovny Run-time jazyka C (CRT) je součástí standardní knihovny C++, který zahrnuje knihovny standard ISO C99. Knihovny Visual C++, které implementují CRT podporují vývoj nativního kódu a obě Smíšeného nativního a spravovaného kódu. Všechny verze CRT podporují vícevláknové. Většina knihoven podporuje jak statické propojení, propojit knihovnu přímo do kódu, nebo dynamické propojení umožňuje kódu použít běžné soubory DLL.

Spouští se v sadě Visual Studio 2015, CRT byla refaktorována, do nové binární soubory. Universal CRT (UCRT) obsahuje funkce a globální prvky exportovat ve standardní knihovně C99 CRT. UCRT je teď součástí Windows a dodává v rámci Windows 10. Statickou knihovnu, knihovna DLL knihovny importu a soubory hlaviček pro UCRT jsou teď součástí Windows 10 SDK. Při instalaci Visual C++ instaluje instalační program sady Visual Studio dílčí sadu Windows 10 SDK, aby jeho používání UCRT. Můžete použít UCRT na libovolnou verzi systému Windows podporuje Visual Studio 2015 a novější verze. Můžete znovu distribuovat pomocí vcredist pro podporované verze systému Windows než Windows 10. Další informace najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).

V následující tabulce jsou uvedeny knihoven, které implementují UCRT.

|Knihovna|Přidružené knihovny DLL|Vlastnosti|Možnost|Direktivy preprocesoru|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|Žádné|Staticky odkazuje UCRT do kódu.|**/MT**|_MT|
|libucrtd.lib|Žádné|Ladicí verze UCRT pro statické propojování. Redistributable.|**/MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|Importovat knihovny DLL pro UCRT.|**/ MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|Importní knihovny DLL, pro ladicí verzi UCRT. Redistributable.|**/ MDd**|_DEBUG, _MT, _DLL|

Knihovna vcruntime obsahuje kód specifický pro implementaci Visual C++ CRT, jako je zpracování výjimek a ladění, podpora, kontroly za běhu a informace o typu, podrobnosti implementace a určité funkce, rozšířené knihovny. Tato knihovna je specifické pro verzi kompilátoru použít.

Tato tabulka shrnuje, které implementují knihovnu vcruntime knihoven.

|Knihovna|Přidružené knihovny DLL|Vlastnosti|Možnost|Direktivy preprocesoru|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|Žádné|Staticky propojené do kódu.|**/MT**|_MT|
|libvcruntimed.lib|Žádné|Ladicí verze pro statické propojování. Redistributable.|**/MTd**|_MT, _DEBUG|
|vcruntime.lib|vcruntime\<verze > .dll|Importovat knihovny DLL pro vcruntime.|**/ MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<version>d.dll|Importovat knihovny DLL pro ladění vcruntime. Redistributable.|**/ MDd**|_DEBUG, _MT, _DLL|

> [!NOTE]
> Kdy UCRT refaktoring došlo k chybě, funkce modulu Runtime souběžnosti se přesunuly do concrt140.dll, která byla přidána do Distribuovatelný balíček C++. Tato knihovna DLL je požadovaná pro C++ paralelní kontejnery a algoritmy, jako `concurrency::parallel_for`. Kromě toho standardní knihovny C++ potřebuje tuto knihovnu DLL na Windows XP pro podporu synchronizace primitiv, protože Windows XP nemá podmínku proměnné.

Kód, který inicializuje CRT je v jednom z několika knihoven, podle toho, jestli knihovny CRT staticky nebo dynamicky propojené, nebo nativního, spravovaného nebo smíšený kód. Tento kód zpracovává spuštění CRT, interní vlákno inicializace dat a ukončení. Je specifické pro verzi kompilátoru použít. Tato knihovna je vždy staticky propojeny, i když se používá dynamicky propojené UCRT.

Tato tabulka obsahuje seznam knihoven, které implementují CRT inicializace a ukončování.

|Knihovna|Vlastnosti|Možnost|Direktivy preprocesoru|
|-------------|---------------------|------------|-----------------------------|
|libcmt.lib|Staticky odkazuje nativní spuštění CRT do kódu.|**/MT**|_MT|
|libcmtd.lib|Staticky odkazuje ladicí verzi nativní spuštění CRT. Redistributable.|**/MTd**|_DEBUG, _MT|
|msvcrt.lib|Statická knihovna pro nativní spuštění CRT pro použití s UCRT knihovny DLL a vcruntime.|**/ MD**|_MT, _DLL|
|msvcrtd.lib|Statická knihovna pro nativní spuštění CRT pro použití s UCRT knihovny DLL a vcruntime ladicí verzi. Redistributable.|**/ MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|Statické knihovny pro smíšená nativní a spravované CRT po spuštění pro použití s UCRT knihovny DLL a vcruntime.|**/ CLR**||
|msvcmrtd.lib|Statické knihovny pro smíšená nativní a spravované CRT po spuštění pro použití s UCRT knihovny DLL a vcruntime ladicí verzi. Redistributable.|**/ CLR**||
|msvcurt.lib|**Zastaralé** statickou knihovnu, čistě spravované CRT.|**/ CLR: pure**||
|msvcurtd.lib|**Zastaralé** statické knihovny pro ladicí verze čistě spravované CRT. Redistributable.|**/ CLR: pure**||

Pokud jste se program z příkazového řádku bez možnosti kompilátoru, který určuje knihovny run-time jazyka C, linker použil staticky propojené knihovny CRT: libcmt.lib libvcruntime.lib a libucrt.lib.

Použití staticky propojených CRT znamená, že žádné informace o stavu uložené běhové knihovny jazyka C bude místní do této instance CRT. Například, pokud používáte [strtok – _strtok_l –, wcstok –, _wcstok_l –, _mbstok –, _mbstok_l –](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) při použití staticky propojených CRT, pozice `strtok` Analyzátor je nezávislá na `strtok` stavu, použít v kódu ve stejném procesu (ale v jiné knihovně DLL nebo EXE) připojený k jiné instanci statické CRT. Naproti tomu dynamicky propojené CRT sdílí stavu pro veškerý kód v rámci procesu, která je dynamicky propojené s CRT. Tento problém se nevztahuje, pokud používáte nové bezpečnější verze těchto funkcí; například `strtok_s` nemá žádné potíže.

Protože knihovny DLL vytvořené odkazování na statické CRT bude mít svůj vlastní stav CRT, není doporučeno staticky propojit CRT v knihovně DLL Pokud důsledků to výslovně požadovaných a rozumím jí. Například, pokud zavoláte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) v spustitelný soubor, který načte knihovnu DLL propojené s vlastní statické CRT, nebudou všechny hardwarové výjimky generovaná kódem v knihovně DLL zachytit translator, ale výjimky hardwaru generovaný kód v hlavní zachytí se spustitelný soubor.

Pokud používáte **/CLR** přepínač kompilátoru váš kód zůstane propojena s statickou knihovnu, msvcmrt.lib. Statická knihovna poskytuje proxy server mezi spravovaným kódem a nativní CRT. Nelze použít staticky propojených CRT ( **/MT** nebo **/MTD** možnosti) s **/CLR**. Použít dynamicky propojené knihovny (**/MD** nebo **/MDd**) místo toho. Čistě spravované knihovny CRT jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Další informace o použití CRT s **/CLR**, naleznete v tématu [smíšený (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md).

K sestavení ladicí verze vaší aplikace [_DEBUG](../c-runtime-library/debug.md) příznak musí být definován a aplikace musí být spojen s ladicí verzí jednoho z těchto knihoven. Další informace o použití ladicích verzí knihoven, naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

Tato verze CRT není plně splňující podmínky standardu C99. Konkrétně se \<tgmath.h > záhlaví a makra CX_LIMITED_RANGE/FP_CONTRACT – Direktiva pragma se nepodporují. Některé prvky, jako je například význam specifikátory parametrů ve standardních funkcích vstupně-výstupních operací používají starší verzi interpretace ve výchozím nastavení. Můžete použít /Zc – možnosti kompilátoru shody a určete možnosti linkeru můžete ovládat některé knihovny shody

## <a name="c-standard-library"></a>Standardní knihovna C++

|Standardní knihovna C++|Vlastnosti|Možnost|Direktivy preprocesoru|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|S více vlákny, statické propojení|**/MT**|_MT|
|msvcprt.lib|Odkaz s více vlákny, dynamické (Importovat knihovny pro MSVCP*verze*.dll)|**/ MD**|_MT, _DLL|
|libcpmtd.lib|S více vlákny, statické propojení|**/MTd**|_DEBUG, _MT|
|msvcprtd.lib|Odkaz s více vlákny, dynamické (Importovat knihovny pro MSVCP*verze*D.DLL)|**/ MDd**|_DEBUG, _MT, _DLL|

Při sestavování projektu verzi jednu základní knihovny jazyka C za běhu (libcmt.lib, msvcmrt.lib, msvcrt.lib) je propojený ve výchozím nastavení, v závislosti na možnosti kompilátoru zvolíte (s více vlákny, knihovny DLL, / CLR). Zadáte-li jeden z [souborech hlaviček standardní knihovny C++](../standard-library/cpp-standard-library-header-files.md) ve vašem kódu, standardní knihovna C++ se propojí v automaticky Visual c++ v době kompilace. Příklad:

```cpp
#include <ios>
```

Pro binární kompatibilitu může být určeno více než jeden soubor DLL knihovnu jeden import. Aktualizace verze můžou zavést *dot knihovny*, samostatné knihovny DLL, které představují nové funkce knihovny. Například Visual Studio 2017 verze 15.6 zavedené msvcp140_1.dll pro podporu funkcí další standardní knihovny bez narušení ABI podporuje msvcp140.dll. Knihovna importu msvcprt.lib součástí sady nástrojů pro Visual Studio 2017 verze 15.6 podporuje obě knihovny DLL a vcredist pro tuto verzi nainstaluje i knihovny DLL. Po odeslání, knihovnu tečkou má pevnou ABI a nebude mít nikdy žádná závislost na novější knihovny tečkou.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Jaké problémy existují, pokud aplikace používá více než jedna verze CRT?

Každý spustitelné bitové kopie (EXE nebo DLL) může mít svůj vlastní staticky propojených CRT, nebo můžete dynamicky propojit CRT. Verze CRT součástí staticky nebo dynamicky načíst konkrétní Image závisí na verzi nástroje a knihovny, který byl sestaven s. Jednoho procesu může načíst více EXE a DLL obrázky, každý s vlastní CRT. Každá z těchto CRTs mohou používat různé allocator, mohou mít odlišnou strukturu interní rozložení a mohou použít režim jiného úložiště. To znamená, že přidělené paměti, CRT prostředky nebo třídy, které jsou předány přes hranice knihovny DLL může způsobit problémy v Správa paměti, využití interní statické nebo rozložení interpretace. Například pokud třída je přidělená v jedna knihovna DLL, ale předán a odstraněn jiným, které CRT dealokátor slouží? Chyby způsobené můžete v rozsahu od malý do okamžitě závažná a proto směrování přenosu těchto prostředků, se důrazně nedoporučuje.

Mnohé z těchto problémů můžete vyhnout pomocí technologie binární rozhraní aplikace (ABI) místo, protože jsou stabilní a verzování. Návrh rozhraní k předávání informací podle hodnoty nebo pracovat v paměti, které je předáno volající export knihovny DLL spíše než přidělen lokálně a vrátit zpět volajícímu. Strukturovaná data mezi spustitelné bitové kopie pomocí techniky sběrného systému. Zapouzdření místně prostředků a manipulace prostřednictvím obslužné rutiny nebo funkce, které můžete zpřístupnit klientům povolit pouze.

Je také možné vyhnout některé z těchto potíží, pokud všechny Image v procesu použít stejnou verzi dynamicky načíst CRT. Aby bylo zajištěno, že všechny komponenty používat stejnou verzi knihovny DLL CRT, je vytvořit pomocí **/MD** možnost a použijte stejné nastavení vlastnosti a sady nástrojů kompilátoru.

Některé péči Pokud váš program projde určitých prostředků CRT (jako jsou popisovače souborů, národní prostředí a proměnných prostředí) přes hranice knihovny DLL, i když se používá stejnou verzi CRT. Další informace o problematiku a způsob jejich řešení najdete v tématu [potenciální chyby předávání CRT objekty přes hranice knihovny DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).


## <a name="see-also"></a>Viz také:

- [Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)
