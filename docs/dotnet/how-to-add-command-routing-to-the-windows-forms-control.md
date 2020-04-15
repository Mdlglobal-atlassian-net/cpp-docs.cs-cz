---
title: 'Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365172"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) směruje příkazy a zprávy uživatelského rozhraní příkazu update-command do uživatelského ovládacího prvku, aby mohl zpracovávat příkazy knihovny MFC (například položky nabídky rámce a tlačítka panelu nástrojů).

Uživatelský ovládací prvek používá [iCommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) k uložení odkazu `m_CmdSrc`na objekt zdroje příkazu v aplikaci , jak je znázorněno v následujícím příkladu. Chcete-li použít, `ICommandTarget` musíte přidat odkaz na mfcmifc80.dll.

`CWinFormsView`zpracovává několik běžných oznámení zobrazení knihovny MFC jejich předáním do spravovaného uživatelského ovládacího prvku. Tato oznámení zahrnují [metody OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) a [OnActivateView.](../mfc/reference/iview-interface.md#onactivateview)

Toto téma předpokládá, že jste již dříve dokončili [postup: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) a [postup: Vytvoření uživatelského ovládacího prvku a zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Vytvoření hostitelské aplikace knihovny MFC

1. Otevřete knihovnu ovládacího prvku formulářů systému Windows, kterou jste vytvořili v [části Postup: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

1. Přidejte odkaz na soubor mfcmifc80.dll, který můžete provést klepnutím pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení**, výběrem **možnosti Přidat**, **Odkaz**a potom procházením aplikace Microsoft Visual Studio 10.0\VC\atlmfc\lib.

1. Otevřete UserControl1.Designer.cs a přidejte následující příkaz using:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. Také v UserControl1.Designer.cs změňte tento řádek:

    ```
    partial class UserControl1
    ```

   měli změnit na:

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Přidejte to jako první řádek `UserControl1`definice třídy pro :

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Přidejte do něj `UserControl1` následující definice metod (id ovládacího prvku knihovny MFC vytvoříme v dalším kroku):

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

1. Otevřete aplikaci Knihovny MFC, kterou jste vytvořili v [části Postup: Vytvoření uživatelského ovládacího prvku a zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Přidejte možnost nabídky, `singleMenuHandler`která vyvolá .

   Přejděte do **zobrazení zdrojů** (Ctrl+Shift+E), rozbalte složku **Nabídka** a poklikejte na **IDR_MFC02TYPE**. Zobrazí se editor nabídek.

   Přidejte možnost nabídky v dolní části nabídky **Zobrazení.** Všimněte si ID možnosti nabídky v okně **Vlastnosti.** Uložte soubor.

   V **Průzkumníku řešení**otevřete soubor Resource.h, zkopírujte hodnotu ID pro možnost nabídky, kterou `m_CmdSrc.AddCommandHandler` jste právě přidali, `Initialize` a vložte tuto hodnotu jako první parametr do volání v metodě projektu C# (v případě potřeby je nahraďte). `32771`

1. Sestavení a spuštění projektu.

   V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   V nabídce **Ladění** klepněte na tlačítko **Start bez ladění**.

   Vyberte možnost nabídky, kterou jste přidali. Všimněte si, že metoda v dll je volána.

## <a name="see-also"></a>Viz také

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource – rozhraní](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget – rozhraní](../mfc/reference/icommandtarget-interface.md)
