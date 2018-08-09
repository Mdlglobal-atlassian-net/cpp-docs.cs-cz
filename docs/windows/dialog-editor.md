---
title: Editor dialogových oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c2f5339237bec053df6bf26fb161854f83f572a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651847"
---
# <a name="dialog-editor"></a>Editor dialogových oken
**Dialogové okno** editor umožňuje vytvoření nebo úpravu prostředků dialogových oken. Otevřete editor dialogového okna poklikáním na soubor .rc dialogu v **zobrazení prostředků** okno (**zobrazení** > **zobrazení prostředků**). Všimněte si, že **zobrazení prostředků** není k dispozici ve verzích Express.  
  
 Jedním z prvních kroků při vytváření nového dialogového okna (nebo šablony dialogového okna) je přidání ovládacích prvků dialogového okna. V **dialogové okno** editor, je možné uspořádat ovládací prvky podle určité velikosti, tvaru nebo zarovnání, nebo je můžete přesouvat přibližně pro práci v dialogovém okně. Rovněž lze ovládací prvky snadno odstranit.  
  
 Dialogové okno lze uložit jako šablonu, takže je možné jej znovu použít. Rovněž lze snadno přepínat mezi návrhem dialogového okna a editací kódu, který jej implementuje.  
  
 V Editoru dialogového okna je rovněž možné upravovat vlastnosti jednoho nebo více ovládacích prvků. Můžete změnit pořadí ovládacích prvků, to znamená, když pořadí, ve kterém ovládací prvky získávají zaměřit **kartu** stisknutí klávesy, nebo lze definovat přístupovou klávesu (kombinaci kláves), který umožňuje uživatelům vybrat ovládací prvek pomocí klávesnice. Seznam přednastavených přístupových kláves naleznete v tématu [klávesy akcelerátoru pro Editor dialogového okna](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 **Dialogové okno** editor také umožňuje použití vlastních ovládacích prvků, včetně ovládacích prvků ActiveX. Kromě toho můžete upravit [zobrazení formuláře](../mfc/reference/cformview-class.md), [zobrazení záznamů](../data/record-views-mfc-data-access.md), nebo [dialogové pruhy](../mfc/dialog-bars.md).  
  
 Od verze Visual Studio 2015, můžete použít editor dialogového okna pro definování dynamického rozložení, které určují, jak ovládací prvky přesunutí a změna velikosti, když uživatel změní dialogové okno. Další informace najdete v tématu [dynamické rozložení](../mfc/dynamic-layout.md).  
  
-   [Vytvoření nového dialogového okna](../windows/creating-a-new-dialog-box.md)  
  
-   [Vytvoření dialogového okna, které uživatelé nemohou zavřít. za běhu](../windows/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [Přepínání mezi editorem dialogových oken a kódem](../windows/switching-between-dialog-box-controls-and-code.md)  
  
-   [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
  
-   [Přidání obslužných rutin události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [Testování dialogového okna](../windows/testing-a-dialog-box.md)  
  
-   [Klávesy akcelerátoru pro editor dialogového okna](../windows/accelerator-keys-for-the-dialog-editor.md)  
  
-   [Řešení potíží s editorem dialogového okna](../windows/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  Při použití **dialogové okno** editoru v mnoha případech můžete kliknutím na tlačítko pravým tlačítkem myši zobrazit místní nabídku s často používanými příkazy.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)   
 [Třídy ovládacích prvků](../mfc/control-classes.md)   
 [Třídy dialogových oken](../mfc/dialog-box-classes.md)   
 [Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)