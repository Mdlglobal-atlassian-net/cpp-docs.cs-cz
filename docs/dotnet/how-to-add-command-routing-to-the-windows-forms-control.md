---
title: "Postupy: Přidat příkaz prvku směrování do ovládacího prvku Windows Forms. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bcd082b22c61e2444d70d936c225e538c2429222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms
[CWinFormsView](../mfc/reference/cwinformsview-class.md) směrování příkazů a zpráv příkaz aktualizace uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů).  
  
 Uživatelský ovládací prvek používá [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) k uložení odkaz na zdrojový objekt příkazu v `m_CmdSrc`, jak je znázorněno v následujícím příkladu. Chcete-li použít `ICommandTarget` musíte přidat odkaz na mfcmifc80.dll.  
  
 `CWinFormsView`zpracovává několik běžných oznámení zobrazení knihovny MFC předáváním do spravovaného uživatelského ovládacího prvku. Tato oznámení zahrnují [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) a [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) metody.  
  
 Toto téma předpokládá, že jste dokončili dříve [postupy: vytvoření uživatelského ovládacího prvku a vložení v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) a [postupy: vytvoření uživatelského ovládacího prvku a poskytování zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci MFC  
  
1.  Otevřete knihovnu ovládacích prvků Windows Forms jste vytvořili v [postupy: vytvoření uživatelského ovládacího prvku a vložení v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
2.  Přidat odkaz na mfcmifc80.dll, které můžete provést kliknutím pravým tlačítkem na uzel projektu v **Průzkumníku řešení**, vyberete **přidat**, **odkaz**a poté přejděte na Microsoft Visual Studio 10.0\VC\atlmfc\lib.  
  
3.  Otevřete UserControl1.Designer.cs a přidejte následující příkaz using:  
  
    ```  
    using Microsoft.VisualC.MFC;  
    ```  
  
4.  Navíc v UserControl1.Designer.cs, změňte tento řádek:  
  
    ```  
    partial class UserControl1  
    ```  
  
     k tomuto:  
  
    ```  
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget  
    ```  
  
5.  Přidat jako první řádek definici třídy `UserControl1`:  
  
    ```  
    private ICommandSource m_CmdSrc;  
    ```  
  
6.  Přidejte následující definice metod k `UserControl1` (vytvoříme ID ovládacího prvku MFC v dalším kroku):  
  
    ```  
    public void Initialize (ICommandSource cmdSrc)  
    {  
       m_CmdSrc = cmdSrc;  
       // need ID of control in MFC dialog and callback function   
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));  
    }  
  
    private void singleMenuHandler (uint cmdUI)  
    {  
       // User command handler code  
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");  
    }  
    ```  
  
7.  Otevřete aplikaci MFC, kterou jste vytvořili v [postupy: vytvoření uživatelského ovládacího prvku a poskytování zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
8.  Přidejte položku nabídky, který bude vyvolat `singleMenuHandler`.  
  
     Přejděte na **zobrazení prostředků** (Ctrl + Shift + E), rozbalte **nabídky** složku a pak dvojitým kliknutím **IDR_MFC02TYPE**. Zobrazí se editor nabídek.  
  
     Přidejte položku nabídky v dolní části **zobrazení** nabídky. Všimněte si ID příkazu v nabídce **vlastnosti** okno. Uložte soubor.  
  
     V **Průzkumníku řešení**, otevřete soubor Resource.h, zkopírujte hodnotu ID pro položku nabídky jste právě přidali a vložte tuto hodnotu jako první parametr `m_CmdSrc.AddCommandHandler` volání v projektu jazyka C# `Initialize` (nahrazení –Metoda`32771` v případě potřeby).  
  
9. Sestavte a spusťte projekt.  
  
     Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
     Vyberte možnost nabídky, které jste přidali. Všimněte si, že se zavolá tato metoda v knihovna .dll.  
  
## <a name="see-also"></a>Viz také  
 [Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [ICommandSource rozhraní](../mfc/reference/icommandsource-interface.md)   
 [Rozhraní ICommandTarget rozhraní](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](http://msdn.microsoft.com/Library/22096734-e074-4aca-8523-4b15590109f9)