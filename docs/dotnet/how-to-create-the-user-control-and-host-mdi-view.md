---
title: 'Postupy: Vytvoření uživatelského ovládacího prvku a hostování zobrazení MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 634dd9c1ad2ce9199cec0dfa7ef067bd45f242f6
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630838"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Postupy: Vytvoření uživatelského ovládacího prvku a hostování zobrazení MDI

Následující kroky ukazují, jak vytvořit .NET Framework uživatelský ovládací prvek, vytvořit uživatelský ovládací prvek v knihovně třídy ovládacího prvku (konkrétně v projektu knihovny ovládacích prvků systému Windows) a potom zkompilovat projekt do sestavení. Ovládací prvek lze následně spotřebovat z aplikace MFC, která používá třídy odvozené od [třídy CView](../mfc/reference/cview-class.md) a [třídy CWinFormsView](../mfc/reference/cwinformsview-class.md).

Informace o tom, jak vytvořit uživatelský ovládací prvek model Windows Forms a vytvořit knihovnu tříd ovládacího prvku, naleznete [v tématu How to: Vytváření uživatelských ovládacích](/dotnet/framework/winforms/controls/how-to-author-composite-controls)prvků.

> [!NOTE]
>  V některých případech se model Windows Forms ovládací prvky, jako je například ovládací prvek mřížky jiného výrobce, nemusí chovat spolehlivě při hostování v aplikaci knihovny MFC. Doporučeným řešením je umístit uživatelský ovládací prvek model Windows Forms do aplikace MFC a umístit ovládací prvek mřížky třetí strany do uživatelského ovládacího prvku.

Tento postup předpokládá, že jste vytvořili projekt knihovny model Windows Forms Controls s názvem WindowsFormsControlLibrary1, podle postupu v [tématu How to: Vytvořte uživatelský ovládací prvek a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Vytvoření hostitelské aplikace MFC

1. Vytvořte projekt aplikace MFC.

   V nabídce **soubor** vyberte **Nový**a pak klikněte na **projekt**. Ve složce **vizuálu C++**  vyberte možnost **aplikace MFC**.

   Do pole **název** zadejte `MFC02` a změňte nastavení **řešení** na možnost **Přidat do řešení**. Klikněte na **OK**.

   V **Průvodci aplikací knihovny MFC**přijměte všechny výchozí hodnoty a potom klikněte na tlačítko **Dokončit**. Tím se vytvoří aplikace MFC s rozhraním více dokumentů.

1. Nakonfigurujte projekt pro podporu modulu CLR (Common Language Runtime).

   V **Průzkumník řešení**klikněte pravým tlačítkem myši `MFC01` na uzel projektu a v místní nabídce vyberte možnost **vlastnosti** . Zobrazí se dialogové okno **stránky vlastností** .

   V části **Vlastnosti konfigurace**vyberte **Obecné**. V části **výchozí nastavení projektu** nastavte podporu **modulu CLR (Common Language Runtime)** na **podporu modulu CLR (/CLR)** .

   V části **Vlastnosti konfigurace**rozbalte **C/C++**  a klikněte na uzel **Obecné** . Nastavte **formát ladicích informací** na **programovou databázi (/Zi)** .

   Klikněte na uzel **generování kódu** . Nastavte **možnost povolit minimální opětovné sestavení** na **ne (/GM-)** . Nastavte také **základní kontroly za běhu** na **výchozí**.

   Změny se projeví po kliknutí na **OK** .

1. V souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší) přidejte následující řádek:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Přidejte odkaz na ovládací prvek .NET.

   V **Průzkumník řešení**klikněte pravým tlačítkem myši `MFC02` na uzel projektu a vyberte **Přidat**, **odkazy**. Na **stránce vlastností**klikněte na **Přidat nový odkaz**, vyberte WindowsFormsControlLibrary1 (na kartě **projekty** ) a klikněte na **OK**. Tím se přidá odkaz ve formuláři Možnosti kompilátoru [/Fu](../build/reference/fu-name-forced-hash-using-file.md) , takže program se zkompiluje. také zkopíruje WindowsFormsControlLibrary1. dll do `MFC02` adresáře projektu, takže se program spustí.

1. V souboru stdafx. h vyhledejte tento řádek:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Přidejte tyto řádky nad něj:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Upravte třídu zobrazení tak, aby dědila z [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   V MFC02View. h nahraďte [CView](../mfc/reference/cview-class.md) pomocí [CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, že se kód zobrazí takto:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Pokud chcete přidat další zobrazení do aplikace MDI, budete muset volat [CWinApp:: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pro každé zobrazení, které vytvoříte.

1. Upravte soubor MFC02View. cpp pro změnu CView na CWinFormsView v makru IMPLEMENT_DYNCREATE a mapě zpráv a nahraďte existující prázdný konstruktor následujícím konstruktorem:

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Sestavte a spusťte projekt.

   V **Průzkumník řešení**klikněte pravým tlačítkem na MFC02 a vyberte **nastavit jako spouštěný projekt**.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   V nabídce **ladit** klikněte na **Spustit bez ladění**.

## <a name="see-also"></a>Viz také:

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
