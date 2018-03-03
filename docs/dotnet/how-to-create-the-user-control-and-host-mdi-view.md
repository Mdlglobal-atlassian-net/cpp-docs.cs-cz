---
title: "Postupy: vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8b9b3c8ff385aed22785386c035ed537d8d97e97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI
Následující postup popisuje vytvoření uživatelského ovládacího prvku rozhraní .NET Framework, vytváření uživatelského ovládacího prvku v knihovnu tříd ovládacího prvku (konkrétně knihovny ovládacích prvků Windows projekt) a pak kompilace projektu do sestavení. Ovládací prvek může být používán pak z aplikace MFC, která používá třídy odvozené od třídy [CView – třída](../mfc/reference/cview-class.md) a [CWinFormsView třída](../mfc/reference/cwinformsview-class.md).  
  
 Informace o postupu při vytvoření uživatelského ovládacího prvku Windows Forms a vytváření knihovny tříd řízení najdete v tématu [postupy: vytváření uživatelských ovládacích prvků](/dotnet/framework/winforms/controls/how-to-author-composite-controls).  
  
> [!NOTE]
>  V některých případech nemusí ovládací prvky Windows Forms, jako je například ovládacího prvku mřížky třetích stran chovat spolehlivě, pokud hostované v aplikaci MFC. Doporučené řešení je umístit uživatelského ovládacího prvku Windows Forms v aplikaci MFC a umístěte ovládací prvek mřížky třetích stran v rámci uživatelského ovládacího prvku.  
  
 Tento postup předpokládá, že jste vytvořili projekt Windows Forms – ovládací prvky knihovny s názvem WindowsFormsControlLibrary1, podle postupu v [postupy: vytvoření uživatelského ovládacího prvku a vložení v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Chcete-li vytvořit hostitelskou aplikaci MFC  
  
1.  Vytvoření aplikace knihovny MFC projektu.  
  
     Na **soubor** nabídce vyberte možnost **nový**a potom klikněte na **projektu**. V **Visual C++** složky, vyberte **aplikace knihovny MFC**.  
  
     V **název** zadejte `MFC02` a změňte **řešení** nastavení **přidat do řešení**. Click **OK**.  
  
     V **Průvodce aplikací knihovny MFC**přijměte všechny výchozí hodnoty a pak klikněte na tlačítko **Dokončit**. Tím se vytvoří aplikace knihovny MFC rozhraní více dokumentů.  
  
2.  Konfigurace projektu pro podporu Common Language Runtime (CLR).  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `MFC01` uzel projektu a vyberte **vlastnosti** v místní nabídce. **Stránky vlastností** zobrazí se dialogové okno.  
  
     V části **vlastnosti konfigurace**, vyberte **Obecné**. V části **výchozí projekt** nastavte **podpory Common Language Runtime** k **Podpora Common Language Runtime (/ clr)**.  
  
     V části **vlastnosti konfigurace**, rozbalte položku **C/C++** a klikněte na tlačítko **Obecné** uzlu. Nastavit **ladění formátu informací** k **programu databáze (/Zi)**.  
  
     Klikněte **generování kódu** uzlu. Nastavit **povolit minimální opětovné sestavení** k **ne (/ Gm –)**. Nastavte také **základní kontroluje Runtime** k **výchozí**.  
  
     Klikněte na tlačítko **OK** proveďte změny.  
  
3.  V stdafx.h přidejte následující řádek:  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  Přidáte odkaz na ovládací prvek .NET.  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `MFC02` uzel projektu a vyberte **přidat**, **odkazy**. V **stránka vlastností**, klikněte na tlačítko **přidat nový odkaz**, vyberte WindowsFormsControlLibrary1 (v části **projekty** kartě) a klikněte na tlačítko **OK** . Tento příkaz přidá odkaz ve formě [/FU](../build/reference/fu-name-forced-hash-using-file.md) tak, aby se kompilace programu – možnost kompilátoru; také zkopíruje WindowsFormsControlLibrary1.dll do `MFC02` adresáře projektu tak, aby se bude program spouštět.  
  
5.  Ve stdafx.h vyhledejte tento řádek:  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Přidejte tyto řádky nad ním:  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Upravte zobrazení třídy tak, aby dědila z [CWinFormsView](../mfc/reference/cwinformsview-class.md).  
  
     V MFC02View.h nahraďte [CView](../mfc/reference/cview-class.md) s [CWinFormsView](../mfc/reference/cwinformsview-class.md) tak, aby se kód zobrazí takto:  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     Pokud chcete přidat další zobrazení do vaší aplikace MDI, budete muset volat [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pro každý zobrazení, které vytvoříte.  
  
7.  Upravte soubor MFC02View.cpp změnit CView na CWinFormsView v IMPLEMENT_DYNCREATE – makro a mapy zpráv a nahradit stávající prázdný konstruktor s konstruktorem vidíte níže:  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  Sestavte a spusťte projekt.  
  
     V **Průzkumníku řešení**, klikněte pravým tlačítkem na MFC02 a vyberte **nastavit jako spouštěný projekt**.  
  
     Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
## <a name="see-also"></a>Viz také  
 [Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)