---
title: 'Postupy: vlastnosti volání a metody modelu Windows Forms řízení | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 206c7bc89ce2bbc48beb1d95f3929ea4694fce20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>Postupy: Vlastnosti volání a metody ovládacího prvku modelu Windows Forms
Protože [CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol) vrací ukazatel na <xref:System.Windows.Forms.Control?displayProperty=fullName>a nikoli ukazatel na `WindowsControlLibrary1::UserControl1`, je třeba přidat člena uživatelského ovládacího prvku typu a inicializovat jej v [IView::OnInitialUpdate ](../mfc/reference/iview-interface.md#oninitialupdate). Nyní můžete volat metody a vlastnosti pomocí `m_ViewControl`.  
  
 Toto téma předpokládá, že jste dokončili dříve [postupy: vytvoření uživatelského ovládacího prvku a vložení v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) a [postupy: vytvoření uživatelského ovládacího prvku a poskytování zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci MFC  
  
1.  Otevřete aplikaci MFC, kterou jste vytvořili v [postupy: vytvoření uživatelského ovládacího prvku a poskytování zobrazení MDI hostitele](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).  
  
2.  Přidejte následující řádek do části veřejné přepsání `CMFC02View` deklarace v MFC02View.h třídy.  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  Přidejte přepsání pro OnInitialupdate.  
  
     Zobrazení **vlastnosti** okno (F4). V **zobrazení tříd** (CTRL + SHIFT + C), vyberte třídu CMFC02View. V **vlastnosti** okně vyberte ikonu pro přepsání. Přesuňte se seznamem na OnInitialUpdate. Klikněte na rozevírací seznam a vyberte \<Přidat >. V MFC02View.cpp. Ujistěte se, že tělo funkce OnInitialUpdate vypadá takto:  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  Sestavte a spusťte projekt.  
  
     Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
     Všimněte si, že je nyní inicializováno textového pole.  
  
## <a name="see-also"></a>Viz také  
 [Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)