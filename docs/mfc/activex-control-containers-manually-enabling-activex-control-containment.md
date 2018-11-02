---
title: 'ActiveX – kontejnery ovládacích prvků: Ruční povolení uzavření ovládacího prvku ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 1fdf27975516715ea350af1f917eb43179f3e6d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510116"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX – kontejnery ovládacích prvků: Ruční povolení uzavření ovládacího prvku ActiveX

Pokud jste nepovolili podporu ovládacích prvků ActiveX při generování aplikace pomocí Průvodce aplikací MFC, budete muset ručně přidat tuto podporu. Tento článek popisuje postup pro ruční přidání používání kontejnerů ovládacích prvků ActiveX do stávající aplikace kontejneru OLE. Pokud víte předem, který má podporu ovládacích prvků ActiveX v kontejneru OLE, najdete v článku [vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

> [!NOTE]
>  Tento článek používá založené na dialogu ActiveX ovládací prvek kontejneru projekt s názvem kontejneru a vloženému ovládacímu prvku s názvem KR jako příklady v procedurách a kódu.

Podpora ovládacích prvků ActiveX, je nutné přidat jeden řádek kódu do dvou souborů projektu.

- Upravit hlavním dialogu `InitInstance` – funkce (nacházející se v KONTEJNERU. CPP) pomocí Průvodce aplikací knihovny MFC provedením volání do [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), jako v následujícím příkladu:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Přidejte do projektu STDAFX následující. H hlavičkový soubor:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Po dokončení těchto kroků znovu sestavit projekt kliknutím **sestavení** na **sestavení** nabídky.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

