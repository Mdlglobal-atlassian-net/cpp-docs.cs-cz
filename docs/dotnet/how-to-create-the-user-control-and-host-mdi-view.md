---
title: 'Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374457"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI

Následující kroky ukazují, jak vytvořit uživatelský ovládací prvek rozhraní .NET Framework, vytvořit uživatelský ovládací prvek v knihovně tříd ovládacích tříd (konkrétně projekt knihovny ovládacích prvku systému Windows) a potom zkompilovat projekt do sestavení. Ovládací prvek pak může být spotřebována z aplikace knihovny MFC, která používá třídy odvozené z [CView Class](../mfc/reference/cview-class.md) a [CWinFormsView Class](../mfc/reference/cwinformsview-class.md).

Informace o vytvoření uživatelského ovládacího prvku formuláře Windows Forms a vytvoření knihovny tříd ovládacích prvků naleznete v [tématu How to: Author User Controls](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
> V některých případech ovládací prvky windows forms, jako je například ovládací prvek Grid jiného výrobce, nemusí chovat spolehlivě při hostování v aplikaci knihovny MFC. Doporučeným zástupem je umístění uživatelského ovládacího prvku formulářů Windows Forms do aplikace knihovny MFC a umístění ovládacího prvku Grid jiného výrobce do ovládacího prvku User.

Tento postup předpokládá, že jste vytvořili projekt knihovny ovládacích prvků systému Windows Forms s názvem WindowsFormsControlLibrary1 podle postupu v [části Postup: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Vytvoření hostitelské aplikace knihovny MFC

1. Vytvořte projekt aplikace knihovny MFC.

   V nabídce **Soubor** vyberte **Nový**a klepněte na **položku Project**. Ve složce **Visual C++** vyberte **položku Aplikace knihovny MFC**.

   Do pole **Název** `MFC02` zadejte a změňte nastavení **Řešení** na Přidat **do řešení**. Klikněte na tlačítko **OK**.

   V **Průvodci aplikací knihovny MFC**přijměte všechny výchozí hodnoty a klepněte na tlačítko **Dokončit**. Tím se vytvoří aplikace knihovny MFC s rozhraním více dokumentů.

1. Nakonfigurujte projekt pro podporu clr (Common Language Runtime).

   V **Průzkumníku řešení**klepněte pravým tlačítkem `MFC01` myši na uzel projektu a z kontextové nabídky vyberte **vlastnosti.** Zobrazí se dialogové okno **Stránky vlastností.**

   V části **Vlastnosti konfigurace**vyberte **obecné**. V části **Výchozí nastavení projektu** nastavte podporu common language **runtime** pro **podporu běžného jazykového běhu (/clr).**

   V **části Vlastnosti konfigurace**rozbalte **c/c++** a klikněte na **obecný** uzel. Nastavte **formát informací o ladění** na **programovou databázi (/Zi)**.

   Klikněte na uzel **Generování kódu.** Nastavte **možnost Povolit minimální opětovné sestavení** na ne **(/Gm-)**. Nastavte také **hodnotu Základní kontroly za běhu** na **výchozí hodnotu**.

   Chcete-li změny použít, klepněte na tlačítko **OK.**

1. V *pch.h* (*stdafx.h* v Visual Studiu 2017 a starší) přidejte následující řádek:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Přidejte odkaz na ovládací prvek .NET.

   V **Průzkumníku řešení**klepněte pravým tlačítkem `MFC02` myši na uzel projektu a vyberte přidat , **Odkazy**. **Add** Na **stránce vlastností**klepněte na **tlačítko Přidat nový odkaz**, vyberte položku WindowsFormsControlLibrary1 (na kartě **Projekty)** a klepněte na tlačítko **OK**. Tím přidáte odkaz ve formě možnosti kompilátoru [/FU,](../build/reference/fu-name-forced-hash-using-file.md) takže program bude kompilovat; také zkopíruje soubor WindowsFormsControlLibrary1.dll do adresáře `MFC02` projektu, aby byl program spuštěn.

1. V stdafx.h, najít tento řádek:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Přidejte nad něj tyto řádky:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Upravte třídu zobrazení tak, aby dědila z [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   V mfc02View.h nahraďte [CView](../mfc/reference/cview-class.md) [CView CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, aby se kód zobrazil takto:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Pokud chcete přidat další zobrazení do aplikace MDI, budete muset volat [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pro každé zobrazení, které vytvoříte.

1. Upravte soubor MFC02View.cpp a změňte cview na CWinFormsView v IMPLEMENT_DYNCREATE makra a mapy zpráv a nahraďte existující prázdný konstruktor konstruktorem uvedeným níže:

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Sestavení a spuštění projektu.

   V **Průzkumníku řešení**klepněte pravým tlačítkem myši na knihovnu MFC02 a vyberte **příkaz Nastavit jako počáteční projekt**.

   V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   V nabídce **Ladění** klepněte na tlačítko **Start bez ladění**.

## <a name="see-also"></a>Viz také

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
