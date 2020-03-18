---
title: Funkce knihovny CRT
ms.date: 08/20/2018
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
ms.openlocfilehash: a350e2c45d9ccf83fb09a76f43b63a6b17273cff
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438556"
---
# <a name="crt-library-features"></a>Funkce knihovny CRT

Toto téma popisuje různé soubory. lib, které tvoří běhové knihovny jazyka C, i jejich přidružené možnosti kompilátoru a direktivy preprocesoru.

## <a name="c-run-time-libraries-crt"></a>Běhové knihovny jazyka C (CRT)

Knihovna run-time jazyka C (CRT) je součástí C++ standardní knihovny, která zahrnuje standardní knihovnu ISO C99. Vizuální C++ knihovny, které implementují nativní vývoj kódu a jak smíšený nativní a spravovaný kód. Všechny verze CRT podporují vývoj s více vlákny. Většina knihoven podporuje statické propojení, odkazování knihovny přímo do kódu nebo dynamické propojení, aby mohl váš kód používat běžné soubory DLL.

Počínaje verzí Visual Studio 2015 byl CRT refaktorované do nových binárních souborů. Universal CRT (UCRT) obsahuje funkce a Globals exportované standardní knihovnou CRT C99. UCRT je teď součástí Windows a dodává se jako součást Windows 10. Statická knihovna, knihovna importu DLL a hlavičkové soubory pro UCRT se teď nacházejí v sadě Windows 10 SDK. Při instalaci vizuálu C++nainstaluje instalační program sady Visual Studio podmnožinu sady Windows 10 SDK, která je nutná k použití rozhraní UCRT. UCRT můžete použít na libovolné verzi Windows, kterou podporuje Visual Studio 2015 a novější verze. Můžete ji znovu distribuovat pomocí vcredist pro podporované verze Windows, jiné než Windows 10. Další informace najdete v tématu [Redistribuce vizuálních C++ souborů](../windows/redistributing-visual-cpp-files.md).

V následující tabulce jsou uvedeny knihovny, které implementují rozhraní UCRT.

|Knihovna|Přidružená knihovna DLL|Vlastnosti|Možnost|Direktivy preprocesoru|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt. lib|Žádná|Staticky propojí UCRT s vaším kódem.|**/MT**|_MT|
|libucrtd.lib|Žádná|Ladicí verze UCRT pro statické propojení. Nedistribuovatelné|**/MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|Knihovna importů DLL pro UCRT.|**/MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|Knihovna importů DLL pro ladicí verzi UCRT. Nedistribuovatelné|**/MDd**|_DEBUG, _MT, _DLL|

Knihovna vcruntime obsahuje kód specifický C++ pro implementaci vizuálního CRT, jako je například zpracování výjimek a podpora ladění, kontroly za běhu a informace o typu, podrobnosti implementace a některé rozšířené funkce knihovny. Tato knihovna je specifická pro použitou verzi kompilátoru.

Tato tabulka obsahuje seznam knihoven, které implementují knihovnu vcruntime.

|Knihovna|Přidružená knihovna DLL|Vlastnosti|Možnost|Direktivy preprocesoru|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime. lib|Žádná|Staticky propojená s vaším kódem.|**/MT**|_MT|
|libvcruntimed.lib|Žádná|Verze ladění pro statické propojení. Nedistribuovatelné|**/MTd**|_MT, _DEBUG|
|vcruntime. lib|vcruntime\<verze >. dll|Knihovna importů DLL pro vcruntime.|**/MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<verze > d. dll|Knihovna importů DLL pro vcruntime ladění. Nedistribuovatelné|**/MDd**|_DEBUG, _MT, _DLL|

> [!NOTE]
> Při refaktoringu UCRT byly funkce Concurrency Runtime přesunuty do souboru concrt140. dll, který byl přidán do C++ redistribuovatelného balíčku. Tato knihovna DLL je vyžadována C++ pro paralelní kontejnery a algoritmy, jako je například `concurrency::parallel_for`. Kromě toho C++ standardní knihovna vyžaduje, aby tato knihovna DLL v systému Windows XP podporovala prvky synchronizace, protože systém Windows XP nemá proměnné podmínky.

Kód, který inicializuje CRT, je v jedné z několika knihoven, na základě toho, zda je knihovna CRT staticky nebo dynamicky propojena, nebo nativní, spravovaná nebo smíšený kód. Tento kód zpracovává spuštění CRT, interní inicializaci dat na vlákno a ukončení. Je specifický pro použitou verzi kompilátoru. Tato knihovna je vždycky propojená staticky, i když používáte dynamicky propojené UCRT.

