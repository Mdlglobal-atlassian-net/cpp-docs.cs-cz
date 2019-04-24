---
title: 'Stránka vlastností kroku vlastního sestavení: Obecné'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: 329923140cf5a8f05e5c032ddb9e25c0ea45ec2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273076"
---
# <a name="custom-build-step-property-page-general"></a>Stránka vlastností kroku vlastního sestavení: Obecné

Pro každou kombinaci konfigurace projektu a cílové platformy v projektu můžete zadat vlastní krok, který se má provést při sestavení projektu.

Verzi Linuxu na této stránce, najdete v části [vlastní krok vlastnosti sestavení (Linux C++)](../../linux/prop-pages/custom-build-step-linux.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Příkazový řádek**

   Příkaz, který má vlastní krok sestavení provést.

- **Popis**

   Zpráva, která se zobrazí při spuštění vlastního kroku sestavení

- **Výstupy**

   Výstupní soubor, který je vygenerován vlastním krokem sestavení. Toto nastavení je povinné, aby přírůstkové sestavení fungovalo správně.

- **Další závislosti**

   Seznam případných dalších vstupních souborů, které se mají použít ve vlastním kroku sestavení, oddělených středníkem.

- **Po spuštění a provést před**

   Tyto volby definují, kdy se vlastní krok v rámci procesu sestavení spustí. Zadávají se ve vztahu k cílům uvedeným v seznamu. Nejčastěji používané cíle jsou BuildGenerateSources, BuildCompile a BuildLink, které představují nejdůležitější kroky v procesu sestavení. Další často používané cíle jsou Midl, CLCompile a Link.

- **Považovat výstup za obsah**

   Tato možnost je jenom pro aplikace univerzální platformy Windows nebo Windows Phone, které zahrnují všechny soubory obsahu v balíčku .appx smysluplné.

### <a name="to-specify-a-custom-build-step"></a>Zadání vlastního kroku sestavení

1. V panelu nabídky zvolte **projektu**, **vlastnosti**. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V **stránky vlastností** dialogové okno, přejděte na **vlastnosti konfigurace**, **vlastní krok sestavení**, **Obecné** stránky.

1. Podle potřeby upravte nastavení.

## <a name="see-also"></a>Viz také:

[Odkaz na stránku vlastností projektu jazyka C++](property-pages-visual-cpp.md)
