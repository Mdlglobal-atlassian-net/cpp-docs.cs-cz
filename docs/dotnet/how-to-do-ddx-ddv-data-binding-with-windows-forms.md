---
title: 'Postupy: Proveďte DDX / DDV datové vazby pomocí Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 558c763fd18cd1569ff23435bf6156b3117f117d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740949"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Postupy: Proveďte DDX/DDV datové vazby pomocí Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) volání [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) vytvořit ovládací prvek s odpovídajícím ID prostředku ovládacího prvku. Pokud používáte `DDX_ManagedControl` pro `CWinFormsControl` ovládacího prvku (ve vygenerovaném kódu), neměli by jste volat `CreateManagedControl` explicitně pro stejný ovládací prvek.

Volání `DDX_ManagedControl` v [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) k vytvoření ovládacích prvků z ID prostředků. Pro data systému exchange není potřeba používat funkce DDX/DDV s ovládacími prvky Windows Forms. Místo toho můžete kód pro přístup k vlastnosti spravovatelného ovládacího prvku v umístit `DoDataExchange` metody třídy dialogového okna (nebo zobrazení), jako v následujícím příkladu.

Následující příklad ukazuje, jak svázat řetězec nativní C++ uživatelský ovládací prvek .NET.

## <a name="example"></a>Příklad

Následuje příklad datové vazby DDX/DDV řetězce MFC `m_str` s uživatelsky definované `NameText` vlastnost uživatelský ovládací prvek .NET.

Ovládací prvek je vytvořen při [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) volání `CMyDlg::DoDataExchange` poprvé, tak, aby kód, který odkazuje `m_UserControl` musí být pozdější než `DDX_ManagedControl` volání.

Tento kód lze implementovat v MFC01 aplikaci, kterou jste vytvořili v [jak: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

Umístěte do deklarace CMFC01Dlg, vložte následující kód:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Příklad

Ukládejte provádění CMFC01Dlg, vložte následující kód:

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

Teď přidáme metodu obslužné rutiny pro kliknutí na tlačítko OK. Klikněte na tlačítko **zobrazení prostředků** kartu. V okně zobrazení prostředků, dvakrát klikněte na `IDD_MFC01_DIALOG`. Prostředku dialogového okna se zobrazí v editoru prostředků. Dvakrát klikněte na tlačítko OK...

Definování obslužné rutiny následujícím způsobem.

```
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Příklad

A přidejte následující řádek do implementace BOOL CMFC01Dlg::OnInitDialog().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Teď můžete sestavit a spustit aplikaci. Všimněte si, že veškerý text v textovém poli se zobrazí v místním okně se zprávou, po zavření aplikace.

## <a name="see-also"></a>Viz také:

[CWinFormsControl – třída](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
