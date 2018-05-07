---
title: Přidání členské proměnné (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2a8ef8f7bcdc2d90893acdad98705c9588a5d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="adding-a-member-variable--visual-c"></a>Přidání členské proměnné (Visual C++)
Členské proměnné můžete přidat do třídy pomocí zobrazení tříd. Členské proměnné může být buď pro [výměny dat a ověření dat](../mfc/dialog-data-exchange-and-validation.md), nebo mohou být obecné. Průvodce data členské proměnné je určená speciálně pro trvat příslušné informace a použít ho k vložení elementy ve zdrojových souborech na vhodného umístění. Přidáním členské proměnné z [editoru dialogového okna](../windows/dialog-editor.md) v [zobrazení prostředků](../windows/resource-view-window.md), nebo z [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Když navrhujete a implementujete dialogové okno, může pro vás efektivnější dialogovém okně editor k přidávání ovládacích prvků pole dialogové okno a potom implementovat ovládací prvky členské proměnné.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Přidání členské proměnné pro ovládací prvek dialogového okna v zobrazení zdrojů pomocí Průvodce přidáním členské proměnné  
  
1.  V zobrazení zdrojů rozbalte uzel projektu a dialogové okno uzel k zobrazení seznamu dialogová okna projektu.  
  
2.  Dvakrát klikněte na dialogových oken, do které chcete přidat členské proměnné a otevře se v editoru dialogových oken.  
  
3.  V dialogovém okně zobrazí v editoru dialogového okna klikněte pravým tlačítkem na ovládací prvek, ke které chcete přidat členské proměnné.  
  
4.  V místní nabídce klikněte na tlačítko **přidat proměnnou** zobrazíte [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Výchozí hodnota je již součástí **ID ovládacího prvku**.  
  
5.  Zadejte informace do polí příslušné průvodce. V tématu [ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.  
  
6.  Klikněte na tlačítko **Dokončit** přidejte definice a implementaci kódu do projektu a zavřete průvodce.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Přidání členské proměnné ze zobrazení tříd pomocí Průvodce přidáním členské proměnné  
  
1.  V [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), rozbalte uzel projektu pro zobrazení třídy v projektu.  
  
2.  Klikněte pravým tlačítkem na třídu, ke které chcete přidat proměnnou.  
  
3.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat proměnnou** zobrazíte Průvodce přidáním členské proměnné.  
  
4.  Zadejte informace do polí příslušné průvodce. V tématu [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) podrobnosti.  
  
5.  Klikněte na tlačítko **Dokončit** přidejte definice a implementaci kódu do projektu a zavřete průvodce.  
  
## <a name="see-also"></a>Viz také  
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)