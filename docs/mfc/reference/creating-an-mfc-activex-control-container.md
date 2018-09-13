---
title: Vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.container
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7167f00e3abf74d4638bc79615d68ed81fafabf9
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535116"
---
# <a name="creating-an-mfc-activex-control-container"></a>Vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC
Kontejneru ovládacího prvku ActiveX je nadřazené program, který poskytuje prostředí pro ovládací prvek ActiveX (dříve OLE) ke spuštění. Můžete vytvořit aplikaci může obsahovat ovládací prvky ActiveX s nebo bez knihovny MFC, ale je mnohem jednodušší provádět pomocí knihovny MFC.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](../activex-controls.md).  
  
 Vytvoření kontejneru program knihovny MFC pomocí [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md) umožňuje přístup k mnoha funkcím ovládací prvky ActiveX a automatizace, které jsou implementovány ve třídách knihovny MFC a ActiveX. Tyto funkce zahrnout úpravy s náhledem, automatizace, vytváření složených souborů a podpora pro ovládací prvky. Průvodce aplikací knihovny MFC visual možnosti úprav, které budou podporovat váš program nadřazené patří vytváření kontejneru, mini serveru, úplný server a program, který je kontejner a server.  
  
-   **Nová aplikace knihovny MFC**. K vytvoření nové aplikace knihovny MFC, která obsahuje automatizace, úpravy s náhledem, složené soubory nebo řízení podpory, pomocí Průvodce aplikací knihovny MFC a vyberte příslušné možnosti automatizace.  
  
-   **Existující aplikaci MFC**. Pokud přidáváte používání kontejnerů ovládacích prvků do existující aplikaci MFC, přečtěte si téma [OLE – kontejnery ovládacích prvků: Ruční povolení OLE používání kontejnerů ovládacích prvků](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).  
  
### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Chcete-li vytvořit kontejner ActiveX pro některý z následujících typů aplikací  
  
1.  [Kontejnery](../../mfc/containers.md)  
  
2.  [Úpravy s náhledem](../../mfc/ole-mfc.md)  
  
3.  [Ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>Viz také  
 [Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)

