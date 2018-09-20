---
title: Převádění bitmap na panely nástrojů (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03b12e22adafcbca37910ea556ab9c8a33f9e4d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444863"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>Převádění bitmap na panely nástrojů (C++)

Můžete vytvořit nový panel nástrojů v projektu jazyka C++ převedením rastrový obrázek. Obrázek z rastrového obrázku se převede na obrázky tlačítek pro panel nástrojů. Obvykle rastrový obrázek obsahuje několik imagí tlačítko v jediné bitmapě pomocí jedné image pro každé tlačítko. Image může mít libovolnou velikost; Výchozí hodnota je 16 pixelů na šířku a výšku obrázku. Můžete zadat velikost obrázky tlačítek v [nový prostředek panelu nástrojů – dialogové okno](../windows/new-toolbar-resource-dialog-box.md) při výběru **panelu nástrojů editoru** z **Image** nabídky v editoru obrázků.

### <a name="to-convert-bitmaps-to-a-toolbar"></a>Převod bitmap na panelu nástrojů

1. Otevřete existující prostředek rastrového obrázku v [editor obrázků](../windows/image-editor-for-icons.md). (Pokud rastrového obrázku není v souboru .rc, klikněte pravým tlačítkem na soubor .rc, zvolte **Import** z místní nabídky, přejděte na rastrový obrázek, které chcete přidat do souboru .rc a potom klikněte na **otevřít**.)

2. Z **Image** nabídce zvolte **panelu nástrojů editoru**.

   [Nový prostředek panelu nástrojů – dialogové okno](../windows/new-toolbar-resource-dialog-box.md) se zobrazí. Můžete změnit šířku a výšku obrázky ikon tak, aby odpovídaly rastrového obrázku. Obrázek panelu nástrojů se následně zobrazí v editoru panelu nástrojů.

3. K dokončení převodu, změňte příkaz **ID** pomocí tlačítka [okno vlastností](/visualstudio/ide/reference/properties-window). Zadejte nový **ID** nebo vyberte **ID** z rozevíracího seznamu.

   > [!TIP]
   > **Vlastnosti** okno obsahuje tlačítko připínáčku v záhlaví programu. Kliknutím na toto tlačítko povolí nebo zakáže **automaticky skrýt** okna. Rychle procházet všechny vlastnosti tlačítka panelu nástrojů bez nutnosti znovu otevřít windows jednotlivých vlastností, zapněte **automaticky skrýt** vypnout proto **vlastnosti** okno zůstane bez pohybu.

Identifikátory příkazů tlačítka na nový panel nástrojů můžete také změnit pomocí [okno vlastností](/visualstudio/ide/reference/properties-window). Informace o úpravách nový panel nástrojů najdete v tématu [vytváření, přesouvání a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Vytváření nových panelů nástrojů](../windows/creating-new-toolbars.md)<br/>
[Editor panelu nástrojů](../windows/toolbar-editor.md)