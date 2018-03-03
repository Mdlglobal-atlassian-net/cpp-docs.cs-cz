---
title: "Stránky vlastností (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.NotAProp.Edit
dev_langs:
- C++
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0c342148266dff9551d2705f8095250daf2b096
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="property-pages-visual-c"></a>Stránky vlastností (Visual C++)

Pomocí stránky vlastností můžete zadat nastavení pro projekty v sadě Visual Studio. Otevřete **stránky vlastností** dialogové okno pro sadu Visual Studio na projekt **projektu** nabídce zvolte **vlastnosti**.

Můžete zadat nastavení projektu tak, aby se vztahují všechny konfigurace sestavení, nebo můžete zadat jiný projekt vlastnosti pro každou konfiguraci sestavení. Můžete například zadat určitá nastavení pro konfiguraci verze a další nastavení pro konfiguraci ladění.

Ne všechny stránky k dispozici jsou však nemusí být zobrazeny v **stránky vlastností** dialogové okno. Které stránky se zobrazí, závisí na typy souborů v projektu.

Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

Projekty jiný systém než Windows, najdete v části [odkazu na stránku vlastností C++ Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Výchozí vlastnosti vs. Změněné vlastnosti

Při použití **nový projekt** dialogové okno Vytvořit projekt sady Visual Studio využívá šablony zadaného projektu k chybě při inicializaci vlastností projektu. Proto hodnoty vlastností v šabloně můžete představit jako výchozí hodnoty pro tento typ projektu. V jiných typech projektů vlastnosti může mít různé výchozí hodnoty.

Pokud se mění, zobrazí se tučným písmem hodnotu vlastnosti projektu. Vlastnosti projektu se dají změnit z následujících důvodů:

- Průvodce aplikace změní vlastnost, protože vyžaduje hodnotu vlastnosti jiný než ten, který je uveden v šabloně projektů.

- Zadejte hodnotu jinou vlastnost v **nový projekt** dialogové okno.

- Zadejte hodnotu jinou vlastnost na stránce vlastností projektu.

> [!TIP]
> Pokud chcete zobrazit poslední sadu hodnot vlastností, které MSBuild používá k vytvoření projektu, zkontrolujte preprocesoru výstupního souboru, který můžete vytvořit pomocí Tento příkazový řádek: **MSBuild / předběžně zpracovat:** *preprocessor_output_ Název souboru*<sub>opt</sub> *project_filename*<sub>opt</sub>

## <a name="resetting-properties"></a>Obnovení vlastnosti

Při prohlížení **stránky vlastností** dialogové okno pro projekt a projekt uzel je vybrána v **Průzkumníku řešení**, pro mnoho vlastností, můžete vybrat **Zdědit z nadřazené nebo produktu project výchozí hodnoty** nebo změňte hodnotu jiným způsobem.

Při prohlížení **stránky vlastností** dialogové okno pro projekt a soubor je vybrána v **Průzkumníku řešení**, pro mnoho vlastností, můžete vybrat **Zdědit z nadřazené nebo produktu project výchozí** nebo změňte hodnotu jiným způsobem. Ale pokud projekt obsahuje mnoho souborů, které mají hodnoty vlastností, které se liší od výchozí hodnoty projektu, projekt bude trvat déle sestavení.

> [!TIP]
> Chcete-li aktualizovat **stránky vlastností** dialogové okno tak, aby zobrazila nejnovější výběr, zvolte **použít**.

Většina výchozí nastavení projektu je výchozí nastavení systému (platforma). Některé výchozí hodnoty projektu odvozena z šablony stylů, která se použijí při aktualizaci vlastností v **výchozích nastavení projektu** části **Obecné** stránku vlastností konfigurace pro projekt. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Zadání uživatelem definované hodnoty

Je nutné zadat hodnotu pro některé vlastnosti. Hodnotu definovanou uživatelem může obsahovat alfanumerické znaky nebo názvy makro souboru projektu. Některé z těchto vlastností můžete provést pouze jednu hodnotu definovanou uživatelem, ale jiné může trvat seznam více hodnot oddělených středníky.

Chcete-li zadat uživatelem definovanou hodnotu pro vlastnost, nebo seznam, pokud vlastnost může trvat několik uživatelem definované hodnoty ve sloupci vpravo od názvu vlastnosti, proveďte jeden z následujících akcí:

- Zadejte hodnotu nebo seznam hodnot.

- Vyberte šipku rozevíracího seznamu. Pokud **upravit** je k dispozici, zvolte jej a potom do textového pole zadejte hodnotu nebo seznam hodnot. Alternativní způsob pro zadání seznamu je na samostatném řádku do textového pole zadejte jednotlivé hodnoty. Na stránce vlastností hodnoty zobrazí jako seznam oddělený středníkem.

   Chcete-li vložit makro souboru projektu jako hodnotu, zvolte **makra** a potom dvakrát klikněte na název makra.

- Vyberte šipku rozevíracího seznamu. Pokud **Procházet** je k dispozici, zvolte jej a potom vyberte jednu nebo více hodnot.

Pro více hodnot vlastností **Zdědit z nadřazené nebo produktu project výchozí** možnost je k dispozici, zvolte na šipku rozevíracího seznamu ve sloupci vpravo od názvu vlastnosti a vyberte možnost **upravit**. Ve výchozím nastavení je tato možnost vybrána.

Všimněte si, že stránka vlastností na aktuální úrovni pro více hodnot vlastnost, která dědí z jiné úrovně zobrazí pouze nastavení. Například, pokud je vybrán soubor v **Průzkumníku řešení** a vyberte C/C++ **Definice preprocesoru** vlastnost souborů definic se zobrazí, ale zděděná definice úrovni projektu nejsou zobrazeny. Chcete-li zobrazit aktuální úrovni a zděděné hodnoty, zvolte na šipku rozevíracího seznamu ve sloupci vpravo od názvu vlastnosti a potom zvolte **upravit**. Pokud použijete [model projektu Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), toto chování platí také pro objekty souborů a projektů. To znamená když dotazujete pro hodnoty u vlastnosti na úrovni souborů, nebudou získat hodnoty této vlastnosti na úrovni projektu. Na úrovni projektu musíte explicitně získat hodnoty vlastnosti. Kromě toho některé zděděné hodnoty vlastnosti mohou pocházet z šablony stylů, která není přístupná prostřednictvím kódu programu.

## <a name="in-this-section"></a>V tomto oddílu

[Pokročilé, Nástroj Manifest, vlastnosti konfigurace \<název projektu > dialogové okno stránky vlastností](../ide/advanced-manifest-tool.md)

[Stránky vlastností příkazového řádku](../ide/command-line-property-pages.md)

[Stránka vlastností vlastního kroku sestavení: Obecné](../ide/custom-build-step-property-page-general.md)

[Přidávání odkazů](../ide/adding-references-in-visual-cpp-projects.md)

[Obecná stránka vlastností (soubor)](../ide/general-property-page-file.md)

[Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md)

[Obecné, Nástroj Manifest, vlastnosti konfigurace \<název projektu > dialogové okno stránky vlastností](../ide/general-manifest-tool-configuration-properties.md)

[HLSL – stránky vlastností](../ide/hlsl-property-pages.md)

[HLSL – stránky vlastností: Upřesnit](../ide/hlsl-property-pages-advanced.md)

[HLSL – stránky vlastností: Obecné](../ide/hlsl-property-pages-general.md)

[HLSL – stránky vlastností: Výstupní soubory](../ide/hlsl-property-pages-output-files.md)

[Vstup a výstup, Manifest nástroj, vlastnosti konfigurace, \<název projektu > dialogové okno stránky vlastností](../ide/input-and-output-manifest-tool.md)

[Izolované modelu COM, Nástroj Manifest, vlastnosti konfigurace, \<název projektu > dialogové okno stránky vlastností](../ide/isolated-com-manifest-tool.md)

[Stránky vlastností linkeru](../ide/linker-property-pages.md)

[Stránka vlastností spravovaných prostředků](../ide/managed-resources-property-page.md)

[Stránky vlastností nástroje manifest](../ide/manifest-tool-property-pages.md)

[MIDL – stránky vlastností](../ide/midl-property-pages.md)

[MIDL – stránky vlastností: Upřesnit](../ide/midl-property-pages-advanced.md)

[MIDL – stránky vlastností: Obecné](../ide/midl-property-pages-general.md)

[MIDL – stránky vlastností: Výstup](../ide/midl-property-pages-output.md)

[NMake – stránka vlastností](../ide/nmake-property-page.md)

[Stránky vlastností prostředků](../ide/resources-property-pages.md)

[Stránka vlastností adresářů VC++](../ide/vcpp-directories-property-page.md)

[Stránka vlastností webových odkazů](../ide/web-references-property-page.md)

[Stránka vlastností nástroje Generátor dat XML](../ide/xml-data-generator-tool-property-page.md)

[Stránky vlastností nástroje Generátor dokumentů XML](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Viz také

[Postupy: Vytváření a odebrání závislostí projektu](/visualstudio/ide/how-to-create-and-remove-project-dependencies)  
[Postupy: Vytvoření a úprava konfigurací](/visualstudio/ide/how-to-create-and-edit-configurations)  
