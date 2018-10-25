---
title: Hostování Windows tvoří uživatelský ovládací prvek jako dialogového okna knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 86a820e54e63c21c3ec4b9ace538bd6bfb4e9c0a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052855"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC

Knihovna MFC poskytuje šablony třídy [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) tak, aby uživatelského ovládacího prvku Windows Forms může hostovat (<xref:System.Windows.Forms.UserControl>) v modálním nebo nemodálním dialogovém okně knihovny MFC. `CWinFormsDialog` je odvozen od třídy knihovny MFC [CDialog](../mfc/reference/cdialog-class.md), takže můžete spustit dialogové okno modální a nemodální.

Proces, který `CWinFormsDialog` používá k hostování uživatelského ovládacího prvku je podobný tomu popsanému v [hostitelské poskytování uživatelského Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Ale `CWinFormsDialog` spravuje inicializace a poskytování hostitelských služeb uživatelského ovládacího prvku, takže není nutné naprogramovat ručně.

Ukázková aplikace, která ukazuje použití s knihovnou MFC modelu Windows Forms, naleznete v tématu [MFC a integrace formulářů Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci knihovny MFC

1. Vytvořte projekt aplikace knihovny MFC.

   Na **souboru** nabídce vyberte možnost **nový**a potom klikněte na tlačítko **projektu**. V **Visual C++** složky, vyberte **aplikace knihovny MFC**.

   V **název** zadejte `MFC03` a změňte nastavení řešení na **přidat do řešení**. Klikněte na tlačítko **OK**.

   V **Průvodce aplikací knihovny MFC**, přijměte všechny výchozí hodnoty a klikněte na **Dokončit**. Tím se vytvoří aplikace knihovny MFC s rozhraním více dokumentů.

1. Konfigurace projektu.

   V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **MFC03** uzel projektu a zvolte **vlastnosti**. **Stránky vlastností** zobrazí se dialogové okno.

   V **stránky vlastností** v dialogu **vlastnosti konfigurace** ovládacího prvku stromu, vyberte **Obecné**, pak v **výchozínastaveníprojektu**nastavte **Common Language Runtime support** k **Common Language Runtime Support (/ clr)**. Klikněte na tlačítko **OK**.

1. Přidejte odkaz na ovládací prvek .NET.

   V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **MFC03** uzel projektu a zvolte **přidat**, **odkazy**. V **stránku vlastností**, klikněte na tlačítko **přidat nový odkaz**, vyberte WindowsControlLibrary1 (v části **projekty** kartu) a klikněte na tlačítko **OK**. To přidá odkaz ve formuláři [/FU](../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru tak, že program bude kompilován; také zkopíruje WindowsControlLibrary1.dll do `MFC03` adresáře projektu tak, aby se bude program spouštět.

1. Přidat `#include <afxwinforms.h>` do stdafx.h na konci existujícího `#include` příkazy.

1. Přidejte novou třídu, která je podtřídou `CDialog`.

   Klikněte pravým tlačítkem na název projektu a přidání třídy knihovny MFC (nazývanou CHostForWinForm), která je podtřídou `CDialog`. Vzhledem k tomu, že nepotřebujete prostředky dialogového, můžete odstranit ID prostředku (vyberte **zobrazení prostředků**, rozbalte **dialogové okno** složku a odstraňte `IDD_HOSTFORWINFORM` prostředků.  Potom odeberte všechny odkazy na ID v kódu.).

1. Nahraďte `CDialog` v CHostForWinForm.h a CHostForWinForm.cpp soubory s `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Volejte DoModal na třídě CHostForWinForm.

   V MFC03.cpp přidejte `#include "HostForWinForm.h"`.

   Před příkaz return v definici CMFC03App::InitInstance přidejte:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Sestavte a spusťte projekt.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

   Dále přidáte kód ke sledování stavu ovládacího prvku Windows Forms z aplikace knihovny MFC.

9. Přidejte obslužnou rutinu pro OnInitDialog.

   Zobrazení **vlastnosti** okno (F4). V **zobrazení tříd**, vyberte CHostForWinForm. V **vlastnosti** okna, vyberte možnost přepsání a v řádku pro OnInitDialog klikněte v levém sloupci a vyberte \< Přidat >. Tím přidáte následující řádek do CHostForWinForm.h:

    ```cpp
    virtual BOOL OnInitDialog();
    ```

10. Definujte OnInitDialog (v CHostForWinForm.cpp) takto:

    ```
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

11. Dále přidejte obslužnou rutinu OnButton1. Přidejte následující řádky do veřejné sekce třídy CHostForWinForm v CHostForWinForm.h:

    ```
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   V CHostForWinForm.cpp přidejte tuto definici:

    ```
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

12. Sestavte a spusťte projekt. Když kliknete na tlačítko, které je ve formuláři Windows se spustí kód v aplikaci knihovny MFC.

   Dále přidáte kód k zobrazení hodnoty z kódu MFC, do textového pole ve formuláři Windows.

13. Do veřejné sekce třídy CHostForWinForm v CHostForWinForm.h přidejte následující deklarace:

    ```
    CString m_sEditBoxOnWinForm;
    ```

14. V definici DoDataExchange v CHostForWinForm.cpp přidejte následující tři řádky na konec funkce:

    ```
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

15. V definici OnButton1 v CHostForWinForm.cpp přidejte následující tři řádky na konec funkce:

    ```
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

16. Sestavte a spusťte projekt.

## <a name="see-also"></a>Viz také

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)