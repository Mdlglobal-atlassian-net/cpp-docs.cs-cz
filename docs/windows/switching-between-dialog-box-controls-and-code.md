---
title: "Přepínání mezi ovládacími prvky dialogové okno a kódu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog editor, accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog editor, switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 831b8ca3eddec1bfd13d166d98454206bfac1bfb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="switching-between-dialog-box-controls-and-code"></a>Přepínání mezi ovládacími prvky a kódem dialogového okna
V aplikacích MFC dvojitým kliknutím na dialogové okno Ovládací prvky na jejich kód obslužné rutiny nebo rychle vytvořit se zakázaným inzerováním funkce obslužných rutin.  
  
 Ovládací prvek, klikněte na tlačítko **ControlEvents** tlačítko nebo **zprávy** v tlačítko [vlastnosti – okno](/visualstudio/ide/reference/properties-window) Chcete-li zobrazit úplný seznam zpráv systému Windows a události k dispozici pro vybranou položku. Zvolte ze seznamu k vytvoření nebo úpravě funkce obslužných rutin.  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>Přejít ke kódu z editoru dialogových oken  
  
1.  Dvakrát klikněte na ovládací prvek v dialogovém okně Přejít na deklaraci pro její zpracování funkce naposledy implementovaná zpráv. (Pro třídy na základě ATL dialogových oken, můžete vždy přejít k definici konstruktor.)  
  
### <a name="to-view-events-for-a-control"></a>Chcete-li zobrazit události pro ovládací prvek  
  
1.  Ovládací prvek, klikněte **ControlEvents** tlačítka na [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
    > [!NOTE]
    >  Kliknutím **ControlEvents** tlačítko při *dialogové okno* má fokus zpřístupňuje seznam všech ovládacích prvků v dialogových oken, které můžete rozbalit upravit události pro jednotlivé ovládací prvky.  
  
     Když jeden ovládací prvek má právě fokus, v dialogovém okně, můžete ho klikněte pravým tlačítkem a vyberte **přidejte obslužné rutiny události** z místní nabídky. Umožňuje zadat třídu, ke kterému se přidá obslužná rutina. Další informace najdete v tématu [přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).  
  
### <a name="to-view-messages-for-a-dialog-box"></a>Zobrazení zpráv pro dialogové okno  
  
1.  Dialogové okno vybraný, klikněte na **zprávy** v tlačítko [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor dialogových oken](../windows/dialog-editor.md)

