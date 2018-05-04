---
title: Doporučení pro výběr mezi použitím knihovny ATL a MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116f2066b98951aa2a470021f5527542ac8cbe46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Doporučení pro výběr mezi použitím knihovny ATL a MFC
Při vývoji součásti a aplikace, můžete si vybrat mezi dva přístupy – ATL a MFC (knihovny Microsoft Foundation Class).  
  
## <a name="using-atl"></a>Pomocí knihovny ATL  
 ATL je rychlý a snadný způsob, jak vytvořit komponenty modelu COM v jazyce C++ a udržovat malé nároky. Vytvoření ovládacího prvku, pokud nepotřebujete všechny integrovanou funkci, která automaticky poskytuje MFC pomocí knihovny ATL.  
  
## <a name="using-mfc"></a>Použití prostředí MFC  
 MFC umožňuje vytvoření úplné aplikace, ovládací prvky ActiveX a aktivní dokumenty. Pokud jste již vytvořili ovládacího prvku s knihovnou MFC, můžete pokračovat v prostředí MFC vývoj. Při vytváření nového ovládacího prvku, zvažte použití knihovny ATL, pokud nepotřebujete všechny knihovny MFC integrovanou funkci.  
  
## <a name="using-atl-in-an-mfc-project"></a>Pomocí knihovny ATL v projektu knihovny MFC  
 Můžete přidat podporu pro pomocí knihovny ATL v projektu knihovny MFC existující spuštěním průvodce. Podrobnosti najdete v tématu [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do ATL](../atl/introduction-to-atl.md)

