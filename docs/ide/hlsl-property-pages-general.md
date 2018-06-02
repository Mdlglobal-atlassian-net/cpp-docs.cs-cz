---
title: 'HLSL – stránky vlastností: Obecné | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs:
- C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77cc9a44076999633fd17b049cbcfad75f65eb7e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33340135"
---
# <a name="hlsl-property-pages-general"></a>HLSL – stránky vlastností: Obecné
Chcete-li nakonfigurovat následující vlastnosti kompilátoru HLSL (fxc.exe), použijte jeho **Obecné** stránku vlastností. Informace o tom, jak získat přístup **Obecné** najdete v části stránky vlastností ve složce HLSL [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Další zahrnuté adresáře**  
 Cesta zahrnutí přidá jeden nebo více adresářů. K oddělení adresáře použijte středníky.  
  
 Tato vlastnost odpovídá **/I [cesta]** argument příkazového řádku.  
  
 **Název vstupního bodu**  
 Určuje vstupní bod pro shaderu. Výchozí hodnota je **hlavní**.  
  
 Tato vlastnost odpovídá **/E [name]** argument příkazového řádku.  
  
 **Zakázat optimalizace**  
 **Ano (/ Od)** zakázat optimalizace; jinak **ne**. Výchozí hodnota je **Ano (/ Od)** pro **ladění** konfigurace a **ne** pro **verze** konfigurace.  
  
 **/Od** argument příkazového řádku pro kompilátor HLSL implicitně vztahuje **/Gfp** argument příkazového řádku, ale výstup nemusí být stejný jako výstup, který vytváří předáním i **/Od**  a **/Gfp** argumenty příkazového řádku explicitně.  
  
 **Povolit ladění informace**  
 **Ano (/Zi)** povolit informace o ladění; jinak **ne**. Výchozí hodnota je **Ano (/Zi)** pro **ladění** konfigurace a **ne** pro **verze** konfigurace.  
  
 **Typ shaderu**  
 Určuje druh shaderu. Různé druhy shadery implementovat různé části grafiky kanálu. Jsou k dispozici jenom v modelech novější shaderu určité druhy shadery (které je určené vlastností **shaderu modelu** vlastnost) – například výpočetní shadery byly zavedeny v modelu shaderu 5.  
  
 Tato vlastnost odpovídá **[typ]** část **_ /T [typ] [model]** argument příkazového řádku pro kompilátor HLSL. **Shaderu modely** určuje vlastnost **[model]** část argumentu.  
  
 **Model shaderu**  
 Určuje shaderu modelu. Různé shaderu modely mají různé možnosti. Obecně platí novější modely shaderu nabízí rozšířené možnosti, ale vyžadují více moderní grafiky hardware pro spuštění kódu shaderu. Určité druhy shadery (které jsou určené **shaderu typ** vlastnost) jsou k dispozici jenom v modelech novější shaderu – například výpočetní shadery byly zavedeny v modelu shaderu 5.  
  
 Tato vlastnost odpovídá **[model]** část **_ /T [typ] [model]** argument příkazového řádku pro kompilátor HLSL. **Shaderu typ** určuje vlastnost **[typ]** část argumentu.  
  
 **Definice preprocesoru**  
 Přidá jednu nebo víc definic – symbol preprocesoru, které chcete použít pro HLSL souboru se zdrojovým kódem. K oddělení definice symbolu použijte středníky.  
  
 Tato vlastnost odpovídá **/D [definice]** argument příkazového řádku pro kompilátor HLSL.  
  
## <a name="see-also"></a>Viz také  
 [HLSL – stránky vlastností](../ide/hlsl-property-pages.md)   
 [HLSL – stránky vlastností: Upřesnit](../ide/hlsl-property-pages-advanced.md)   
 [HLSL – stránky vlastností: Výstupní soubory](../ide/hlsl-property-pages-output-files.md)