---
title: 'Hlsl – stránky vlastností: Výstupní soubory'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
ms.openlocfilehash: 746781142d9989910f526c85b38516e8d5302ada
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739492"
---
# <a name="hlsl-property-pages-output-files"></a>Hlsl – stránky vlastností: Výstupní soubory

Pokud chcete konfigurovat následující vlastnosti kompilátor HLSL (fxc.exe), použijte jeho **výstupní soubory** vlastnost. Informace o tom, jak získat přístup **výstupní soubory** zobrazit stránku vlastností ve složce HLSL [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Název proměnné v hlavičce**

   Určuje název pole, které se používá k kódovaného HLSL objektový kód. Pole je obsažen v záhlaví souboru, který je výstup kompilátoru HLSL. Název souboru hlaviček **název hlavičkového souboru** vlastnost.

Tato vlastnost odpovídá **/Vn [název]** argument příkazového řádku.

- **Název hlavičkového souboru**

   Určuje název souboru hlaviček, který je výstup kompilátoru HLSL. Záhlaví obsahuje HLSL objektový kód, který je zakódován do pole. Název pole je zadán **název proměnné v hlavičce** vlastnost.

Tato vlastnost odpovídá **/Fh [název]** argument příkazového řádku.

- **Název souboru objektů**

   Určuje název souboru objektu, který je výstup kompilátoru HLSL. Výchozí hodnota je **$(OutDir) % (název souboru) .cso**.

Tato vlastnost odpovídá **/Fo [název]** argument příkazového řádku.

- **Výstup assembleru**

   **Výpis pouze sestavení (/ Fc)** výstup jenom příkazy jazyka assembleru. **Kód sestavení a hexadecimální hodnoty (/ Fx)** do výstupního sestavení jazyka DDL a odpovídající operační kód v šestnáctkové soustavě. Bez výpisu je výstup standardně.

- **Výstupní soubor assembleru**

   Určuje název souboru výpisu sestavení, který je výstup kompilátoru HLSL.

   Tato vlastnost odpovídá **/Fc [název]** a **/Fx [název]** argumenty příkazového řádku.

## <a name="see-also"></a>Viz také:

[HLSL – stránky vlastností](../ide/hlsl-property-pages.md)<br>
[HLSL – stránky vlastností: Obecné](../ide/hlsl-property-pages-general.md)<br>
[HLSL – stránky vlastností: Upřesnit](../ide/hlsl-property-pages-advanced.md)
