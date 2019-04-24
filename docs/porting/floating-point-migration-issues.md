---
title: Problémy migrace s plovoucí desetinnou čárkou
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: a259cf276c0347fda4954b46318cc79be88028ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205202"
---
# <a name="floating-point-migration-issues"></a>Problémy migrace s plovoucí desetinnou čárkou

Někdy při upgradu projektů na novější verzi sady Visual Studio, můžete zjistit, že jste změnili výsledky určitých operací s plovoucí desetinnou čárkou. Obecně se stane pro jednu ze dvou důvodů: Generování provedené změny, které využívají lepší procesoru a opravy chyb a změny na algoritmy používané matematické funkce v knihovně modulu runtime jazyka C (CRT) Obecně platí nové výsledky jsou správné a v mezích určeného standard jazyka. Přečtěte si k podívejte se, co se změnilo, a pokud je důležité, jak získat stejné výsledky vašich funkcí je teď před.

## <a name="new-math-functions-and-universal-crt-changes"></a>Nový matematické funkce a změny Universal CRT

Většina matematické funkce CRT byly k dispozici v sadě Visual Studio let, ale spuštění v sadě Visual Studio 2013, všechny funkce vyžadované ISO C99 jsou zahrnuty. Tyto funkce jsou implementované vyvážit výkon s správnosti. Protože vytváření správně zakulacený výsledky ve všech případech může být nepřekonatelně drahé, tyto funkce jsou navržené tak efektivně vytvářet aproximace správně zakulacený výsledek. Ve většině případů výsledek vytvořený je v rámci +/-1 jednotku nejnižší přesnosti, nebo *ulp*, výsledku správně zakulacený, ale mohou nastat případy, ve kterých je větší nepřesnost. Pokud jste používali různé matematické knihovny pro získání těchto funkcí před, může být zodpovědná za změny ve výsledcích implementace rozdíly.

Když matematické funkce se přesunuly na Universal CRT v sadě Visual Studio 2015, byly použity některé nové algoritmy a bylo opraveno několik chyb při provádění funkce, které byly Novinky v sadě Visual Studio 2013. Tyto změny můžou vést k zjistitelná rozdíly ve výsledcích výpočtů s plovoucí desetinnou čárkou, které používají tyto funkce. Funkce, které se vyskytly chyby problémy byly erf, exp2 –, zbývající, remquo –, scalbln a scalbn – a jejich plovoucí desetinnou čárkou a long double variant.  Další změny v sadě Visual Studio 2015 oprava potíží při zachování s plovoucí desetinnou čárkou aplikace word a výjimek stavu informací o stavu bodu _clear87 – _clearfp –, fegetenv, fesetenv a feholdexcept funkcí.

## <a name="processor-differences-and-compiler-flags"></a>Procesor rozdíly a příznaky kompilátoru

Hodnoty s plovoucí mnoho matematických knihovních funkcí mají různé implementace pro rozdílné architektury procesoru bodu. Například x86 32-bit CRT může mít jinou implementaci než 64-bit x64 CRT. Kromě toho některé funkce mohou mít několik implementací pro danou architekturu procesoru. Nejúčinnější implementace je vybrán dynamicky za běhu v závislosti na instrukční sadu podporovaných procesoru. Například v 32bitové x86 CRT, některé funkce mají obě x87 provádění a implementaci SSE2. Při spuštění na procesor, který podporuje SSE2, se používá rychlejší provádění SSE2. Když se používá Procesorem, který nepodporuje SSE2, pomalejší x87 použita implementace. Můžete je vidět při migraci starý kód, protože výchozí x86 kompilátoru architektura možnost změnit na [SSE2](../build/reference/arch-x86.md) v sadě Visual Studio 2012. Protože různé implementace matematických knihovních funkcí může pomocí různých procesorů pokyny a různé algoritmy jejich výsledky, funkce mohou mít různé výsledky na různých platformách. Ve většině případů jsou výsledky v rámci +/-1 ulp výsledku správně zakulacený, ale skutečné výsledky se mohou lišit mezi procesory.

Vylepšení správnosti generování kódu v různých režimech bodu s plovoucí desetinnou čárkou v sadě Visual Studio může také ovlivnit výsledky operací s plovoucí desetinnou čárkou, oproti původní kód nový kód, i když se používá stejný příznaky kompilátoru. Například kód generovaný sady Visual Studio 2010 při [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) (výchozí) nebo `/fp:strict` byl zadán nemusí rozšíření hodnoty zprostředkující not-a-number (NaN) prostřednictvím výrazy správně. Díky tomu se některé výrazy, které přiřadil číselného výsledku v starší kompilátory mohou nyní správně NaN nakonec jako výsledek vznikl. Rozdíly může také zobrazit, protože povolené optimalizace kódu pro `/fp:fast` využívat další funkce procesoru. Tyto optimalizace můžete použít méně pokyny, ale může mít vliv generované výsledky, protože byly odstraněny některé dříve vidět zprostředkující operace.

## <a name="how-to-get-identical-results"></a>Jak získat shodné výsledky

Ve většině případů s plovoucí desetinnou čárkou změny v nejnovější kompilátory a knihovny mít za následek rychlejší a více správné chování, nebo obojí. Lepší výkon procesoru power můžete dokonce vidět, kdy SSE2 pokyny nahradit x87 pokyny. Nicméně pokud máte kód, který se musí přesně možná replikace plovoucí bodu chování staršího kompilátoru, zvažte použití funkcí pro nativní cílení na více platforem sady Visual Studio a sestavte projekt ovlivněné starší sady nástrojů. Další informace najdete v tématu [pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů](use-native-multi-targeting.md).

## <a name="see-also"></a>Viz také:

[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)