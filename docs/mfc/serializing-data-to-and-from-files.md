---
title: Serializace dat do a z soubory | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d28b12e19b302f5576d2cd76c931e0036c208185
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="serializing-data-to-and-from-files"></a>Serializace dat při vstupu i výstupu ze souborů
Základní představu o trvalost je, že objekt by měl být schopni zapisovat jeho aktuální stav indikován hodnoty jeho členské proměnné, do trvalého úložiště. Objekt později, může být znovu vytvořen, čtení, nebo "deserializaci" stav objektu z trvalého úložiště. Zde bod klíče je zodpovědná za čtení a zápis vlastní stav samotného objektu. Proto pro třídu jako trvalé, musí implementovat operace základní serializace.  
  
 Rozhraní framework poskytuje výchozí implementaci pro ukládání dokumentů k souborům disku v reakci na uložení a uložit jako příkazy v nabídce Soubor a načítání ze souborů na disku v reakci na příkaz Otevřít dokumenty. S velmi málo práce můžete implementovat dokumentu možnost zápisu a čtení jeho dat do a ze souboru. Přepsání je hlavní co musíte udělat [serializace](../mfc/reference/cobject-class.md#serialize) členské funkce ve třídě dokumentů.  
  
 Průvodce aplikací MFC umístí kosterního přepsání **CDocument** – členská funkce `Serialize` ve třídě dokumentů, které jsou pro vás vytvoří. Poté, co jste implementovali členské proměnné vaší aplikace, můžete vyplnit vaší `Serialize` přepsat s kódem, který odesílá data na "archivu objekt" připojení k souboru. A [CArchive](../mfc/reference/carchive-class.md) objektu je podobná `cin` a `cout` vstupu a výstupu objekty knihovny iostream C++. Ale `CArchive` zapíše a čte binární formát, není formátovaný text.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Serializace](../mfc/serialization-in-mfc.md)  
  
-   [Role dokumentu v serializaci](#_core_the_document.92.s_role_in_serialization)  
  
-   [Role data v serializaci](#_core_the_data.92.s_role_in_serialization)  
  
-   [Obcházení mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a>Role dokumentu v serializaci  
 Rozhraní framework odpoví automaticky v nabídce soubor otevřít, uložte a uložit jako příkazy voláním dokumentu `Serialize` – členská funkce, pokud je implementována. `ID_FILE_OPEN` Příkazu, například volání funkce obslužné rutiny do objektu application. Během tohoto procesu uživatel uvidí a reaguje na dialogové okno otevřít soubor a rozhraní získá název souboru, který uživatel vybere. Vytvoří rozhraní `CArchive` objekt nastavil pro načítání dat do dokumentu a předá archivu do `Serialize`. Rozhraní framework již otevřena soubor. Kód v vašeho dokumentu `Serialize` – členská funkce čte data prostřednictvím archivu, rekonstrukce datové objekty podle potřeby. Další informace o serializaci, najdete v článku [serializace](../mfc/serialization-in-mfc.md).  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a>Role Data v serializaci  
 Obecně platí typu třídy data by měla být schopen serializovat sám sebe. To znamená když objekt můžete předat do archivu, objekt by měl vědět, jak samotné zapsat do archivu a jak číst sám sebe z archivu. MFC poskytuje podporu pro vytváření tříd serializovatelný tímto způsobem. Pokud návrh třídu k definování typu dat a máte v úmyslu serializaci dat daného typu, návrh pro serializaci.  
  
## <a name="see-also"></a>Viz také  
 [Použití dokumentů](../mfc/using-documents.md)

