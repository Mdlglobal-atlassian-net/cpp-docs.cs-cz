---
title: Průvodce C++ přenosem a upgradem Microsoftu
description: Upgradujte C++ kód Microsoft na nejnovější verzi sady Visual Studio.
ms.date: 11/18/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: 723879ad03b9b66c7490804e890f07d6d55e9dae
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303344"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Průvodce C++ přenosem a upgradem Microsoftu

Tento článek poskytuje návod pro upgrade kódu Microsoft C++ na nejnovější verzi sady Visual Studio. Pro projekty vytvořené v aplikaci Visual Studio 2010 až 2015 stačí otevřít projekt v aplikaci Visual Studio 2019. Můžete upgradovat projekt sady Visual Studio 2008 nebo starší ve dvou krocích. Pomocí sady Visual Studio 2010 nejdříve převeďte projekt na formát MSBuild. Pak otevřete projekt v aplikaci Visual Studio 2019. Úplné pokyny najdete v tématu [upgrade C++ projektů z dřívějších verzí sady Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

Sady nástrojů v sadě Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 jsou binární kompatibilní. Nyní můžete upgradovat na novější verzi kompilátoru, aniž by bylo nutné upgradovat závislosti knihoven. Další informace najdete v tématu [ C++ binární kompatibilita 2015-2019](binary-compat-2015-2017.md).

Při upgradu projektů, které používají open source knihovny nebo které mají být spouštěny na různých platformách, doporučujeme migrovat na projekt založený na CMaki. Další informace najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md) .

## <a name="reasons-to-upgrade-c-code"></a>Důvody pro upgrade C++ kódu

Pokud starší verze aplikace běží uspokojivě, v zabezpečeném prostředí a není v aktivním vývoji, nemusí být pro upgrade k dispozici žádná motivace. Zvažte však upgrade v těchto případech: vaše aplikace vyžaduje průběžnou údržbu. Nebo, provádíte nový vývoj funkcí nebo vylepšení výkonu nebo zabezpečení. Upgrade přináší tyto výhody:

- Stejný kód může běžet rychleji, protože jsme vylepšili optimalizace kompilátoru.

- Moderní C++ funkce a postupy programování odstraňují mnoho běžných příčin chyb a vytváří kód, který je mnohem snazší udržovat než starší idiomy ve stylu jazyka C.

- Doba sestavování je rychlejší, protože zlepšení výkonu v kompilátoru a linkeru.

- Lepší soulad s normami. Možnost kompilátoru [/Permissive-](../build/reference/permissive-standards-conformance.md) vám pomůže identifikovat kód, který neodpovídá aktuálnímu C++ standardu.

- Lepší zabezpečení za běhu, včetně bezpečnějších funkcí [knihovny prostředí runtime jazyka C](../c-runtime-library/security-features-in-the-crt.md) . A, funkce kompilátoru, jako je například [Kontrola ochrany](../build/reference/guard-enable-guard-checks.md) a adresování (novinka v aplikaci Visual Studio 2019 verze 16,4).

## <a name="multitargeting-vs-upgrading"></a>Cílení na více verzí vs. upgrade

Možná upgrade základu kódu na novou sadu nástrojů není pro vás možnost. Nejnovější sadu Visual Studio můžete stále používat k vytváření a úpravám projektů, které používají starší sady nástrojů a knihovny. V aplikaci Visual Studio 2019 můžete využívat funkce, jako například:

- Moderní nástroje pro statickou analýzu, včetně C++ základních pokynů pro kontrolu a Clang-uklizený, vám pomůžou identifikovat potenciální problémy ve zdrojovém kódu.

- Automatické formátování podle vašeho výběru moderních stylů může pomáhat s tím, že starší verze kódu budou mnohem čitelnější.

Další informace naleznete v tématu [použití nativního cílení na více platforem v aplikaci Visual Studio k sestavení starých projektů](use-native-multi-targeting.md).

## <a name="in-this-section"></a>V tomto oddílu

|Název|Popis|
|-----------|-----------------|
|[Upgrade C++ projektů z dřívějších verzí sady Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Postup upgradu základní znakové sady na Visual Studio 2019 a V142 kompilátoru.|
|[Nástroje IDE pro upgrade C++ kódu](ide-tools-for-upgrading-code.md)|Užitečné funkce IDE, které vám pomůžou v procesu upgradu.|
|[C++binární kompatibilita 2015-2019](binary-compat-2015-2017.md)|Využití knihoven v140 a v141, jak je z projektů V142.|
|[Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí](use-native-multi-targeting.md)|Použijte Visual Studio 2019 se staršími kompilátory a knihovnami.|
|[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)|Seznam všech změn v nástrojích knihovny a sestavení C++ společnosti Microsoft ze sady Visual Studio 2003 až 2015, které mohou vyžadovat změny v kódu.|
|[Novinky Visual C++ 2003–2015](visual-cpp-what-s-new-2003-through-2015.md)|Všechny informace "Co je nového" pro společnost Microsoft C++ ze sady visual Studio 2003 prostřednictvím sady visual Studio 2015.|
|[Přenos a upgrade: Příklady a případové studie](porting-and-upgrading-examples-and-case-studies.md)|V této části jsme převedli a upgradují několik ukázek a aplikací a probrali zkušenosti a výsledky. Tyto články vám poskytnou představu o tom, co je součástí procesu přenosu a upgradu. V celém procesu probereme tipy a triky pro upgrade a ukážeme, jak byly vyřešeny konkrétní chyby.|
|[Portování do Univerzální platforma Windows](porting-to-the-universal-windows-platform-cpp.md)|Obsahuje informace o přenosech kódu do Windows 10.|
|[Úvod do prostředí Visual C++ pro uživatele systému UNIX](introduction-to-visual-cpp-for-unix-users.md)|Poskytuje informace pro uživatele systému UNIX, kteří jsou novinkou v jazyce Visual C++ a chtějí s ním být produktivní.|
|[Spouštění programů Linux ve Windows](porting-from-unix-to-win32.md)|Popisuje možnosti migrace aplikací pro systém UNIX do systému Windows.|

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Co je nového pro C++ kompilátor v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
