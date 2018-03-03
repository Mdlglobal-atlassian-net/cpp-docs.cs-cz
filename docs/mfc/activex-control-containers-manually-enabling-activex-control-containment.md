---
title: "Kontejnery ovládacích prvků ActiveX: Ruční povolení uzavření ovládacího prvku ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf1ba1273a349f685b70fec6706b566c2b618f23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX – kontejnery ovládacích prvků: Ruční povolení uzavření ovládacího prvku ActiveX
Pokud jste nepovolili podporu ovládacích prvků ActiveX při vygenerování aplikace pomocí Průvodce aplikací MFC, bude mít tato podpora přidat ručně. Tento článek popisuje proces pro ruční přidání uzavření ovládacího prvku ActiveX na existující aplikaci kontejneru OLE. Pokud znáte předem chcete podporu ovládacích prvků ActiveX v kontejneru vaší OLE, najdete v článku [vytvoření kontejneru ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
> [!NOTE]
>  Tento článek používá na základě dialogové okno ActiveX řízení kontejneru projekt s názvem kontejneru a vloženému ovládacímu prvku s názvem str jako příklady v postupy a kódu.  
  
 Podpora ovládacích prvků ActiveX, musíte přidat jeden řádek kódu na dva soubory vašeho projektu.  
  
-   Upravit hlavním dialogu `InitInstance` – funkce (tuto možnost najdete v KONTEJNERU. CPP) pomocí Průvodce aplikací MFC, že zavoláte [AfxEnableControlContainer –](reference/ole-initialization.md#afxenablecontrolcontainer), jako v následujícím příkladu:  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   Přidejte následující STDAFX vašeho projektu. Soubor hlaviček H:  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 Po dokončení těchto kroků, znovu sestavte projekt kliknutím **sestavení** na **sestavení** nabídky.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

