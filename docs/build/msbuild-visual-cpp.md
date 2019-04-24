---
title: MSBuild na příkazovém řádku - C++
ms.date: 12/12/2018
f1_keywords:
- MSBuild
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: 565b1c47b4476fa7cb830e15b978b389f4344ee1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273310"
---
# <a name="msbuild-on-the-command-line---c"></a>MSBuild na příkazovém řádku - C++

Obecně doporučujeme používat Visual Studio k nastavení vlastností projektu a vyvolávání systém MSBuild. Můžete však použít **MSBuild** nástroje přímo z příkazového řádku. Proces sestavení se řídí tím informace v souboru projektu (.vcxproj), které můžete vytvářet a upravovat. Soubor projektu určuje možnosti sestavení na základě sestavení fáze, podmínky a události. Kromě toho můžete zadat nula nebo více příkazového řádku *možnosti* argumenty.

> **MSBuild.exe** [ *project_file* ] [ *možnosti* ]

Použití **/target** (nebo **/t**) a **/property** (nebo **/p**) možnosti příkazového řádku k přepsání specifické vlastnosti a cíle, které jsou zadaná v souboru projektu.

Základní funkcí souboru projektu je zadání *cílové*, což je určitá operace použitá na váš projekt a vstupy a výstupy, které jsou nutné k provedení této operace. Soubor projektu může určit jeden nebo více cílů, které mohou zahrnovat výchozí cíl.

Každý cíl se skládá ze sekvence jedné nebo více *úlohy*. Každá úloha je reprezentována třídou rozhraní .NET Framework, která obsahuje jeden spustitelný příkaz. Například [cl – úloha](/visualstudio/msbuild/cl-task) obsahuje [cl.exe](reference/compiling-a-c-cpp-program.md) příkaz.

A *parametr úlohy* je vlastnost úlohy třídy a obvykle představuje možnost příkazového řádku pro spustitelný příkaz. Například `FavorSizeOrSpeed` parametr `CL` úlohy odpovídá **/Os** a **/Ot** – možnosti kompilátoru.

Další parametry úlohy podporují infrastrukturu MSBuild. Například `Sources` parametr úlohy Určuje sadu úkolů, které mohou být spotřebovány dalšími úkoly. Další informace o úlohách MSBuild naleznete v tématu [– referenční dokumentace úlohy](/visualstudio/msbuild/msbuild-task-reference).

Většina úkolů vyžaduje vstup a výstup, jako jsou názvy souborů, cesty a řetězce, čísla nebo logické parametry. Společný vstup například je název pro kompilaci zdrojového souboru .cpp. Důležitý vstupní parametr je řetězec, který určuje konfiguraci sestavení a platformy, například "Debug\|Win32". Vstupy a výstupy jsou určeny jeden nebo více uživatelem definované XML `Item` elementů obsažených v `ItemGroup` elementu.

Soubor projektu můžete také určit uživatelem definované *vlastnosti* a `ItemDefinitionGroup` *položky*. Vlastnosti a položky tvoří páry název/hodnota, které lze použít jako proměnné v sestavení. Název součásti páru definuje *– makro*, a součást hodnoty prohlašuje *hodnotu makra*. Makru vlastnosti lze přistupovat pomocí $(*název*) zápisem a makro položky lze přistupovat pomocí %(*název*) notaci.

Dalších prvky XML v souboru projektu mohou testovat makra a podmíněně nastavit hodnotu všech maker nebo řídit spuštění sestavení. Názvy maker a řetězce literálů mohou být spojeny ke generování konstrukce, jako je třeba název a cesta k souboru. Na příkazovém řádku **/property** možnost nastaví nebo přepíše vlastnost projektu. Položky nelze odkazovat na příkazovém řádku.

Systém MSBuild může podmíněně spustit cíl před nebo po jiném cíli. Systém také může vytvořit jiný cíl závislosti na tom, jestli jsou soubory, které cíl využívá novější než soubory, které vydává.

Další informace o nástroji MSBuild naleznete v tématu:

- [Nástroj MSBuild](/visualstudio/msbuild/msbuild) koncepty přehled nástroje MSBuild.

- [Referenční dokumentace nástroje MSBuild](/visualstudio/msbuild/msbuild-reference) referenční informace o systému MSBuild.

- [Referenční dokumentace schématu souboru projektu](/visualstudio/msbuild/msbuild-project-file-schema-reference) uvádí prvky schématu MSBuild XML, spolu s jejich atributy a nadřazené a podřízené prvky. Obzvláště zvažte [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [cílové](/visualstudio/msbuild/target-element-msbuild), a [úloh](/visualstudio/msbuild/task-element-msbuild) elementy.

- [Odkaz na příkazový řádek](/visualstudio/msbuild/msbuild-command-line-reference) popisuje argumenty příkazového řádku a možnosti, které lze použít s msbuild.exe.

- [Úloha odkazu](/visualstudio/msbuild/msbuild-task-reference) úlohy nástroje MSBuild popisuje. Obzvláště zvažte tyto prvky, které jsou specifické pro Visual C++: [BscMake Task](/visualstudio/msbuild/bscmake-task), [CL Task](/visualstudio/msbuild/cl-task), [CPPClean Task](/visualstudio/msbuild/cppclean-task), [LIB Task](/visualstudio/msbuild/lib-task), [Link Task](/visualstudio/msbuild/link-task), [MIDL Task](/visualstudio/msbuild/midl-task), [MT Task](/visualstudio/msbuild/mt-task), [RC Task](/visualstudio/msbuild/rc-task), [SetEnv Task](/visualstudio/msbuild/setenv-task), [VCMessage Task](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>V tomto oddílu

|Termín|Definice|
|----------|----------------|
|[Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Popisuje způsob vytvoření projektu jazyka Visual C++ pomocí **MSBuild**.|
|[Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)|Ukazuje, jak určit akci, ke které dochází v particuler fázi v buildu: před začátkem sestavení; Před spuštěním kroku odkazu; nebo po ukončení sestavení.|
|[Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Ukazuje, jak přidat fázi uživatelem definované pořadí sestavení.|
|[Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)|Ukazuje, jak přidružit určitý soubor nástroj sestavení.|
|[Postupy: Integrace vlastních nástrojů do vlastností projektu](how-to-integrate-custom-tools-into-the-project-properties.md)|Ukazuje, jak přidat možnosti pro vlastní nástroj ve vlastnostech projektu.|
|[Postupy: Změna cílové architektury a sady nástrojů](how-to-modify-the-target-framework-and-platform-toolset.md)|Ukazuje, jak sestavit projekt pro více rozhraní nebo sad nástrojů.|

## <a name="see-also"></a>Viz také:

[Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)
