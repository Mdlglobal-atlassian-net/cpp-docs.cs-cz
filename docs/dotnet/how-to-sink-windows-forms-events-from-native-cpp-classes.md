---
title: 'Postupy: jímky událostí modelu Windows Forms z nativních tříd jazyka C++ | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0fec32bf179424b5ec0164e4511f74eae44f7320
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++
Můžete povolit nativní třídy C++ přijímat zpětná volání ze spravovaných událostí z ovládacích prvků Windows Forms nebo jiných formulářů s formátem mapy maker MFC. Zpracování událostí ve zobrazeních a dialogových oknech se podobá provedení stejné úlohy pro ovládací prvky.  
  
 K tomu budete muset:  
  
-   Připojit `OnClick` obslužné rutiny události pro ovládací prvek s využitím [MAKE_DELEGATE –](../mfc/reference/delegate-and-interface-maps.md#make_delegate).  
  
-   Vytvořit mapu delegáta pomocí [BEGIN_DELEGATE_MAP –](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP –](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), a [EVENT_DELEGATE_ENTRY –](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).  
  
 Tato ukázka pokračuje v práci, jste to udělali v [postup: provést vazby dat k DDX/DDV s modelem Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
  
 Nyní, kterou přidružíte váš ovládací prvek MFC (`m_MyControl`) s delegátem obslužné rutiny spravovaného událostí nazvané `OnClick` pro spravovaný <xref:System.Windows.Forms.Control.Click> událostí.  
  
### <a name="to-attach-the-onclick-event-handler"></a>Připojit obslužné rutiny události OnClick:  
  
1.  Přidejte následující kód do implementace BOOL CMFC01Dlg::OnInitDialog:  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  Přidejte následující kód do veřejného oddílu v deklaraci třídy CMFC01Dlg: veřejné CDialog.  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  Nakonec přidejte implementaci pro `OnClick` do CMFC01Dlg.cpp:  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [MAKE_DELEGATE –](../mfc/reference/delegate-and-interface-maps.md#make_delegate)   
 [BEGIN_DELEGATE_MAP –](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)   
 [END_DELEGATE_MAP –](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY –](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)