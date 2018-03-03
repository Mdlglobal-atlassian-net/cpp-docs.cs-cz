---
title: "Přidání příjemce OLE DB ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: defc933014bd287eb48f53635efba12a40960711
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-ole-db-consumer"></a>Přidání příjemce OLE DB knihovny ATL
Tento průvodce slouží k přidání příjemce technologie OLE DB knihovny ATL do projektu. Příjemce technologie ATL OLE DB se skládá vazeb OLE DB přístupového objektu třídy a data potřebná pro přístup k datovému zdroji. Projekt musí být vytvořen jako aplikace ATL COM nebo MFC nebo Win32 aplikaci, která obsahuje podpory knihovny ATL (který automaticky přidá průvodce příjemcem knihovny ATL technologie OLE DB).  
  
 **Poznámka:** přidáte do projektu MFC příjemce technologie OLE DB. Pokud tak učiníte, průvodce příjemcem knihovny ATL technologie OLE DB potřebná podpora COM přidáte do svého projektu. Předpokladem je, že při vytváření projektu knihovny MFC jste vybrali **– ovládací prvky ActiveX** políčko (v **upřesňující funkce** stránky Průvodce aplikací MFC projektu), je ve výchozím nastavení. Výběrem této možnosti zajistíte, že aplikace zavolá **funkce CoInitialize** a **CoUninitialize**. Pokud jste nevybrali **– ovládací prvky ActiveX** při vytváření projektu knihovny MFC, je třeba volat **funkce CoInitialize** a **CoUninitialize** v hlavním kódu.  
  
### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Chcete-li přidat příjemce technologie OLE DB knihovny ATL do projektu  
  
1.  V zobrazení tříd klikněte pravým tlačítkem na projekt. V místní nabídce klikněte na tlačítko **přidat** a pak klikněte na **přidat třídu**.  
  
2.  Ve složce Visual C++, dvakrát klikněte **ATL příjemce technologie OLE DB** ikonu nebo vyberte ho a klikněte na tlačítko **otevřete**.  
  
     Otevře se průvodce příjemcem knihovny ATL technologie OLE DB.  
  
3.  Definujte nastavení, jak je popsáno v [průvodce příjemcem knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md).  
  
4.  Klikněte na tlačítko **Dokončit** zavřete průvodce. Nově vytvořený kód příjemce technologie OLE DB se vloží do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)

