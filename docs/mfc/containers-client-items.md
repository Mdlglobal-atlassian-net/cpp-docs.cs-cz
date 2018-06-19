---
title: 'Kontejnery: Klientské položky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14979f1c5f11e9a229c408e33e7c17d8776a54a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344214"
---
# <a name="containers-client-items"></a>Kontejnery: Klientské položky
Tento článek vysvětluje, co jsou klientské položky a z co třídy aplikace by měl být odvozen jeho klientské položky.  
  
 Klientské položky jsou datové položky, které patří do jiných aplikací, které jsou součástí nebo odkazuje dokumentu aplikace OLE kontejneru. Klientské položky, jejichž data jsou obsažena v tomto dokumentu jsou vloženy; ty, jejichž data jsou uložena v jiném umístění kontejneru dokument odkazuje jsou propojeny.  
  
 Třída dokumentu v aplikaci OLE je odvozená od třídy [COleDocument](../mfc/reference/coledocument-class.md) spíše než z **CDocument**. `COleDocument` Třída dědí z **CDocument** všechny funkce, které jsou nezbytné pro používání document/view – architektura, na které MFC aplikace využívají. `COleDocument` také definuje rozhraní, které zpracovává dokumentu jako kolekce `CDocItem` objekty. Několik `COleDocument` členské funkce jsou k dispozici pro přidávání, získávání a odstraňování elementů této kolekce.  
  
 Každá aplikace kontejneru by měl být odvozen z alespoň jednu třídu `COleClientItem`. Objekty této třídy představují položek, vložené nebo propojené v dokumentu OLE. Tyto objekty existují po celou dobu životnosti dokument obsahující, pokud jsou odstraněny z dokumentu.  
  
 `CDocItem` je základní třídou pro `COleClientItem` a `COleServerItem`. Objekty třídy odvozené od těchto dvou fungují jako prostředníci mezi položkou OLE a klientské a serverové aplikace, v uvedeném pořadí. Pokaždé, když je přidání nové položky OLE do dokumentu rozhraní MFC framework přidá nový objekt klientské aplikace `COleClientItem`-odvozené třídy dokumentu kolekce `CDocItem` objekty.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery](../mfc/containers.md)   
 [Kontejnery: Složené soubory](../mfc/containers-compound-files.md)   
 [Kontejnery: Problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md)   
 [Kontejnery: Pokročilé funkce](../mfc/containers-advanced-features.md)   
 [COleClientItem – třída](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem – třída](../mfc/reference/coleserveritem-class.md)
