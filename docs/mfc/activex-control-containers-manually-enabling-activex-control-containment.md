---
title: 'ActiveX – kontejnery ovládacích prvků: Ruční povolení uzavření ovládacího prvku ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322063"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX – kontejnery ovládacích prvků: Ruční povolení uzavření ovládacího prvku ActiveX

Pokud jste při generování aplikace pomocí Průvodce aplikací knihovny MFC nepovolili podporu ovládacího prvku ActiveX, budete muset tuto podporu přidat ručně. Tento článek popisuje proces ručního přidání omezení ovládacího prvku ActiveX do existující aplikace kontejneru OLE. Pokud předem víte, že chcete podporu ovládacího prvku ActiveX v kontejneru OLE, přečtěte si článek [Vytvoření kontejneru ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

> [!NOTE]
> Tento článek používá projekt kontejneru ovládacího prvku ActiveX založený na dialogu s názvem Kontejner a vložený ovládací prvek s názvem Circ jako příklady v postupech a kódu.

Chcete-li podporovat ovládací prvky ActiveX, je nutné přidat jeden řádek kódu do dvou souborů projektu.

- Upravte funkci hlavního `InitInstance` dialogu (nalezenou v kontejneru. CPP) průvodcem aplikací knihovny MFC, který provádí volání [afxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), jako v následujícím příkladu:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Přidejte následující do projektu STDAFX. H hlavičkový soubor:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Po dokončení těchto kroků znovu vytvořte projekt kliknutím na **sestavení** v nabídce **Sestavení.**

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)
