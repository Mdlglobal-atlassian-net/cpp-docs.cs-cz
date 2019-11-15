---
title: Visual Studio IDE Tools pro upgrade C++ kódu
description: Editor C++ kódu a nástroje pro analýzu kódu v aplikaci Visual Studio vám pomůžou modernizovat C++ svůj základ kódu.
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: 3f85b955b688489bfc04c4bfc0605201e883e3d4
ms.sourcegitcommit: 4dde7914608508e47c21cae03ac58fe953a0c29b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119531"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>Visual Studio IDE Tools pro upgrade C++ kódu

Visual Studio pomáhá s upgradem C++ starší verze kódu pomocí možností kompilátoru, upozornění analýzy kódu a funkcí editoru, jako jsou rychlé opravy, rychlé informace a vylepšené posuvníky. Termín "starší kód" odkazuje na některou z těchto kategorií:

- Kód, který byl dříve povolen kompilátorem C++ společnosti Microsoft (MSVC), ale nikdy není v C++ souladu se standardem.

   Chcete-li upgradovat starší nevyhovující MSVC kód, zapněte možnost kompilátoru [/Permissive-](../build/reference/permissive-standards-conformance.md) . Všechny instance nevyhovujících použití jsou podtrženy červenou vlnovkou v editoru kódu. Chybové zprávy v okně **Seznam chyb** obsahují doporučení, jak chybu opravit. Kliknutím na kód chyby přejdete na jeho stránku s usnadněním v dokumentaci. Pokud opravíte všechny chyby najednou, můžete upgradovat nevyhovující kód ve fázích tak, že zapnete možnost **povolující** volbu, opravíte některé chyby a znovu vypnete možnost. Kód bude zkompilován s novými vylepšeními a můžete se vrátit a opravit zbývající problémy později. Příklady nevyhovujícího MSVC kódu najdete na stránce [/Permissive-](../build/reference/permissive-standards-conformance.md) .

- Kód, který byl povolen v dřívější verzi C++ Standard, ale je zastaralý nebo odebraný v novější verzi.

   Chcete-li upgradovat na novější jazykovou verzi, nastavte možnost [ C++ standardní jazyk](../build/reference/std-specify-language-standard-version.md) na požadovaný standard a opravte všechny chyby kompilace, které jsou vyvolány. Obecně doporučujeme nastavit jazykovou Standard na [/std: c++ 17](../build/reference/std-specify-language-standard-version.md). Chyby vyvolané při upgradu na novější verzi nejsou v souvislosti s chybami, které jsou vyvolány při použití možnosti **povolující** možnost.

