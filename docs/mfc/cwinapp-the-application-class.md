---
title: CWinApp – třída aplikace
ms.date: 11/04/2016
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: 8518e21a9fa6bcf5ac640cff25b17c5028046b06
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447019"
---
# <a name="cwinapp-the-application-class"></a>CWinApp – třída aplikace

Hlavní třída aplikace v knihovně MFC zapouzdřuje inicializaci, spuštění a ukončení aplikace pro operační systém Windows. Aplikace postavená na rozhraní musí mít jeden a jenom jeden objekt třídy odvozené z [CWinApp](../mfc/reference/cwinapp-class.md). Tento objekt je vytvořen před vytvořením systému Windows.

`CWinApp` je odvozen od `CWinThread`, která představuje hlavní vlákno provádění aplikace, což může mít jeden nebo více vláken. V posledních verzích knihovny MFC jsou členské funkce `InitInstance`, **Run**, `ExitInstance`a `OnIdle` ve skutečnosti ve třídě `CWinThread`. Tyto funkce jsou popsány zde, jako kdyby byly místo toho `CWinApp` členy, protože diskuze se týká role objektu jako objekt aplikace, nikoli jako primární vlákno.

> [!NOTE]
>  Vaše třída aplikace představuje primární podproces provádění vaší aplikace. Pomocí funkcí Win32 API můžete také vytvořit sekundární vlákna provádění. Tato vlákna mohou používat knihovnu MFC. Další informace naleznete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Podobně jako jakýkoli program pro operační systém Windows má vaše aplikace architektury funkci `WinMain`. V aplikaci architektury však nepíšete `WinMain`. Je dodávána knihovnou tříd a je volána při spuštění aplikace. `WinMain` provádí standardní služby, jako je například registrace tříd oken. Pak zavolá členské funkce objektu Application k inicializaci a spuštění aplikace. (Můžete přizpůsobit `WinMain` přepsáním `CWinApp` členských funkcí, které `WinMain` volání.)

Pro inicializaci aplikace `WinMain` volá `InitApplication` `InitInstance` a členské funkce objektu aplikace. Chcete-li spustit smyčku zpráv aplikace, `WinMain` volá členskou funkci **Run** . Při ukončení `WinMain` volá členskou funkci `ExitInstance` objektu aplikace.

> [!NOTE]
>  Názvy zobrazené **tučně** v této dokumentaci označují prvky dodávané knihovna Microsoft Foundation Class a vizuálu C++. Názvy zobrazené v `monospaced` typ označují prvky, které můžete vytvořit nebo přepsat.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp a průvodce aplikací MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Speciální služby CWinApp](../mfc/special-cwinapp-services.md)
