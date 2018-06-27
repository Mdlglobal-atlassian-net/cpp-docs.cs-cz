---
title: Serializace v prostředí MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b46dc8500543ce94b7d8d6a3415b22d019619d83
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952590"
---
# <a name="serialization-in-mfc"></a>Serializace v prostředí MFC
Tento článek vysvětluje, že zadaná v knihovny pro třídu Foundation Microsoft (MFC) umožňující objekty, které chcete zachovat mezi mechanismu serializace spouští vašeho programu.  
  
 Serializace je proces zápisu nebo čtení objektu do nebo z trvalého úložiště média jako je soubor na disku. Serializace je ideální pro případy, kdy je žádoucí, aby udržení stavu strukturovaná data (například C++ třídy nebo struktury) během nebo po spuštění programu. Serializace objektů poskytovaných v prostředí MFC umožňuje tuto funkci používat standardní a konzistentním způsobem, kerberosu uživatele z potřeba provádět souborové operace ručně.  
  
 MFC poskytuje integrovanou podporu pro serializaci ve třídě `CObject`. Proto všechny třídy odvozené od `CObject` můžete využít výhod `CObject`na protokol serializace.  
  
 Základní představu o serializace je, že objekt by měl být schopni zapisovat jeho aktuální stav, obvykle indikován hodnotu jeho členské proměnné, do trvalého úložiště. Objekt později, může být znovu vytvořen, čtení, nebo při deserializaci objektu stavu z úložiště. Serializace zpracovává všechny podrobnosti o objektu ukazatelů a cyklické odkazy na objekty, které se použijí při serializaci objektu. Bod klíče je, že samotného objektu je zodpovědná za čtení a zápis svůj stav. Proto pro třídu být serializovatelný musí implementovat operace základní serializace. Jak je vidět ve skupině serializace článků, je snadné přidat tuto funkci na třídu.  
  
 MFC používá objekt `CArchive` třída jako zprostředkovatel mezi objekt, který má být serializován a střední úložiště. Tento objekt je vždy přidružený `CFile` objektu, ze které získá informace potřebné pro serializaci, včetně názvu souboru a zda je požadovaná operace čtení nebo zápisu. Objekt, který provede operaci serializace můžete použít `CArchive` objektu bez ohledu na povaze paměťového média.  
  
 A `CArchive` objektu používá přetížené vložení (**<\<**) a extrakce (**>>**) operátory provést zápis a čtení operací. Další informace najdete v tématu [ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md) v článku serializace: serializace objektu.  
  
> [!NOTE]
>  Nezaměňujte `CArchive` se pro obecné účely iostream – třídy, které jsou pro formátovaný text pouze. `CArchive` Třída je pro binární formát serializovaných objektů.  
  
 Pokud chcete, můžete obejít MFC serializace pro vytvoření vlastní mechanismus pro trvalé datové úložiště. Je nutné přepsat členské funkce tříd, které zahájí serializace v příkazu uživatele. Viz popis v [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md) id_file_open – id_file_save – a id_file_save_as – standardní příkazy.  
  
 V následujících článcích popisuje dvě hlavní úlohy, které vyžadují pro serializaci:  
  
-   [Serializace: Příprava serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md)  
  
-   [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)  
  
 Článek [serializace: Serializace vs. Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md) popisuje po vhodnými bezpečnostními vstupu a výstupu v databázových aplikacích serializace.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [CArchive – třída](../mfc/reference/carchive-class.md)   
 [CObject – třída](../mfc/reference/cobject-class.md)   
 [CDocument – třída](../mfc/reference/cdocument-class.md)   
 [CFile – třída](../mfc/reference/cfile-class.md)
