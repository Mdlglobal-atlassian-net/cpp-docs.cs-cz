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
ms.openlocfilehash: 6ee8042fccf2e0b635535a77d9c9a6bc68bd9999
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291545"
---
# <a name="hlsl-property-pages-output-files"></a>Hlsl – stránky vlastností: Výstupní soubory

Pokud chcete konfigurovat následující vlastnosti kompilátor HLSL (fxc.exe), použijte jeho **výstupní soubory** vlastnost. Informace o tom, jak získat přístup k **výstupní soubory** zobrazit stránku vlastností ve složce HLSL [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

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

[HLSL – stránky vlastností](hlsl-property-pages.md)<br>
[HLSL – stránky vlastností: Obecné](hlsl-property-pages-general.md)<br>
[HLSL – stránky vlastností: Upřesnit](hlsl-property-pages-advanced.md)
