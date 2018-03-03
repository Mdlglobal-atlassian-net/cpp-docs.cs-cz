---
title: "Karta Editor dialogového okna, panel nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls ino dialog boxes
- custom controls [Visual Studio], dialog boxes
- controls [C++], standard
- Dialog editor, creating controls
- controls [C++], adding to dialog boxes
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9db31d6e152be10f2c4934b7b1f239d1e08387f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-editor-tab-toolbox"></a>Karta editoru dialogového okna, panel nástrojů
Karta Editor dialogového okna se zobrazí v [okno sady nástrojů](/visualstudio/ide/reference/toolbox) když pracujete v editoru dialogového okna. Přidání ovládacích prvků do vašeho nové dialogové okno, přetáhněte ovládací prvky z panelu nástrojů na vytváření dialogových oken (Další informace najdete v tématu [přidání ovládacího prvku do dialogového okna](adding-a-control-to-a-dialog-box.md)). Potom můžete pohyb ovládací prvky nebo změnit jejich velikost a tvar.  
  
 Standardní ovládací prvky panelu nástrojů k dispozici jsou:  
  
-   [Tlačítko – ovládací prvek](../mfc/reference/cbutton-class.md)  
  
-   [Ovládací prvek zaškrtávací políčko](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Ovládacího prvku pole se seznamem](../mfc/reference/ccombobox-class.md)  
  
-   [Ovládacích prvků pro úpravy](../mfc/reference/cedit-class.md)  
  
-   Skupinový rámeček  
  
-   [Ovládací prvek seznam](../mfc/reference/clistbox-class.md)  
  
-   [Ovládací prvek přepínač](../mfc/reference/styles-used-by-mfc.md#button-styles)  
  
-   [Statické ovládací prvek Text](../mfc/reference/cstatic-class.md)  
  
-   [Obrázek ovládacího prvku](../mfc/reference/cpictureholder-class.md)  
  
-   [Upravit 2.0 bohaté ovládací prvek](../mfc/using-cricheditctrl.md)  
  
-   [Posuvník](../mfc/reference/cscrollbar-class.md)  
  
 [Běžné ovládací prvky Windows](../mfc/controls-mfc.md) k dispozici v sadě nástrojů poskytují vyšší funkce ve vaší aplikaci. Mezi ně patří:  
  
-   [Posuvník](../mfc/slider-control-styles.md)  
  
-   [Ovládací prvek typu číselník](../mfc/using-cspinbuttonctrl.md)  
  
-   [Ovládací prvek průběh](../mfc/styles-for-the-progress-control.md)  
  
-   [Ovládací prvek aktivního klíč](../mfc/using-a-hot-key-control.md)  
  
-   [Ovládací prvek seznamu](../mfc/list-control-and-list-view.md)  
  
-   [Ovládací prvek stromu](../mfc/tree-control-styles.md)  
  
-   [Ovládací prvek karty](../mfc/tab-controls-and-property-sheets.md)  
  
-   [Ovládacího prvku animace](../mfc/using-an-animation-control.md)  
  
-   [Čas pro výběr data](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [Ovládací prvek měsíční kalendář](../mfc/month-calendar-control-examples.md)  
  
-   [Ovládací prvek adresy IP](../mfc/reference/cipaddressctrl-class.md)  
  
-   [Ovládacího prvku rozšířené pole se seznamem](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [Vlastní ovládací prvek](custom-controls-in-the-dialog-editor.md)  
  
 Do dialogového okna můžete přidat vlastní ovládací prvky výběrem **vlastního ovládacího prvku** ikonu na panelu nástrojů a přetáhnete ji na vašem dialogovém okně. Přidání ovládacího prvku Syslink, přidat vlastní ovládací prvek, pak změňte ovládacího prvku **třída** vlastnost **Syslink**. To způsobí, že vlastnosti, které chcete aktualizovat a zobrazit vlastnosti ovládacích prvků Syslink. Informace o obálkovou třídu knihovny MFC, najdete v části [CLinkCtrl](../mfc/reference/clinkctrl-class.md).  
  
 Můžete také [přidávání ovládacích prvků ActiveX do dialogového okna vaší](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
 Můžete také přizpůsobit okno sady nástrojů pro snadnější použití. Další informace najdete v tématu [pomocí sady nástrojů](/visualstudio/ide/using-the-toolbox).  

 Další informace o používání ovládacího prvku RichEdit 1.0 s MFC najdete v tématu [pomocí ovládacího prvku RichEdit 1.0 s MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../mfc/controls-mfc.md)   
 [Třídy ovládacích prvků](../mfc/control-classes.md)   
 [Třídy dialogových oken](../mfc/dialog-box-classes.md)   
 [Styly posuvníku](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)   
 [Příklady ovládacích prvků pro úpravy s formátováním](../mfc/rich-edit-control-examples.md)   
 [Přidání obslužných rutin událostí pro ovládací prvky dialogové okno](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Ovládací prvky dialogových oken a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)

