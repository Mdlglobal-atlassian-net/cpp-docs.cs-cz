---
title: Filozofie návrhu třídy obecné | Dokumentace Microsoftu
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
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe64ee4d9e6fc678d97c3e9fe37a85e53807541
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416640"
---
# <a name="general-class-design-philosophy"></a>Obecná filosofie návrhu tříd

Microsoft Windows byla navržená tak dlouho, než se stal oblíbený jazyk C++. Protože nepřeberným množstvím aplikací využívají rozhraní (API) Windows jazyka C, toto rozhraní se zachová v dohledné budoucnosti. Libovolné rozhraní C++ Windows musí být proto postavená na procedurální rozhraní API jazyka C. Zaručí se tak, že bude aplikací v jazyce C++ může existovat vedle sebe s aplikacemi C.

Knihovny Microsoft Foundation Class je objektově orientované rozhraní pro Windows, který splňuje následující požadavky návrhu:

- Významné snížení úsilí o napsání aplikace pro Windows.

- Rychlost provádění srovnatelné s rozhraní API jazyka C.

- Režijní náklady na kód minimální velikost.

- Možnost volat jakékoli funkce Windows C přímo.

- Jednodušší převodu stávajících aplikací C do C++.

- Možnost využívat z existujícího základu jazyka C Windows programovací prostředí.

- Snadnější použití rozhraní API Windows pomocí C++ než s C.

- Snadnější použití, ale výkonné abstrakce složité funkce, jako jsou ovládací prvky ActiveX, Podpora databáze, tisk, panely nástrojů a stavové řádky.

- True rozhraní API Windows pro jazyk C++, který efektivně používá funkce jazyka C++.

Další informace o návrhu knihovny MFC naleznete v tématu:

- [Architektura aplikace](../mfc/application-framework.md)

- [Vztah k rozhraní API jazyka C](../mfc/relationship-to-the-c-language-api.md)

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

