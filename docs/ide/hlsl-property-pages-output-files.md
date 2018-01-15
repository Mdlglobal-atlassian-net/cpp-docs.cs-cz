---
title: "HLSL – stránky vlastností: Výstupní soubory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs: C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04f6ad8889c9a713b3b64284b329c21d5a2cd49e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-output-files"></a>HLSL – stránky vlastností: Output Files
Chcete-li nakonfigurovat následující vlastnosti kompilátoru HLSL (fxc.exe), použijte jeho **výstupní soubory** vlastnost. Informace o tom, jak získat přístup **výstupní soubory** najdete v části stránky vlastností ve složce HLSL [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Název proměnné záhlaví**  
 Určuje název pole, které se používá k kódovaného kód HLSL objektu. Toto pole je obsažený v záhlaví souboru, který je výstup v kompilátoru HLSL. Název záhlaví souboru je zadán **název hlavičky souboru** vlastnost.  
  
 Tato vlastnost odpovídá **/Vn [name]** argument příkazového řádku.  
  
 **Název hlavičky souboru**  
 Určuje název soubor hlaviček, který je výstup kompilátorem HLSL. Záhlaví obsahuje kód HLSL objektu, který je zakódován do pole. Název pole je zadán **název proměnné záhlaví** vlastnost.  
  
 Tato vlastnost odpovídá **/Fh [name]** argument příkazového řádku.  
  
 **Název souboru objektů**  
 Určuje název objektu souboru, který je výstup kompilátorem HLSL. Výchozí hodnota je **.cso % (název souboru) $(OutDir)**.  
  
 Tato vlastnost odpovídá **/Fo [name]** argument příkazového řádku.  
  
 **Výstup assembleru**  
 **Výpis pouze sestavení (nebo Fc)** výstup jenom příkazy jazyka sestavení. **Kódu sestavení a Hex (nebo Fx)** do výstupního sestavení jazyka DDL a odpovídající operační kód v šestnáctkové soustavě. Ve výchozím nastavení je žádné výpis výstupu.  
  
 **Výstupní soubor assembleru**  
 Určuje název souboru sestavení seznamu, který je výstup kompilátorem HLSL.  
  
 Tato vlastnost odpovídá **/Fc [name]** a **/Fx [name]** argumenty příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [HLSL – stránky vlastností](../ide/hlsl-property-pages.md)   
 [HLSL – stránky vlastností: Obecné](../ide/hlsl-property-pages-general.md)   
 [HLSL – stránky vlastností: Upřesnit](../ide/hlsl-property-pages-advanced.md)