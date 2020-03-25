---
title: Vytvoření projektu C++ makefile v aplikaci Visual Studio
ms.date: 08/05/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects [C++]
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: b96b7a1663e5d5886615dd976900f8eda9daeccc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169887"
---
# <a name="create-a-c-makefile-project"></a>Vytvoření projektu C++ souboru pravidel

Soubor *pravidel* je textový soubor, který obsahuje pokyny, jak kompilovat a propojit (nebo *sestavit*) sadu souborů C++ zdrojového kódu. Programový *program* přečte soubor pravidel a vyvolá kompilátor, linker a případně jiné programy, aby mohl vytvořit spustitelný soubor. Implementace *IT programu od Microsoftu se nazývá* [NMAKE](nmake-reference.md).

Máte-li existující projekt makefile, máte tyto možnosti, pokud chcete kód nebo ho ladit v integrovaném vývojovém prostředí sady Visual Studio:

- Vytvořte projekt makefile v aplikaci Visual Studio, který používá existující soubor pravidel ke konfiguraci souboru. vcxproj, který bude Visual Studio používat pro technologii IntelliSense. (Nebudete mít všechny funkce IDE, které získáte s nativním projektem MSBuild.) Viz [Vytvoření projektu souboru pravidel](#create_a_makefile_project) níže.
- Pomocí průvodce **vytvořením nového projektu z existujících souborů kódu** vytvořte nativní projekt MSBuild ze zdrojového kódu. Původní soubor pravidel se za tímto souborem nepoužije. Další informace najdete v tématu [Postupy: vytvoření C++ projektu z existujícího kódu](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 a novější**: pomocí funkce **Otevřít složku** můžete upravit a sestavit projekt makefile tak, jak je, bez jakéhokoli zásahu do systému MSBuild. Další informace naleznete v tématu [Otevřít složku projekty pro C++ ](../open-folder-projects-cpp.md).
- **Visual Studio 2019 a novější**: Vytvořte projekt makefile se systémem UNIX pro Linux.

## <a name="a-namecreate_a_makefile_project-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> vytvoření projektu makefile pomocí šablony projektu makefile

V aplikaci Visual Studio 2017 nebo novější je šablona projektu Makefile k dispozici, C++ když je nainstalovaná úloha vývoj desktopových aplikací.

Postupujte podle pokynů průvodce a zadejte příkazy a prostředí používané souborem pravidel. Pak můžete použít tento projekt k sestavení kódu v aplikaci Visual Studio.

Ve výchozím nastavení projekt makefile nezobrazuje v Průzkumník řešení žádné soubory. Projekt makefile určuje nastavení sestavení, která se projeví na stránce vlastností projektu.

Výstupní soubor zadaný v projektu nemá žádný vliv na název, který generuje skript sestavení; deklaruje pouze záměr. Váš soubor pravidel stále řídí proces sestavení a určuje cíle sestavení.

::: moniker range="vs-2019"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>Vytvoření projektu makefile v aplikaci Visual Studio 2019

1. V hlavní nabídce aplikace Visual Studio vyberte **soubor** > **Nový** > **projekt** a do vyhledávacího pole zadejte "makefile". Nebo, v dialogovém okně **Nový projekt** rozbalte položku  **C++ Visual** > **General** (Visual Studio 2015) nebo **jiný** (Visual Studio 2017) a pak vyberte ze dvou možností podle toho, jestli budete cílit na Windows nebo Linux.

1. **Pouze Windows**: na stránce **nastavení konfigurace ladění** zadejte příkaz, výstup, vyčistit a znovu sestavte informace pro ladění a maloobchodní buildy. Klikněte na **Další** , pokud chcete zadat různá nastavení pro konfiguraci vydané verze.

1. Kliknutím na tlačítko **Dokončit** zavřete dialogové okno a otevřete nově vytvořený projekt v **Průzkumník řešení**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>Vytvoření projektu makefile v aplikaci Visual Studio 2015 nebo Visual Studio 2017

1. Na úvodní stránce sady Visual Studio zadejte do pole hledání **nového projektu** text "makefile". Nebo, v dialogovém okně **Nový projekt** rozbalte položku **Visual C++**  > **General** (Visual Studio 2015) nebo **jiný** (Visual Studio 2017) a pak vyberte možnost **projekt makefile** v podokně šablony a otevřete tak Průvodce projektu.

1. Na stránce **nastavení aplikace** zadejte příkaz, výstup, vyčistit a znovu sestavte informace pro ladění a maloobchodní sestavení.

1. Kliknutím na tlačítko **Dokončit** zavřete průvodce a otevřete nově vytvořený projekt v **Průzkumník řešení**.

::: moniker-end

Na stránce vlastností projektu můžete zobrazit a upravit jeho vlastnosti. Informace o zobrazení stránky vlastností naleznete v tématu [Nastavení vlastností kompilátoru a sestavení v C++ sadě Visual Studio](../working-with-project-properties.md) .

## <a name="makefile-project-wizard"></a>Průvodce projektem souboru pravidel

Po vytvoření projektu makefile můžete zobrazit a upravit každou z následujících možností na stránce **NMAKE** stránky vlastností projektu.

- **Příkazový řádek sestavení:** Určuje příkazový řádek, který se má spustit, když uživatel vybere sestavení v nabídce sestavení. Zobrazuje se v poli příkazového řádku sestavení na stránce vlastností projektu.

- **Výstup:** Určuje název souboru, který bude obsahovat výstup z příkazového řádku. Ve výchozím nastavení je tato možnost založena na názvu projektu. Zobrazuje se v poli výstup na stránce vlastností projektu na stránce NMAKE.

- **Příkazy pro vyčištění:** Určuje příkazový řádek, který se spustí, když uživatel vybere vyčistit v nabídce sestavení. Zobrazuje se v poli vyčistit příkazový řádek na stránce vlastností projektu.

- **Příkazový řádek opětovného sestavení:** Určuje příkazový řádek, který se spustí, když uživatel vybere znovu sestavení z nabídky sestavit. Zobrazuje se v poli znovu sestavit vše v příkazovém řádku na stránce vlastností projektu na stránce NMAKE.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Postupy: Povolení technologie IntelliSense pro projekty souborů pravidel

Technologie IntelliSense se v projektech makefile nezdařila, pokud je nastavení některých projektů nebo možností kompilátoru nesprávně nastaveno. Pomocí těchto kroků můžete nakonfigurovat projekty makefile tak, aby technologie IntelliSense fungovala podle očekávání:

1. Otevřete dialogové okno **stránky vlastností** . Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte uzel **Vlastnosti konfigurace** .

1. Vyberte stránku vlastností **NMAKE** a pak podle potřeby upravte vlastnosti v části **IntelliSense** .

   - Nastavte vlastnost **Definice preprocesoru** tak, aby definovala všechny symboly preprocesoru v projektu makefile. Další informace naleznete v tématu [/d (Definice preprocesoru)](d-preprocessor-definitions.md).

   - Nastavte vlastnost **zahrnout cestu pro hledání** tak, aby určovala seznam adresářů, které kompilátor vyhledá, aby vyřešil odkazy na soubory, které jsou předány direktivám preprocesoru v projektu makefile. Další informace najdete v tématu [/i (další adresáře k zahrnutí)](i-additional-include-directories.md).

   - Pro projekty vytvořené pomocí CL. Z příkazového okna nastavte proměnnou prostředí **include** tak, aby určovala adresáře, které kompilátor bude hledat, aby vyřešil odkazy na soubory, které jsou předány direktivám preprocesoru v projektu makefile.

   - Nastavte vlastnost **Vynucené zahrnutí** k určení, které soubory hlaviček mají být zpracovány při sestavování projektu makefile. Další informace najdete v tématu [/Fi (zahrnutý soubor s povinným názvem)](fi-name-forced-include-file.md).

   - Nastavte vlastnost **cesta pro vyhledávání sestavení** tak, aby určovala seznam adresářů, které kompilátor bude hledat, aby vyřešil odkazy na sestavení .NET v projektu. Další informace najdete v tématu [/AI (určení adresářů metadat)](ai-specify-metadata-directories.md).

   - Nastavte vlastnost **Vynucené použití sestavení** k určení, která sestavení .NET mají být zpracována při sestavování projektu makefile. Další informace najdete v tématu [/Fu (název vynuceného #using souboru)](fu-name-forced-hash-using-file.md).

   - Nastavte vlastnost **Další možnosti** tak, aby určovala další přepínače kompilátoru pro použití technologií IntelliSense při C++ analýze souborů.

1. Kliknutím na tlačítko **OK** zavřete stránky vlastností.

1. Pomocí příkazu **Uložit vše** uložte upravená nastavení projektu.

Při příštím otevření projektu makefile ve vývojovém prostředí sady Visual Studio spusťte příkaz **Vyčistit řešení** a poté příkaz **Sestavit řešení** v projektu makefile. Technologie IntelliSense by měla v integrovaném vývojovém prostředí fungovat správně.

## <a name="see-also"></a>Viz také

[Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE – referenční zdroje](nmake-reference.md)<br>
[Postupy: vytvoření C++ projektu z existujícího kódu](../how-to-create-a-cpp-project-from-existing-code.md)
[speciálních znaků v souboru pravidel](special-characters-in-a-makefile.md)<br/>
[Obsah souboru pravidel](contents-of-a-makefile.md)<br/>
