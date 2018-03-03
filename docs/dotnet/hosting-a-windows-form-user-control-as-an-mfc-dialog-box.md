---
title: "Hostování Windows Form uživatelský ovládací prvek jako dialogového okna knihovny MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ad1d800619eb84a470dbc5e472e9191d13e8796
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC
MFC poskytuje šablony třídy [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) tak, aby je možné hostovat uživatelského ovládacího prvku Windows Forms (<xref:System.Windows.Forms.UserControl>) v modální nebo nemodálním dialogovém okně knihovny MFC. `CWinFormsDialog`je odvozena od třídy MFC [CDialog](../mfc/reference/cdialog-class.md), takže dialogové okno může být spuštěn jako modální nebo nemodální.  
  
 Proces, `CWinFormsDialog` používá k hostování uživatelského ovládacího prvku je podobný tomu popsaném v [hostitelské poskytování uživatelského Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Ale `CWinFormsDialog` spravuje inicializace a hostování uživatelského ovládacího prvku tak, aby nemá naprogramovat ručně.  
  
 Ukázkové aplikace, která ukazuje použití MFC modelu Windows Forms, najdete v části [integrace produktů Windows Forms a MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci MFC  
  
1.  Vytvoření aplikace knihovny MFC projektu.  
  
     Na **soubor** nabídce vyberte možnost **nový**a potom klikněte na **projektu**. V **Visual C++** složky, vyberte **aplikace knihovny MFC**.  
  
     V **název** zadejte `MFC03` a změňte nastavení řešení pro **přidat do řešení**. Klikněte na tlačítko **OK**.  
  
     V **Průvodce aplikací knihovny MFC**přijměte všechny výchozí hodnoty a pak klikněte na tlačítko **Dokončit**. Tím se vytvoří aplikace knihovny MFC rozhraní více dokumentů.  
  
2.  Konfigurace projektu.  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **MFC03** uzel projektu a zvolte **vlastnosti**. **Stránky vlastností** zobrazí se dialogové okno.  
  
     V **stránky vlastností** v dialogovém **vlastnosti konfigurace** ovládací prvek stromu, vyberte **Obecné**, potom v **výchozínastaveníprojektu**nastavte **podpory Common Language Runtime** k **Podpora Common Language Runtime (/ clr)**. Click **OK**.  
  
3.  Přidáte odkaz na ovládací prvek .NET.  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **MFC03** uzel projektu a zvolte **přidat**, **odkazy**. V **stránka vlastností**, klikněte na tlačítko **přidat nový odkaz**, vyberte WindowsControlLibrary1 (v části **projekty** kartě) a klikněte na tlačítko **OK**. Tento příkaz přidá odkaz ve formě [/FU](../build/reference/fu-name-forced-hash-using-file.md) tak, aby se kompilace programu – možnost kompilátoru; také zkopíruje WindowsControlLibrary1.dll do `MFC03` adresáře projektu tak, aby se bude program spouštět.  
  
4.  Přidat `#include <afxwinforms.h>` do stdafx.h na konci existující `#include` příkazy.  
  
5.  Přidejte novou třídu, která je podtřídou `CDialog`.  
  
     Klikněte pravým tlačítkem na název projektu a přidání třídy knihovny MFC (nazývanou CHostForWinForm), která je podtřídou `CDialog`. Vzhledem k tomu, že není nutné pole prostředku dialogového okna, můžete odstranit ID prostředku (vyberte zobrazení zdroje, rozbalte složku, dialogové okno a odstranit IDD_HOSTFORWINFORM prostředek.  Pak odeberte všechny odkazy na ID v kódu.).  
  
6.  Nahraďte `CDialog` v souborech CHostForWinForm.h a CHostForWinForm.cpp s `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.  
  
7.  Volání DoModal na třídě CHostForWinForm.  
  
     V MFC03.cpp přidejte `#include "HostForWinForm.h"`.  
  
     Před příkaz return v definici CMFC03App::InitInstance přidejte:  
  
     `CHostForWinForm m_HostForWinForm;`  
  
     `m_HostForWinForm.DoModal();`  
  
8.  Sestavte a spusťte projekt.  
  
     Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
     Dále přidáte kód ke sledování stavu ovládacího prvku v rozhraní Windows Forms z aplikace MFC.  
  
9. Přidejte obslužnou rutinu pro OnInitDialog.  
  
     Zobrazení **vlastnosti** okno (F4). V **zobrazení tříd**, vyberte CHostForWinForm. V **vlastnosti** okně vyberte přepsání a v řádku pro OnInitDialog, klikněte v levém sloupci a vyberte \< Přidat >. Tento postup přidá následující řádek do CHostForWinForm.h:  
  
    ```  
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
  
11. Dále přidejte obslužnou rutinu OnButton1. Přidejte následující řádky do části veřejné třídy CHostForWinForm v CHostForWinForm.h:  
  
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
  
12. Sestavte a spusťte projekt. Po kliknutí na tlačítko, které se na formuláři Windows se spustí kód v aplikaci MFC.  
  
     Dále přidáte kód, který zobrazí z kódu MFC hodnotu do textového pole ve formuláři Windows.  
  
13. V části veřejné třídy CHostForWinForm v CHostForWinForm.h přidejte následující prohlášení:  
  
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
 [Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)