Tato tabulka obsahuje seznam knihoven, které implementují inicializaci a ukončení CRT.

|Knihovna|Vlastnosti|Možnost|Direktivy preprocesoru|
|-------------|---------------------|------------|-----------------------------|
|libcmt.lib|Staticky propojí nativní spuštění CRT s vaším kódem.|**/MT**|_MT|
|libcmtd.lib|Staticky propojí ladicí verzi nativního spuštění CRT. Nedistribuovatelné|**/MTd**|_DEBUG, _MT|
|msvcrt.lib|Statická knihovna pro nativní spuštění CRT pro použití s knihovnou DLL UCRT a vcruntime.|**/MD**|_MT, _DLL|
|msvcrtd.lib|Statická knihovna pro ladicí verzi nativního spuštění CRT pro použití s knihovnou DLL UCRT a vcruntime. Nedistribuovatelné|**/MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|Statická knihovna pro smíšené nativní a spravované spuštění CRT pro použití s knihovnou DLL UCRT a vcruntime.|**možností**||
|msvcmrtd.lib|Statická knihovna pro ladicí verzi smíšeného nativního a spravovaného spuštění CRT pro použití s knihovnou DLL UCRT a vcruntime. Nedistribuovatelné|**možností**||
|msvcurt.lib|**Zastaralé** Statická knihovna pro čistě spravovanou knihovnu CRT.|**/CLR: Pure**||
|msvcurtd.lib|**Zastaralé** Statická knihovna pro ladicí verzi čistě spravovaného CRT. Nedistribuovatelné|**/CLR: Pure**||

Pokud propojíte program z příkazového řádku bez možnosti kompilátoru, která určuje knihovnu run-time jazyka C, linker použije staticky propojené knihovny CRT: Libcmt. lib, libvcruntime. lib a libucrt. lib.

Použití staticky propojeného CRT znamená, že všechny informace o stavu uložené v běhové knihovně jazyka C budou místní k této instanci CRT. Například pokud používáte [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok _mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) při použití staticky propojeného CRT, pozice analyzátoru `strtok` nesouvisí se stavem `strtok` použitým v kódu ve stejném procesu (ale v jiné knihovně DLL nebo exe), která je propojena s jinou instancí statického CRT. Naproti tomu dynamicky propojený stav sdílených složek CRT pro veškerý kód v rámci procesu, který je dynamicky propojen s CRT. Tato obava se nevztahuje, pokud používáte nové bezpečnější verze těchto funkcí. například `strtok_s` nemá tento problém.

Vzhledem k tomu, že knihovna DLL vytvořená odkazem na statickou CRT bude mít svůj vlastní stav CRT, není doporučeno propojit staticky na CRT v knihovně DLL, pokud nejsou důsledky této skutečnosti konkrétně požadovány a srozumitelné. Například pokud zavoláte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) ve spustitelném souboru, který načte knihovnu DLL propojenou s vlastním statickým CRT, všechny výjimky hardwaru generované kódem v knihovně DLL nebudou zachyceny, ale budou zachyceny výjimky hardwaru generované kódem v hlavním spustitelném souboru.

Pokud používáte přepínač **/CLR** kompilátoru, váš kód bude propojen se statickou knihovnou msvcmrt. lib. Statická knihovna poskytuje proxy mezi spravovaným kódem a nativním CRT. Nemůžete použít staticky propojené CRT (možnosti **/Mt** nebo **/MTD** ) s možností **/CLR**. Místo toho použijte dynamicky propojené knihovny ( **/MD** nebo **/MDD**). Čistě spravované knihovny CRT jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Další informace o použití CRT s **/CLR**naleznete v tématu [smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md).

Chcete-li sestavit ladicí verzi aplikace, musí být definován příznak [_DEBUG](../c-runtime-library/debug.md) a aplikace musí být propojeny s ladicí verzí jedné z těchto knihoven. Další informace o použití ladicích verzí souborů knihoven naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

Tato verze CRT není plně vyhovující standardu C99. Konkrétně > záhlaví \<tgmath. h a makra direktivy pragma CX_LIMITED_RANGE/FP_CONTRACT nejsou podporována. Některé prvky, jako například význam specifikátorů parametrů ve standardních vstupně-výstupních operacích, používají ve výchozím nastavení starší interpretace. Můžete použít možnosti shody kompilátoru/Zc a zadat možnosti linkeru pro řízení některých aspektů shody knihovny,

