---
title: Synchronizace změn mezi platformou Xcode a sadou Visual Studio
ms.date: 10/17/2019
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.openlocfilehash: ab941551c519acee49f658d8a8ff1b9fe0e4ba49
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177533"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronizace změn mezi platformou Xcode a sadou Visual Studio

Vývoj mobilních aplikací pomocí C++ součástí sady Visual Studio zahrnuje vzdálené možnosti synchronizace vaší práce mezi vaším počítačem a vaším počítačem Mac. Při párování vašich počítačů s Visual Studiem a Mac jsou k dispozici nové možnosti pro projekty aplikací pro iOS v aplikaci Visual Studio, které můžete použít k otevření projektu v Xcode, přesunutí kódu mezi Xcode a Visual Studio a vyčištění dočasného adresáře projektu Xcode.

Použití možností vzdálený počítač, váš projekt musí být projekt aplikace pro iOS a sady Visual Studio musí být párována s vašeho macu. Požadavky a pokyny, jak spárovat počítač Mac, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>V nabídce vzdáleného počítače

V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt aplikace pro iOS, aby se zobrazila kontextová nabídka. Vyberte položku **vzdálený počítač** , aby se zobrazily dostupné možnosti vzdáleného počítače.

![Položka nabídky se vzdáleným počítačem v Průzkumník řešení](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "Položka nabídky se vzdáleným počítačem v Průzkumník řešení")

Tyto příkazy umožňují otevřít projekt v Xcode, přesunout místní změny nebo celý projekt mezi Visual Studio a Xcode a vyčistit dočasné soubory na vzdáleném počítači.

## <a name="open-in-xcode"></a>Otevřít v Xcode

Chcete-li projekt otevřít v Xcode ze sady Visual Studio, v podnabídce **vzdálený počítač** vyberte možnost **otevřít v Xcode** a otevřete vybraný projekt na spárovaném vzdáleném počítači. Server `vcremote` slouží k otevření Xcode na Macu a přechodu do dočasného adresáře vytvořeného na počítači Mac, který obsahuje kopii projektu. Visual Studio se zobrazí dialogové okno zobrazující dočasný adresář pro projekt používá. Akce prováděné na vzdáleném počítači jsou také zobrazeny v okně **výstup** v aplikaci Visual Studio. Chcete-li je zobrazit, může být nutné vybrat možnost  **C++ Visual Remote Machine** v rozevíracím seznamu **Zobrazit výstup z** v horní části okna **výstup** .

![V okně výstup se zobrazí akce vzdáleného počítače.](../cross-platform/media/cppmdd-u2-remotemachine-output.png "V okně výstup se zobrazí akce vzdáleného počítače.")

Na Macu můžete použít všechny nástroje Xcode k úpravě kódu a prostředků, scénářů a akcí. V aplikaci Visual Studio je projekt aplikace pro iOS poznámkou "otevřeno v Xcode", aby označoval, že se na vzdáleném počítači mohou provádět změny. Po dokončení úprav můžete stahování ze vzdáleného počítače nebo přírůstkové načítat vzdálené příkazy pro kopírování změn zpět do projektu sady Visual Studio.

## <a name="push-to-remote-and-incremental-push-to-remote"></a>Vložit do vzdálené a přírůstkové nabízení na vzdálený počítač

Pokud jste provedli změny pro váš projekt aplikace pro iOS v sadě Visual Studio, přírůstkové vložení do vzdálených příkazů a metodou Push do vzdáleného umožňuje přesunout soubory změněné projektu na spárovaném vzdálený počítač. Nasdílení změn do vzdáleného příkazu zkopíruje všechny soubory projektu do vzdáleného počítače. Přírůstkové vložit do vzdáleného příkazu zkopíruje jen změněné soubory na vzdálený počítač. Pro velké projekty s malým změnám přírůstkové příkaz šetří čas a šířky pásma.

Chcete-li zkopírovat soubory projektu do počítače Mac, v aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace pro iOS a otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte buď možnost **Push na vzdálené** , nebo **přírůstkové vložení na vzdáleném** počítači, kde se zkopírují soubory projektu ze sady Visual Studio do vašeho počítače Mac.

## <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Vyžádání ze vzdáleného a přírůstkové stahování ze vzdáleného počítače

Až provedete změny projektu v Xcode, přesuňte změny zpět do sady Visual Studio a udržujte projekty synchronizované.

Chcete-li zkopírovat soubory projektu z počítače Mac, v aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace pro iOS a otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte buď možnost získat **ze vzdáleného** počítače, nebo **přírůstkové stahování ze vzdáleného úložiště** a zkopírujte soubory projektu z počítače Mac do sady Visual Studio.

## <a name="clean-remote"></a>Vyčistit vzdálený počítač

Vyčistit vzdálený příkaz slouží k odstranění souborů v adresáři dočasné projektu ve vzdáleném počítači. Obsah adresáře, včetně žádné zdrojové soubory nebo sestavení produkty, odeberou se na vašem počítači Mac. Ujistěte se, že všechny změny, které chcete zachovat zpět do sady Visual Studio s použitím o přijetí změn ze vzdáleného ani přírůstkové přijmout jejich změny ze vzdáleného před použitím příkazu vyčistit vzdálený nebyly synchronizovány.

Chcete-li vyčistit dočasný adresář projektu na vzdáleném počítači, v aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace pro iOS a otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte možnost **vyčistit vzdálené** pro odebrání souborů adresáře projektu z počítače Mac.
