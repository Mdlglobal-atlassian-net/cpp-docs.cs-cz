---
title: 'Postupy: Použití sady Windows 10 SDK v desktopové aplikaci pro Windows'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 8dbf18d24c0369507743c3c1da624838f9ab4703
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513818"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Postupy: Použití sady Windows 10 SDK v desktopové aplikaci pro Windows

Když vytvoříte klasický desktopový projekt Windows v sadě Visual Studio 2017, nastaví se ve výchozím nastavení pro sestavení s verzí sady Windows 10 SDK, která byla nainstalována při instalaci nebo poslední C++ aktualizaci úlohy desktopu. Tato verze Windows SDK je kompatibilní se systémem Windows 7 nebo novějším. Další informace o cílení na konkrétní verze Windows najdete v tématu [použití hlaviček Windows](/windows/win32/WinProg/using-the-windows-headers) .

Pokud chcete cílit na starší verzi sady SDK, můžete otevřít **projekt | Vlastnosti** a vyberte si z dalších verzí sady SDK, které jsou k dispozici v rozevírací nabídce Windows SDKá verze.

Počínaje sadou Visual Studio 2015 a sadou Windows 10 SDK byla Knihovna CRT rozdělena do dvou částí (ucrtbase), která obsahuje funkce, které jsou přijatelné pro použití v univerzálních aplikacích pro Windows, a jednu, která obsahuje vše jiného (knihovny vcruntime140). Vzhledem k tomu, že sada Windows 10 SDK obsahuje nové funkce, například mnoho funkcí C99, je třeba provést tyto kroky, aby bylo možné tyto funkce používat. Viz [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

### <a name="to-target-the-windows-10-sdk"></a>Zaměření na sadu Windows 10 SDK

1. Ujistěte se, že je nainstalovaná sada Windows 10 SDK. Sada Windows 10 SDK je nainstalovaná jako součást **vývoje C++ desktopových** aplikací. Samostatná verze je k dispozici na webu [soubory ke stažení a nástroje pro Windows 10](https://developer.microsoft.com/windows/downloads).

2. Otevřete místní nabídku uzlu projektu a vyberte možnost **změnit cílovou verzi sady SDK**.

   ![Změnit cílovou verzi sady SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   Zobrazí se dialogové okno **Kontrola akcí řešení** .

   ![Zkontrolovat akce řešení](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. V rozevíracím seznamu **verze cílové platformy** vyberte verzi sady Windows 10 SDK, na kterou chcete cílit. Kliknutím na tlačítko OK použijte změnu.

   Všimněte si, že 8,1 v tomto kontextu odkazuje na verzi Windows SDK, která je také zpětně kompatibilní se systémy Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 a Windows Vista.

   V případě úspěchu tohoto kroku se zobrazí následující text v okně výstup:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. Otevřete vlastnosti projektu a v části **Vlastnosti konfigurace, obecné** si všimněte hodnot **verze Windows Target Platform**. Změna hodnoty zde má stejný účinek jako následující postup. Viz [Obecná stránka vlastností (projekt)](../build/reference/general-property-page-project.md).

   ![Verze cílové platformy](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Tato akce změní hodnoty maker projektu, které obsahují cesty k hlavičkovým souborům a souborům knihoven. Chcete-li zjistit, co se změnilo, vyberte v části **Visual C++**  Directory v dialogovém okně **Vlastnosti projektu** jednu z vlastností, jako je například **Adresář include**, vyberte možnost otevřít rozevírací seznam a vyberte \<možnost Upravit >. Zobrazí se dialogové okno **Zahrnout adresáře** .

   ![Zahrnout adresáře – dialogové okno](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Klikněte na tlačítko **makra > >** a posuňte se dolů seznam maker na makra Windows SDK, aby se zobrazily všechny nové hodnoty.

   ![Windows SDK makra](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. V případě potřeby opakujte pro ostatní projekty a znovu sestavte řešení.

### <a name="to-target-the-windows-81-sdk"></a>Zaměření na sadu Windows 8.1 SDK

1. Otevřete místní nabídku uzlu projektu a vyberte možnost **změnit cílovou verzi sady SDK**.

2. V rozevíracím seznamu **verze cílové platformy** vyberte **8,1**.

## <a name="see-also"></a>Viz také:

[Desktopové aplikace pro Windows C++(Visual)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)