---
title: 'Postupy: Vytvoření datové vazby DDX/DDV ve Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754359"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Postupy: Vytvoření datové vazby DDX/DDV s modelem Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) volá [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) k vytvoření ovládacího prvku odpovídajícího ID ovládacího prvku prostředku. Pokud používáte `DDX_ManagedControl` `CWinFormsControl` pro ovládací prvek (v kódu generovaném `CreateManagedControl` průvodcem), neměli byste explicitně volat pro stejný ovládací prvek.

Volání `DDX_ManagedControl` v [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) k vytvoření ovládacích prvků z ID prostředků. Pro výměnu dat není nutné používat funkce DDX/DDV s ovládacími prvky Windows Forms. Místo toho můžete umístit kód pro přístup k `DoDataExchange` vlastnostem spravovaného ovládacího prvku v metodě třídy dialog (nebo zobrazení), jako v následujícím příkladu.

Následující příklad ukazuje, jak svázat nativní řetězec C++ s uživatelským ovládacím prvkem .NET.

## <a name="example"></a>Příklad

Následuje příklad datové vazby DDX/DDV řetězce `m_str` knihovny MFC `NameText` s uživatelem definovanou vlastností uživatelského ovládacího prvku .NET.

Ovládací prvek je vytvořen při [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) volá `CMyDlg::DoDataExchange` poprvé, `m_UserControl` takže jakýkoli `DDX_ManagedControl` kód, který odkazy musí přijít po volání.

Tento kód můžete implementovat v aplikaci MFC01, kterou jste vytvořili v [části Postup: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

Vložte následující kód do deklarace CMFC01Dlg:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Příklad

Vložte následující kód do implementace CMFC01Dlg:

```cpp
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

Nyní přidáme metodu obslužné rutiny pro kliknutí na tlačítko OK. Klikněte na kartu **Zobrazení zdrojů.** V zobrazení zdrojů poklepejte na položku `IDD_MFC01_DIALOG`. Prostředek dialogového okna se zobrazí v Editoru prostředků. Poté poklepejte na tlačítko OK.

Definujte obslužnou rutinu následujícím způsobem.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Příklad

A přidejte následující řádek k implementaci BOOL CMFC01Dlg::OnInitDialog().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Teď můžete aplikaci sestavit a spustit. Všimněte si, že jakýkoli text v textovém poli se zobrazí v rozbalovacím poli zprávy při zavření aplikace.

## <a name="see-also"></a>Viz také

[Třída CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
