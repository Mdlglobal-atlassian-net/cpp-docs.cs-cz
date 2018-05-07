---
title: 'Postupy: vytvoření uživatelského ovládacího prvku a vložení v dialogovém okně | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 20472a80b35318fa4c6d34221a61345de9e40f9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Postupy: Vytvoření uživatelského ovládacího prvku a vložení tohoto prvku do dialogového okna
Postup v tomto článku předpokládá, že vytváříte dialogu založený ([CDialog – třída](../mfc/reference/cdialog-class.md)) projektu Microsoft Foundation třídy (MFC), ale také můžete přidat podporu pro ovládací prvek Windows Forms k existující dialogového okna knihovny MFC.  
  
### <a name="to-create-the-net-user-control"></a>Vytvoření uživatelského ovládacího prvku rozhraní .NET  
  
1.  Vytvoření projektu Visual C# Windows Forms řízení knihovny s názvem `WindowsFormsControlLibrary1`.  
  
     Na **soubor** nabídky, klikněte na tlačítko **nový** a pak klikněte na **projektu**. V **Visual C#** složky, vyberte **knihovny ovládacích prvků Windows Forms**.  
  
     Přijměte `WindowsFormsControlLibrary1` název projektu kliknutím **OK**.  
  
     Ve výchozím nastavení, bude název prvku .NET `UserControl1`.  
  
2.  Přidat podřízené ovládací prvky pro `UserControl1`.  
  
     V **sada nástrojů**, otevřete **všechny formuláře Windows** seznamu. Přetáhněte **tlačítko** řídit k `UserControl1` návrhovou plochu.  
  
     Také přidat **TextBox** ovládacího prvku.  
  
3.  V **Průzkumníku řešení**, dvakrát klikněte na **UserControl1.Designer.cs** otevřete pro úpravy. Změňte deklaraci do textového pole a tlačítko z `private` k `public`.  
  
4.  Sestavte projekt.  
  
     Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci MFC  
  
1.  Vytvoření aplikace knihovny MFC projektu.  
  
     Na **soubor** nabídky, klikněte na tlačítko **nový** a pak klikněte na **projektu**. V **Visual C++** složky, vyberte **aplikace knihovny MFC**.  
  
     V **název** zadejte `MFC01`. Změňte nastavení řešení na **přidat do řešení**. Click **OK**.  
  
     V **Průvodce aplikací knihovny MFC**, typ aplikace, vyberte **dialogové okno na základě**. Přijměte zbývající výchozí nastavení a klikněte na **Dokončit**. Tím se vytvoří MFC aplikace, která má dialogového okna knihovny MFC.  
  
2.  Přidání ovládacího prvku zástupného symbolu do dialogového okna knihovny MFC.  
  
     Na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**. V **zobrazení prostředků**, rozbalte **dialogové okno** složku a dvojím kliknutím `IDD_MFC01_DIALOG`. Prostředku dialogového okna se zobrazí v **Editor prostředků**.  
  
     V **sada nástrojů**, otevřete **editoru dialogového okna** seznamu. Přetáhněte **statický Text** řízení prostředku dialogového okna. **Statický Text** ovládací prvek bude sloužit jako zástupný symbol pro ovládací prvek .NET Windows Forms. Jeho velikost přibližně velikosti ovládacího prvku Windows Forms.  
  
     V **vlastnosti** změňte **ID** z **statický Text** řídit k `IDC_CTRL1` a změňte **zarážek tabulátorů** vlastnosti **True**.  
  
3.  Konfigurace projektu pro podporu Common Language Runtime (CLR).  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt MFC01 a pak klikněte na tlačítko **vlastnosti**.  
  
     V **stránky vlastností** dialogovém **vlastnosti konfigurace**, vyberte **Obecné**. V **výchozí projekt** nastavte **podpory Common Language Runtime** k **Podpora Common Language Runtime (/ clr)**.  
  
     V části **vlastnosti konfigurace**, rozbalte položku **C/C++** a vyberte **Obecné** uzlu. Nastavit **ladění formátu informací** k **programu databáze (/Zi)**.  
  
     Vyberte **generování kódu** uzlu. Nastavit **povolit minimální opětovné sestavení** k **ne (/ Gm –)**. Nastavte také **základní kontroluje Runtime** k **výchozí**.  
  
     Klikněte na tlačítko **OK** aby se změny projevily.  
  
4.  Přidáte odkaz na ovládací prvek .NET.  
  
     V **Průzkumníku řešení**klikněte pravým tlačítkem na projekt MFC01 a pak klikněte na tlačítko **přidat**, **odkazy**. Na **stránka vlastností**, klikněte na tlačítko **přidat nový odkaz**, vyberte **WindowsFormsControlLibrary1** (v části **projekty** kartě) a klikněte na tlačítko **OK**. Tento příkaz přidá odkaz ve formě [/FU](../build/reference/fu-name-forced-hash-using-file.md) tak, aby se kompilace programu – možnost kompilátoru. Také převádí kopii WindowsFormsControlLibrary1.dll ve složce projektu \MFC01\ tak, aby se bude program spouštět.  
  
5.  Ve Stdafx.h vyhledejte tento řádek:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Výše, přidejte tyto řádky:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Přidejte kód k vytvoření spravovaného ovládacího prvku.  
  
     Nejprve deklarujte spravované ovládací prvek. V MFC01Dlg.h přejděte na deklaraci třídy dialogového okna a přidat člena data uživatelského ovládacího prvku v oboru chráněné, následujícím způsobem.  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     Potom zadejte implementaci pro spravované ovládací prvek. V MFC01Dlg.cpp, v dialogovém okně přepsání z `CMFC01Dlg::DoDataExchange` který byl vygenerován pomocí Průvodce aplikací MFC (ne `CAboutDlg::DoDataExchange`, což je ve stejném souboru), přidejte následující kód k vytvoření spravovaného ovládacího prvku a přidružte ji k statické ovládacímu prvku IDC_CTRL1.  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  Sestavte a spusťte projekt.  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem na **MFC01** a pak klikněte na **nastavit jako spouštěný projekt**.  
  
     Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**. V dialogovém okně knihovny MFC by měl zobrazit ovládacího prvku Windows Forms.  
  
## <a name="see-also"></a>Viz také  
 [Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)