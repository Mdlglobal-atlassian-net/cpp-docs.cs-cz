---
title: 'CWinApp: Třída aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6b076798c9ad07a8ca8da1a898c263997e27fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414586"
---
# <a name="cwinapp-the-application-class"></a>CWinApp – třída aplikace

Třída hlavní aplikace v prostředí MFC zapouzdřuje inicializace, spuštění a ukončení aplikace operačního systému Windows. Aplikace založená na rozhraní musí mít jeden a pouze jeden objekt třídy odvozené z [CWinApp](../mfc/reference/cwinapp-class.md). Tento objekt je vytvořen před vytvořením systému windows.

`CWinApp` je odvozen z `CWinThread`, která představuje hlavní vlákno provádění pro vaši aplikaci, která může mít jeden nebo více vláken. V nejnovější verze knihovny MFC `InitInstance`, **spustit**, `ExitInstance`, a `OnIdle` členské funkce jsou ve skutečnosti ve třídě `CWinThread`. Tyto funkce jsou popsány zde, jako by byly `CWinApp` členy místo, protože diskuse se týká objektu role jako objekt aplikace, nikoli jako primární vlákno.

> [!NOTE]
>  Třída vaší aplikace se považuje za primární vlákno provádění vaší aplikace. Pomocí funkce rozhraní Win32 API, můžete také vytvořit sekundární vlákna exekuce. Tato vlákna můžete použít knihovnu MFC. Další informace najdete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Stejně jako jakékoli programu operačního systému Windows, rozhraní framework aplikace má `WinMain` funkce. V rozhraní framework aplikace, ale nenapíšete `WinMain`. Zadaná pomocí knihovny tříd a je volána při spuštění aplikace. `WinMain` provede standardním službám, jako je registrace tříd oken. Poté zavolá členské funkce objektu aplikace k inicializaci a spuštění aplikace. (Můžete přizpůsobit `WinMain` tak, že přepíšete `CWinApp` členské funkce, která `WinMain` volání.)

Inicializace aplikace, `WinMain` volá objekt aplikace `InitApplication` a `InitInstance` členské funkce. Ke spuštění aplikace smyčky zpráv, `WinMain` volání **spustit** členskou funkci. Při ukončení `WinMain` volá objekt aplikace `ExitInstance` členskou funkci.

> [!NOTE]
>  Názvy ukazuje **tučné** v této dokumentaci označuje prvky poskytnutých knihovny Microsoft Foundation Class a Visual C++. Názvy ukazuje `monospaced` typ označení elementy, které můžete vytvářet ani přepisovat.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp a průvodce aplikací MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Speciální služby CWinApp](../mfc/special-cwinapp-services.md)

