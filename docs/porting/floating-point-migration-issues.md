---
title: Problémy migrace s plovoucí desetinnou čárkou
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: 0a84b764d395063f38cae299cff75437318b024e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626982"
---
# <a name="floating-point-migration-issues"></a>Problémy migrace s plovoucí desetinnou čárkou

Někdy, když upgradujete projekty na novější verzi sady Visual Studio, můžete zjistit, že se změnily výsledky některých operací s plovoucí desetinnou čárkou. K tomu obvykle dochází z jednoho ze dvou důvodů: změny v generování kódu, které pobírají lepší výhodu dostupného procesoru, a opravy chyb nebo změny algoritmů používaných v matematických funkcích v knihovně CRT (C Runtime Library). Obecně platí, že nové výsledky jsou správné v rámci omezení určených jazykovým standardem. Přečtěte si, abyste zjistili, co se změnilo, a pokud je důležité, jak získat stejné výsledky, jaké vaše funkce získaly.

## <a name="new-math-functions-and-universal-crt-changes"></a>Nové matematické funkce a univerzální změny CRT

Většina matematických funkcí CRT je k dispozici v aplikaci Visual Studio po dobu let, ale počínaje Visual Studio 2013, jsou zahrnuty všechny funkce vyžadované normou ISO C99. Tyto funkce jsou implementovány pro rovnováhu výkonu se správností. Vzhledem k tomu, že výsledkem správného zaokrouhlení výsledku je, že každý případ může být zakazující nákladný, jsou tyto funkce navržené tak, aby se pro správný zaoblený výsledek vytvořila Přibližná aproximace. Ve většině případů se výsledek vygeneroval do +/-1 jednotky s minimální přesností nebo *ULP*se správným zaobleným výsledkem, i když existují případy s větší přesností. Pokud jste k získání těchto funkcí používali jinou knihovnu pro matematiku, mohou být za změnu ve výsledcích implementace rozdíly v implementaci.

V případě, že se matematické funkce přesunuly do univerzálního CRT v aplikaci Visual Studio 2015, byly použity některé nové algoritmy a několik chyb v implementaci funkcí, které byly nové v Visual Studio 2013 byly opraveny. Tyto změny mohou vést ke zjistitelným rozdílům ve výsledcích výpočtů s plovoucí desetinnou čárkou, které tyto funkce používají. Funkce, které byly problémy s chybou, byly ERF, exp2 –, zbytek, remquo –, scalbln a scalbn – a jejich plovoucí a dlouhé dvojité varianty.  Další změny v aplikaci Visual Studio 2015 opravily problémy při zachování stavového slova plovoucí desetinné čárky a informací o stavu výjimky v _clear87, _clearfp, fegetenv, fesetenv a feholdexcept Functions.

## <a name="processor-differences-and-compiler-flags"></a>Rozdíly v procesorech a příznaky kompilátoru

Mnoho funkcí matematické knihovny s plovoucí desetinnou čárkou má různé implementace pro různé architektury PROCESORů. Například 32 x86 CRT může mít jinou implementaci než 64 CRT. Kromě toho mohou mít některé funkce pro danou architekturu procesoru více implementací. Nejúčinnější implementace je vybrána dynamicky za běhu v závislosti na sadách instrukcí, které CPU podporuje. Například v 32 x86 CRT některé funkce mají implementaci x87 i implementaci SSE2. Při spuštění na procesoru, který podporuje SSE2, se použije rychlejší implementace SSE2. Při spuštění na procesoru, který nepodporuje SSE2, se použije pomalejší implementace x87. Může se zobrazit při migraci starého kódu, protože výchozí možnost architektury kompilátoru x86 se změnila na [/arch: SSE2](../build/reference/arch-x86.md) v aplikaci Visual Studio 2012. Vzhledem k tomu, že různé implementace funkcí v rámci matematické knihovny můžou k vytváření výsledků používat jiné instrukce procesoru a různé algoritmy, můžou funkce na různých platformách vydávat různé výsledky. Ve většině případů jsou výsledky v rámci většího zaokrouhleného výsledku mezi +/-1 ULP, ale skutečné výsledky se můžou v různých procesorech lišit.

Vylepšení správnosti generování kódu v různých režimech plovoucí desetinné čárky v aplikaci Visual Studio může také ovlivnit výsledky operací s plovoucí desetinnou čárkou, pokud je starý kód porovnán s novým kódem, a to i při použití stejných příznaků kompilátoru. Například kód vygenerovaný v rámci sady Visual Studio 2010, pokud je [/FP: přesný](../build/reference/fp-specify-floating-point-behavior.md) (výchozí) nebo `/fp:strict`, nesmí mít správně šířené mezilehlé hodnoty not-a-Number (NaN) prostřednictvím výrazů. Proto některé výrazy, které mají číselný výsledek ve starších kompilátorech, teď můžou správně vytvořit NaN výsledek. Můžete také zobrazit rozdíly, protože optimalizace kódu povolené pro `/fp:fast` nyní využívají více funkcí procesoru. Tyto optimalizace můžou používat méně instrukcí, ale mohou mít vliv na vygenerované výsledky, protože byly odebrány některé dříve viditelné mezilehlé operace.

## <a name="how-to-get-identical-results"></a>Jak získat identické výsledky

Ve většině případů se změny plovoucí desetinné čárky v nejnovějších kompilátorech a knihovnách vyplývají z důvodu rychlejšího nebo více správných chování nebo obojího. V případě, že SSE2 pokyny nahrazují pokyny x87, můžete dokonce sledovat výkon procesoru s vyšším výkonem. Nicméně pokud máte kód, který musí přesně replikovat chování s plovoucí desetinnou čárkou staršího kompilátoru, zvažte použití nativních funkcí cílení na více platforem sady Visual Studio a sestavení ovlivněného projektu pomocí starší sady nástrojů. Další informace naleznete v tématu [použití nativního cílení na více platforem v aplikaci Visual Studio k sestavení starých projektů](use-native-multi-targeting.md).

## <a name="see-also"></a>Viz také:

[Upgrade projektů z dřívějších verzí sady VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)