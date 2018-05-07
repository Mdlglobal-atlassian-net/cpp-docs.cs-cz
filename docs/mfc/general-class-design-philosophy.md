---
title: Obecná filosofie návrhu tříd | Microsoft Docs
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
ms.openlocfilehash: 7b2d0915c4b2940e93b781e7a56e2640c64a7f20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="general-class-design-philosophy"></a>Obecná filosofie návrhu tříd
Microsoft Windows byla navržená tak dlouho, než se aktivovala oblíbených jazyka C++. Vzhledem k tisícům aplikací používá rozhraní (API) Windows jazyka C, že rozhraní se zachová v dohledné budoucnosti. Každé rozhraní C++ Windows musí být proto postavená na procedurální rozhraní API jazyka C. To zaručuje, že aplikace C++ nebudou existovat společně s aplikacemi C.  
  
 Knihovny Microsoft Foundation Class je objektově orientované rozhraní systému Windows, který splňuje následující požadavky návrhu:  
  
-   Výraznému snížení úsilí psát aplikace pro Windows.  
  
-   Rychlost provádění srovnatelný s rozhraní API jazyka C.  
  
-   Režijní náklady na kód minimální velikost.  
  
-   Schopnost volat jakékoli funkce Windows C přímo.  
  
-   Jednodušší převod existujících aplikací C na C++.  
  
-   Možnost využívat z existující základní programovací prostředí Windows jazyka C.  
  
-   Snadnější použití rozhraní API systému Windows s C++ než s C.  
  
-   Usnadňují použití ještě výkonné abstrakce komplikovanější, funkce, jako jsou ovládací prvky ActiveX, Podpora databáze, tisk, panely nástrojů a stavové řádky.  
  
-   Hodnota TRUE, rozhraní API systému Windows pro jazyk C++, která efektivně používá funkce jazyka C++  
  
 Další informace ohledně návrhu knihovny MFC najdete v tématu:  
  
-   [Architektura aplikace](../mfc/application-framework.md)  
  
-   [Vztah k rozhraní API jazyka C](../mfc/relationship-to-the-c-language-api.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

