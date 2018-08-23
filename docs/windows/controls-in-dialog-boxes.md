---
title: Ovládací prvky v dialogových oknech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls, about dialog box controls
- dialog box controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70e3bcfb644893f1dc8b41b9c11a3aee5c92103d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591955"
---
# <a name="controls-in-dialog-boxes"></a>Ovládací prvky v dialogových oknech

Do pole pomocí dialogového okna můžete přidat ovládací prvky [karta editoru dialogového okna](../windows/dialog-editor-tab-toolbox.md) v [okno nástrojů](/visualstudio/ide/reference/toolbox), což vám umožní vybrat ovládací prvek a přetáhněte ji do dialogových oken. Ve výchozím nastavení okno panelu nástrojů je nastavena na automatické skrývání. Se zobrazí jako karty na levý okraj vašeho řešení při otevření editoru dialogového okna. Ale můžete připnout **nástrojů** okno do pozice po kliknutí **automaticky skrýt** tlačítko v pravém horním rohu okna. Další informace o tom, jak řídit chování tohoto okna najdete v tématu [okno Správa](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Nejrychlejší způsob, jak přidat ovládací prvky do dialogového okna, umístění existujících ovládacích prvků nebo přesunutí ovládacích prvků z jednoho dialogového okna do jiného, je použít metodu přetahování myší. Umístění ovládacího prvku je popsaný v tečkovaná čára, dokud je přetáhnout do dialogových oken. Při přidání ovládacího prvku do dialogového okna s metodou přetažení myší, ovládací prvek dostane standardní výšku vhodné pro tento typ ovládacího prvku.

Při přidání ovládacího prvku do dialogového okna nebo jiného umístění, jeho konečné umístění může být stanoveno pomocí vodítek a okrajů, nebo zda je třeba rozložení mřížky zapnuté.

Po přidání ovládacího prvku do dialogového okna, můžete změnit vlastnosti, jako je titulek v [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete vybrat více ovládacích prvků a změňte jejich vlastnosti všechny najednou.

- [Přidání, úprava nebo odstranění ovládacích prvků](adding-editing-or-deleting-controls.md)

- [Výběr ovládacích prvků](../windows/selecting-controls.md)

- [Změna velikosti jednotlivých ovládacích prvků](../windows/sizing-individual-controls.md)

- [Nastavení stejné šířky, výšky nebo velikosti ovládacích prvků](../windows/making-controls-the-same-width-height-or-size.md)

- [Nastavení velikosti pole se seznamem a jeho rozevíracího seznamu](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [Přidání hodnot do ovládacího prvku pole se seznamem](../windows/adding-values-to-a-combo-box-control.md)

- [Nastavení šířky vodorovného posuvníku](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [Vlastní ovládací prvky v editoru dialogových oken](custom-controls-in-the-dialog-editor.md)

- [Definice klávesových zkratek (přístupové klávesy)](../windows/defining-mnemonics-access-keys.md)

- [Určení umístění a velikosti dialogového okna](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Přidání obslužných rutin události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)  
[Editor dialogových oken](../windows/dialog-editor.md)