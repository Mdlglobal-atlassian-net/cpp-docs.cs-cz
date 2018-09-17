---
title: 'Stránka vlastností kroku vlastního sestavení: Obecná | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
dev_langs:
- C++
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df655f06d3b6d6b2b7b36f83f7c109adce758fef
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721991"
---
# <a name="custom-build-step-property-page-general"></a>Stránka vlastností vlastního kroku sestavení: Obecné
Pro každou kombinaci konfigurace projektu a cílové platformy v projektu můžete zadat vlastní krok, který se má provést při sestavení projektu.  

Verzi Linuxu na této stránce, najdete v části [vlastní krok vlastnosti sestavení (Linux C++)](../linux/prop-pages/custom-build-step-linux.md).
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
- **Příkazový řádek**

   Příkaz, který má vlastní krok sestavení provést.  
  
- **Popis**

   Zpráva, která se zobrazí při spuštění vlastního kroku sestavení  
  
- **výstupy**

   Výstupní soubor, který je vygenerován vlastním krokem sestavení. Toto nastavení je povinné, aby přírůstkové sestavení fungovalo správně.  
  
- **Další závislosti**

   Seznam případných dalších vstupních souborů, které se mají použít ve vlastním kroku sestavení, oddělených středníkem.  
  
- **Po spuštění a provést před**

   Tyto volby definují, kdy se vlastní krok v rámci procesu sestavení spustí. Zadávají se ve vztahu k cílům uvedeným v seznamu. Nejčastěji používané cíle jsou BuildGenerateSources, BuildCompile a BuildLink, které představují nejdůležitější kroky v procesu sestavení. Další často používané cíle jsou Midl, CLCompile a Link.  
  
- **Považovat výstup za obsah**

   Tato možnost je jenom pro aplikace univerzální platformy Windows nebo Windows Phone, které zahrnují všechny soubory obsahu v balíčku .appx smysluplné.  
  
### <a name="to-specify-a-custom-build-step"></a>Zadání vlastního kroku sestavení  
  
1.  V panelu nabídky zvolte **projektu**, **vlastnosti**. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
2.  V **stránky vlastností** dialogové okno, přejděte na **vlastnosti konfigurace**, **vlastní krok sestavení**, **Obecné** stránky.  
  
3.  Podle potřeby upravte nastavení.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)