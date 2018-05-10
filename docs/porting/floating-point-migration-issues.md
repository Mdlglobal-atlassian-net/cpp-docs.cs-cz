---
title: Problémy s plovoucí desetinnou čárkou migrace | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e6578486ada758482b270cd5505338e2acf3eb9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="floating-point-migration-issues"></a>Problémy s plovoucí desetinnou čárkou migrace  
  
Někdy při upgradu vašich projektů na novější verzi sady Visual Studio, můžete zjistit, že došlo ke změně výsledků určité operace s plovoucí desetinnou čárkou. K tomu obvykle dojde pro jednu ze dvou důvodů: generování kódu změny tohoto lepší využít k dispozici procesoru a opravy chyb nebo změny algoritmy používané v matematické funkce v běhové knihovny jazyka C (CRT). Obecně platí jsou správné pro v rámci určeného standardní jazyk nové výsledky. Přečtěte si k podívejte se, co se změnilo, a pokud je důležité, jak získat stejné výsledky funkce tu před.  

## <a name="new-math-functions-and-universal-crt-changes"></a>Matematické nové funkce a změny Universal CRT  
  
Většina matematické funkce CRT byly k dispozici v sadě Visual Studio let, ale od ve Visual Studiu 2013 se všechny funkce, které vyžadují ISO C99 jsou zahrnuty. Tyto funkce jsou implementované vyvážit výkonu s správnost. Vzhledem k vytváření správně zaokrouhlené výsledek v každém případě může být výtažkovými, tyto funkce jsou navrženy pro efektivní vytvořit blízká aproximace správně zaokrouhlené výsledek. Ve většině případů výsledku vytvořeného je v rámci +/-1 jednotka minimálně přesnost nebo *ulp*, správně zaokrouhlené výsledku, ale někdy může být níž se nachází větší nepřesnost. Pokud jste používali knihovnu různých matematické získat tyto funkce před, může být zodpovědná za změnu v hodnotě výsledky implementace rozdíly.   
    
Když matematické funkce se přesunuly na Universal CRT v sadě Visual Studio 2015, byly použity některé nových algoritmů a bylo opraveno několik chyb při provádění funkce, které byly nové v sadě Visual Studio 2013. Tyto změny může vést k rozpoznat rozdíly ve výsledcích výpočty s plovoucí desetinnou čárkou, které používají tyto funkce. Funkce, které měl chyb problémy bylo ERF –, exp2 –, zbývající, remquo –, scalbln a scalbn – a jejich float a long double variant.  Další změny v sadě Visual Studio 2015 vyřešili problémy v zachování plovoucí word a výjimky stavu informací o stavu bodu _clear87 – _clearfp –, fegetenv, fesetenv a feholdexcept funkcí.  
  
## <a name="processor-differences-and-compiler-flags"></a>Procesor rozdíly a příznaky kompilátoru  
  
Řadu procedura bodu matematické funkce knihovny mají různé implementace pro různé architektury procesoru. Například x86 32-bit CRT může mít jinou implementaci než 64-bit x64 CRT. Kromě toho některé funkce mohou mít více implementace pro danou architekturu procesoru. Nejúčinnější implementace je vybrán dynamicky za běhu v závislosti na sady instrukcí nepodporuje procesoru. Například v x86 32-bit CRT, některé funkce mají obě x87 implementaci a SSE2 implementace. Při spuštění na procesor, který podporuje SSE2, rychlejší implementace SSE2 se používá. Při spuštění na procesor, který nepodporuje SSE2, pomalejší x87, které slouží k implementaci. Můžete je vidět, při migraci původní kód, protože výchozí x86 kompilátoru architektura možnost změnit tak, aby [/arch:SSE2](../build/reference/arch-x86.md) v sadě Visual Studio 2012. Protože různými implementacemi matematické funkce knihovny může používat jinou pokyny procesoru a různé algoritmy nepřineslo jejich výsledky, funkce mohou mít různé výsledky na různých platformách. Ve většině případů jsou výsledky v rámci +/-1 ulp správně zaokrouhlené výsledek, ale skutečný výsledek se může lišit mezi procesory.  
  
Generování kódu správnost vylepšení v různých režimech bodu plovoucí v sadě Visual Studio může také ovlivnit výsledky operací s plovoucí desetinnou čárkou srovnání starý kód je nový kód, i když se používá stejné příznaky kompilátoru. Například kód vygenerovaný Visual Studio 2010 při [/fp: přesné](../build/reference/fp-specify-floating-point-behavior.md) (výchozí) nebo **/fp: striktní** byl zadán nemusí mít rozšíří hodnoty zprostředkující not-a-number (NaN) prostřednictvím výrazy správně. Proto některé výrazů, které jste dali číselného výsledku v starší kompilátory může nyní správně vytvořit v důsledku toho NaN. Může se také zobrazit rozdíly protože optimalizace kódu pro **/fp:fast** nyní využívat další funkce procesoru. Tyto optimalizace můžete použít méně pokyny, ale může mít vliv generovaného výsledky, protože některé dříve viditelné zprostředkující operace byly odebrány.  
  
## <a name="how-to-get-identical-results"></a>Jak získat identické výsledky  
  
Ve většině případů s plovoucí desetinnou čárkou změny v nejnovější kompilátory a mít za následek rychlejší nebo více správné chování, nebo obojí. Lepší výkon spotřeby procesoru může zobrazit i při SSE2 pokyny nahradit x87 pokyny. Ale pokud máte kód, který se musí přesně replikaci adresáře procedura bodu chování starší kompilátoru, zvažte použití sady Visual Studio nativní cílení na více možností a vytváření ovlivněných projektu se starší nástrojů. Další informace najdete v tématu [pomocí nativní cílení na více v sadě Visual Studio staré projekty sestavení](use-native-multi-targeting.md).  
  
## <a name="see-also"></a>Viz také  
  
[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)  
