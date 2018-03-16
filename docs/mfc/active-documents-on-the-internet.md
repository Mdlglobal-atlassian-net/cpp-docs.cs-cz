---
title: "Aktivní dokumenty na Internetu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], creating
- application wizards [MFC], active documents
- active documents [MFC], programming steps
- application wizards [MFC]
- active documents [MFC], using application wizards
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0980f048b9be411308b159dea0ceaa71f8eee563
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="active-documents-on-the-internet"></a>Aktivní dokumenty na Internetu
Aktivní dokumenty zadejte rozšíření pro tradiční vložené objekty. Aktivní dokumenty může být vícestránkové a jsou zobrazeny v celého klienta. Proveďte vyjednávání tradiční nabídky a můžete upravit na místě a také v otevřeném okně v serverové aplikace. Místo zobrazení jako malé šrafované ohraničení obdélníku, jsou aktivní dokumenty úplné rámce a aktivní vždy na místě.  
  
 Aktivní dokumenty lze zobrazit v kontejneru jako Microsoft Office vazač, který poskytuje způsob, jak vytvořit složeného dokumentu složená z různých typů dokumentů. například Excel, Word, a typ vašeho vlastní šablony dokumentů, z nichž každý lze upravit úplné rámce. Aktivní dokumenty lze také zobrazit v prohlížeči, například Microsoft Internet Explorer, což je kontejner pro aktivní dokument.  
  
 **Aktivní dokument výhody:**  
  
-   Dokumenty lze zobrazit úplnou rámce, v okně celý klienta.  
  
-   Dokumenty lze otevřít v samostatném okně aplikace.  
  
     Pro dokument otevřít podpůrnou aplikací na straně klienta, musí existovat, nebo samostatně stáhnout před spuštěním aplikace. Prohlížeč lze zapisovat nabízí omezené funkce (Word, PowerPoint a Excel zadejte prohlížečů pro své dokumenty). Plnou verzi aplikace nabízejí plná podpora úpravy.  
  
-   Dokumenty jsou vždy aktivní na místě.  
  
-   Příkazy nabídky vyvolat z kontejneru mohou být směrovány do dokumentu.  
  
-   Dokumenty lze zobrazit ve webovém prohlížeči. To umožňuje bezproblémovou integraci mezi dokumenty a další webové stránky.  
  
     Uživatele můžete procházet HTML webovou stránku, pak tabulky aplikace Excel a potom na dokument, který jste napsali použití prostředí MFC podpora pro aktivní dokumenty. Uživatele můžete přejít pomocí známé webové rozhraní, jako prohlížeč přepínače bez problémů mezi nabídky a zobrazení stránky HTML, Excel a dokumentu vaší aplikace.  
  
-   Zobrazí všechny aplikace v běžný rámec.  
  
## <a name="requirements-for-active-documents"></a>Požadavky pro aktivní dokumenty  
 Rozhraní uvedená v následující tabulce zahrnují rozhraní již požadován pro embedded servery a několik nové rozhraní, které jsou specifické pro aktivní dokumenty. MFC poskytuje výchozí implementaci pro většinu těchto rozhraní [COleServerDoc](../mfc/reference/coleserverdoc-class.md) třídy.  
  
|A dokumentu, který...|Implementuje tyto rozhraní|  
|-------------------------|---------------------------------|  
|Používá složené soubory jako mechanismus jeho úložiště.|`IPersistStorage`.|  
|Podporuje základní funkce vnoření aktivní dokumenty, včetně vytvoření ze souboru.|`IPersistFile`, `IOleObject`, a `IDataObject`.|  
|Podporuje aktivace na místě.|`IOleInPlaceObject` a `IOleInPlaceActiveObject` (pomocí kontejneru `IOleInPlaceSite` a **IOleInPlaceFrame** rozhraní).|  
|Podporuje aktivní dokument rozšíření, které zahrnují tyto nové rozhraní. Některé rozhraní jsou volitelné.|`IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, a `IPrint`.|  
  
 MFC poskytuje podporu pro rozšíření stávající podpora embedded serveru pro aktivní dokumenty.  
  
## <a name="add-active-document-support-to-a-new-application"></a>Přidání podpory pro aktivní dokument do nové aplikace  
 Chcete-li vytvořit novou aplikaci s podporou aktivní dokument: V the Průvodce aplikací knihovny MFC na **podporu složeného dokumentu** v části "podpora vyberte složeného dokumentu" vyberte **úplný server** nebo  **Kontejner/úplný server**a v části "Vyberte další možnosti" zaškrtněte políčko u **server pro aktivní dokument**.  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> Převést existující Server v rámci procesu MFC na Server pro aktivní dokument  
 Pokud vaše aplikace byla vytvořena s verzí aplikace Visual C++ starší než verze 4.2 a je již jako server v procesu, můžete přidat podporu pro aktivní dokument změnou následující třídy:  
  
|Typ třídy|Dříve odvozené od|Změna k odvozování z|  
|----------------|---------------------------|---------------------------|  
|Rámečkem na místě|`COleIPFrameWnd`|**COleDocIPFrameWnd**|  
|Položka|`COleServerItem`|`CDocObjectServerItem`|  
  
 Budete také změnit, jak informace byly uloženy v registru a provést několik dalších změn. Pokud vaše aplikace právě obsahuje žádná podpora pro komponenty modelu COM, můžete přidat podporu serveru spuštěním Průvodce aplikace a integrace kódu pro konkrétní součást COM s vaší stávající aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

