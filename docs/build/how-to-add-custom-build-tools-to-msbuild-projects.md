---
title: 'Postupy: Přidání vlastního nástroje sestavení do projektů MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3793e4223d00f219cc4f1d7b09e67453901bd6d1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Postupy: Přidání vlastního nástroje sestavení do projektů MSBuild
Vlastní sestavovací nástroje je nástroj definovaný uživatelem, příkazového řádku, který je přidružen konkrétní soubor.  
  
 Pro konkrétní soubor zadejte v souboru projektu (VCXPROJ) příkazového řádku provést, žádné další vstupní nebo výstupní soubory a zprávu zobrazíte. Pokud **MSBuild** určí, že výstupní soubory jsou zastaralé s ohledem na vaše vstupní soubory, zobrazí se zpráva a spustí nástroj příkazového řádku.  
  
 Chcete-li zadat, když se spustí nástroj pro vlastní sestavení, použijte jednu nebo obě `CustomBuildBeforeTargets` a `CustomBuildAfterTargets` elementů XML v souboru projektu. Například může určit, že vaše vlastní sestavovací nástroje spustit po MIDL kompilátoru a před kompilátor C/C++. Zadejte `CustomBuildBeforeTargets` elementu, který chcete spustit nástroj před spuštěním konkrétní cílový; `CustomBuildAfterTargets` elementu, který chcete spustit nástroj po konkrétní cílový; nebo obou elementů ke spuštění nástroje mezi provádění dva cíle. Pokud není zadán ani element, vaše vlastní sestavovací nástroje provede na jeho výchozí umístění, které je před **MIDL** cíl.  
  
 Vlastní kroky sestavení a vlastní sestavovací nástroje sdílet informace uvedené v `CustomBuildBeforeTargets` a `CustomBuildAfterTargets` elementů XML. Zadejte tyto cíle jednou v souboru projektu.  
  
### <a name="to-add-a-custom-build-tool"></a>Chcete-li přidat vlastní sestavovací nástroje  
  
1.  Přidat skupinu položek do souboru projektu a přidejte položku pro každý vstupní soubor. Zadejte příkaz, další vstupy, výstupy a zprávu jako metadata položky, jak je vidět tady. Tento příklad předpokládá, že soubor "li Tento soubor" existuje ve stejném adresáři jako projektu.  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>Chcete-li definovat, kdy v buildu se provést vlastní sestavovací nástroje  
  
1.  Přidejte následující skupiny vlastností do souboru projektu. Musíte zadat alespoň jeden z cílů, ale druhá můžete vynechat, pokud vás zajímá pouze s vaší krok sestavení spustit před (nebo po) na určitý cíl. Tento příklad provede vlastní krok po kompilování, ale před propojením.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření projektu Visual C++ pomocí nástroje MSBuild](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Postupy: použití událostí sestavení v projektech MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)