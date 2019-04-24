---
title: 'Postupy: Příkaz přidat ovládací prvek směrování Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: 8f633cf744314833409a3ffeacf8c850429e099c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222907"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Postupy: Příkaz přidat ovládací prvek směrování Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) směřuje příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů).

Uživatelský ovládací prvek používá [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) k uložení odkazu do zdrojového objektu příkazu v `m_CmdSrc`, jak je znázorněno v následujícím příkladu. Chcete-li použít `ICommandTarget` musíte přidat odkaz na mfcmifc80.dll.

`CWinFormsView` zpracovává několik obecných zobrazovacích oznámení knihovny MFC předáváním do spravovaného uživatelského ovládacího prvku. Tato oznámení zahrnují [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) a [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) metody.

Toto téma předpokládá, že jste již dříve dokončili [jak: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) a [jak: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci knihovny MFC

1. Otevřete Knihovna ovládacích prvků formulářů Windows, kterou jste vytvořili v [jak: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

1. Přidejte odkaz na mfcmifc80.dll, což lze provést kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumníka řešení**, kde vyberou **přidat**, **odkaz**a poté přejděte na Microsoft Visual Studio 10.0\VC\atlmfc\lib.

1. Otevřete UserControl1.Designer.cs a přidejte následující příkaz using:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. Navíc v UserControl1.Designer.cs, změňte tento řádek:

    ```
    partial class UserControl1
    ```

   K tomuto:

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. To přidejte jako první řádek definice třídy pro `UserControl1`:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Přidejte následující definice metod do `UserControl1` (budeme vytvářet ID ovládacího prvku knihovny MFC v dalším kroku):

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

1. Otevřete aplikaci knihovny MFC, kterou jste vytvořili v [jak: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Přidat položku nabídky, která se vyvolá `singleMenuHandler`.

   Přejděte na **zobrazení prostředků** (Ctrl + Shift + E), rozbalte **nabídky** složku a poté dvojitým kliknutím **IDR_MFC02TYPE**. Zobrazí se editor nabídky.

   Přidejte položku nabídky v dolní části **zobrazení** nabídky. Všimněte si, že ID příkazu v nabídce **vlastnosti** okna. Uložte soubor.

   V **Průzkumníka řešení**, otevřete soubor Resource.h, zkopírujte hodnotu ID pro položku nabídky, kterou jste právě přidali a vložte tuto hodnotu jako první parametr `m_CmdSrc.AddCommandHandler` volání v projektu C# `Initialize` (nahrazení –Metoda`32771` v případě potřeby).

9. Sestavte a spusťte projekt.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

   Vyberte možnost nabídky, kterou jste přidali. Všimněte si, že je volána metoda v knihovně .dll.

## <a name="see-also"></a>Viz také:

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource – rozhraní](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget – rozhraní](../mfc/reference/icommandtarget-interface.md)
