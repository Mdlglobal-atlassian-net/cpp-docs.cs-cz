---
title: 'Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild'
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
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild

Pro vlastní nástroj sestavení je definovaný uživatelem, příkazového řádku nástroj, který je přidružený k konkrétní soubor.

Pro konkrétní soubor zadejte v souboru projektu (.vcxproj) příkazový řádek pro spuštění, jakékoli další vstupní nebo výstupní soubory a zprávy pro zobrazení. Pokud **MSBuild** určí, že výstupní soubory jsou aktuální s ohledem na vstupní soubory, zobrazí zprávu a spustí nástroj příkazového řádku.

Chcete-li určit, kdy vlastní nástroj sestavení spustí, použít jeden nebo oba `CustomBuildBeforeTargets` a `CustomBuildAfterTargets` elementů XML v souboru projektu. Například můžete určit, že vaše vlastní nástroj sestavení spouštět v kompilátoru MIDL a kompilátor C/C++. Zadejte `CustomBuildBeforeTargets` elementu, chcete-li spustit nástroj před spuštěním konkrétnímu cíli; `CustomBuildAfterTargets` elementu, chcete-li spustit nástroj po konkrétní cílový; nebo oba prvky ke spuštění nástroje mezi provádění dva cíle. Pokud není zadán žádný element, vaše vlastní nástroj sestavení spustí ve výchozím umístění, která je před **MIDL** cíl.

Vlastní sestavovací nástroje a vlastní kroky sestavení sdílet informace uvedené v `CustomBuildBeforeTargets` a `CustomBuildAfterTargets` elementů XML. Zadejte tyto cíle jednou v souboru projektu.

### <a name="to-add-a-custom-build-tool"></a>Chcete-li přidat vlastní nástroj sestavení

1. Přidejte skupinu položek do souboru projektu a přidání položky pro každý vstupní soubor. Zadejte příkaz, další vstupy, výstupy a zprávu jako metadata položky, jak je znázorněno zde. Tento příklad předpokládá, že soubor "li Tento soubor" existuje ve stejném adresáři jako váš projekt.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Chcete-li definovat, kdy v buildu se spustí vlastní sestavovací nástroje

1. Přidejte následující skupiny vlastností do souboru projektu. Je nutné zadat alespoň jeden z cílů, ale druhá můžete vynechat, pokud vás zajímá jenom tím, že vaše krok sestavení spustit před (nebo po) konkrétnímu cíli. V tomto příkladu se provádí vlastní krok po kompilaci, ale před propojením.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Viz také:

[Návod: Vytvoření projektu C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)<br/>
[Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)
