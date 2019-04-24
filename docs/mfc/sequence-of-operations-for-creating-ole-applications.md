---
title: Posloupnost operací při vytváření aplikací OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: b7fa989d1a3b799cf6b427e27142d4479be900bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308183"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Posloupnost operací při vytváření aplikací OLE

V následující tabulce jsou uvedeny vaši roli a roli v rámci při vytváření OLE propojování a vkládání aplikací. Představují možnosti k dispozici pro místo posloupnost kroků provést.

### <a name="creating-ole-applications"></a>Vytváření aplikací OLE

|Úloha|Můžete provést|Nepodporuje rozhraní framework|
|----------|------------|------------------------|
|Vytvoření komponenty COM.|Spuštění Průvodce aplikací knihovny MFC. Zvolte **úplný server** nebo **mini serveru** v **Podpora složených dokumentů** kartu.|Rozhraní framework generuje kostry aplikace s možností komponenty modelu COM povolena. Všechny možnosti modelu COM lze přenést do stávající aplikace s jen drobné změny.|
|Vytvoření zcela nové aplikace typu kontejner.|Spuštění Průvodce aplikací knihovny MFC. Zvolte **kontejneru** v **Podpora složených dokumentů** kartu. Zobrazení tříd, přejděte na editor zdrojového kódu. Zadejte kód pro vaše funkce modelu COM obslužné rutiny.|Rozhraní framework generuje kostru aplikace, který může vložit objekty modelu COM, které jsou vytvořené pomocí modelu COM komponenty (server) aplikací.|
|Vytvořte aplikaci, která podporuje automatizaci úplně od začátku.|Spuštění Průvodce aplikací knihovny MFC. Zvolte **automatizace** z **rozšířené funkce** kartu. Zobrazení tříd můžete zpřístupnit metody a vlastnosti v aplikaci pro automatizaci.|Rozhraní framework generuje kostru aplikace, které můžete aktivovat a automatizované jiné aplikace.|

## <a name="see-also"></a>Viz také:

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)<br/>
[Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[Posloupnost operací při vytváření databázových aplikací](../mfc/sequence-of-operations-for-creating-database-applications.md)
