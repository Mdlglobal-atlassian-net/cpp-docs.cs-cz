---
title: 'Postupy: Přidání vlastního kroku sestavení do projektů MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.addcustombuildstep
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa8d433b782d8436f6211ab9efe55fcaad3492ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Postupy: Přidání vlastního kroku sestavení do projektů MSBuild
Vlastní krok sestavení je krok uživatelem definované v sestavení. Vlastní krok sestavení se chová stejně jako jakýkoli jiný *nástroj příkazu* krok, jako je například standardní nástroj krok kompilaci nebo odkaz.  
  
 Zadejte vlastní krok sestavení v souboru projektu (VCXPROJ). V kroku můžete zadat příkazový řádek provést žádné další vstupní nebo výstupní soubory a zobrazit zprávu. Pokud **MSBuild** určí, že výstupní soubory jsou zastaralé s ohledem na vaše vstupní soubory, zobrazí se zpráva a provede příkaz.  
  
 Pokud chcete zadat umístění vlastní sestavovací krok v pořadí sestavení cílů, použít jeden nebo oba `CustomBuildAfterTargets` a `CustomBuildBeforeTargets` elementů XML v souboru projektu. Například můžete zadat, spuštění vlastního kroku sestavení za cíl nástroj propojení a před cíl manifestu nástroj. Vlastní sada dostupných cílů závisí na konkrétní buildu.  
  
 Zadejte `CustomBuildBeforeTargets` element spuštění vlastního kroku sestavení před spuštěním konkrétní cílový, `CustomBuildAfterTargets` elementu, který chcete spustit v kroku po spuštění konkrétní cílový nebo obou elementů provést krok mezi dvěma přiléhající cíle. Pokud není zadán ani element, vaše vlastní sestavovací nástroje provede na výchozího umístění, což je po **odkaz** cíl.  
  
 Vlastní kroky sestavení a vlastní sestavovací nástroje sdílet informace uvedené v `CustomBuildBeforeTargets` a `CustomBuildAfterTargets` elementů XML. Proto zadejte tyto cíle jen jednou v souboru projektu.  
  
### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Chcete-li definovat, co je provedený vlastního kroku sestavení  
  
1.  Přidejte skupinu vlastností do souboru projektu. V této skupině vlastnost zadejte příkaz, vstupy a výstupy a zprávu, jak je znázorněno v následujícím příkladu. Tento příklad vytvoří soubor .cab ze souboru main.cpp jste vytvořili v [návod: použití nástroje MSBuild k vytvoření projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md).  
  
    ```  
    <ItemDefinitionGroup>  
      <CustomBuildStep>  
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>  
        <Outputs>$(TargetName).cab</Outputs>  
        <Inputs>$(TargetFileName)</Inputs>  
      </CustomBuildStep>  
    </ItemDefinitionGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Chcete-li definovat, kde v buildu se provést vlastní krok sestavení  
  
1.  Přidejte následující skupiny vlastností do souboru projektu. Můžete zadat i cíle, nebo jeden můžete vynechat, pokud chcete vlastní krok provést před nebo po konkrétní cílový. Tento příklad říká **MSBuild** k provedení vlastní krok po kroku kompilovat, ale před krok propojení.  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření projektu Visual C++ pomocí nástroje MSBuild](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [Postupy: použití událostí sestavení v projektech MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)