---
title: Obecná filosofie návrhu tříd
ms.date: 11/04/2016
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
ms.openlocfilehash: 34a173802e3fa43615c05da4ce747592f851228f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441184"
---
# <a name="general-class-design-philosophy"></a>Obecná filosofie návrhu tříd

Systém Microsoft Windows byl navržený dlouho C++ před tím, než se jazyk stal oblíbeným. Vzhledem k tomu, že tisíce aplikací používají rozhraní API (Windows Application Programming Interface) jazyka C, bude toto rozhraní udržováno v předvídatelné budoucnosti. Jakékoli C++ rozhraní systému Windows musí být proto postavené nad procedurální rozhraní API pro jazyk C. To zaručuje, C++ že aplikace budou moci koexistovat s aplikacemi jazyka C.

Knihovna Microsoft Foundation Class je objektově orientované rozhraní systému Windows, které splňuje následující cíle návrhu:

- Významné snížení úsilí při psaní aplikace pro Windows.

- Rychlost spuštění srovnatelná s jazykem jazyka C-Language API.

- Minimální režijní náklady na velikost kódu.

- Možnost volat jakoukoli funkci Windows C přímo

- Jednodušší převod stávajících aplikací v jazyce C C++na.

- Schopnost využívat stávající základ programovacího prostředí systému Windows pro jazyk C.

- Jednodušší používání rozhraní API systému Windows s C++ výjimkou jazyka C.

- Jednodušší je používat stále výkonné abstrakce složitých funkcí, jako jsou ovládací prvky ActiveX, podpora databází, tisk, panely nástrojů a stavové řádky.

- True Windows API pro C++ efektivně používá C++ jazykové funkce.

Další informace o návrhu knihovny MFC naleznete v tématu:

- [Aplikační rozhraní](../mfc/application-framework.md)

- [Vztah k rozhraní API jazyka C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
