---
title: 'Postupy: Přidání vlastního nástroje sestavení do projektů MSBuild'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 812932d9e668ab5ee0eb75eadbf75be3d791cddb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220715"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Postupy: Přidání vlastního nástroje sestavení do projektů MSBuild

Vlastní nástroj sestavení je uživatelsky definovaný nástroj příkazového řádku, který je přidružen ke konkrétnímu souboru.

Pro konkrétní soubor zadejte do souboru projektu (. vcxproj) příkazový řádek, který se má spustit, všechny další vstupní nebo výstupní soubory a zprávu, která se má zobrazit. Pokud nástroj **MSBuild** zjistí, že vaše výstupní soubory jsou bez ohledu na vstupní soubory, zobrazí zprávu a spustí nástroj příkazového řádku.

Chcete-li určit, kdy se vlastní nástroj sestavení spustí, použijte jeden nebo `CustomBuildBeforeTargets` oba `CustomBuildAfterTargets` elementy XML v souboru projektu. Například můžete určit, že vlastní nástroj sestavení je spuštěn po kompilátoru MIDL a před kompilátorem jazyka C/C++. Určete `CustomBuildBeforeTargets` prvek pro spuštění nástroje před konkrétním cílovým spuštěním; `CustomBuildAfterTargets` element pro spuštění nástroje po určitém cíli; nebo oba elementy ke spuštění nástroje mezi spuštěním dvou cílů. Pokud není zadán žádný element, vlastní nástroj sestavení se spustí ve výchozím umístění, které je před cílem **MIDL** .

Vlastní kroky sestavení a nástroje pro vlastní sestavení sdílejí informace zadané v prvcích `CustomBuildBeforeTargets` XML `CustomBuildAfterTargets` a. Zadejte tyto cíle v souboru projektu v jednom okamžiku.

### <a name="to-add-a-custom-build-tool"></a>Přidání vlastního nástroje sestavení

1. Přidejte skupinu položek do souboru projektu a přidejte položku pro každý vstupní soubor. Zadejte příkaz, další vstupy, výstupy a zprávy jako metadata položky, jak je znázorněno zde. V tomto příkladu se předpokládá, že soubor "FAQ. txt" existuje ve stejném adresáři jako váš projekt.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Chcete-li definovat, kde v sestavení budou spouštěny vlastní nástroje sestavení

1. Přidejte do souboru projektu následující skupinu vlastností. Je nutné zadat alespoň jeden z cílů, ale pokud chcete, aby se váš krok sestavení prováděl před (nebo po) konkrétním cílem, můžete ho vynechat. Tento příklad provede vlastní krok po kompilaci, ale před propojením.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Viz také

[Návod: vytvoření projektu jazyka C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)
