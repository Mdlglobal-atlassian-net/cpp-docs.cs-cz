---
title: 'Hlsl – stránky vlastností: Obecné'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
ms.openlocfilehash: cc7c0837def7628414d017a660453915a472318e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751437"
---
# <a name="hlsl-property-pages-general"></a>Hlsl – stránky vlastností: Obecné

Pokud chcete konfigurovat následující vlastnosti kompilátor HLSL (fxc.exe), použijte jeho **Obecné** stránku vlastností. Informace o tom, jak získat přístup **Obecné** zobrazit stránku vlastností ve složce HLSL [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Další adresáře souborů k zahrnutí**

   Přidá jednu nebo více adresářů, do cesty zahrnutí. K oddělení adresářů použijte středníky.

Tato vlastnost odpovídá **/I [cesta]** argument příkazového řádku.

- **Název vstupního bodu**

   Určuje vstupního bodu pro shader. Výchozí hodnota je **hlavní**.

Tato vlastnost odpovídá **/E [název]** argument příkazového řádku.

- **Zakázat optimalizace**

   **Ano (/ Od)** zakázat optimalizace; v opačném případě **ne**. Výchozí hodnota je **Ano (/ Od)** pro **ladění** konfigurací a **ne** pro **vydání** konfigurace.

**/Od** argument příkazového řádku pro kompilátor HLSL se implicitně týká **/gfp** argument příkazového řádku, ale výstup nemusí být stejný jako výstup, který je vytvořen pomocí předání i **/Od**  a **/gfp** argumenty příkazového řádku explicitně.

- **Povolit ladicí informace**

   **Ano (/Zi)** povolit ladicí informace; v opačném případě **ne**. Výchozí hodnota je **Ano (/Zi)** pro **ladění** konfigurací a **ne** pro **vydání** konfigurace.

- **Typ shaderu**

   Určuje typ shaderu. Různé druhy shadery implementace různých součástí zřetězení grafiky. Některé typy shaderů jsou k dispozici jenom v novější modely shaderů (které je určené vlastností **Shader Model** vlastnost) – například výpočetní shadery byly zavedeny v model shaderu 5.

   Tato vlastnost odpovídá  **\[typ]** část **/T \[typ] _\[modelu]** argument příkazového řádku pro kompilátor HLSL. **Modely shaderů** vlastnost určuje, **[model]** část argumentu.

- **Model shaderu**

   Určuje model shaderu. Shader různé modely mají různé možnosti. Obecně platí více modely shaderů nabízí rozšířené možnosti, ale i Modernější hardwarovou akceleraci ke spouštění kódu shaderu. Některé typy shaderů (které je určené vlastností **typ shaderu** vlastnosti) jsou k dispozici jenom v novější modely shaderů – například výpočetní shadery byly zavedeny v model shaderu 5.

   Tato vlastnost odpovídá  **\[modelu]** část **/T \[typ] _\[modelu]** argument příkazového řádku pro kompilátor HLSL. **Typ shaderu** určuje vlastnost **[typ]** část argumentu.

- **Definice preprocesoru**

   Přidá jednu nebo víc definic preprocesoru symbol má použít pro HLSL souboru se zdrojovým kódem. K oddělení definice symbolů použijte středníky.

   Tato vlastnost odpovídá **/D \[definice]** argument příkazového řádku pro kompilátor HLSL.

## <a name="see-also"></a>Viz také:

[HLSL – stránky vlastností](../ide/hlsl-property-pages.md)<br>
[HLSL – stránky vlastností: Upřesnit](../ide/hlsl-property-pages-advanced.md)<br>
[HLSL – stránky vlastností: Výstupní soubory](../ide/hlsl-property-pages-output-files.md)
