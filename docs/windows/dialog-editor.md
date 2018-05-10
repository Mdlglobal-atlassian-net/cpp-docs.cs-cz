---
title: Editor dialogových oken | Microsoft Docs
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
ms.openlocfilehash: 7b8cb99b2002dab3fb04ffa8c5b117a49d23adc1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="dialog-editor"></a>Editor dialogových oken
Editor dialogového okna umožňuje vytváření nebo úpravu prostředků dialogových oken. Otevřete dialogové okno editor poklikáním na soubor .rc dialog s v okně zobrazení prostředků (**zobrazení &#124; zobrazení prostředků**). Zobrazení prostředků není k dispozici ve verzích Express.  
  
 Jedním z prvních kroků při vytváření nového dialogového okna (nebo šablony dialogového okna) je přidání ovládacích prvků dialogového okna. V Editoru dialogového okna lze pro práci v dialogovém okně uspořádat ovládací prvky tak, aby odpovídaly určité velikosti, tvaru nebo zarovnání, nebo je lze přetáhnout. Rovněž lze ovládací prvky snadno odstranit.  
  
 Dialogové okno lze uložit jako šablonu, takže je možné jej znovu použít. Rovněž lze snadno přepínat mezi návrhem dialogového okna a editací kódu, který jej implementuje.  
  
 V Editoru dialogového okna je rovněž možné upravovat vlastnosti jednoho nebo více ovládacích prvků. Rovněž lze změnit pořadí ovládacích prvků, to znamená pořadí, ve kterém ovládací prvky získávají fokus po stisknutí klávesy TAB, nebo lze definovat přístupovou klávesu (kombinaci kláves), která umožní uživatelům vybrat ovládací prvek pomocí klávesnice. Seznam přednastavených přístupových klíčů najdete v tématu [klávesy akcelerátoru pro Editor dialogových oken](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Editor dialogového okna rovněž umožňuje použití vlastních ovládacích prvků, včetně ovládacích prvků ActiveX. Kromě toho můžete upravit [zobrazení formuláře](../mfc/reference/cformview-class.md), [zobrazení záznamů](../data/record-views-mfc-data-access.md), nebo [dialogové pruhy](../mfc/dialog-bars.md).  
  
 Od verze sady Visual Studio 2015, můžete pomocí editoru dialogových oken k definování dynamické rozložení, které určují, jak přesunout ovládací prvky a velikost, pokud uživatel změní velikost dialogové okno. Další informace najdete v tématu [dynamické rozložení](../mfc/dynamic-layout.md).  
  
-   [Vytvoření nového dialogového okna](../windows/creating-a-new-dialog-box.md)  
  
-   [Vytváření dialogu, který uživatelé nemohou zavřít. v době běhu](../windows/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [Přepínání mezi editoru dialogového okna a kódem](../windows/switching-between-dialog-box-controls-and-code.md)  
  
-   [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
  
-   [Přidání obslužných rutin události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [Testování dialogového okna](../windows/testing-a-dialog-box.md)  
  
-   [Klávesy akcelerátoru pro editor dialogového okna](../windows/accelerator-keys-for-the-dialog-editor.md)  
  
-   [Řešení potíží s editorem dialogového okna](../windows/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  Při použití editoru dialogového okna lze v mnoha případech po kliknutí pravým tlačítkem myši zobrazit místní nabídku s často používanými příkazy.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [ovládací prvky](../mfc/controls-mfc.md)   
 [Třídy ovládacích prvků](../mfc/control-classes.md)   
 [Třídy dialogových oken](../mfc/dialog-box-classes.md)   
 [Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)

