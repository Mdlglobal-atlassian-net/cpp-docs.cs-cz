---
title: Serializace v prostředí MFC | Dokumentace Microsoftu
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
ms.openlocfilehash: ebd11488f0f86123bcf95d210072cc61dcc31c60
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409230"
---
# <a name="serialization-in-mfc"></a>Serializace v prostředí MFC

Tento článek vysvětluje mechanizmus serializace, který v třídy knihovny MFC (Microsoft Foundation) umožňující objektů zachována i mezi spuštěními vaší aplikace.

Serializace je proces zápisu nebo čtení objektu do nebo z trvalého úložiště média, jako je soubor na disku. Serializace je ideální pro situace, kde je požadován pro uchování stavu strukturovaných dat (třeba C++ třídy nebo struktury) během nebo po spuštění programu. Serializace objektů poskytovaných knihovnou MFC umožňuje to je však standardní a konzistentním způsobem, homogenního uživatele nutnosti provádět operace se soubory ručně.

Knihovna MFC poskytuje integrovanou podporu pro serializaci ve třídě `CObject`. Proto všechny třídy odvozené z `CObject` můžou těžit z výhod `CObject`na protokol serializace.

Základní myšlenka serializace je, že objekt by měl být schopni napsat jejím aktuálním stavu, obvykle indikován hodnoty jeho členů proměnných do trvalého úložiště. Později objekt můžete znovu vytvořit čtením nebo rekonstrukcí stavu objektu z úložiště. Serializace zpracovává všechny podrobnosti o objektu ukazatele a cyklické odkazy na objekty, které se použijí při serializaci objektu. Zásadním aspektem je, že objekt samotný zodpovídá za čtení a zápis svůj stav. Proto pro, aby byla třída serializovatelný, musí implementovat operace základní serializace. Jak je uvedeno ve skupině serializace články, je snadné přidat tuto funkci na třídu.

Knihovna MFC používá objekt `CArchive` třídu jako prostředník mezi objekt, který má být serializován a paměťovému médiu. Tento objekt je vždy přidruženo `CFile` objekt, který získá informace potřebné pro serializaci, včetně názvu souboru a určuje, zda požadovaná operace je pro čtení nebo zápisu. Můžete použít objekt, který provádí operace serializace `CArchive` objektu bez ohledu na druh paměťovému médiu.

A `CArchive` objekt používá přetížené vložení (**<\<**) a extrakce (**>>**) operátoři mohli provést zápis a čtení operací. Další informace najdete v tématu [ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md) v článku serializace: serializace objektu.

> [!NOTE]
>  Nepleťte si `CArchive` třída s atributem pro obecné účely iostream – třídy, které jsou pro formátovaný pouze text. `CArchive` Je třída Serializované objekty binární formát.

Pokud chcete, můžete obejít MFC serializace za účelem vytvoření vlastní mechanismus pro ukládání trvalých dat. Je potřeba přepsat členské funkce třídy, které se zahájí serializace příkazového uživatele. Viz diskuze v [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md) id_file_open – id_file_save – a id_file_save_as – standardní příkazy.

V následujících článcích zahrnují dva hlavní úkoly vyžadované pro serializaci:

- [Serializace: Příprava serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md)

- [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

Tento článek [serializace: Serializace vs. Databáze vstupní a výstupní](../mfc/serialization-serialization-vs-database-input-output.md) popisuje po serializace je příslušný postup vstupní a výstupní v databázových aplikacích.

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive – třída](../mfc/reference/carchive-class.md)<br/>
[CObject – třída](../mfc/reference/cobject-class.md)<br/>
[CDocument – třída](../mfc/reference/cdocument-class.md)<br/>
[CFile – třída](../mfc/reference/cfile-class.md)
