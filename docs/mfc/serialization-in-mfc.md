---
title: Serializace v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: eca4d0357977bc7ef21063718c738ae5bd8e7431
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372753"
---
# <a name="serialization-in-mfc"></a>Serializace v prostředí MFC

Tento článek vysvětluje mechanismus serializace k dispozici v Knihovně tříd Microsoft Foundation (MFC) povolit objekty zachovat mezi spuštění programu.

Serializace je proces zápisu nebo čtení objektu do nebo z trvalého paměťového média, jako je například soubor na disku. Serializace je ideální pro situace, kdy je žádoucí zachovat stav strukturovaných dat (například třídy nebo struktury jazyka C++) během nebo po spuštění programu. Použití serializačních objektů poskytovaných knihovnou MFC umožňuje, aby k tomu došlo standardním a konzistentním způsobem, což uživatele zbavuje nutnosti provádět operace se soubory ručně.

Knihovna MFC poskytuje integrovanou podporu pro `CObject`serializaci ve třídě . Všechny třídy odvozené `CObject` z proto `CObject`můžete využít 's serializační protokol.

Základní myšlenkou serializace je, že objekt by měl být schopen zapsat svůj aktuální stav, obvykle označený hodnotou jeho členských proměnných, do trvalého úložiště. Později objekt může být znovu vytvořen čtením nebo rekonstrukcí stavu objektu z úložiště. Serializace zpracovává všechny podrobnosti ukazatelů objektu a cyklické odkazy na objekty, které se používají při serializaci objektu. Klíčovým bodem je, že samotný objekt je zodpovědný za čtení a zápis vlastního stavu. Proto pro třídu serializovat, musí implementovat základní serializace operace. Jak je znázorněno ve skupině serializace článků, je snadné přidat tuto funkci do třídy.

Knihovna MFC používá `CArchive` objekt třídy jako prostředníkmezi objektserializovat a paměťové médium. Tento objekt je vždy `CFile` přidružen k objektu, ze kterého získá potřebné informace pro serializaci, včetně názvu souboru a zda je požadovaná operace čtení nebo zápis. Objekt, který provádí operaci serializace `CArchive` můžete použít objekt bez ohledu na povahu paměťového média.

Objekt `CArchive` používá přetížené vkládání**<**( )**>>** a extrakce ( ) operátory provádět operace zápisu a čtení. Další informace naleznete [v tématu Ukládání a načítání cobjects prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md) v článku Serializace: Serializace objektu.

> [!NOTE]
> Nezaměňujte `CArchive` třídu s třídou iostream pro obecné účely, které jsou pouze pro formátovaný text. Třída `CArchive` je pro binární formát serializované objekty.

Pokud chcete, můžete obejít serializaci knihovny MFC a vytvořit vlastní mechanismus pro trvalé ukládání dat. Budete muset přepsat členské funkce třídy, které iniciují serializaci na příkaz uživatele. Podívejte se na diskusi v [technické poznámce 22](../mfc/tn022-standard-commands-implementation.md) standardních příkazů ID_FILE_OPEN, ID_FILE_SAVE a ID_FILE_SAVE_AS.

Následující články pokrývají dva hlavní úkoly potřebné pro serializaci:

- [Serializace: Příprava serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md)

- [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

Článek [Serializace: Serializace vs. Vstup a výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md) popisuje, kdy je serializace vhodnou vstupní a výstupní technikou v databázových aplikacích.

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[Třída CArchiv](../mfc/reference/carchive-class.md)<br/>
[CObject – třída](../mfc/reference/cobject-class.md)<br/>
[CDocument – třída](../mfc/reference/cdocument-class.md)<br/>
[CFile – třída](../mfc/reference/cfile-class.md)
