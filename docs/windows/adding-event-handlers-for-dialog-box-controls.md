---
title: Přidání obslužných rutin událostí pro ovládací prvky dialogové okno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, adding event handlers to controls
- controls [C++], event handlers
- dialog box controls, events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f05a9bc05dea6d217505e2e098dc2fde0d251894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863696"
---
# <a name="adding-event-handlers-for-dialog-box-controls"></a>Přidání obslužných rutin události pro ovládací prvky dialogového okna
Pro projekt dialogových oken, které jsou spojeny s třídou můžete využít některé klávesových zkratek při vytváření obslužných rutin událostí. Dokáže rychle vytvořit obslužnou rutinu pro událost upozornění na výchozí ovládací prvek nebo pro všechny příslušné zpráv systému Windows.  
  
#### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Chcete-li vytvořit obslužnou rutinu pro událost upozornění na výchozí ovládací prvek  
  
1.  Dvakrát klikněte na ovládací prvek. Otevře se textovém editoru.  
  
2.  Přidejte kód obslužné rutiny oznámení ovládacího prvku v textovém editoru.  
  
#### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Chcete-li vytvořit obslužnou rutinu pro všechny příslušné zpráv systému Windows  
  
1.  Klikněte na ovládací prvek, pro které chcete ke zpracování události oznámení.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), klikněte **ControlEvents** tlačítko Zobrazit seznam běžných události systému Windows přidruženého k ovládacímu prvku. Například standardní **OK** tlačítko **o** dialogové okno zobrazí následující události oznámení:  
  
 **BN_CLICKED**  
  
 **BN_DOUBLECLICKED**  
  
 **BN_KILLFOCUS**  
  
 **BN_SETFOCUS**  
  
    > [!NOTE]
    >  Případně vyberte dialogové okno a klikněte na **ControlEvents** tlačítko Zobrazit seznam běžných události systému Windows pro všechny ovládací prvky v dialogovém okně.  
  
3.  V **vlastnosti** oken, klikněte v pravém sloupci vedle události pro zpracování a pak vyberte název události navrhované oznámení (například **OnBnClickedOK** popisovače **BN_CLICKED** ).  
  
    > [!NOTE]
    >  Alternativně můžete zadat název obslužné rutiny události své volby, nikoli název obslužné rutiny události výchozí výběr.  
  
     Jakmile vyberete události, Visual Studio otevře textového editoru a zobrazí kód obslužné rutiny události. Například následující kód je přidána pro výchozí **OnBnClickedOK**:  
  
 ```  
    void CAboutDlg::OnBnClickedOk(void)  
 { *// TODO: Add your control notification handler code here  
 }  
 ```  
  
 Pokud chcete přidat obslužné rutiny události pro třídu jiné než jedna implementace dialogových oken, použijte [Průvodce obslužnou rutinou události](../ide/event-handler-wizard.md). Další informace najdete v tématu [přidání obslužné rutiny události](../ide/adding-an-event-handler-visual-cpp.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Výchozí události ovládacích prvků](../windows/default-control-events.md)   
 [Definování členských proměnných pro ovládací prvky dialogového okna](../windows/defining-member-variables-for-dialog-controls.md)   
 [Ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md)   
 [Přidání třídy](../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)

