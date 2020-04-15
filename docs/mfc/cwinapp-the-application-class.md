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
ms.openlocfilehash: 007a4e53fd9b3eae612947cd76ee352776572d4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373528"
---
# <a name="cwinapp-the-application-class"></a>CWinApp – třída aplikace

Hlavní třída aplikace v knihovně MFC zapouzdřuje inicializaci, spuštění a ukončení aplikace pro operační systém Windows. Aplikace postavená na rámci musí mít jeden a pouze jeden objekt třídy odvozené z [CWinApp](../mfc/reference/cwinapp-class.md). Tento objekt je vytvořen před vytvořením oken.

`CWinApp`je odvozen `CWinThread`od , který představuje hlavní vlákno provádění pro vaši aplikaci, která může mít jeden nebo více podprocesů. V posledních verzích knihovny `InitInstance`MFC , `OnIdle` **Spustit**, `ExitInstance`a `CWinThread`členské funkce jsou ve skutečnosti ve třídě . Tyto funkce jsou zde popsány, jako by byly `CWinApp` členy místo, protože diskuse se týká role objektu jako aplikační objekt, nikoli jako primární vlákno.

> [!NOTE]
> Vaše třída aplikace představuje primární vlákno spuštění aplikace. Pomocí funkcí rozhraní API Win32 můžete také vytvořit sekundární vlákna provádění. Tato vlákna můžete použít knihovnu knihovny knihovny Knihovny mfc. Další informace naleznete v tématu [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Stejně jako jakýkoli program pro operační systém `WinMain` Windows, vaše framework aplikace má funkci. V rámcové aplikaci však nepíšete `WinMain`. Dodává se knihovnou tříd a volá se při spuštění aplikace. `WinMain`provádí standardní služby, jako je registrace tříd oken. Potom volá členské funkce objektu aplikace k inicializaci a spuštění aplikace. (Můžete přizpůsobit `WinMain` přepsáním `CWinApp` členských `WinMain` funkcí, které volají.)

Chcete-li aplikaci `WinMain` inicializovat, `InitApplication` zavolá `InitInstance` funkce objektu aplikace a členské funkce. Chcete-li spustit smyčku `WinMain` zpráv aplikace, volání **spustit** členovou funkci. Při ukončení `WinMain` volá člennou `ExitInstance` funkci aplikačního objektu.

> [!NOTE]
> Názvy zobrazené **tučně** v této dokumentaci označují prvky dodané knihovnou tříd Microsoft Foundation a visual c++. Názvy `monospaced` zobrazené v textu označují prvky, které vytvoříte nebo přepíšete.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp a průvodce aplikací MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Speciální služby CWinApp](../mfc/special-cwinapp-services.md)
