---
title: 'Rychlý start: Analýza kódu pro C/C++'
description: Spusťte statickou analýzu kódu Jazyka C++ v sadě Visual Studio, abyste zjistili běžné problémy s kódováním a vady.
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370576"
---
# <a name="quickstart-code-analysis-for-cc"></a>Rychlý start: Analýza kódu pro C/C++

Můžete zlepšit kvalitu aplikace spuštěním analýzy kódu pravidelně na kód C nebo C++. Analýza kódu vám může pomoci najít běžné problémy a porušení správné programovací praxe. A zjistí vady, které je obtížné objevit prostřednictvím testování. Jeho upozornění se liší od chyb kompilátoru a upozornění: Hledá konkrétní vzory kódu, které jsou známy způsobit problémy. To znamená, že kód, který je platný, ale stále může způsobit problémy, a to buď pro vás, nebo pro ostatní lidi, kteří používají váš kód.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurace sad pravidel pro projekt

1. V **Průzkumníku řešení**otevřete místní nabídku názvu projektu a pak zvolte **Vlastnosti**.

1. Volitelně v seznamech **Konfigurace** a **platforma** zvolte konfiguraci sestavení a cílovou platformu.

1. Chcete-li spustit analýzu kódu při každém sestavení projektu pomocí vybrané konfigurace, zaškrtněte políčko **Povolit analýzu kódu při sestavení.** Analýzu kódu můžete spustit také ručně otevřením nabídky **Analyzovat** a potom zvolit **spustit analýzu kódu na** projektu *Název* nebo **Spustit analýzu kódu v souboru**.

