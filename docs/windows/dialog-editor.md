---
title: "Editor dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs: C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e520fb524cd25709b9d03ae992305a4fac41763
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dialog-editor"></a>Editor dialogových oken
Editor dialogového okna umožňuje vytváření nebo úpravu prostředků dialogových oken. Otevřete dialogové okno editor poklikáním na soubor .rc dialog s v okně zobrazení prostředků (**zobrazení &#124; Zobrazení prostředků**). Zobrazení prostředků není k dispozici ve verzích Express.  
  
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
  
-   [Přidání obslužných rutin událostí pro ovládací prvky dialogové okno](../windows/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [Testování dialogového okna](../windows/testing-a-dialog-box.md)  
  
-   [Klávesy akcelerátoru pro Editor dialogových oken](../windows/accelerator-keys-for-the-dialog-editor.md)  
  
-   [Řešení potíží s editoru dialogových oken](../windows/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  Při použití editoru dialogového okna lze v mnoha případech po kliknutí pravým tlačítkem myši zobrazit místní nabídku s často používanými příkazy.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)   
 [Třídy ovládacích prvků](../mfc/control-classes.md)   
 [Třídy dialogových oken](../mfc/dialog-box-classes.md)   
 [Ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)

