---
title: 'Postupy: Vytvoření uživatelského ovládacího prvku a vložení tohoto prvku do dialogového okna'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
ms.openlocfilehash: ccb7219b9c7b3a64da61a77097b147424a92a701
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649992"
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Postupy: Vytvoření uživatelského ovládacího prvku a vložení tohoto prvku do dialogového okna

V krocích v tomto článku se předpokládá, že vytváříte na dialogu založený ([CDialog – třída](../mfc/reference/cdialog-class.md)) projektu Microsoft Foundation Classes (MFC), ale můžete také přidat podporu pro ovládací prvek Windows Forms do existujícího dialogového okna knihovny MFC.

### <a name="to-create-the-net-user-control"></a>Chcete-li vytvořit uživatelský ovládací prvek .NET

1. Vytvoření projektu Visual C# Windows Knihovna ovládacích prvků formulářů s názvem `WindowsFormsControlLibrary1`.

   Na **souboru** nabídky, klikněte na tlačítko **nový** a potom klikněte na tlačítko **projektu**. V **Visual C#** složky, vyberte **Knihovna ovládacích prvků Windows Forms**.

   Přijměte `WindowsFormsControlLibrary1` název projektu kliknutím **OK**.

   Ve výchozím nastavení, bude mít název ovládací prvek .NET `UserControl1`.

1. Přidejte podřízené ovládací prvky `UserControl1`.

   V **nástrojů**, otevřete **všechny formuláře Windows** seznamu. Přetáhněte **tlačítko** ovládací prvek `UserControl1` návrhovou plochu.

   Také přidat **TextBox** ovládacího prvku.

1. V **Průzkumníka řešení**, dvakrát klikněte na panel **UserControl1.Designer.cs** otevřete pro úpravy. Změňte deklaraci textového pole a tlačítka z `private` k `public`.

1. Sestavte projekt.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci knihovny MFC

1. Vytvořte projekt aplikace knihovny MFC.

   Na **souboru** nabídky, klikněte na tlačítko **nový** a potom klikněte na tlačítko **projektu**. V **Visual C++** složky, vyberte **aplikace knihovny MFC**.

   V **název** zadejte `MFC01`. Změňte nastavení řešení na **přidat do řešení**. Klikněte na tlačítko **OK**.

   V **Průvodce aplikací knihovny MFC**, jako typ aplikace vyberte **na bázi dialogu**. Potvrďte zbývající výchozí nastavení a klikněte na tlačítko **Dokončit**. Tím se vytvoří aplikace knihovny MFC, která má dialogového okna knihovny MFC.

1. Přidání ovládacího prvku zástupného prvku do dialogového okna knihovny MFC.

   Na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**. V **zobrazení prostředků**, rozbalte **dialogové okno** složky a dvojím kliknutím `IDD_MFC01_DIALOG`. Prostředku dialogového okna se zobrazí v **Editor prostředků**.

   V **nástrojů**, otevřete **editoru dialogového okna** seznamu. Přetáhněte **statický Text** ovládacího prvku do dialogu prostředků. **Statický Text** ovládací prvek bude sloužit jako zástupný pro ovládací prvek .NET Windows Forms. Změňte jeho velikost přibližně na velikost ovládacího prvku Windows Forms.

   V **vlastnosti** okno Změnit **ID** z **statický Text** mít pod kontrolou `IDC_CTRL1` a změnit **TabStop** vlastnost **True**.

1. Konfigurace projektu pro podporu Common Language Runtime (CLR).

   V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu MFC01 a klikněte na **vlastnosti**.

   V **stránky vlastností** dialogovém okně **vlastnosti konfigurace**vyberte **Obecné**. V **výchozí nastavení projektu** nastavte **Common Language Runtime support** k **Common Language Runtime Support (/ clr)**.

   V části **vlastnosti konfigurace**, rozbalte **C/C++** a vyberte **Obecné** uzlu. Nastavte **formát ladicích informací** k **Program Database (/Zi)**.

   Vyberte **generování kódu** uzlu. Nastavte **povolit minimální opětovné sestavení** k **ne (/ Gm-)**. Nastavit také **Basic Runtime Checks** k **výchozí**.

   Klikněte na tlačítko **OK** změny se projeví.

1. Přidejte odkaz na ovládací prvek .NET.

   V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu MFC01 a klikněte na **přidat**, **odkazy**. Na **stránku vlastností**, klikněte na tlačítko **přidat nový odkaz**vyberte **WindowsFormsControlLibrary1** (v části **projekty** kartu) a klikněte na tlačítko **OK**. To přidá odkaz ve formuláři [/FU](../build/reference/fu-name-forced-hash-using-file.md) tak, že program bude kompilován – možnost kompilátoru. Také vloží kopii WindowsFormsControlLibrary1.dll do složky \MFC01\ projektu tak, aby se bude program spouštět.

1. Ve Stdafx.h vyhledejte tento řádek:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Výše, přidejte tyto řádky:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Přidejte kód k vytvoření spravovatelného ovládacího prvku.

   Nejprve deklarujte spravovatelný ovládací prvek. V MFC01Dlg.h přejděte do deklarace dialogové třídy a takto přidejte datové členy uživatelského ovládacího prvku do chráněného rozsahu.

    ```
    class CMFC01Dlg : public CDialog
    {
       // ...
       // Data member for the .NET User Control:
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;
    ```

   Dále poskytněte implementaci spravovatelného ovládacího prvku. V MFC01Dlg.cpp, v dialogovém okně přepište `CMFC01Dlg::DoDataExchange` vygenerované průvodcem aplikací MFC (nikoli `CAboutDlg::DoDataExchange`, což je ve stejném souboru), přidejte následující kód k vytvoření spravovatelného ovládacího prvku a přidružte jej k statické ovládacímu prvku IDC_CTRL1.

    ```
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
    {
       CDialog::DoDataExchange(pDX);
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);
    }
    ```

1. Sestavte a spusťte projekt.

   V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MFC01** a potom klikněte na tlačítko **nastavit jako spouštěný projekt**.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**. V dialogovém okně knihovny MFC zobrazeno ovládacího prvku Windows Forms.

## <a name="see-also"></a>Viz také

[Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)