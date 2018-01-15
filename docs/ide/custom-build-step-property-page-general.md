---
title: "Stránka vlastností vlastního sestavení krok: Obecná | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
dev_langs: C++
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63e599a2a24716de2de3e23cb3a7c2342b036b81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="custom-build-step-property-page-general"></a>Stránka vlastností vlastního kroku sestavení: Obecné
Pro každou kombinaci konfigurace projektu a cílové platformy v projektu můžete zadat vlastní krok, který se má provést při sestavení projektu.  

Linux verzi této stránce, naleznete v části [vlastní sestavení krok vlastnosti (Linux C++)](../linux/prop-pages/custom-build-step-linux.md).
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Příkazový řádek**  
 Příkaz, který má vlastní krok sestavení provést.  
  
 **Popis**  
 Zpráva, která se zobrazí při spuštění vlastního kroku sestavení  
  
 **Výstupy**  
 Výstupní soubor, který je vygenerován vlastním krokem sestavení. Toto nastavení je povinné, aby přírůstkové sestavení fungovalo správně.  
  
 **Další závislosti**  
 Seznam případných dalších vstupních souborů, které se mají použít ve vlastním kroku sestavení, oddělených středníkem.  
  
 **Po spuštění a provést před**  
 Tyto volby definují, kdy se vlastní krok v rámci procesu sestavení spustí. Zadávají se ve vztahu k cílům uvedeným v seznamu. Nejčastěji používané cíle jsou BuildGenerateSources, BuildCompile a BuildLink, které představují nejdůležitější kroky v procesu sestavení. Další často používané cíle jsou Midl, CLCompile a Link.  
  
 Považovat výstup za obsah  
 Tato možnost má smysl pouze v aplikacích pro Windows Store nebo Windows Phone, které v balíčku .appx zahrnují všechny obsahové soubory.  
  
### <a name="to-specify-a-custom-build-step"></a>Zadání vlastního kroku sestavení  
  
1.  Na řádku nabídek zvolte **projektu**, **vlastnosti**. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
2.  V **stránky vlastností** dialogové okno pole, přejděte **vlastnosti konfigurace**, **vlastní krok sestavení**, **Obecné** stránky.  
  
3.  Podle potřeby upravte nastavení.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)