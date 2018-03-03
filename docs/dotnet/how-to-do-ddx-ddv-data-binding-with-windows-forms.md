---
title: "Postupy: vytvoření datové vazby DDX DDV s modelem Windows Forms | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9996fd10bad8578bd70739aa10b863bcea7f3c18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Postupy: Vytvoření datové vazby DDX/DDV s modelem Windows Forms
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) volání [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) k vytvoření ovládacího prvku odpovídající ID prostředku ovládacího prvku. Pokud používáte `DDX_ManagedControl` pro `CWinFormsControl` ovládací prvek (v generované v průvodci kódu), by neměl volání `CreateManagedControl` explicitně pro stejný ovládací prvek.  
  
 Volání `DDX_ManagedControl` v [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) k vytvoření ovládacích prvků z ID prostředků. Pro data systému exchange není potřeba použít funkce DDX/DDV s Windows Forms – ovládací prvky. Místo toho můžete umístit kód pro přístup k vlastnostem spravovaného ovládacího prvku `DoDataExchange` metoda třídě dialog (nebo zobrazení) jako v následujícím příkladu.  
  
 Následující příklad ukazuje, jak vytvořit vazbu na nativní řetězec C++ uživatelského ovládacího prvku rozhraní .NET.  
  
## <a name="example"></a>Příklad  
 Následuje příklad datové vazby DDX/DDV řetězec MFC `m_str` s uživatelsky definované `NameText` vlastnost uživatelského ovládacího prvku rozhraní .NET.  
  
 Ovládací prvek je vytvořen, když [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) volání `CMyDlg::DoDataExchange` poprvé, tak, aby kód, který odkazuje `m_UserControl` musí být pozdější `DDX_ManagedControl` volání.  
  
 Tento kód můžete implementovat v aplikaci MFC01, kterou jste vytvořili v [postupy: vytvoření uživatelského ovládacího prvku a vložení v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
 Chápat deklaraci CMFC01Dlg, vložte následující kód:  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## <a name="example"></a>Příklad  
 Chápat implementaci CMFC01Dlg, vložte následující kód:  
  
```  
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
{  
   CDialog::DoDataExchange(pDX);  
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);  
  
   if (pDX->m_bSaveAndValidate) {  
      m_str = m_MyControl->textBox1->Text;  
   } else  
   {  
      m_MyControl->textBox1->Text = gcnew System::String(m_str);  
   }  
}  
```  
  
## <a name="example"></a>Příklad  
 Teď přidáme metodu obslužné rutiny pro a klikněte na tlačítko OK. Klikněte **zobrazení prostředků** kartě. V zobrazení zdrojů, dvakrát klikněte na `IDD_MFC01_DIALOG`. Prostředku dialogového okna se zobrazí v editoru prostředků. Dvakrát klikněte na tlačítko OK...  
  
 Obslužná rutina definujte takto.  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## <a name="example"></a>Příklad  
 A přidejte následující řádek na implementaci BOOL CMFC01Dlg::OnInitDialog().  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 Teď můžete sestavit a spustit aplikaci. Všimněte si, že jakýkoli text v textovém poli se zobrazí automaticky otevírané okno se zprávou, po ukončení aplikace.  
  
## <a name="see-also"></a>Viz také  
 [CWinFormsControl – třída](../mfc/reference/cwinformscontrol-class.md)   
 [DDX_ManagedControl –](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)   
 [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)