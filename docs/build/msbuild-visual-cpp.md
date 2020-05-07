---
title: MSBuild na příkazovém řádku – C++
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220572"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild na příkazovém řádku – C++

Obecně doporučujeme, abyste použili sadu Visual Studio k nastavení vlastností projektu a vyvolali systém MSBuild. Nástroj **MSBuild** ale můžete použít přímo z příkazového řádku. Proces sestavení je řízen informacemi v souboru projektu (. vcxproj), které lze vytvořit a upravit. Soubor projektu určuje možnosti sestavení na základě fází sestavení, podmínek a událostí. Kromě toho můžete zadat nula nebo více argumentů *možností* příkazového řádku.

> **MSBuild. exe** [ *project_file* ] [ *Možnosti* ]

Použijte možnosti příkazového řádku **/target** (nebo **/t**) a **/Property** (nebo **/p**) k přepsání specifických vlastností a cílů, které jsou zadány v souboru projektu.

Základní funkcí souboru projektu je určit *cíl*, který je konkrétní operací použitým pro váš projekt, a vstupy a výstupy, které jsou nutné k provedení této operace. Soubor projektu může určit jeden nebo více cílů, které mohou zahrnovat výchozí cíl.

Každý cíl se skládá z posloupnosti jednoho nebo více *úloh*. Jednotlivé úlohy jsou reprezentovány .NET Framework třídou, která obsahuje jeden spustitelný příkaz. Například [úloha CL](/visualstudio/msbuild/cl-task) obsahuje příkaz [CL. exe](reference/compiling-a-c-cpp-program.md) .

*Parametr Task* je vlastnost úlohy třídy, která obvykle představuje možnost příkazového řádku spustitelného příkazu. Například `FavorSizeOrSpeed` parametr `CL` úlohy odpovídá možnostem kompilátoru **/OS** a **/ot** .

Další parametry úlohy podporují infrastrukturu MSBuild. Například parametr `Sources` Task určuje sadu úloh, které mohou být spotřebovány jinými úkoly. Další informace o úlohách MSBuild naleznete v tématu [Reference k úkolu](/visualstudio/msbuild/msbuild-task-reference).

Většina úloh vyžaduje vstupy a výstupy, jako jsou názvy souborů, cesty a řetězcové, číselné nebo logické parametry. Například běžným vstupem je název zdrojového souboru. cpp ke kompilaci. Důležitý vstupní parametr je řetězec, který určuje konfiguraci sestavení a platformu, například "ladit\|Win32". Vstupy a výstupy jsou určené jedním nebo více uživatelsky definovanými `Item` prvky XML obsaženými `ItemGroup` v elementu.

Soubor projektu může také určit uživatelem definované *vlastnosti* a `ItemDefinitionGroup` *položky*. Vlastnosti a položky ve formě dvojice název/hodnota, které lze použít jako proměnné v sestavení. Název komponenty páru definuje *makro*a komponenta Value deklaruje *hodnotu makra*. K makru vlastnosti se dostanete pomocí zápisu $ (*Name*) a k makru položky se dostanete pomocí%(*Name*).

Jiné prvky XML v souboru projektu mohou testovat makra a následně podmíněně nastavit hodnotu jakéhokoli makra nebo řídit spuštění sestavení. Názvy maker a řetězcové literály lze zřetězit, aby bylo možné generovat konstrukce, jako je například cesta a název souboru. V příkazovém řádku možnost **/Property** nastaví nebo přepíše vlastnost projektu. Na příkazový řádek nelze odkazovat na položky.

Systém MSBuild může podmíněně spustit cíl před nebo po jiném cíli. Systém může také vytvořit cíl na základě toho, zda soubory, které cíl využívá, jsou novější než soubory, které posílá.

Další informace o nástroji MSBuild najdete v těchto tématech:

- Nástroj [MSBuild](/visualstudio/msbuild/msbuild) Přehled konceptů MSBuild.

- [Referenční](/visualstudio/msbuild/msbuild-reference) dokumentace nástroje MSBuild Referenční informace o systému MSBuild.

- [Referenční dokumentace schématu souboru projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference) Obsahuje prvky schématu XML nástroje MSBuild spolu s jejich atributy a nadřazenými a podřízenými prvky. Obzvláště Poznamenejte si prvky [Item](/visualstudio/msbuild/itemgroup-element-msbuild), [Property](/visualstudio/msbuild/propertygroup-element-msbuild), [target](/visualstudio/msbuild/target-element-msbuild)a [Task](/visualstudio/msbuild/task-element-msbuild) .

- [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) Popisuje argumenty a možnosti příkazového řádku, které lze použít s nástrojem MSBuild. exe.

- [Odkaz na úkol](/visualstudio/msbuild/msbuild-task-reference) Popisuje úlohy nástroje MSBuild. Zvláště si všimněte těchto úkolů, které jsou specifické pro Visual C++: [BSCMAKE Task](/visualstudio/msbuild/bscmake-task), [CL](/visualstudio/msbuild/cl-task), [CPPClean – Task](/visualstudio/msbuild/cppclean-task), [lib Task](/visualstudio/msbuild/lib-task), [propojování Task](/visualstudio/msbuild/link-task), [Task MIDL](/visualstudio/msbuild/midl-task), [Mt Task](/visualstudio/msbuild/mt-task), [RC](/visualstudio/msbuild/rc-task)Task, [setenv – Task](/visualstudio/msbuild/setenv-task), [VCMessage – Task](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>V tomto oddílu

|Označení|Definice|
|----------|----------------|
|[Návod: vytvoření projektu jazyka C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Ukazuje, jak vytvořit projekt sady Visual Studio C++ pomocí nástroje **MSBuild**.|
|[Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Ukazuje, jak zadat akci, která se nachází ve fázi particuler v sestavení: před zahájením sestavování; před zahájením kroku propojení; nebo po konci sestavení.|
|[Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Ukazuje, jak přidat uživatelsky definovanou fázi do sekvence sestavení.|
|[Postupy: Přidání vlastního nástroje sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Ukazuje, jak přidružit nástroj sestavení k určitému souboru.|
|[Postupy: Integrace vlastních nástrojů do vlastností projektu](how-to-integrate-custom-tools-into-the-project-properties.md)|Ukazuje, jak přidat možnosti pro vlastní nástroj do vlastností projektu.|
|[Postupy: Změna cílové architektury a sady nástrojů](how-to-modify-the-target-framework-and-platform-toolset.md)|Ukazuje, jak zkompilovat projekt pro více platforem nebo sad nástrojů.|

## <a name="see-also"></a>Viz také

[Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)
