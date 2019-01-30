---
title: Výběr ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.author: Michael.Blome
ms.topic: tutorial
ms.service: cpp
author: mikeblome
ms.openlocfilehash: 008c99ae4b2cba5ff8f8b9ab069bb1b8085b7524
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293634"
---
# <a name="selecting-controls"></a>Výběr ovládacích prvků

Vyberte ovládací prvky na velikost, zarovnání, přesunutí, kopírování, nebo je odstranit a dokončete operaci, kterou chcete. Ve většině případů je třeba vybrat více než jeden ovládací prvek při použití nástroje pro velikost a zarovnání na [nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Při výběru ovládacího prvku, má šedé ohraničení kolem něj plný (aktivní) nebo prázdný (neaktivní) "úchyty," squares malý, který se zobrazí v ohraničení výběru. Když vyberete více ovládacích prvků, dominantního ovládacího prvku má solid úchyty a všechny ostatní vybrané ovládací prvky mají prázdný úchyty.

Při nastavování velikosti nebo zarovnání více ovládacích prvků **dialogové okno** editor používá "dominantního ovládacího prvku" zjistit, jak se ostatní ovládací prvky velikosti nebo zarovnána. Ve výchozím nastavení dominantní ovládací prvek je první ovládací prvek.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-controls"></a>Výběr více ovládacích prvků

1. V [okno nástrojů](/visualstudio/ide/reference/toolbox), vyberte **ukazatel** nástroj.

1. Tažením nakreslete rámeček výběru okolo ovládací prvky, které chcete vybrat ve vašem dialogovém okně.

   Když uvolníte tlačítko myši, všechny řídí uvnitř a protínající se operátory jsou vybrané pole výběru.

   \- nebo –

   Podržte stisknutou klávesu **Shift** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

   \- nebo –

   Podržte stisknutou klávesu **Ctrl** klíče a vyberte ovládací prvky, které chcete zahrnout do výběru.

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Odebrat ovládací prvek ze skupiny z vybraných ovládacích prvků nebo přidání ovládacího prvku na skupinu vybraných ovládacích prvků

1. Se skupinou vybraných ovládacích prvků, podržte stisknutou klávesu **Shift** klíče a vyberte ovládací prvek, který chcete odstranit nebo přidat do existujícího výběru.

   > [!NOTE]
   > Podržení **Ctrl** klíč a výběru ovládacího prvku Výběr způsobí, že, které řídí dominantního ovládacího prvku v tomto výběru.

## <a name="to-specify-the-dominant-control"></a>K určení dominantního ovládacího prvku

1. Podržte stisknutou klávesu **Ctrl** key a klikněte na ovládací prvek, který chcete použít k ovlivnění velikosti či umístění jiných ovládacích prvků *první*.

> [!NOTE]
> Úchyty dominantního ovládacího prvku jsou pořádné popisovače podřízených ovládacích prvků, které jsou prázdné. Všechny další změny velikosti nebo zarovnání podle dominantního ovládacího prvku.

## <a name="to-change-the-dominant-control"></a>Chcete-li změnit dominantního ovládacího prvku

1. Zrušte aktuální výběr kliknutím mimo všechny aktuálně vybrané ovládací prvky.

1. Opakujte předchozí postup nejprve výběr jiného ovládacího prvku.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)