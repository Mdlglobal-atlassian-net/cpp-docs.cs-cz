---
title: Uspořádání ovládacích prvků v dialogových oknech (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24c318f6028db1f2c64b2d2d334648fe4d47619f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390783"
---
# <a name="arrangement-of-controls-on-dialog-box-ces"></a>Uspořádání ovládacích prvků v dialogovém okně pole es (C++)

**Dialogové okno** editor poskytuje rozložení nástroje, které Zarovnat a nastavení velikosti ovládacích prvků automaticky. Pro většinu úloh můžete použít [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Všechny **editoru dialogového okna** nástrojů příkazy jsou také k dispozici na **formátu** nabídky a většina mají [klávesových zkratek](../windows/accelerator-keys-for-the-dialog-editor.md).

Mnoho příkazů rozložení pro dialogová okna jsou k dispozici, jenom když vyberete více než jeden ovládací prvek. Můžete vybrat ovládací prvek jednoho nebo více ovládacích prvků a při výběru více než jeden ovládací prvek první z nich, kterou jste vybrali ve výchozím nastavení je "dominantního" ovládacího prvku. Další informace o výběru ovládacích prvků a dominantního ovládacího prvku, naleznete v tématu [ovládací prvky výběru](../windows/selecting-controls.md).

Umístění, výšku a šířku aktuálního ovládacího prvku se zobrazí v pravém dolním rohu stavového řádku. Při výběru celé dialogové stavový řádek zobrazuje pozice dialogových oken jako celek a jeho výška a šířka.

- [Stavy editoru dialogových oken (vodítka a mřížky)](../windows/dialog-editor-states-guides-and-grids.md)

- [Seskupení přepínačů v dialogovém okně](../windows/grouping-radio-buttons-on-a-dialog-box.md)

- [Zarovnání skupin ovládacích prvků](../windows/aligning-groups-of-controls.md)

- [Rovnoměrné nastavení mezer mezi ovládacími prvky](../windows/evening-the-spacing-between-controls.md)

- [Zarovnání ovládacích prvků v dialogovém okně](../windows/centering-controls-in-a-dialog-box.md)

- [Uspořádání tlačítek podél pravé nebo dolní strany dialogového okna](../windows/arranging-push-buttons-along-the-right-or-bottom-of-a-dialog-box.md)

- [Změna pořadí karet ovládacích prvků](../windows/changing-the-tab-order-of-controls.md)

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)