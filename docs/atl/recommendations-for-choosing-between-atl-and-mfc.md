---
title: "Doporučení pro výběr mezi použitím knihovny ATL a MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d912c6cd997c23b9623d20a104327fb6e4701494
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Úvod do knihovny ATL](../atl/introduction-to-atl.md)

