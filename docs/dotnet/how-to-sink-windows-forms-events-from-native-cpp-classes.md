---
title: 'Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: 1bc601a4dbd7a51695b6964ab4d0ee47531c1b2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555906"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++

Můžete povolit nativních tříd jazyka C++ přijmout zpětná volání z spravovaných událostí vyvolaných z ovládacích prvků Windows Forms nebo jiných formulářů s formátem mapy maker MFC. Zpracování událostí v zobrazeních a dialogových oknech se podobá provedení stejné úlohy pro ovládací prvky.

Chcete-li to provést, budete muset:

- Připojit `OnClick` obslužnou rutinu události pro ovládací prvek s využitím [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate).

- Vytvořit delegáta mapy pomocí [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), a [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).

Tento příklad pokračuje v práci, jste to udělali v [jak: proveďte DDX/DDV datové vazby pomocí Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

Nyní, váš ovládací prvek MFC přidružíte (`m_MyControl`) s spravovaná událost obslužné rutiny delegáta volá `OnClick` pro spravovanou <xref:System.Windows.Forms.Control.Click> událostí.

### <a name="to-attach-the-onclick-event-handler"></a>Obslužná rutina události OnClick připojit:

1. Přidejte následující kód do implementace BOOL CMFC01Dlg::OnInitDialog:

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. Přidejte následující kód do veřejné sekce v deklaraci třídy CMFC01Dlg: veřejné CDialog.

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. Nakonec přidejte implementaci pro `OnClick` do CMFC01Dlg.cpp:

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>Viz také

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)