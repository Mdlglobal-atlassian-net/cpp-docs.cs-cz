---
title: 'ODBC: Knihovna kurzorů rozhraní ODBC'
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367184"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Knihovna kurzorů rozhraní ODBC

Toto téma popisuje knihovnu kurzorů ODBC a vysvětluje, jak ji používat. Další informace naleznete v tématu:

- [Knihovna kurzorů a ovladače ODBC úrovně 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Umístěné aktualizace a sloupce časového razítka](#_core_positioned_updates_and_timestamp_columns)

- [Použití knihovny kurzorů](#_core_using_the_cursor_library)

Knihovna kurzorů ROZHRANÍ ODBC je dynamická knihovna (DLL), která se nachází mezi Správcem ovladačů ROZHRANÍ ODBC a ovladačem. Z hlediska ROZHRANÍ ODBC ovladač udržuje kurzor sledovat jeho pozici v sadě záznamů. Kurzor označuje pozici v sadě záznamů, do které jste se již posouvali – aktuální záznam.

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Knihovna kurzorů a ovladače ODBC úrovně 1

Knihovna kurzorů rozhraní ODBC poskytuje ovladači úrovně 1 následující nové funkce:

- Posouvání vpřed a vzad. Ovladače úrovně 2 nepotřebují knihovnu kurzorů, protože jsou již posuvitelné.

- Podpora pro snímky. Knihovna kurzoru spravuje vyrovnávací paměť obsahující záznamy snímku. Tato vyrovnávací paměť odráží odstranění a úpravy záznamů programu, ale nikoli přidání, odstranění nebo úpravy jiných uživatelů. Proto snímek je pouze tak aktuální jako vyrovnávací paměť knihovny kurzoru. Vyrovnávací paměť také neodráží vlastní dodatky, dokud nezavoláte `Requery`. Sady dynasadí nepoužívají knihovnu kurzorů.

Knihovna kurzorů poskytuje snímky (statické kurzory), i když nejsou obvykle podporovány ovladačem. Pokud ovladač již podporuje statické kurzory, není nutné načíst knihovnu kurzoru získat podporu snímek. Pokud používáte knihovnu kurzorů, můžete použít pouze snímky a sady záznamů pouze pro předávání. Pokud ovladač podporuje sady dynasety (KEYSET_DRIVEN kurzory) a chcete je používat, nesmíte používat knihovnu kurzorů. Pokud chcete použít snímky i sady dynase, musíte je `CDatabase` založit na dvou různých objektech (dvě různá připojení), pokud ovladač nepodporuje obojí.

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Umístěné aktualizace a sloupce časového razítka

> [!NOTE]
> Zdroje dat ROZHRANÍ ODBC jsou přístupné prostřednictvím tříd knihovny MFC ODBC, jak je popsáno v tomto tématu, nebo prostřednictvím tříd DAO (MFC Data Access Object).

> [!NOTE]
> Pokud ovladač ROZHRANÍ `SQLSetPos`ODBC podporuje , který knihovna MFC používá, pokud je k dispozici, toto téma se vás nevztahuje.

Většina ovladačů úrovně 1 nepodporuje umístěné aktualizace. Tyto ovladače spoléhají na knihovnu kurzorů, aby v tomto ohledu emulovaly možnosti ovladačů úrovně 2. Knihovna kurzorů emuluje podporu umístěných aktualizací provedením prohledávané aktualizace neměnných polí.

V některých případech může sada záznamů obsahovat sloupec časového razítka jako jedno z těchto neměnných polí. Při používání sad záznamů knihovny MFC s tabulkami, které obsahují sloupce časového razítka, vznikají dva problémy.

První problém se týká aktualizovatelných snímků v tabulkách se sloupci časového razítka. Pokud tabulka, ke které je snímek vázán, obsahuje `Requery` sloupec `Edit` časového `Update`razítka, měli byste zavolat po volání a . Pokud tomu tak není, pravděpodobně nebudete moci znovu upravit stejný záznam. Při volání `Edit` a `Update`potom se záznam zapíše do zdroje dat a sloupec časového razítka se aktualizuje. Pokud nezavoláte `Requery`, hodnota časového razítka pro záznam ve snímku již neodpovídá odpovídajícímu časovému razítku ve zdroji dat. Při pokusu o aktualizaci záznamu znovu zdroj dat může zakázat aktualizaci z důvodu neshody.

Druhý problém se týká omezení třídy [CTime](../../atl-mfc-shared/reference/ctime-class.md) při použití s `RFX_Date` funkcí k přenosu informací o čase a datu do nebo z tabulky. Zpracování `CTime` objektu ukládá určitou režii ve formě dalšího zprostředkujícího zpracování během přenosu dat. Rozsah dat `CTime` objektů může být také příliš omezující pro některé aplikace. Nová verze `RFX_Date` funkce přebírá parametr *ODBC TIMESTAMP_STRUCT* `CTime` namísto objektu. Další informace naleznete `RFX_Date` v tématu [Makra a globální](../../mfc/reference/mfc-macros-and-globals.md) úrovně v *referenční příručce knihovny MFC*.

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Použití knihovny kurzorů

Když se připojíte ke zdroji dat – voláním [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) – můžete určit, zda se má pro zdroj dat použít knihovna kurzorů. Pokud budete vytvářet snímky na tomto zdroji `CDatabase::useCursorLib` dat, `dwOptions` zadejte v parametru možnost hodnotu HODNOTIta `OpenEx` nebo zadejte hodnotu TRUE pro parametr *bUseCursorLib* `Open` na (výchozí hodnota je TRUE). Pokud ovladač ODBC podporuje sady dynasety a chcete otevřít sady dynaseje ve zdroji dat, nepoužívejte knihovnu kurzorů (maskuje některé funkce ovladače potřebné pro dynasady). V takovém `CDatabase::useCursorLib` případě nezadávejte v `OpenEx` ani nezadávejte hodnotu FALSE pro parametr *bUseCursorLib* v . `Open`

## <a name="see-also"></a>Viz také

[Základy rozhraní ODBC](../../data/odbc/odbc-basics.md)
