---
title: CWinApp Třída aplikace
ms.date: 11/04/2016
f1_keywords:
- CWinApp
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
ms.openlocfilehash: d9f0d4f5ba6b6b070b23ce98ecda8c7accf44934
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258707"
---
# <a name="cwinapp-the-application-class"></a>CWinApp Třída aplikace

Třída hlavní aplikace v prostředí MFC zapouzdřuje inicializace, spuštění a ukončení aplikace operačního systému Windows. Aplikace založená na rozhraní musí mít jeden a pouze jeden objekt třídy odvozené z [CWinApp](../mfc/reference/cwinapp-class.md). Tento objekt je vytvořen před vytvořením systému windows.

`CWinApp` je odvozen z `CWinThread`, která představuje hlavní vlákno provádění pro vaši aplikaci, která může mít jeden nebo více vláken. V nejnovější verze knihovny MFC `InitInstance`, **spustit**, `ExitInstance`, a `OnIdle` členské funkce jsou ve skutečnosti ve třídě `CWinThread`. Tyto funkce jsou popsány zde, jako by byly `CWinApp` členy místo, protože diskuse se týká objektu role jako objekt aplikace, nikoli jako primární vlákno.

> [!NOTE]
>  Třída vaší aplikace se považuje za primární vlákno provádění vaší aplikace. Pomocí funkce rozhraní Win32 API, můžete také vytvořit sekundární vlákna exekuce. Tato vlákna můžete použít knihovnu MFC. Další informace najdete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Stejně jako jakékoli programu operačního systému Windows, rozhraní framework aplikace má `WinMain` funkce. V rozhraní framework aplikace, ale nenapíšete `WinMain`. Zadaná pomocí knihovny tříd a je volána při spuštění aplikace. `WinMain` provede standardním službám, jako je registrace tříd oken. Poté zavolá členské funkce objektu aplikace k inicializaci a spuštění aplikace. (Můžete přizpůsobit `WinMain` tak, že přepíšete `CWinApp` členské funkce, která `WinMain` volání.)

Inicializace aplikace, `WinMain` volá objekt aplikace `InitApplication` a `InitInstance` členské funkce. Ke spuštění aplikace smyčky zpráv, `WinMain` volání **spustit** členskou funkci. Při ukončení `WinMain` volá objekt aplikace `ExitInstance` členskou funkci.

> [!NOTE]
>  Názvy ukazuje **tučné** v této dokumentaci označuje prvky poskytnutých knihovny Microsoft Foundation Class a Visual C++. Názvy ukazuje `monospaced` typ označení elementy, které můžete vytvářet ani přepisovat.

## <a name="see-also"></a>Viz také:

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp a průvodce aplikací MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Speciální služby CWinApp](../mfc/special-cwinapp-services.md)
