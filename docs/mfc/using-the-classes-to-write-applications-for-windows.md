---
title: "Použití tříd pro psaní aplikací pro Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90790e12d2137324c4d641f1beac6c5cae0cff31
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Použití tříd pro psaní aplikací pro Windows
Dohromady třídy v knihovně Microsoft Foundation Class (MFC) tvoří "aplikační rozhraní," na kterém vytváříte aplikaci pro operační systém Windows. Velmi obecné úrovni rozhraní definuje kostru aplikace a poskytuje implementace standardní uživatelského rozhraní, které se dají umístit do kostru. Je vaše úloha jako programátory vyplnit zbytek kostru, které jsou všechny tyto věci, které jsou specifické pro vaši aplikaci. Začít můžete získat pomocí Průvodce aplikací MFC k vytvoření těchto souborů pro velmi důkladné Startovní aplikace. Implementace logika specifické pro aplikaci pomocí Microsoft Visual C++ editory prostředků vizuálně, navrhnout vaše prvky uživatelského rozhraní zobrazení tříd příkazů pro připojení k kód a knihovna tříd těchto elementů.  
  
 Verze 3.0 a novějších rozhraní MFC Framework podporuje programování pro Win32 platformy, včetně systému Microsoft Windows 95 a novější a verze systému Windows NT 3.51 a novější. Podpora MFC Win32 zahrnuje více vláken. Použijte verzi 1.5*x* Pokud musíte udělat programování 16 bitů.  
  
 Tato řada článků představuje komplexní přehled o rozhraní. Také zde popsány hlavních objektů, které tvoří vaše aplikace a jak se vytvářejí. Mezi témata popsaná v těchto článcích jsou následující:  
  
-   [Rozhraní framework](../mfc/framework-mfc.md).  
  
-   Rozdělení práce mezi rozhraní a váš kód, jak je popsáno v [podpoře Framework](../mfc/building-on-the-framework.md).  
  
-   [Třída aplikace](../mfc/cwinapp-the-application-class.md), který zapouzdřuje funkce na úrovni aplikace.  
  
-   Jak [dokumentu šablony](../mfc/document-templates-and-the-document-view-creation-process.md) vytvářet a spravovat dokumenty a jejich přidružené zobrazení a okna s rámečkem.  
  
-   Třída [CWnd](../mfc/window-objects.md), kořenová základní třída všechny systémy windows.  
  
-   [Grafické objekty](../mfc/graphic-objects.md), jako jsou například pera a štětce.  
  
 Ostatní části rozhraní patří:  
  
-   [Objekty oken: Přehled](../mfc/window-objects.md)  
  
-   [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)  
  
-   [CObject kořenová základní třída v prostředí MFC](../mfc/using-cobject.md)  
  
-   [Document/View – architektura](../mfc/document-view-architecture.md)  
  
-   [Dialogová okna](../mfc/dialog-boxes.md)  
  
-   [Ovládací prvky](../mfc/controls-mfc.md)  
  
-   [Ovládací pruhy](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Správa paměti](../mfc/memory-management.md)  
  
     Kromě toho, která poskytuje několik výhod v psaní aplikací pro operační systém Windows, MFC taky je mnohem jednodušší pro psaní aplikací, které konkrétně používají propojování a vkládání technologie OLE. Můžete použít aplikace OLE visual úpravy kontejneru, server visual úpravy OLE nebo obojí a automatizace můžete přidat tak, aby ostatní aplikace můžete použít objekty z vaší aplikace nebo i jednotky vzdáleně.  
  
-   [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)  
  
     OLE řízení development kit (CDK) je nyní plně integrována rozhraní. Tento článek rodiny poskytuje přehled vývoje ovládacího prvku ActiveX MFC. (Ovládací prvky ActiveX dříve označované jako ovládací prvky OLE.)  
  
-   [Databáze programování](../data/data-access-programming-mfc-atl.md)  
  
     MFC také poskytuje dvě sady databázové třídy, které usnadňují psaní přístup k datům aplikací. Použití databázových tříd rozhraní ODBC, můžete připojení k databázím prostřednictvím ovladače rozhraní připojení ODBC (Open Database), vyberte záznamů z tabulek a zobrazit informace o záznamu v formuláři na obrazovce. Použití tříd objekt DAO (Data Access), můžete pracovat s databázemi prostřednictvím databázový stroj Microsoft Jet nebo zdrojů dat externí (databázovém stroji Jet), včetně zdroje dat ODBC.  
  
     Kromě toho MFC je plně povolena pro psaní aplikací, které používají kódování Unicode a vícebajtové znakové sady (MBCS), konkrétně dvoubajtové znakové sady (DBCS).  
  
 Obecné informace MFC dokumentaci najdete v tématu [obecná témata MFC](../mfc/general-mfc-topics.md).  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

