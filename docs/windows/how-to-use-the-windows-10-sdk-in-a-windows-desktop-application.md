---
title: 'Postupy: použití sady Windows 10 SDK v desktopové aplikaci systému Windows'
description: Jak nastavit cílovou verzi sady SDK v projektu desktopové aplikace systému Windows tak, aby používala sadu Windows 10 SDK.
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725731"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Postupy: použití sady Windows 10 SDK v desktopové aplikaci systému Windows

Když vytvoříte nový klasický desktopový projekt Windows v sadě Visual Studio, cílí na Windows 10 SDK ve výchozím nastavení. Sada Visual Studio nainstaluje verzi této sady SDK při instalaci C++ desktopové úlohy. Sada Windows 10 SDK podporuje psaní kódu pro Windows 7 SP1 a novější. Další informace o cílení na konkrétní verze systému Windows naleznete v tématu [použití hlaviček Windows](/windows/win32/WinProg/using-the-windows-headers) a [aktualizace winver a _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

Pokud upgradujete existující projekt, máte možnost volby: můžete dál používat cílovou Windows SDK určenou v projektu. Nebo můžete změnit cíl projektu tak, aby používal sadu Windows 10 SDK. S Windows 10 SDK získáte výhody podpory pro nejnovější operační systémy a jazykové standardy.

## <a name="use-the-right-windows-sdk-for-your-project"></a>Použití pravé Windows SDK pro váš projekt

Počínaje sadou Visual Studio 2015 se knihovna modulu runtime jazyka C (CRT) rozdělila na dvě části: jedna součást, ucrtbase, obsahuje standardní funkce CRT specifické pro jazyk C a Microsoft, které můžete použít v univerzálních aplikacích pro Windows. Tato knihovna je nyní známá jako Universal CRT nebo UCRT a přesunula se do sady Windows 10 SDK. UCRT obsahuje mnoho nových funkcí, například funkce C99, které jsou potřeba pro podporu nejnovějších C++ jazykových standardů. Druhá část původní CRT je vcruntime. Obsahuje běhovou podporu C, spouštěcí a ukončovací kód a všechno ostatní, co se do UCRT nedostalo. Knihovna vcruntime se nainstaluje společně s C++ kompilátorem a sadou nástrojů v sadě Visual Studio. Další informace najdete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

UCRT je teď systémová komponenta, která je nainstalovaná v každé verzi Windows 10. Je dostupná taky jako instalovatelný komponenta pro všechny dřívější podporované verze Windows. Sadu Windows 10 SDK můžete použít k zacílení na všechny podporované verze systému Windows. Úplný seznam podporovaných operačních systémů najdete v tématu [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Chcete-li změnit cílení projektů tak, aby používaly sadu Windows 10 SDK při upgradu z verze projektu před sadou Visual Studio 2015, postupujte podle následujících kroků:

### <a name="to-target-the-windows-10-sdk"></a>Zaměření na sadu Windows 10 SDK

1. Ujistěte se, že je nainstalovaná sada Windows 10 SDK. Sada Windows 10 SDK je nainstalovaná jako součást  **C++ vývoje desktopových** aplikací. Samostatná verze je k dispozici na webu [soubory ke stažení a nástroje pro Windows 10](https://developer.microsoft.com/windows/downloads).

1. Otevřete místní nabídku uzlu projektu a vyberte **změnit cílení projektů**. (V dřívějších verzích sady Visual Studio klikněte na **změnit cílovou verzi sady SDK**.) Zobrazí se dialogové okno **Kontrola akcí řešení** .

   ![Zkontrolovat akce řešení](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. V rozevíracím seznamu **verze cílové platformy** vyberte verzi sady Windows 10 SDK, na kterou chcete cílit. Obecně řečeno, doporučujeme zvolit nejnovější nainstalovanou verzi. Kliknutím na tlačítko **OK** použijte změnu.

   8,1 v tomto kontextu odkazuje na sadu SDK Windows 8.1.

   V případě úspěchu tohoto kroku se zobrazí následující text v okně výstup:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. Otevřete dialogové okno Vlastnosti projektu. V části **Vlastnosti konfigurace** > **Obecné** si všimněte hodnot **verze cílové platformy Windows**. Změna hodnoty zde má stejný účinek jako následující postup. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](../build/reference/general-property-page-project.md).

   ![Verze cílové platformy](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Tato akce změní hodnoty maker projektu, které obsahují cesty k hlavičkovým souborům a souborům knihoven. Chcete-li zjistit, co se změnilo, otevřete oddíl **vizuálních C++ adresářů** v dialogovém okně **vlastností projektu** . Vyberte jednu z vlastností, například **adresáře include**. Pak otevřete rozevírací seznam hodnota vlastnosti a vyberte **\<upravit >** . Zobrazí se dialogové okno **Zahrnout adresáře** .

   ![Zahrnout adresáře – dialogové okno](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Klikněte na tlačítko **makra > >** a posuňte se dolů seznam maker na makra Windows SDK, aby se zobrazily všechny nové hodnoty.

   ![Windows SDK makra](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. Opakujte postup změny cíle pro ostatní projekty řešení podle potřeby a znovu sestavte řešení.

### <a name="to-target-the-windows-81-sdk"></a>Zaměření na sadu Windows 8.1 SDK

1. Otevřete místní nabídku uzlu projektu v Průzkumník řešení a vyberte **změnit cílení projektů**. (V dřívějších verzích sady Visual Studio klikněte na **změnit cílovou verzi sady SDK**.)

2. V rozevíracím seznamu **verze cílové platformy** vyberte **8,1**.

## <a name="see-also"></a>Viz také:

[Návod: vytvoření tradiční desktopové aplikace systému WindowsC++()](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