## <a name="c-standard-library"></a>Standardní knihovna C++

|Standardní knihovna C++|Vlastnosti|Možnost|Direktivy preprocesoru|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|Multithreading, statický odkaz|**/MT**|_MT|
|msvcprt.lib|Multithreading, dynamické propojení (import knihovny pro MSVCP*verze*. dll)|**/MD**|_MT, _DLL|
|libcpmtd.lib|Multithreading, statický odkaz|**/MTd**|_DEBUG, _MT|
|msvcprtd.lib|Multithreading, dynamické propojení (import knihovny pro MSVCP*verze*D. dll)|**/MDd**|_DEBUG, _MT, _DLL|

Když sestavíte verzi projektu, jedna ze základních knihoven run-time jazyka C (Libcmt. lib, msvcmrt. lib, Msvcrt. lib) je ve výchozím nastavení propojena v závislosti na zvolené možnosti kompilátoru (vícevláknové, DLL,/CLR). Pokud zahrnete do kódu jeden ze [ C++ standardních souborů hlaviček knihovny](../standard-library/cpp-standard-library-header-files.md) , C++ standardní knihovna se v době kompilace automaticky propojí pomocí vizuálu C++ . Příklad:

```cpp
#include <ios>
```

V případě binární kompatibility může být více než jeden soubor DLL určen jedinou knihovnou importu. Aktualizace verze mohou zavést *knihovny teček*, samostatné knihovny DLL, které zavádějí nové funkce knihovny. Například Visual Studio 2017 verze 15,6 zavedla msvcp140_1. dll pro podporu dalších funkcí standardní knihovny bez přerušení ABI podporovaného knihovnou msvcp140. dll. Knihovna importu MSVCPRT. lib obsažená v sadě nástrojů pro Visual Studio 2017 verze 15,6 podporuje obě knihovny DLL a VCRedist pro tuto verzi nainstaluje obě knihovny DLL. Po odeslání má knihovna teček pevný ABI a nikdy nebude mít závislost na pozdější knihovně teček.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Jaké problémy existují, pokud aplikace používá více než jednu verzi CRT?

Každá spustitelná Image (EXE nebo DLL) může mít vlastní staticky propojenou CRT, nebo může dynamicky propojit s CRT. Verze CRT staticky zahrnutá v nebo dynamicky načtená konkrétní imagí závisí na verzi nástrojů a knihoven, se kterými byla vytvořena. Jeden proces může načítat několik imagí EXE a DLL, z nichž každý má vlastní CRT. Každý z těchto CRTs může používat jiný Alokátor, může mít různá interní rozložení struktury a může používat jiné uspořádání úložišť. To znamená, že přidělená paměť, prostředky CRT nebo třídy předané přes hranice knihovny DLL mohou způsobit problémy v rámci správy paměti, interního statického použití nebo interpretace rozložení. Například pokud je třída přidělena v jedné knihovně DLL, ale předává a odstranila ji jiný, které dealokace CRT se používá? Chyby způsobené chybou můžou být v rozsahu od nejemného po bezprostřední závažnou a proto se důrazně nedoporučuje přímý přenos takových prostředků.

Mnohé z těchto potíží se můžete vyhnout použitím technologií ABI (Application Binary Interface), protože jsou navržené tak, aby byly stabilní a s verzí. Navrhněte exportovaná rozhraní knihovny DLL, aby předávala informace podle hodnoty, nebo fungovala v paměti, která je předána volajícím místo toho, aby byla přidělena místně a vrácena volajícímu. Pomocí technik zařazování můžete kopírovat strukturovaná data mezi spustitelnými bitovými kopiemi. Zapouzdření prostředků místně a povoluje pouze manipulaci prostřednictvím popisovačů nebo funkcí vystavování klientům.

Některé z těchto problémů je také možné vyhnout, pokud všechny bitové kopie v procesu používají stejnou dynamicky načtenou verzi CRT. Chcete-li zajistit, aby všechny komponenty používaly stejnou verzi knihovny CRT, sestavte je pomocí možnosti **/MD** a použijte stejné nastavení sady nástrojů a vlastností kompilátoru.

Některá péče je nutná, pokud váš program před hranicemi knihoven DLL předává určité prostředky CRT (jako jsou popisovače souborů, místní hodnoty a proměnné prostředí), a to i v případě, že používáte stejnou verzi CRT. Další informace o problémech, které je potřeba vyřešit, najdete v tématu [možné chyby při předávání objektů CRT napříč hranicemi knihoven DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)
