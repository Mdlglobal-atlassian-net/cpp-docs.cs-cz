---
title: 'Rychlý start: Analýza kódu pro C/C++'
description: Spusťte statickou analýzu C++ kódu v aplikaci Visual Studio a zjistěte běžné problémy s kódováním a vady.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.openlocfilehash: 5ee8f702ddf489732f664ae73eed75b18dc46e86
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418779"
---
# <a name="quickstart-code-analysis-for-cc"></a>Rychlý start: Analýza kódu pro C/C++

Kvalitu aplikace můžete zlepšit spuštěním analýzy kódu pravidelně na jazyku C nebo C++ kódu. To vám může pomáhat najít běžné problémy, porušení dobrého programovacího postupu nebo vady, které se obtížně zjišťují prostřednictvím testování. Upozornění analýzy kódu se liší od kompilátoru chyby a upozornění, protože analýza kódu hledá vzory v konkrétním kódu, které jsou platné, ale přesto vytvořit problémy pro vy nebo ostatní uživatelé, kteří používají váš kód.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurace sad pravidel pro projekt

1. V **Průzkumník řešení**otevřete místní nabídku pro název projektu a pak zvolte možnost **vlastnosti**.

1. Volitelně můžete v seznamech **Konfigurace** a **platforma** zvolit konfigurace sestavení a cílovou platformu.

1. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, zaškrtněte políčko **Povolit analýzu kódu při sestavení** . Můžete také spustit analýzu kódu ručně otevřením nabídky **analyzovat** a následným výběrem možnosti **Spustit analýzu kódu v** *ProjectName* nebo **Spustit analýzu kódu v souboru**.

1. Vyberte [sadu pravidel](using-rule-sets-to-specify-the-cpp-rules-to-run.md) , kterou chcete použít, nebo vytvořte [vlastní sadu pravidel](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor). Pokud používáte LLVM/Clang-CL, přečtěte si téma [použití Clang-uklizený v aplikaci Visual Studio](../code-quality/clang-tidy.md) ke konfiguraci možností analýzy Clang-uklizený.

### <a name="standard-cc-rule-sets"></a>Standardní sady CC++ /pravidla

Sada Visual Studio obsahuje dvě standardní sady pravidel pro nativní kód:

|Sada pravidel|Popis|
|--------------|-----------------|
|Nativní minimální doporučená pravidla společnosti Microsoft|Tato sada pravidel se zaměřuje na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a chyb aplikací. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše nativní projekty.|
|Nativní doporučená pravidla společnosti Microsoft|Tato sada pravidel se zabývá širokou škálou problémů. Obsahuje všechna pravidla pro nativní minimální doporučená pravidla společnosti Microsoft.|

## <a name="run-code-analysis"></a>Spustit analýzu kódu

Na stránce Analýza kódu stránky vlastností projektu lze konfigurovat analýzu kódu pro spuštění při každém sestavení projektu. Můžete také spustit analýzu kódu ručně.

Spuštění analýzy kódu v řešení:

- V nabídce **sestavení** vyberte možnost **Spustit analýzu kódu v řešení**.

Spuštění analýzy kódu v projektu:

1. V Průzkumník řešení vyberte název projektu.

1. V nabídce **sestavení** vyberte možnost **Spustit analýzu kódu pro** *název projektu*.

Spuštění analýzy kódu v souboru:

1. V Průzkumník řešení vyberte název souboru.

1. V nabídce **sestavení** zvolte možnost **Spustit analýzu kódu v souboru** nebo stiskněte **kombinaci kláves CTRL + SHIFT + ALT + F7**.

   Projekt nebo řešení jsou kompilovány a je spuštěna analýza kódu. Výsledky se zobrazí v Seznam chyb.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analyzovat a vyřešit upozornění analýzy kódu

Chcete-li analyzovat konkrétní upozornění, vyberte název upozornění v Seznam chyb. Upozornění se rozbalí, aby se zobrazily další informace o problému. Pokud je to možné, analýza kódu zobrazuje čísla řádků a logiku analýzy, která vedla k upozornění. Chcete-li získat podrobné informace o upozornění, včetně možných řešení problému, vyberte ID upozornění, abyste zobrazili příslušné téma online nápovědy.

Když vyberete upozornění, zvýrazní se řádek kódu, který způsobil upozornění, v editoru kódu sady Visual Studio.

Po zjištění problému ho mohli vyřešit ve vašem kódu. Pak znovu spusťte analýzu kódu, abyste se ujistili, že se už nezobrazuje v Seznam chyb a že vaše oprava nevyvolala žádná nová upozornění.

## <a name="suppress-code-analysis-warnings"></a>Potlačit upozornění analýzy kódu

Existují situace, kdy byste se mohli rozhodnot Neopravovat upozornění analýzy kódu. Můžete se rozhodnout, že řešení upozornění vyžaduje příliš mnoho nahrávání ve vztahu k pravděpodobnost, že problém vzniknou v žádné Skutečná implementace kódu. Nebo může domnívat, že je nevhodná pro konkrétní kontext, který se používá v tomto upozornění analýzy. Jednotlivá upozornění můžete potlačit, aby se už nezobrazovala v Seznam chyb.

### <a name="to-suppress-a-warning"></a>Potlačení upozornění

1. Pokud se nezobrazují podrobné informace, vyberte název upozornění a rozbalte ho.

1. V dolní části upozornění klikněte na odkaz **Akce** .

1. Zvolte možnost **potlačit zprávu** a pak zvolte možnost **zdroj**.

   Potlačení vkládání zprávy `#pragma warning (disable:[warning ID])`, které potlačí upozornění na řádek kódu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Vytváření pracovních položek pro upozornění analýzy kódu

Funkci sledování pracovní položky můžete použít k protokolování chyb z aplikace Visual Studio. Chcete-li použít tuto funkci, je nutné se připojit k instanci Team Foundation Server.

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Vytvoření pracovní položky pro jedno nebo více upozornění C/C++ kódu

1. V Seznam chyb rozbalte a vyberte upozornění.

1. V místní nabídce pro upozornění zvolte **vytvořit pracovní položku**a pak zvolte typ pracovní položky.

1. Visual Studio vytvoří jednu pracovní položku pro vybraná upozornění a zobrazí pracovní položku v okně dokumentu integrovaného vývojového prostředí (IDE).

1. Přidejte další informace a pak zvolte **Uložit pracovní položku**.

## <a name="search-and-filter-code-analysis-results"></a>Hledání a filtrování výsledků analýzy kódu

Můžete hledat dlouhé seznamy varovné zprávy a upozornění v řešení vícenásobného projektu můžete filtrovat.

- **Filtrování upozornění podle názvu nebo ID upozornění**: zadejte klíčové slovo do vyhledávacího pole.

- **Filtrování upozornění podle závažnosti**: ve výchozím nastavení se zprávám analýzy kódu přiřadí závažnost **Upozornění**. Závažnost jedné nebo více zpráv můžete přiřadit jako **chybu** v sadě vlastních pravidel. Ve sloupci **závažnost** **Seznam chyb**klikněte na šipku rozevíracího seznamu a pak na ikonu filtru. Chcete-li zobrazit pouze zprávy, které jsou přiřazeny příslušné závažnosti, vyberte možnost **Upozornění** nebo **Chyba** . Zvolte **možnost Vybrat vše** , chcete-li zobrazit všechny zprávy.

## <a name="see-also"></a>Viz také

- [Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