- Kód, který odpovídá všem verzím Standard, ale již není považována za osvědčený postup v moderních C++verzích.

   Pro identifikaci kódu, kde jsou doporučeny změny, spusťte [analýzu kódu](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="open-and-convert-a-legacy-project"></a>Otevření a převod starší verze projektu

Pokud je váš starší projekt založen na starší verzi sady Visual Studio, můžete jej otevřít v aplikaci Visual Studio 2017 nebo Visual Studio 2019. Visual Studio ho automaticky převede na aktuální schéma projektu s podporou pro všechny nejnovější funkce kompilátoru a rozhraní IDE.

![Upgrade projektu](media/upgrade-dialog-v142.png "Upgrade projektu")

Další informace naleznete v tématu [upgrade C++ projektů z dřívějších verzí sady Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

## <a name="search-the-code-base"></a>Hledat v základu kódu

Upgrade základu kódu často zahrnuje prohledávání více souborů. Pokud chcete hledat cokoli v základu kódu, stisknutím **kombinace kláves CTRL + T** Zobrazte pole **Přejít do všech** vyhledávacích polí.

![Přejít na vše](media/go-to-all.png "Přejít na vše")

Chcete-li zúžit rozsah hledání, zadejte jeden z filtrů s jedním písmenem, následovaný mezerou a požadovanou věc.

## <a name="error-list"></a>Seznam chyb

Po nastavení C++ požadovaného jazykového standardu a všech dalších možností kompilátoru ( **vlastnosti** **projektu** >  > **Obecné**) zkompilujte projekt stisknutím **kombinace kláves CTRL + SHIFT + B** . Můžete očekávat, že se zobrazí některé chyby a upozornění ve formě červené vlnovky na různých místech kódu. Chyby se také zobrazí v **Seznam chyb**. Pokud chcete získat další informace o určité chybě, klikněte na kód chyby a přejděte na stránku s nápovědu v dokumentaci. Kódy chyb, které začínají řetězcem "C", jsou chyby kompilátoru. Kódy začínající na "MSB" jsou chyby nástroje MSBuild, které indikují problém s konfigurací projektu.

![Chyby kompilátoru a MSBuild v Seznam chyb](media/compiler-error-list.png "Chyby kompilátoru a MSBuild v Seznam chyb")

## <a name="document-health-indicator"></a>Indikátor stavu dokumentu

Indikátor stavu dokumentu ve spodní části editoru zobrazuje počet chyb a upozornění v aktuálním dokumentu a umožňuje přejít přímo z jednoho upozornění/chyby na další.

![Indikátor stavu dokumentu](media/document-health-indicator.png "Indikátor stavu dokumentu")

V mnoha případech můžete najít další informace o konkrétní chybě v dokumentaci ke zvýšení historie změn v sadě Visual Studio a o dodržování shody.

- [C++vylepšení shody](../overview/cpp-conformance-improvements.md)
- [Historie C++ vizuálních změn 2003 – 2015](visual-cpp-change-history-2003-2015.md)
- [Přehled potenciálních problémů s upgradem](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>Použití analýzy kódu k modernizovatí kódu

Při upgradu doporučujeme spustit v projektu analýzu kódu tak, aby kód splňoval minimálně nativní doporučená pravidla společnosti Microsoft. Tato pravidla jsou kombinací pravidel definovaných společností Microsoft a podmnožinou [ C++ základních pokynů](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines). Díky tomu, že si to vyhovuje, budete značně snižovat nebo eliminovat běžné zdroje chyb a ve stejnou dobu usnadňuje čitelnost kódu a tím i jeho zachování. Analýza kódu s použitím nativních doporučených pravidel společnosti Microsoft je ve výchozím nastavení povolená. Můžete povolit další pravidla v rámci > **vlastností** **projektu** > **analýzy kódu**. Kód, který porušuje jedno z pravidel, je označen jako upozornění a je podtržen zelenou vlnovkou v editoru kódu. Najeďte myší na vlnovku, abyste viděli popis problému, který popisuje **QuickInfo** .

![Popis analýzy kódu](media/code-analysis-tooltip.png "Upozornění analýzy kódu")

Klikněte na ikonu filtru ve sloupci **kód** a vyberte, která upozornění se zobrazí.

![Filtry analýzy kódu v Seznam chyb](media/code-analysis-filter.png "Filtry analýzy kódu v Seznam chyb")

Chyby a upozornění analýzy kódu se zobrazí také v **Seznam chyb** stejně jako chyby kompilátoru.

![Upozornění analýzy kódu v Seznam chyb](media/code-analysis-error-list.png "Upozornění analýzy kódu v Seznam chyb")

Můžete změnit, která pravidla jsou aktivní, a vytvořit vlastní RuleSets. Další informace o použití analýzy kódu naleznete v tématu [Analýza kódu pro C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="use-quick-actions-to-modernize-code"></a>Použití rychlých akcí k modernizovat kódu

Editor kódu poskytuje rychlé akce pro některá běžná doporučení. Po zobrazení ikony žárovky můžete kliknutím na ni Zobrazit dostupné rychlé akce.

### <a name="convert-macros-to-constexpr-functions"></a>Převést makra na funkce constexpr

Následující obrázek znázorňuje použití makra s názvem `AVERAGE`, který má výchozí sémantickou barvu. Obrázek zobrazuje také popis QuickInfo, který se zobrazí, když se ukazatel myši pohybuje na pozadí:

![Rozšíření makra QuickInfo](media/macro-expansion-quick-info.png "Rozšíření makra popisu QuickInfo")

Vzhledem k tomu, že použití maker se v moderních C++případech nedoporučuje, Visual Studio usnadňuje převod maker na funkce **constexpr** :

1. Klikněte pravým tlačítkem na `AVERAGE` a vyberte **Přejít k definici**.
2. Klikněte na ikonu Screwdriver a vyberte **převést makro na constexpr** .

   ![Rychlé makro Action na constexpr](media/quick-action-macro-to-constexpr.png "Rychlé makro Action na constexpr")

Makro je převedeno, jak je znázorněno níže:

![constexpr – funkce](media/constexpr-function.png "constexpr – funkce")

A volání `AVERAGE` je nyní barevně zabarvené jako volání funkce a Rychlé informace ukazuje odvozený typ funkce:

![volání funkce constexpr](media/constexpr-function-call.png "volání funkce constexpr")

### <a name="initialize-variables"></a>Inicializovat proměnné

Neinicializované proměnné mohou uchovávat náhodné hodnoty, které vedou k závažným chybám. Analýza kódu tyto instance označí a editor nabízí rychlou akci:

![Inicializovat proměnnou](media/init-variable.png "Rychlá akce inicializace proměnné")

### <a name="convert-to-raw-string-literal"></a>Převod na nezpracovaný řetězcový literál

Nezpracované řetězcové literály jsou méně náchylné k chybám a jsou pohodlnější pro typ než řetězce s vloženými řídicími znaky. Klikněte pravým tlačítkem na řetězec a vyberte **rychlé akce** , které chcete převést na nezpracovaný řetězcový literál.

![Nezpracovaný řetězcový literál](media/raw-string-literal.png "Nezpracovaný řetězcový literál")

Řetězec je převeden na: `R"(C:\Users\bjarnes\demo\output.txt)"`.
