---
title: 'Postupy: Přidání vlastního kroku sestavení do projektů MSBuild'
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444914"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Postupy: Přidání vlastního kroku sestavení do projektů MSBuild

Vlastní krok sestavení je uživatelem definovaný krok v sestavení. Vlastní krok sestavení se chová stejně jako jakýkoli jiný krok *příkazového nástroje* , jako je například standardní kompilace nebo krok nástroje propojení.

Zadejte vlastní krok sestavení v souboru projektu (. vcxproj). V tomto kroku můžete zadat příkazový řádek, který se má provést, všechny další vstupní nebo výstupní soubory a zprávu, která se má zobrazit. Pokud nástroj **MSBuild** zjistí, že jsou vaše výstupní soubory zastaralé z hlediska vstupních souborů, zobrazí zprávu a provede příkaz.

Chcete-li určit umístění vlastního kroku sestavení v pořadí cílů sestavení, použijte jeden nebo oba prvky jazyka `CustomBuildAfterTargets` a `CustomBuildBeforeTargets` v souboru projektu. Můžete například určit, že se vlastní krok sestavení spustí po cíli nástroje propojení a před cílem nástroje manifestu. Skutečná sada dostupných cílů závisí na konkrétním sestavení.

Určete `CustomBuildBeforeTargets` prvek, který má provést vlastní krok sestavení před konkrétním cílovým spuštěním, `CustomBuildAfterTargets` elementu, který provede krok po konkrétním cílovém spuštění, nebo obou prvků, aby provedli krok mezi dvěma sousedícími cíli. Pokud není zadán žádný element, vlastní nástroj sestavení se spustí ve výchozím umístění, což je po cíli **propojení** .

Vlastní kroky sestavení a nástroje pro vlastní sestavení sdílejí informace zadané v prvcích `CustomBuildBeforeTargets` XML `CustomBuildAfterTargets` a. Proto v souboru projektu zadejte tyto cíle jen jednou.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Definování toho, co je provedeno vlastním krokem sestavení

1. Přidejte skupinu vlastností do souboru projektu. V této skupině vlastností určete příkaz, jeho vstupy a výstupy a zprávu, jak je znázorněno v následujícím příkladu. Tento příklad vytvoří soubor. cab ze souboru main. cpp, který jste vytvořili v [návodu: použití nástroje MSBuild k vytvoření projektu jazyka C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Chcete-li definovat, kde v sestavení se spustí vlastní krok sestavení

1. Přidejte do souboru projektu následující skupinu vlastností. Můžete zadat oba cíle, nebo můžete vynechat jeden, pokud chcete, aby byl vlastní krok proveden před nebo po určitém cíli. Tento příklad oznamuje nástroji **MSBuild** , aby provedl vlastní krok po kroku kompilace, ale před krok propojení.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Viz také

[Návod: vytvoření projektu jazyka C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Postupy: Přidání vlastního nástroje sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)
