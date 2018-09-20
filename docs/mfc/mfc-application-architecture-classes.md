---
title: Třídy architektury aplikace MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32a842d69e227633f8fbd2291a47296d384a75c6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438623"
---
# <a name="mfc-application-architecture-classes"></a>Třídy architektury aplikace MFC

Třídy v této kategorii přispívat k architektuře rozhraní framework aplikace. Si poskytují funkce, které jsou společné pro většinu aplikací. Vyplňte rozhraní framework, které doplňují specifické pro aplikaci. Obvykle tak učiníte odvození nové třídy z třídy architektury a potom přidáním nové členy nebo přepsání existující členské funkce.

[Průvodci aplikací](../mfc/reference/mfc-application-wizard.md) vygenerovat několik typů aplikací, které aplikační platformu používat různými způsoby. SDI (rozhraní s jedním dokumentem) a aplikace MDI (rozhraní více dokumentů) vytěžíte z část rozhraní volá architekturu document/view. Další typy aplikací, jako je například aplikace založené na dialogu, založené na formulářích aplikacemi a knihovnami DLL, použijte jenom některé funkce architektury dokument/zobrazení.

Dokument/zobrazení aplikace obsahují jednu nebo více sad dokumenty, zobrazení a oken s rámečkem. Objekt šablony dokumentu přidruží třídy pro každou sadu dokumentů/zobrazení a rámečku.

I když nemáte používají architekturu document/view – v aplikaci knihovny MFC, existuje mnoho výhod uděláte. MFC OLE kontejneru a server podporu je založen na architekturu document/view, jako je podpora tisku a tisk ve verzi preview.

Všechny aplikace knihovny MFC mají alespoň dva objekty: aplikační objekt odvozený od [CWinApp](../mfc/reference/cwinapp-class.md)a nějaký druh objekt hlavního okna (často nepřímo) odvozený od [CWnd](../mfc/reference/cwnd-class.md). (Nejčastěji, hlavní okno pochází z [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), nebo [CDialog](../mfc/reference/cdialog-class.md), které jsou odvozeny z `CWnd`.)

Aplikace, které používají architekturu document/view obsahují další objekty. Instanční objekty jsou:

- Aplikační objekt odvozené od třídy [CWinApp](../mfc/reference/cwinapp-class.md), jak je uvedeno nahoře.

- Jeden nebo více objektů třídy dokumentu odvozené od třídy [CDocument](../mfc/reference/cdocument-class.md). Objekty třídy dokumentu zodpovídají za interní znázornění dat, pracovat v zobrazení. Mohou být spojeny s datový soubor.

- Jeden nebo více zobrazení objektů odvozené od třídy [CView](../mfc/reference/cview-class.md). Každé zobrazení je okno, které je připojené k dokumentu a přidružené okno rámce. Zobrazení, zobrazení a manipulaci s data obsažená v objektu třídy dokumentu.

Dokument/zobrazení aplikace také obsahují oken s rámečkem (odvozený od [CFrameWnd](../mfc/reference/cframewnd-class.md)) a šablony (odvozený z [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

