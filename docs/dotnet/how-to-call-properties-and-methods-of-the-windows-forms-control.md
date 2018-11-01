---
title: 'Postupy: Vlastnosti volání a metody ovládacího prvku modelu Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
ms.openlocfilehash: 809fa428172dffb5f53e7339e04882b451c8562f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561483"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Postupy: Vlastnosti volání a metody ovládacího prvku modelu Windows Forms

Protože [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) vrací ukazatel na <xref:System.Windows.Forms.Control?displayProperty=fullName>a nikoli ukazatel na `WindowsControlLibrary1::UserControl1`, doporučuje se přidat člena typu ovládacího prvku a inicializovat jej v [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Nyní můžete volat metody a vlastnosti pomocí `m_ViewControl`.

Toto téma předpokládá, že jste již dříve dokončili [postupy: vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) a [postupy: vytvoření uživatelského ovládacího prvku a poskytování zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci knihovny MFC

1. Otevřete aplikaci knihovny MFC, kterou jste vytvořili v [postupy: vytvoření uživatelského ovládacího prvku a poskytování zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Přidejte následující řádek do části veřejné přepsání `CMFC02View` deklarace v MFC02View.h třídy.

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. Přidejte přepsání pro OnInitialupdate.

   Zobrazení **vlastnosti** okno (F4). V **zobrazení tříd** (CTRL + SHIFT + C), vyberte CMFC02View třídu. V **vlastnosti** okna, vyberte ikonu pro přepsání. Přesuňte se dolů seznamem, aby OnInitialUpdate. Klikněte na rozevírací seznam a vyberte \<Přidat >. V MFC02View.cpp. Ujistěte se, že tělo funkce OnInitialUpdate následujícím způsobem:

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. Sestavte a spusťte projekt.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

   Všimněte si, že se teď inicializují do textového pole.

## <a name="see-also"></a>Viz také

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)