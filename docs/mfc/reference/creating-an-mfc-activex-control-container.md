---
title: Vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 27f229a23595d4842a77409a3cedc7a57aa43e6c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079428"
---
# <a name="creating-an-mfc-activex-control-container"></a>Vytvoření kontejneru ovládacího prvku ActiveX prostředí MFC

Kontejner ovládacího prvku ActiveX je nadřazený program, který poskytuje prostředí pro spuštění ovládacího prvku ActiveX (dříve OLE). Můžete vytvořit aplikaci, která je schopna obsahující ovládací prvky ActiveX s knihovnou MFC nebo bez ní, ale je mnohem snazší s knihovnou MFC.

>[!IMPORTANT]
> ActiveX je starší verze technologie, která by se neměla používat pro nový vývoj. Další informace o moderních technologiích, které nahrazují prvky ActiveX, naleznete v tématu [ovládací prvky ActiveX](../activex-controls.md).

Vytvoření programu kontejnerů MFC pomocí [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md) umožňuje přístup k mnoha funkcím ovládacích prvků ActiveX a automatizaci, které jsou implementovány třídami MFC a ActiveX. Mezi tyto funkce patří úpravy vizuálů, automatizace, vytváření složených souborů a podpora ovládacích prvků. Možnosti vizuální úpravy v Průvodci aplikací knihovny MFC, které bude váš nadřazený program podporovat, zahrnují vytvoření kontejneru, zkrácení serveru, úplného serveru a programu, který je současně kontejnerem i serverem.

- **Nová aplikace MFC**. Chcete-li vytvořit nový program knihovny MFC, který zahrnuje automatizaci, úpravy vizuálů, složené soubory nebo podporu ovládacích prvků, použijte Průvodce aplikací knihovny MFC a zvolte příslušné možnosti automatizace.

- **Existující aplikace MFC**. Pokud přidáváte zahrnutí ovládacího prvku do existující aplikace knihovny MFC, přečtěte si téma [ovládací kontejnery OLE: ruční povolení zahrnutí ovládacího prvku OLE](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>Vytvoření kontejneru ActiveX pro některý z následujících typů aplikací

1. [Kontejnery](../../mfc/containers.md)

1. [Úpravy vizuálů](../../mfc/ole-mfc.md)

1. [MFC – ovládací prvky ActiveX](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Viz také

[C++typy projektů v aplikaci Visual Studio](../../build/reference/visual-cpp-project-types.md)
