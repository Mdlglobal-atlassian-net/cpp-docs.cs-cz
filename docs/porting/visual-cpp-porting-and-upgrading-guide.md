---
title: Průvodce C++ přenosem a upgradem Microsoftu
description: Upgradujte C++ kód Microsoft na nejnovější verzi sady Visual Studio.
ms.date: 11/05/2019
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: 04c3950d637c01031e78d0d95e13232143ceb232
ms.sourcegitcommit: 4dde7914608508e47c21cae03ac58fe953a0c29b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119486"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Průvodce C++ přenosem a upgradem Microsoftu

Toto téma poskytuje průvodce pro upgrade kódu Microsoft C++ na nejnovější verzi sady Visual Studio. Pokud provádíte upgrade z projektu vytvořeného v aplikaci Visual Studio 2008 nebo starší, musíte nejprve použít Visual Studio 2010 k převedení projektu na formát MSBuild a pak otevřít projekt v aplikaci Visual Studio 2019. Pro projekty vytvořené v aplikaci Visual Studio 2010 až 2015 stačí otevřít projekt v aplikaci Visual Studio 2019. Úplné pokyny najdete v tématu [upgrade C++ projektů z dřívějších verzí sady Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

Sady nástrojů v sadě Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 jsou binární kompatibilní, což umožňuje upgradovat na novější verzi kompilátoru, aniž by bylo nutné upgradovat závislosti knihoven. Další informace najdete v tématu [ C++ binární kompatibilita mezi 2015 a 2019](binary-compat-2015-2017.md).

Při upgradu projektů, které používají open source knihovny nebo které mají být spouštěny na různých platformách, doporučujeme migrovat na projekt založený na CMaki. Další informace najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md) .

## <a name="reasons-to-upgrade-c-code"></a>Důvody pro upgrade C++ kódu

Pokud starší verze aplikace běží uspokojivě, v zabezpečeném prostředí a není v aktivním vývoji, nemusí být pro upgrade k dispozici mnohem motivace. Nicméně pokud aplikace vyžaduje průběžnou údržbu nebo pokud nový vývoj funkcí zahrnuje vylepšení výkonu nebo zabezpečení, můžete zvážit upgrade kódu z některého z následujících důvodů:

- Stejný kód může běžet rychleji kvůli vylepšeným optimalizacím kompilátoru.

- Moderní C++ funkce a postupy programování eliminují mnoho běžných příčin chyb a vytváří kód, který je mnohem snazší udržovat než starší idiomy ve stylu jazyka C.

- Doba sestavování je výrazně rychlejší, kvůli vylepšením výkonu v kompilátoru a linkeru.

- Lepší soulad s normami. Možnost kompilátoru [/Permissive-](../build/reference/permissive-standards-conformance.md) umožňuje identifikovat kód, který byl dříve povolen kompilátorem společnosti Microsoft C++ , ale nedodržuje aktuální C++ Standard.

- Lepší zabezpečení za běhu, včetně bezpečnějších funkcí [knihovny běhového prostředí jazyka C]() a funkcí kompilátoru, jako je například [Kontrola ochrany](../build/reference/guard-enable-guard-checks.md) a adresování (Visual Studio 2019 verze 16,4).

## <a name="multitargeting-vs-upgrading"></a>Cílení na více verzí vs. upgrade

Pokud upgrade základu kódu na novou sadu nástrojů není možností, můžete stále používat nejnovější verzi sady Visual Studio k vytváření a úpravám projektů, které se kompilují se staršími sadami nástrojů a knihovnami. V aplikaci Visual Studio 2019 můžete využít výhod funkcí, jako například:

- Moderní nástroje pro statickou analýzu, včetně C++ základních pokynů pro kontrolu a Clang-uklizený, vám pomůžou identifikovat potenciální problémy ve zdrojovém kódu.

- Automatické formátování podle vašeho výběru moderních stylů může pomáhat s tím, že starší verze kódu budou mnohem čitelnější.

Další informace naleznete v tématu [použití nativního cílení na více platforem v aplikaci Visual Studio k sestavení starých projektů](use-native-multi-targeting.md).

## <a name="in-this-section"></a>V tomto oddílu

|Název|Popis|
|-----------|-----------------|
|[Upgrade C++ projektů z dřívějších verzí sady Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Postup upgradu základní znakové sady na Visual Studio 2019 a V142 kompilátoru.|
|[Nástroje IDE pro upgrade C++ kódu](ide-tools-for-upgrading-code.md)|Užitečné funkce IDE, které vám pomůžou v procesu upgradu.|
|[C++Binární kompatibilita mezi 2015 a 2019](binary-compat-2015-2017.md)|Využívání knihoven v140 jako z projektů V142.|
|[Sestavení starých projektů v sadě Visual Studio pomocí nativního cílení na více verzí](use-native-multi-targeting.md)|Použijte Visual Studio 2019 se staršími kompilátory a knihovnami.|
|[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)|Seznam všech změn v nástrojích knihovny a sestavení C++ společnosti Microsoft ze sady Visual Studio 2003 až 2015, které mohou vyžadovat změny v kódu.|
|[Novinky Visual C++ 2003–2015](visual-cpp-what-s-new-2003-through-2015.md)|Všechny informace "Co je nového" pro společnost Microsoft C++ ze sady visual Studio 2003 prostřednictvím sady visual Studio 2015.|
|[Přenos a upgrade: Příklady a případové studie](porting-and-upgrading-examples-and-case-studies.md)|V této části jsme převedli a upgradují několik ukázek a aplikací a probrali zkušenosti a výsledky. Můžete se setkat s tím, že vám přečtěte, co je součástí procesu přenosu a upgradu. V celém procesu probereme tipy a triky pro upgrade a ukážeme, jak byly vyřešeny konkrétní chyby.|
|[Portování do Univerzální platforma Windows](porting-to-the-universal-windows-platform-cpp.md)|Obsahuje informace o přenosech kódu do Windows 10.|
|[Úvod do prostředí Visual C++ pro uživatele systému UNIX](introduction-to-visual-cpp-for-unix-users.md)|Poskytuje informace pro uživatele systému UNIX, kteří jsou novinkou v jazyce Visual C++ a chtějí s ním být produktivní.|
|[Spouštění programů Linux ve Windows](porting-from-unix-to-win32.md)|Popisuje možnosti migrace aplikací pro systém UNIX do systému Windows.|

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Co je nového pro C++ kompilátor v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
