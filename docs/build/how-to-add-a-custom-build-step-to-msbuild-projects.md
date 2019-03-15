---
title: 'Postupy: Přidat vlastní krok sestavení do projektů MSBuild'
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 4c64c6875d82000d6a0ac880b103b5e220015cb3
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57814002"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Postupy: Přidat vlastní krok sestavení do projektů MSBuild

Vlastní krok sestavení je krok uživatelem definované v sestavení. Vlastní krok sestavení se chová stejně jako jakýkoli jiný *příkazu nástroje* krok, jako je například standardní nástroj krok kompilace nebo odkaz.

Zadejte vlastní krok sestavení v souboru projektu (.vcxproj). V kroku můžete zadat příkazový řádek ke spuštění jakékoli další vstupní nebo výstupní soubory a napište zprávu zobrazit. Pokud **MSBuild** určí, že výstupní soubory jsou zastaralé z hlediska vstupních souborů, zobrazí zprávu a provede příkaz.

Pokud chcete zadat umístění sestavení vlastní krok v pořadí sestavení cílů, použijte jedno nebo obě `CustomBuildAfterTargets` a `CustomBuildBeforeTargets` elementů XML v souboru projektu. Například můžete zadat, že vlastní krok sestavení spustí nástroj cíl odkazu a cílové nástroj manifest. Vlastní sada dostupných cílů závisí na konkrétním sestavení.

Zadejte `CustomBuildBeforeTargets` element k provedení vlastního kroku sestavení před spuštěním konkrétnímu cíli, `CustomBuildAfterTargets` element k provedení kroku po spuštění konkrétnímu cíli nebo oba elementy pro provedení kroku mezi dva sousedící cíle. Pokud není zadán žádný element, vaše vlastní nástroj sestavení spustí ve výchozím umístění, která je po **odkaz** cíl.

Vlastní sestavovací nástroje a vlastní kroky sestavení sdílet informace uvedené v `CustomBuildBeforeTargets` a `CustomBuildAfterTargets` elementů XML. Proto zadejte tyto cíle jenom jednou v souboru projektu.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Chcete-li definovat, co spuštění vlastního kroku sestavení

1. Přidejte skupiny vlastností do souboru projektu. V této skupině vlastnost zadejte příkaz, jeho vstupů a výstupů a zprávu, jak je znázorněno v následujícím příkladu. Tento příklad vytvoří soubor .cab ze souboru main.cpp, kterou jste vytvořili v [názorný postup: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(TargetFileName)</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Chcete-li definovat, kdy v buildu se spustí vlastní krok sestavení

1. Přidejte následující skupiny vlastností do souboru projektu. Můžete zadat obě cíle nebo jeden můžete vynechat, pokud chcete jenom vlastní krok spustit před nebo po konkrétnímu cíli. Tento příklad říká **MSBuild** provádět vlastní krok po kroku kompilace, ale před krokem odkaz.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Viz také:

[Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
