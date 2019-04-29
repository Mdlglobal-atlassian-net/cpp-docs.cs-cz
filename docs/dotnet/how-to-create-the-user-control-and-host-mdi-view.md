---
title: 'Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 7d535fce47be5504f6f521cda1267344206287da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387432"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI

Následující kroky ukazují, jak vytvořit uživatelský ovládací prvek rozhraní .NET Framework, ovládací prvek v knihovně tříd ovládacího prvku (konkrétně v projektu knihovny ovládacích prvků Windows) a poté zkompilovat projekt do sestavení. Ovládací prvek může být potom používán z aplikace knihovny MFC, která používá třídy odvozené z [CView Class](../mfc/reference/cview-class.md) a [CWinFormsView – třída](../mfc/reference/cwinformsview-class.md).

Informace o tom, jak vytvořit uživatelský ovládací prvek Windows Forms a vytvořit knihovnu tříd ovládacího prvku, naleznete v tématu [jak: Vytváření uživatelských ovládacích prvků](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
>  V některých případech se ovládací prvky Windows Forms, jako je například ovládací prvek mřížky jiného výrobce, pravděpodobně nebudou chovat spolehlivě když jsou hostované v aplikaci MFC. Doporučené řešení je umístit uživatelský ovládací prvek Windows Forms do aplikace knihovny MFC a umístit ovládací prvek mřížky jiného výrobce do uživatelského ovládacího prvku.

Tento postup předpokládá, že jste vytvořili projekt Knihovna ovládacích prvků Windows Forms s názvem WindowsFormsControlLibrary1, podle postupu v [jak: Vytvoření uživatelského ovládacího prvku a hostitele v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci knihovny MFC

1. Vytvořte projekt aplikace knihovny MFC.

   Na **souboru** nabídce vyberte možnost **nový**a potom klikněte na tlačítko **projektu**. V **Visual C++** složky, vyberte **aplikace knihovny MFC**.

   V **název** zadejte `MFC02` a změnit **řešení** nastavení **přidat do řešení**. Klikněte na **OK**.

   V **Průvodce aplikací knihovny MFC**, přijměte všechny výchozí hodnoty a klikněte na **Dokončit**. Tím se vytvoří aplikace knihovny MFC s rozhraním více dokumentů.

1. Konfigurace projektu pro podporu Common Language Runtime (CLR).

   V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `MFC01` uzel projektu a vyberte **vlastnosti** v místní nabídce. **Stránky vlastností** zobrazí se dialogové okno.

   V části **vlastnosti konfigurace**vyberte **Obecné**. V části **výchozí nastavení projektu** nastavte **Common Language Runtime support** k **Common Language Runtime Support (/ clr)**.

   V části **vlastnosti konfigurace**, rozbalte **C/C++** a klikněte na tlačítko **Obecné** uzlu. Nastavte **formát ladicích informací** k **Program Database (/Zi)**.

   Klikněte na tlačítko **generování kódu** uzlu. Nastavte **povolit minimální opětovné sestavení** k **ne (/ Gm-)**. Nastavit také **Basic Runtime Checks** k **výchozí**.

   Klikněte na tlačítko **OK** změny.

1. Ve stdafx.h přidejte následující řádek:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Přidejte odkaz na ovládací prvek .NET.

   V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `MFC02` uzel projektu a vyberte **přidat**, **odkazy**. V **stránku vlastností**, klikněte na tlačítko **přidat nový odkaz**, vyberte WindowsFormsControlLibrary1 (v části **projekty** kartu) a klikněte na tlačítko **OK** . To přidá odkaz ve formuláři [/FU](../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru tak, že program bude kompilován; také zkopíruje WindowsFormsControlLibrary1.dll do `MFC02` adresáře projektu tak, aby se bude program spouštět.

1. Ve stdafx.h vyhledejte tento řádek:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Přidejte tyto řádky nad něj:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Upravte zobrazení třídy tak, aby dědila z [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   V MFC02View.h nahraďte [CView](../mfc/reference/cview-class.md) s [CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, aby kód se zobrazí takto:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Pokud chcete přidat další zobrazení do vaší aplikace MDI, budete muset volat [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pro každé zobrazení, které vytvoříte.

1. Upravte soubor MFC02View.cpp tak, že změníte CView na CWinFormsView v makru IMPLEMENT_DYNCREATE a mapování zpráv a nahradit stávající prázdný konstruktor za konstruktor uvedený níže:

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

   V **Průzkumníka řešení**, pravým tlačítkem myši na MFC02 a vyberte **nastavit jako spouštěný projekt**.

   Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

## <a name="see-also"></a>Viz také:

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
