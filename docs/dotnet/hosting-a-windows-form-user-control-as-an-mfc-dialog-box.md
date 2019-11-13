---
title: Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 7fc2aad1e0a550fb8f22b311518ae9fb16c076a5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964940"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC

Knihovna MFC poskytuje třídu šablon [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) , takže můžete hostovat model Windows Forms uživatelský ovládací prvek (<xref:System.Windows.Forms.UserControl>) v modálním nebo nemodálním dialogovém okně knihovny MFC. `CWinFormsDialog` je odvozen z třídy MFC [CDialog](../mfc/reference/cdialog-class.md), takže dialogové okno lze spustit jako modální nebo nemodální.

Proces, který `CWinFormsDialog` používá k hostování uživatelského ovládacího prvku, je podobný jako v tématu [hostování uživatelského ovládacího prvku Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). `CWinFormsDialog` ale spravuje inicializaci a hostování uživatelského ovládacího prvku tak, aby se nemusela programovat ručně.

Ukázkovou aplikaci, která zobrazuje model Windows Forms používané v prostředí MFC, naleznete v tématu [integrace MFC a model Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

### <a name="to-create-the-mfc-host-application"></a>Vytvoření hostitelské aplikace MFC

1. Vytvořte projekt aplikace MFC.

   V nabídce **soubor** vyberte **Nový**a pak klikněte na **projekt**. Ve složce **vizuálu C++**  vyberte možnost **aplikace MFC**.

   Do pole **název** zadejte `MFC03` a změňte nastavení řešení na možnost **Přidat do řešení**. Klikněte na tlačítko **OK**.

   V **Průvodci aplikací knihovny MFC**přijměte všechny výchozí hodnoty a potom klikněte na tlačítko **Dokončit**. Tím se vytvoří aplikace MFC s rozhraním více dokumentů.

1. Nakonfigurujte projekt.

   V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **MFC03** a vyberte možnost **vlastnosti**. Zobrazí se dialogové okno **stránky vlastností** .

   V dialogovém okně **stránky vlastností** v ovládacím prvku strom **vlastností konfigurace** vyberte možnost **Obecné**a potom v části **výchozí nastavení projektu** nastavte podporu modulu **CLR** na **Common Language Runtime ( /CLR)** . Klikněte na tlačítko **OK**.

1. Přidejte odkaz na ovládací prvek .NET.

   V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **MFC03** a vyberte možnost **Přidat**, **odkazy**. Na **stránce vlastností**klikněte na **Přidat nový odkaz**, vyberte WindowsControlLibrary1 (na kartě **projekty** ) a klikněte na **OK**. Tím se přidá odkaz ve formuláři Možnosti kompilátoru [/Fu](../build/reference/fu-name-forced-hash-using-file.md) , takže program se zkompiluje. také zkopíruje WindowsControlLibrary1. dll do adresáře projektu `MFC03`, takže se program spustí.

1. Přidejte `#include <afxwinforms.h>` do souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší) na konci existujících příkazů `#include`.

1. Přidejte novou třídu, která `CDialog`podtřídy.

   Klikněte pravým tlačítkem na název projektu a přidejte třídu knihovny MFC (s názvem CHostForWinForm), kterou podtřídy `CDialog`. Vzhledem k tomu, že nepotřebujete prostředek dialogového okna, můžete odstranit ID prostředku (vyberte **prostředky**, rozbalte složku **dialogového okna** a odstraňte prostředek `IDD_HOSTFORWINFORM`.  Pak odeberte všechny odkazy na ID v kódu.).

1. Nahraďte `CDialog` v CHostForWinForm. h a CHostForWinForm. cpp soubory pomocí `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Volejte DoModal pro třídu CHostForWinForm.

   Do MFC03. cpp přidejte `#include "HostForWinForm.h"`.

   Před příkazem Return v definici CMFC03App:: InitInstance přidejte:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Sestavte a spusťte projekt.

   V nabídce **sestavení** klikněte na **Sestavit řešení**.

   V nabídce **ladit** klikněte na **Spustit bez ladění**.

   Dále přidáte kód pro monitorování stavu ovládacího prvku v model Windows Forms z aplikace MFC.

1. Přidejte obslužnou rutinu pro OnInitDialog.

   Zobrazí okno **vlastnosti** (F4). V **zobrazení tříd**vyberte CHostForWinForm. V okně **vlastnosti** vyberte možnost přepsání a v řádku pro OnInitDialog klikněte na sloupec vlevo a vyberte \< přidat >. Tím se přidá následující řádek do CHostForWinForm. h:

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. Definujte OnInitDialog (v CHostForWinForm. cpp) následujícím způsobem:

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. Dále přidejte obslužnou rutinu ' Button1 '. Přidejte následující řádky do veřejné sekce třídy CHostForWinForm v CHostForWinForm. h:

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   V CHostForWinForm. cpp přidejte tuto definici:

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. Sestavte a spusťte projekt. Po kliknutí na tlačítko, které je na formuláři Windows, se spustí kód v aplikaci MFC.

    Dále přidáte kód, který bude zobrazen z kódu knihovny MFC, do textového pole ve formuláři Windows.

1. Do veřejné sekce třídy CHostForWinForm v CHostForWinForm. h přidejte následující deklaraci:

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. V definici DoDataExchange v CHostForWinForm. cpp přidejte následující tři řádky na konec funkce:

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. V definici funkce webbutton1 v CHostForWinForm. cpp přidejte následující tři řádky na konec funkce:

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. Sestavte a spusťte projekt.

## <a name="see-also"></a>Viz také:

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[pomocí uživatelského ovládacího prvku Windows Form v MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
