---
title: Odkaz C++ na stránku vlastností projektu Windows – Visual Studio
ms.date: 08/28/2019
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: c9fd4fc00e86e0660972fc0bd37b66b2fea02ee0
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177458"
---
# <a name="windows-c-project-property-page-reference"></a>Odkaz C++ na stránku vlastností projektu Windows

V aplikaci Visual Studio určíte možnosti kompilátoru a linkeru, cesty k souborům a další nastavení sestavení pomocí stránek vlastností projektu. Stránky vlastností a vlastností, které jsou k dispozici, závisí na typu projektu. Například projekt makefile má stránku vlastností NMake, která není přítomna v projektu konzoly MFC nebo Win32. Chcete-li **otevřít stránky vlastností**, v hlavní nabídce vyberte možnost**vlastnosti** **projektu** > , nebo klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**. Jednotlivé soubory mají také stránky vlastností, které umožňují nastavit možnosti kompilace a sestavení pouze pro tento soubor. Následující obrázek znázorňuje stránky vlastností projektu MFC.

![Stránky vlastností pro C++ projekt](media/example-prop-page.png)

V této části najdete stručný přehled stránek vlastností samotných. Možnosti a nastavení, které jsou zpřístupněny na stránkách vlastností, jsou podrobněji zdokumentovány v jejich vlastních tématech a jsou propojeny z témat stránky vlastností. Další informace o vlastnostech projektu naleznete v tématu [nastavení C++ kompilátoru a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

Stránky vlastností v projektech pro Linux najdete v [tématu C++ reference na stránku vlastností Linux](../../linux/prop-pages-linux.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Obecná stránka vlastností (projekt)](general-property-page-project.md)
- [Obecná stránka vlastností (soubor)](general-property-page-file.md)
- [Upřesnit stránku vlastností](advanced-property-page.md)
- [Stránka vlastností adresářů VC++](vcpp-directories-property-page.md)
- [Stránky vlastností linkeru](linker-property-pages.md)
- [Stránky vlastností nástroje manifest](manifest-tool-property-pages.md)
- [HLSL – stránky vlastností](hlsl-property-pages.md)
- [Stránky vlastností příkazového řádku](command-line-property-pages.md)
- [Stránka vlastností vlastního kroku sestavení: Obecné](custom-build-step-property-page-general.md)
- [Přidávání odkazů](../adding-references-in-visual-cpp-projects.md)
- [Stránka vlastností spravovaných prostředků](managed-resources-property-page.md)
- [MIDL – stránky vlastností](midl-property-pages.md)
- [NMake – stránka vlastností](nmake-property-page.md)
- [Stránky vlastností prostředků](resources-property-pages.md)
- [Stránka vlastností webových odkazů](web-references-property-page.md)
- [Stránka vlastností nástroje Generátor dat XML](xml-data-generator-tool-property-page.md)
- [Stránky vlastností nástroje Generátor dokumentů XML](xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Viz také:

[Postupy: Vytváření a odebírání závislostí projektu](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br/>
[Postupy: Vytvoření a úprava konfigurací](/visualstudio/ide/how-to-create-and-edit-configurations)<br/>
[Odkaz C++ na stránku vlastností platformy Linux](../../linux/prop-pages-linux.md)
