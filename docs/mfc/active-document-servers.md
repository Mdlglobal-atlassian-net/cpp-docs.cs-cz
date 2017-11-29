---
title: "Servery pro aktivní dokumenty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 76e1e4d237e486734c734359f4844e27d80dd2a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="active-document-servers"></a>Servery pro aktivní dokumenty
Aktivní dokument servery, jako je například Word, Excel nebo PowerPoint dokumentům hostitele jinými typy aplikací označují jako aktivní dokumenty. Na rozdíl od OLE vložené objekty (které se zobrazí v rámci dané stránky jiného dokumentu), aktivní dokumenty zadejte úplné rozhraní a dokončení nativní funkce serverové aplikace, která je vytvořila. Uživatelé mohou vytvářet dokumenty pomocí potenciál jejich oblíbených aplikací (pokud jsou aktivní dokument povolené) ještě lze považovat za výsledné projektu jedné entity.  
  
 Aktivní dokumenty mohou mít více než jednu stránku a jsou vždy aktivní na místě. Aktivní dokumenty řízení součástí uživatelského rozhraní, sloučení s jejich nabídkami **soubor** a **pomoci** nabídky kontejneru. Tyto zabírají celou oblast úprav kontejneru a řídit zobrazení a rozložení stránky tiskárny (okraje, zápatí a tak dále).  
  
 MFC implementuje servery aktivní dokument s document/view – rozhraní, příkaz expediční mapy, tisk, správu nabídky a správu registru. Požadavky na konkrétní programovací jsou popsané v [aktivní dokumenty](../mfc/active-documents.md).  
  
 MFC podporuje aktivní dokumenty s [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) třídy, které jsou odvozené od [CCmdTarget](../mfc/reference/ccmdtarget-class.md), a [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md), odvozené z [ COleServerItem](../mfc/reference/coleserveritem-class.md). MFC podporuje kontejnery pro aktivní dokument s [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) třídy, které jsou odvozené od [COleClientItem](../mfc/reference/coleclientitem-class.md).  
  
 `CDocObjectServer`mapuje rozhraní aktivní dokument a inicializuje a aktivuje aktivní dokument. MFC taky poskytuje makra pro zpracování směrování příkazů v aktivní dokumenty. Pokud chcete používat aktivní dokumenty ve vaší aplikaci, zahrňte do souboru StdAfx.h AfxDocOb.h.  
  
 Na běžném serveru MFC moduly přiřazení svůj vlastní `COleServerItem`-odvozené třídy. Průvodce aplikací MFC generuje tato třída pro vás, pokud vyberete **mini serveru** nebo **úplný server** zaškrtnutí políčka umožnit aplikačního serveru podporu složeného dokumentu. Pokud vyberete také **server pro aktivní dokument** zaškrtávací políčko, Průvodce aplikací MFC vygeneruje třídy odvozené od `CDocObjectServerItem` místo.  
  
 `COleDocObjectItem` Třída umožňuje kontejner OLE se kontejner. Průvodce aplikací MFC můžete vytvořit kontejner výběrem **kontejner pro aktivní dokument** zaškrtávacího políčka na stránce Průvodce aplikací MFC složené podporu dokumentu. Další informace najdete v tématu [vytvoření aplikace kontejnerů pro aktivní dokument](../mfc/creating-an-active-document-container-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Obsahování pro aktivní dokument](../mfc/active-document-containment.md)
