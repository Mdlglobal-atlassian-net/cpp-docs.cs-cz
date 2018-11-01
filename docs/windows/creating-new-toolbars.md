---
title: Vytváření nových panelů nástrojů (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
ms.openlocfilehash: 3c36579560c78ff77a624e4827df9d6a9302ae57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551304"
---
# <a name="creating-new-toolbars-c"></a>Vytváření nových panelů nástrojů (C++)

### <a name="to-create-a-new-toolbar"></a>Chcete-li vytvořit nový panel nástrojů

1. V **prostředků** zobrazení, klikněte pravým tlačítkem na soubor .rc a pak zvolte **přidat prostředek** z místní nabídky. (Pokud máte existující nástrojů v souboru .rc, je můžete jednoduše kliknout pravým tlačítkem **nástrojů** a pak zvolte položku **vložit nástrojů** z místní nabídky.)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V **přidat prostředek** dialogu **nástrojů** v **typ prostředku** seznamu a potom klikněte na **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **nástrojů** typ prostředku, znamená to, že šablony nástrojů jsou k dispozici. Klikněte na znaménko plus rozbalit seznam šablon, vyberte šablonu a klikněte na **nový**.

   \- nebo –

3. [Převod existujícího rastrového obrázku panelu nástrojů](../windows/converting-bitmaps-to-toolbars.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Editor panelu nástrojů](../windows/toolbar-editor.md)