---
title: Funkce knihovny CRT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.runtime
dev_langs: C++
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
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed41372637e9ee68db087fbe0ad532d9e6bb4935
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crt-library-features"></a>Funkce knihovny CRT
Toto téma popisuje různé soubory .lib, které tvoří běhové knihovny jazyka C a také jejich možnosti přidružené kompilátoru a preprocesor – direktivy.  
  
## <a name="c-run-time-libraries-crt"></a>Běhové knihovny jazyka C (CRT)  
 Knihovny jazyka C Run-time (CRT) je součástí standardní knihovna C++, která zahrnuje standardní knihovna ISO C99. Knihovny jazyka Visual C++, které implementují CRT podporují vývoj nativního kódu a jak smíšený nativního a spravovaného kódu a čistý spravovaného kódu pro .NET – vývoj. Všechny verze CRT podporovat vícevláknové. Většina knihoven podporovat statické propojení, propojení knihovny přímo do kódu, i dynamické propojování umožníte kód používá společné soubory DLL.  
  
 Spouštění v sadě Visual Studio 2015, má byla CRT rozdělili do nové binární soubory. Universal CRT (UCRT) obsahuje funkce a globální funkce exportované sadou standardní knihovny C99 CRT. UCRT je teď součástí Windows a dodává jako součást Windows 10. Statickou knihovnu, knihovny DLL knihovny importu a soubory hlaviček pro UCRT jsou teď součástí Windows 10 SDK. Když instalujete Visual C++, instalaci sady Visual Studio nainstaluje do něj podmnožinu k použití UCRT vyžaduje Windows 10 SDK. Můžete UCRT na libovolnou verzi systému Windows nepodporuje sady Visual Studio 2015 a novější verze. Můžete znovu distribuovat pomocí vcredist pro podporované verze systému Windows než Windows 10. Další informace najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
 Následující tabulka uvádí knihovny, které implementují UCRT.  
  
|Knihovna|Přidružené knihovny DLL|Vlastnosti|Možnost|Preprocesor – direktivy|  
|-------------|--------------------|---------------------|------------|-----------------------------|  
|libucrt.lib|Žádné|Staticky odkazuje UCRT do vašeho kódu.|**/ MT**|_MT –|  
|libucrtd.lib|Žádné|Ladění verzi UCRT pro statické propojení. Není redistributable.|**/ MTd**|_DEBUG –, _MT –|  
|ucrt.lib|ucrtbase.dll|Import knihovny DLL pro UCRT.|**/MD**|_MT –, _DLL –|  
|ucrtd.lib|ucrtbased.dll|Knihovny DLL importovat knihovny pro ladění verzi UCRT. Není redistributable.|**/ MDd**|_DEBUG – _MT –, _DLL –|  
  
 Knihovna vcruntime obsahuje kódu pro konkrétní implementaci Visual C++ CRT, jako je například zpracování výjimek a ladění podpory, kontrol za běhu a informace o typu, podrobnosti implementace a určité funkce Rozšířené knihovny. Tato knihovna je specifické pro verzi kompilátoru použít.  
  
 Tato tabulka uvádí knihovny, které implementují vcruntime knihovny.  
  
|Knihovna|Přidružené knihovny DLL|Vlastnosti|Možnost|Preprocesor – direktivy|  
|-------------|--------------------|---------------------|------------|-----------------------------|  
|libvcruntime.lib|Žádné|Staticky propojené do vašeho kódu.|**/ MT**|_MT –|  
|libvcruntimed.lib|Žádné|Ladicí verze pro statické propojení. Není redistributable.|**/ MTd**|_MT –, _DEBUG –|  
|vcruntime.lib|vcruntime\<verze > .dll|Import knihovny DLL pro vcruntime.|**/MD**|_MT –, _DLL –|  
|vcruntimed.lib|vcruntime\<verze > d.dll|Import knihovny DLL pro vcruntime ladění. Není redistributable.|**/ MDd**|_DEBUG – _MT –, _DLL –|  
  
 Kód, který inicializuje CRT je v jednom z několika knihovny, na základě toho, jestli knihovny CRT staticky nebo dynamicky propojené, nebo nativní, spravované nebo smíšený kód. Tento kód zpracovává CRT spuštění, interní vlákno data inicializace a ukončování. Je specifické pro verzi kompilátoru použít. Tato knihovna je vždy staticky propojené, i když se používá dynamicky propojené UCRT.  
  
 Tato tabulka uvádí knihovny, které implementují inicializace CRT a ukončení.  
  
