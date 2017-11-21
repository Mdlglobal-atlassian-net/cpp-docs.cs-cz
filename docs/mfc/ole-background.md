---
title: "OLE – pozadí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d30559ebfd55041bee767f41f397ec87074c36d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-background"></a>OLE – pozadí
OLE mechanismus, který umožňuje uživatelům vytvářet a upravovat dokumenty obsahující položky nebo "objekty" vytvoří se více aplikací.  
  
> [!NOTE]
>  OLE byl původně zkratka pro propojování a vkládání objektů. Ale ho se nyní označuje jako OLE. Části OLE, které nesouvisí s propojování a vkládání jsou teď součástí technologie Active.  
  
 OLE – dokumenty, v minulosti názvem složených dokumentů, bez problémů integrují různé typy dat nebo součástí. Zvukové soubory, tabulky a bitmap jsou typické příklady nebyly nalezeny v OLE – dokumenty komponenty. Podpora OLE ve vaší aplikace umožňuje uživatelům používat OLE – dokumenty bez starostí o přepínání mezi různými aplikacemi; OLE nemá přepnutí za vás.  
  
 Používáte aplikace kontejnerů pro vytvoření složené dokumenty a serverové aplikace nebo součásti aplikace vytvořit položky v tomto dokumentu kontejneru. Všechny aplikace, které můžete psát může být kontejner, server nebo obojí.  
  
 OLE zahrnuje mnoho různých koncepty všechny pracovní směrem k cílem bezproblémové interakce mezi aplikacemi. Tyto oblasti patří:  
  
 Propojování a vkládání  
 Propojování a vkládání jsou tyto dvě metody pro ukládání položky vytvořené uvnitř dokument OLE, které byly vytvořeny v jiné aplikaci. Obecné informace o rozdílech mezi nimi, najdete v článku [OLE pozadí: propojování a vkládání](../mfc/ole-background-linking-and-embedding.md). Další informace najdete v článcích [kontejnery](../mfc/containers.md) a [servery](../mfc/servers.md).  
  
 Aktivace na místě (úpravy s náhledem)  
 Aktivace vložené položky v kontextu dokument kontejneru se nazývají aktivace na místě nebo úpravy s náhledem. Aplikace typu kontejner rozhraní změny začlenit funkce součásti aplikace, která vytvořila vložené položky. Propojené položky se nikdy neaktivoval na místě, protože skutečná data pro položku je obsažen v samostatném souboru, z kontextu aplikace obsahující odkaz. Další informace o aktivace na místě, najdete v článku [aktivace](../mfc/activation-cpp.md).  
  
> [!NOTE]
>  Propojování a vkládání a aktivace na místě zadejte hlavní funkce úpravy s náhledem OLE.  
  
 Automatizace  
 Automatizace umožňuje jedné aplikace do jednotky jiná aplikace. Řízení aplikace se označuje jako klient automatizace a aplikace se řídí se označuje jako automatizační server nebo součást automatizace. Další informace o automatizaci, najdete v článcích [klienti automatizace](../mfc/automation-clients.md) a [automatizační servery](../mfc/automation-servers.md).  
  
> [!NOTE]
>  Automatizace funguje v kontextech technologie OLE a aktivní. Je možné automatizovat objekty založené na modelu COM.  
  
 Složené soubory  
 Složené soubory poskytují standardní formátu, který zjednodušuje ukládání strukturovaných složených dokumentů pro aplikace rozhraní OLE. V rámci soubor složené úložných mít mnoho funkcí adresářů a datových proudů mít mnoho funkcí souborů. Tato technologie je také označován strukturovaných úložiště. Další informace o složené soubory, najdete v článku [kontejnery: složené soubory](../mfc/containers-compound-files.md).  
  
 Jednotný přenos dat  
 Uniform přenos dat (UDT) je sada rozhraní, které se mají odesílat a přijímat standardní způsobem, bez ohledu na skutečnou metodě vybrané k přenosu dat data. UDT formuláře, které základ pro data přenese pomocí přetažení. UDT nyní slouží jako základ pro existující přenos dat systému Windows, jako je schránka a dynamickou výměnu dat (DDE). Další informace o UDT, najdete v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Přetažení  
 Přetažení je snadné použití, přímo manipulaci techniku přenosu dat mezi aplikacemi, mezi windows v rámci aplikace, nebo dokonce v jednom okně v aplikaci. Přenos dat je vybraná a přetažením požadovaný cíl. Přetažení je založena na přenos dat uniform. Další informace o přetažení, najdete v článku [přetažení](../mfc/drag-and-drop-ole.md).  
  
 Komponentový objektový Model  
 Modelu COM (Component Object) poskytuje infrastrukturu používá při objekty OLE vzájemně komunikovat. Třídy MFC OLE zjednodušit COM programátorů. COM je součástí technologie Active, protože objekty modelu COM tvoří základ technologie OLE a aktivní. Další informace o modelu COM, najdete v článku [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) témata.  
  
 Některé důležité OLE témata jsou popsané v následujících článcích:  
  
-   [OLE – pozadí: Propojování a vkládání](../mfc/ole-background-linking-and-embedding.md)  
  
-   [OLE – pozadí: Kontejnery a servery](../mfc/ole-background-containers-and-servers.md)  
  
-   [OLE – pozadí: Strategie implementace](../mfc/ole-background-implementation-strategies.md)  
  
-   [OLE – pozadí: Implementace MFC](../mfc/ole-background-mfc-implementation.md)  
  
 Obecné informace OLE nebyl nalezen ve výše uvedených článcích vyhledejte OLE na webu MSDN.  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)