1. Zvolte [sadu pravidel,](using-rule-sets-to-specify-the-cpp-rules-to-run.md) kterou chcete použít, nebo vytvořte [vlastní sadu pravidel](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Pokud používáte LLVM/clang-cl, přečtěte si informace o konfiguraci možností analýzy Clang-Tidy [v tématu Clang-Tidy v sadě Visual Studio.](../code-quality/clang-tidy.md)

### <a name="standard-cc-rule-sets"></a>Standardní sady pravidel C/C++

Visual Studio obsahuje tyto standardní sady pravidel pro nativní kód:

| Sada pravidel | Popis |
|--|--|
| **C++ Základní kontrola aritmetické pravidla** | Tato pravidla vynucují kontroly související [s aritmetické operace z C++ základní pokyny](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **Pravidla základních kontrolních hranic jazyka C++** | Tato pravidla [vynucují profil Hranice základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile). |
| **Pravidla třídy základní kontroly jazyka C++** | Tato pravidla vynucují kontroly související s [třídami z základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies). |
| **Pravidla souběžnosti základní kontroly jazyka C++** | Tato pravidla vynucují kontroly související s [souběžnou s pravidly z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency). |
| **Pravidla kontroly jádra jazyka C++** | Tato pravidla vynucují [kontroly související s konstací z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability). |
| **Pravidla deklarace základní kontroly jazyka C++** | Tato pravidla vynucují kontroly související s [deklaracemi z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces). |
| **Pravidla výčtu základní kontroly jazyka C++** | Tato pravidla vynucují [kontroly související s výčty z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum). |
| **C++ Core Check experimentální pravidla** | Tato pravidla shromažďují některé experimentální kontroly. Nakonec očekáváme, že tyto kontroly budou přesunuty do jiných pravidel nebo zcela odebrány. |
| **Pravidla základní kontrolní funkce jazyka C++** | Tato pravidla vynucují kontroly související s [funkcemi z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions). |
| **Pravidla GSL kontroly jádra jazyka C++** | Tato pravidla vynucují kontroly související s [knihovnou podpory pokynů z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl). |
| **Pravidla životnosti základní kontroly jazyka C++** | Tato pravidla vynucují [profil životnosti základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile). |
| **Pravidla ukazatele vlastníka základní kontroly jádra jazyka C++** | Tato pravidla vynucují kontroly správy prostředků související s [vlastníkem&lt;T&gt; z základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Pravidla nezpracovaných ukazatelů kontroly jádra jazyka C++** | Tato pravidla vynucují kontroly správy prostředků související s [nezpracovanými ukazateli z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Pravidla kontroly jádra jazyka C++** | Tato pravidla vynucují podmnožinu kontrol z [základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines). Tato sada pravidel slouží k zahrnutí všech pravidel kontroly jádra jazyka C++ s výjimkou pravidel Výčtu a Experimentální. |
| **Pravidla sdíleného ukazatele pro kontrolu jádra jazyka C++** | Tato pravidla vynucují kontroly správy prostředků související [s typy s sémantikou sdíleného ukazatele z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Pravidla STL core check jazyka C++** | Tato pravidla vynucují kontroly související s [knihovnou standardních šablon jazyka C++ (STL) z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib). |
| **Pravidla stylu základní kontroly jazyka C++** | Tato pravidla vynucují kontroly související s používáním [výrazů a příkazů z základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **Pravidla základního typu kontroly jazyka C++** | Tato pravidla vynucují [typ ový profil základních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile). |
| **C++ Core Check Jedinečná pravidla ukazatele** | Tato pravidla vynucují kontroly správy prostředků související s typy s [jedinečnou sémantikou ukazatele z hlavních pokynů jazyka C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **Pravidla kontroly souběžnosti** | Tato pravidla vynucují sadu kontrol vzoru souběžnosti Win32 v jazyce C++. |
| **Pravidla souběžnosti** | Přidá pravidla souběžnosti z c++ základní pokyny pravidla **souběžnosti pravidla kontroly**. |
| **Nativní minimální pravidla společnosti Microsoft** | Tato pravidla se zaměřují na nejkritičtější problémy v nativním kódu, včetně potenciálních bezpečnostních děr a selhání aplikací. Doporučujeme zahrnout tuto sadu pravidel do libovolné vlastní sady pravidel, kterou vytvoříte pro nativní projekty. |
| **Nativní doporučená pravidla společnosti Microsoft** | Tato pravidla se zaměřují na nejkritičtější a nejčastější problémy v nativním kódu. Tyto problémy zahrnují potenciální bezpečnostní díry a selhání aplikace. Doporučujeme zahrnout tuto sadu pravidel do libovolné vlastní sady pravidel, kterou vytvoříte pro nativní projekty. Tato sada pravidel je určena pro práci s visual studio professional edice a vyšší. Obsahuje všechna pravidla v **nativních minimálních pravidlech společnosti Microsoft**. |

Visual Studio obsahuje tyto standardní sady pravidel pro spravovaný kód:

| Sada pravidel | Popis |
|--|--|
| **Pravidla správné hospo-** | Tato pravidla se zaměřují na logické chyby a běžné chyby při používání rozhraní API rozhraní FRAMEWORK. Zahrnout tuto sadu pravidel rozbalit v seznamu upozornění hlášeny minimální doporučená pravidla. |
| **Základní pravidla obecných zásad návrhu společnosti Microsoft** | Tato pravidla se zaměřují na vynucení osvědčených postupů, aby byl váš kód snadno srozumitelný a použitelný. Tuto sadu pravidel zahrňte, pokud projekt obsahuje kód knihovny nebo pokud chcete vynutit osvědčené postupy pro snadno udržovatelný kód. |
| **Pravidla rozšířené správnosti společnosti Microsoft** | Tato pravidla rozšiřují základní pravidla správnosti maximalizovat hlášené chyby logiky a využití rozhraní. Zvláštní důraz je kladen na konkrétní scénáře, jako je například interop COM a mobilní aplikace. Zvažte zahrnutí této sady pravidel, pokud se jeden z těchto scénářů vztahuje na váš projekt nebo najít další problémy v projektu. |
| **Pravidla rozšířených pokynů pro návrh společnosti Microsoft** | Tato pravidla rozšiřují základní pravidla pokynů pro návrh, aby maximalizovala ohlášené problémy s použitelností a udržovatelností. Zvláštní důraz je kladen na pokyny pro pojmenování. Zvažte zahrnutí této sady pravidel, pokud váš projekt obsahuje kód knihovny nebo pokud chcete vynutit nejvyšší standardy pro psaní udržovatelného kódu. |
| **Pravidla globalizace společnosti Microsoft** | Tato pravidla se zaměřují na problémy, které brání správně zobrazovat data v aplikaci při použití v různých jazycích, národních prostředích a jazykových verzích. Tuto sadu pravidel zahrňte, pokud je vaše aplikace lokalizována nebo globalizována. |
| **Spravovaná minimální pravidla společnosti Microsoft** | Tato pravidla se zaměřují na nejkritičtější problémy v kódu, pro které je analýza kódu nejpřesnější.  Tato pravidla jsou malý počet a jsou určeny pouze ke spuštění v omezených edicích sady Visual Studio.  Použijte minimumRecommendedRules.ruleset s jinými edicemi sady Visual Studio. |
| **Doporučená pravidla spravovaná společností Microsoft** | Tato pravidla se zaměřují na nejkritičtější problémy v kódu. Mezi tyto problémy patří potenciální bezpečnostní díry, selhání aplikace a další důležité chyby logiky a návrhu. Doporučujeme zahrnout tuto sadu pravidel do libovolné vlastní sady pravidel, kterou vytvoříte pro své projekty. |
| **Minimální pravidla pro smíšené (C++ /CLR)** | Tato pravidla se zaměřují na nejkritičtější problémy v projektech jazyka C++, které podporují běžný jazyk runtime. Mezi tyto problémy patří potenciální bezpečnostní díry, selhání aplikace a další důležité chyby logiky a návrhu. Doporučujeme zahrnout tuto sadu pravidel do libovolné vlastní sady pravidel, kterou vytvoříte pro projekty jazyka C++, které podporují běžný jazyk ový čas. |
| **Doporučená pravidla pro smíšené položky společnosti Microsoft (C++ /CLR)** | Tato pravidla se zaměřují na nejběžnější a kritické problémy v projektech jazyka C++, které podporují běžný jazyk runtime. Mezi tyto problémy patří potenciální bezpečnostní díry, selhání aplikace a další důležité chyby logiky a návrhu. Tato sada pravidel je určena pro použití v edici Visual Studio Professional a vyšší. |
| **Pravidla zabezpečení společnosti Microsoft** | Tato sada pravidel obsahuje všechna pravidla zabezpečení společnosti Microsoft. Zahrnout tuto sadu pravidel maximalizovat počet potenciálních problémů se zabezpečením, které jsou hlášeny. |

Chcete-li zahrnout všechna pravidla:

| Sada pravidel | Popis |
|--|--|
| **Všechna pravidla společnosti Microsoft** | Tato sada pravidel obsahuje všechna pravidla. Spuštění této sady pravidel může mít za následek velký počet upozornění jsou hlášeny. Pomocí této sady pravidel získáte ucelený přehled o všech problémech v kódu. Může vám pomoci rozhodnout, které z více zaměřených sad pravidel jsou nejvhodnější ke spuštění pro vaše projekty. |

## <a name="run-code-analysis"></a>Spustit analýzu kódu

Na stránce **Analýza kódu** v dialogovém okně Vlastnosti projektu můžete nakonfigurovat analýzu kódu tak, aby se spouštěla při každém sestavení projektu. Analýzu kódu můžete spustit také ručně.

Spuštění analýzy kódu v řešení:

- V nabídce **Sestavení** zvolte **Spustit analýzu kódu v řešení**.

Spuštění analýzy kódu v projektu:

1. V Průzkumníku řešení vyberte název projektu.

1. V nabídce **Sestavení** zvolte **Spustit analýzu kódu v názvu** *projektu*.

Spuštění analýzy kódu v souboru:

1. V Průzkumníku řešení vyberte název souboru.

1. V nabídce **Sestavení** zvolte **Spustit analýzu kódu v souboru** nebo stiskněte **Ctrl+Shift+Alt+F7**.

   Projekt nebo řešení je zkompilován a spustí analýzu kódu. Výsledky se zobrazí v okně Seznam chyb.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analýza a řešení upozornění na analýzu kódu

V okně Seznam chyb jsou uvedena nalezená upozornění analýzy kódu. Výsledky jsou zobrazeny v tabulce. Pokud je k dispozici další informace o konkrétní upozornění, první sloupec obsahuje ovládací prvek rozšíření. Zvolte ji, chcete-li rozbalit zobrazení pro další informace o problému. Pokud je to možné, analýza kódu zobrazí čísla řádků a logiku analýzy, která vedla k upozornění.

Podrobné informace o upozornění, včetně možných řešení problému, zvolte ID upozornění ve sloupci Kód pro zobrazení odpovídajícího článku nápovědy online.

Poklepáním na upozornění přesuňte kurzor na řádek kódu, který způsobil upozornění v editoru kódu sady Visual Studio. Nebo stiskněte klávesu Enter na vybrané upozornění.

Po pochopení problému, můžete jej vyřešit v kódu. Potom znovu spusťte analýzu kódu a ujistěte se, že upozornění již nezobrazí v seznamu chyb.

## <a name="create-work-items-for-code-analysis-warnings"></a>Vytvořit pracovní položky pro upozornění analýzy kódu

Funkci sledování pracovních položek můžete použít k protokolování chyb z visual studia. Chcete-li použít tuto funkci, musíte se připojit k instanci Serveru Azure DevOps (dříve Team Foundation Server).

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Vytvoření pracovní položky pro jedno nebo více upozornění kódu jazyka C/C++

1. V seznamu chyb rozbalte a vyberte upozornění

1. V místní nabídce upozornění zvolte **Vytvořit pracovní položku**a pak zvolte typ pracovní položky.

1. Visual Studio vytvoří jednu pracovní položku pro vybraná upozornění a zobrazí pracovní položku v okně dokumentu ide.

1. Přidejte další informace a pak zvolte **Uložit pracovní položku**.

## <a name="search-and-filter-code-analysis-results"></a>Výsledky analýzy vyhledávání a filtrování kódu

Můžete vyhledávat dlouhé seznamy varovných zpráv a filtrovat upozornění v řešeních pro více projektů.

- **Filtrování upozornění podle názvu nebo ID upozornění**: Zadejte klíčové slovo do pole Seznam chyb hledání.

- **Filtrování upozornění podle závažnosti**: Ve výchozím nastavení jsou zprávám analýzy kódu přiřazena závažnost **upozornění**. Závažnost jedné nebo více zpráv můžete přiřadit jako **chybu** ve vlastní sadě pravidel. Ve sloupci **Závažnost** **seznamu chyb**zvolte šipku rozevíracího seznamu a pak ikonu filtru. Zvolte **Upozornění** nebo **Chyba,** chcete-li zobrazit pouze zprávy, kterým je přiřazena příslušná závažnost. Chcete-li zobrazit všechny zprávy, zvolte **Vybrat vše.**

## <a name="see-also"></a>Viz také

- [Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