|Knihovna|Vlastnosti|Možnost|Preprocesor – direktivy|  
|-------------|---------------------|------------|-----------------------------|  
|Libcmt.lib|Staticky odkazuje nativní spuštění CRT do vašeho kódu.|**/ MT**|_MT –|  
|libcmtd.lib|Ladicí verze nativní spuštění CRT staticky odkazuje. Není redistributable.|**/ MTd**|_DEBUG –, _MT –|  
|Msvcrt.lib|Statické knihovny pro nativní spuštění CRT pro použití s DLL UCRT a vcruntime.|**/MD**|_MT –, _DLL –|  
|msvcrtd.lib|Statické knihovny pro nativní spuštění CRT pro použití s DLL UCRT a vcruntime ladicí verzi. Není redistributable.|**/ MDd**|_DEBUG – _MT –, _DLL –|  
|msvcmrt.lib|Statické knihovny pro smíšená nativní a spravovaná počáteční CRT pro použití s DLL UCRT a vcruntime.|**/ CLR**||  
|msvcmrtd.lib|Statické knihovny pro ladění verzi smíšený nativní a spravovaná počáteční CRT pro použití s DLL UCRT a vcruntime. Není redistributable.|**/ CLR**||  
|Msvcurt.lib|**Zastaralé** statické knihovny pro čistě spravované CRT.|**/ CLR: pure**||  
|msvcurtd.lib|**Zastaralé** statické knihovny pro ladicí verze čistě spravované CRT. Není redistributable.|**/ CLR: pure**||  
  
 Pokud jste váš program z příkazového řádku bez možnosti kompilátoru, která určuje běhové knihovny jazyka C, linkeru použije staticky propojené knihovny CRT: libcmt.lib, libvcruntime.lib a libucrt.lib.  
  
 Pomocí staticky propojené CRT znamená, že bude místní pro tuto instanci CRT žádné informace o stavu ukládaná běhové knihovny jazyka C. Například, pokud používáte [strtok –, _strtok_l –, wcstok –, _wcstok_l –, _mbstok –, _mbstok_l –](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) při použití staticky propojené CRT, pozice `strtok` Analyzátor je nezávislá na `strtok` stavu používá v kódu v rámci jednoho procesu (ale v různých knihovny DLL nebo EXE) připojený k jiné instanci statické CRT. Naproti tomu dynamicky propojené CRT sdílí stav pro všechny kódu v rámci procesu, který je dynamicky propojené s CRT. Tuto situaci není platné, pokud použijete nové bezpečnější verze těchto funkcí; například `strtok_s` nemá tento problém.  
  
 Protože vytvořené propojení s statické CRT knihovny DLL, bude mít stav CRT, není doporučeno staticky propojit CRT v knihovně DLL Pokud důsledky tohoto konkrétně potřeby a rozumím jim. Například, pokud zavoláte [_set_se_translator –](../c-runtime-library/reference/set-se-translator.md) v spustitelné soubory, které propojené s vlastním statické CRT knihovnu DLL načte, všechny výjimky hardwaru generované kód v knihovně DLL nebude možné zachytila překladač, ale výjimky hardwaru generuje kód v hlavní vzniká, spustitelný soubor.  
  
 Pokud používáte **/CLR** přepínače kompilátoru váš kód bude propojen s statickou knihovnu, msvcmrt.lib. Statické knihovny poskytuje server proxy mezi spravovaného kódu a nativní CRT. Nemůžete použít staticky propojené CRT ( **/MT** nebo **/MTd** možnosti) s **/CLR**. Používat dynamicky propojené knihovny (**/MD** nebo **/MDd**) místo.  
  
 Pokud používáte **/CLR: pure** přepínače kompilátoru váš kód bude propojená se statickou knihovnou msvcurt.lib. Stejně jako u **/CLR**, nemůže propojit s staticky propojené knihovny. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé od verze sady Visual Studio 2015.  
  
 Další informace o používání CRT s **/CLR**, najdete v části [Mixed (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md); pro **/CLR: pure**, najdete v části [prázdná a ověřitelný kód (C + +/ Rozhraní příkazového řádku)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 K sestavení ladicí verze vaší aplikace [_DEBUG –](../c-runtime-library/debug.md) příznak musí být definovaný a aplikace musí být propojena s ladicí verze jednoho z těchto knihoven. Další informace o používání ladicí verze souborů knihovny najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
 Tato verze CRT není plně shoduje s C99 standard. Konkrétně \<tgmath.h > záhlaví a makra CX_LIMITED_RANGE/fp_contract – Direktiva pragma nejsou podporovány. Některé prvky, jako jsou například význam specifikátory parametrů ve standardních funkcích vstupně-výstupních operací používají starší verze interpretace ve výchozím nastavení. Můžete použít /Zc – možnosti kompilátoru shoda a zadejte řídit některé aspekty knihovny shoda – možnosti linkeru  
  
## <a name="c-standard-library"></a>Standardní knihovna C++  
  
|Standardní knihovna C++|Vlastnosti|Možnost|Preprocesor – direktivy|  
|----------------------------|---------------------|------------|-----------------------------|  
|LIBCPMT. LIB|Více vláken, statické propojení|**/ MT**|_MT –|  
|MSVCPRT. LIB|Více vláken, dynamického propojení (Importovat knihovny pro MSVCP\<verze > .dll)|**/MD**|_MT –, _DLL –|  
|LIBCPMTD. LIB|Více vláken, statické propojení|**/ MTd**|_DEBUG –, _MT –|  
|MSVCPRTD. LIB|Více vláken, dynamického propojení (Importovat knihovny pro MSVCP\<verze > D.DLL)|**/ MDd**|_DEBUG – _MT –, _DLL –|  
  
 Při vytváření verzi vašeho projektu, mezi základní běhové knihovny jazyka C (LIBCMT. LIB, MSVCMRT. LIB, MSVCRT. Ve výchozím nastavení je propojený LIB), v závislosti na možnosti kompilátoru zvolíte (s více vlákny, knihovny DLL, / CLR). Pokud můžete použít jeden z [soubory hlaviček standardní knihovna C++](../standard-library/cpp-standard-library-header-files.md) ve vašem kódu standardní knihovna C++ propojí v automaticky ve Visual C++ v době kompilace. Příklad:  
  
```  
#include <ios>   
```  
  
## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Jaké problémy existovat, pokud aplikace používá více než jedna verze CRT?  
 Pokud máte více než jeden DLL nebo EXE, pak můžete mít více než jeden CRT, zda používáte různé verze Visual C++. Například do více knihovny DLL staticky propojení CRT může být stejný problém. Vývojáři dochází k tomuto problému s statické CRTs jste dostali pokyn ke kompilaci s **/MD** používat CRT knihovny DLL. Pokud vaše knihovny DLL úspěšně prostředky CRT přes hranice knihovny DLL, může dojít k potížím s odlišnými CRTs a muset znovu zkompiluje váš projekt pomocí Visual C++.  
  
 Pokud váš program používá více než jedna verze CRT, některé péči při předávání určitých objektů CRT (jako jsou popisovače souborů, národní prostředí a proměnných prostředí) přes hranice knihovny DLL. Další informace o problematika a způsob jejich řešení najdete v tématu [potenciální chyby předávání CRT objekty přes hranice knihovny DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace běhové knihovny jazyka C](../c-runtime-library/c-run-time-library-reference.md)