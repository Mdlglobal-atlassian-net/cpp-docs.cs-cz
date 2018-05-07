---
title: Deklarace proměnné založené na nové třídě ovládacího prvku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 677006d441c940f478b3d23744d1057667307e1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarace proměnné založené na nové třídě ovládacího prvku
Po vytvoření třídy knihovny MFC ovládací prvek, je možné deklarovat proměnné založené na něm. Zajistit kontextu pro nové proměnné musí otevřete editor dialogových oken a dialogových oken, ve které chcete použít vlastní opakovaně použitelné ovládací prvek upravit. Dialogové okno navíc musíte už mít třídu s ním spojená. Informace o použití editoru dialogových oken najdete v tématu [editoru dialogového okna](../../windows/dialog-editor.md).  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Deklarace proměnné založené na třídě opakovaně použitelné  
  
1.  Při úpravách dialogových oken, přetáhněte ovládací prvek stejného typu jako základní třída nový ovládací prvek z panelu ovládacích prvků na dialogové okno.  
  
2.  Umístěte ukazatel myši nad vynechaných ovládacího prvku.  
  
3.  Stiskněte klávesu CTRL a dvakrát klikněte na ovládací prvek.  
  
     [Přidat proměnnou člen](../../ide/add-member-variable-wizard.md) zobrazí se dialogové okno.  
  
4.  V **přístup** vyberte správný přístup pro ovládací prvek.  
  
5.  Klikněte **řídicí proměnná** zaškrtávací políčko.  
  
6.  V **název proměnné** pole, zadejte název.  
  
7.  V části **kategorie**, klikněte na tlačítko **řízení**.  
  
8.  V **ID ovládacího prvku** seznamu, vyberte ovládací prvek, který jste přidali. **Typ proměnné** seznam by měl zobrazit správný typ proměnné a **řízení typu** by měl zobrazovat typ správné ovládacího prvku.  
  
9. V **komentář** pole, jakýkoliv komentář, který se má zobrazit v kódu.  
  
10. Click **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Mapování zpráv do funkcí](../../mfc/reference/mapping-messages-to-functions.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
