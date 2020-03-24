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
ms.openlocfilehash: 51524604cad34ace18ffda2b5f48cc3c5fd89ad7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213093"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Knihovna kurzorů rozhraní ODBC

Toto téma popisuje knihovnu kurzorů rozhraní ODBC a vysvětluje, jak ji použít. Další informace naleznete v tématu:

- [Knihovna kurzorů a ovladače rozhraní ODBC úrovně 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Sloupce umístěné aktualizace a časové razítko](#_core_positioned_updates_and_timestamp_columns)

- [Použití knihovny kurzorů](#_core_using_the_cursor_library)

Knihovna kurzorů rozhraní ODBC je dynamická knihovna (DLL), která se nachází mezi správcem ovladačů ODBC a ovladačem. V terminologii rozhraní ODBC ovladač udržuje kurzor, aby udržel přehled o poloze v sadě záznamů. Kurzor označí pozici v sadě záznamů, na kterou jste již přesunuli – aktuální záznam.

##  <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Knihovna kurzorů a ovladače rozhraní ODBC úrovně 1

Knihovna kurzorů rozhraní ODBC poskytuje ovladačům úrovně 1 následující nové funkce:

- Dopředu a zpětně posouvání. Ovladače úrovně 2 nepotřebují knihovnu kurzorů, protože už jsou rolovací.

- Podpora snímků. Knihovna kurzorů spravuje vyrovnávací paměť obsahující záznamy snímku. Tato vyrovnávací paměť odráží změny v programu a úpravy záznamů, ale ne přidání, odstranění nebo úpravy jiných uživatelů. Proto je snímek pouze aktuální jako vyrovnávací paměť knihovny kurzorů. Vyrovnávací paměť také neodráží vaše vlastní dodatky, dokud nebudete volat `Requery`. Dynamické sady nepoužívají knihovnu kurzorů.

Knihovna kurzorů poskytuje snímky (statické kurzory), a to i v případě, že ovladač není normálně podporován. Pokud ovladač již podporuje statické kurzory, není nutné načíst knihovnu kurzorů a získat tak podporu snímků. Použijete-li knihovnu kurzorů, můžete použít pouze snímky a sady záznamů s dopředné pouze. Pokud ovladač podporuje dynamické sady (KEYSET_DRIVEN kurzory) a chcete je použít, nesmíte použít knihovnu kurzorů. Pokud chcete použít snímky i dynamické sady, je nutné je založit na dvou různých `CDatabase` objektů (dvou různých připojení), pokud ovladač nepodporuje obě.

##  <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Sloupce umístěné aktualizace a časové razítko

> [!NOTE]
>  Zdroje dat ODBC jsou přístupné prostřednictvím tříd knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo prostřednictvím tříd DAO (Data Access Object) knihovny MFC.

> [!NOTE]
>  Pokud ovladač ODBC podporuje `SQLSetPos`, která knihovna MFC používá, je-li k dispozici, toto téma pro vás neplatí.

Většina ovladačů úrovně 1 nepodporuje umístěné aktualizace. Tyto ovladače spoléhají na knihovnu kurzorů k emulaci schopností ovladačů úrovně 2 v tomto ohledu. Knihovna kurzorů emuluje podporu umístěnou na základě hledání v nezměněných polích.

V některých případech sada záznamů může obsahovat sloupec časového razítka jako jedno z těchto nezměněných polí. Při použití sad záznamů knihovny MFC s tabulkami, které obsahují sloupce časového razítka, vznikají dva problémy.

První problém se týká aktualizovatelných snímků v tabulkách se sloupci časových razítek. Pokud tabulka, na kterou je váš snímek svázán, obsahuje sloupec s časovým razítkem, měli byste volat `Requery` po volání `Edit` a `Update`. V takovém případě pravděpodobně nebudete moci znovu upravit stejný záznam. Když zavoláte `Edit` a potom `Update`, záznam se zapíše do zdroje dat a aktualizuje se sloupec časového razítka. Pokud nevoláte `Requery`, hodnota časového razítka záznamu ve snímku se už neshoduje s odpovídajícím časovým razítkem ve zdroji dat. Když se pokusíte aktualizovat záznam znovu, zdroj dat může aktualizaci zakázat kvůli neshodě.

Druhý problém se týká omezení třídy [CTime –](../../atl-mfc-shared/reference/ctime-class.md) při použití s funkcí `RFX_Date` k přenosu informací o čase a data do nebo z tabulky. Zpracování objektu `CTime` při přenosu dat má za následek určitou režii ve formě dalšího průběžného zpracování. Rozsah dat `CTime` objektů může být také příliš omezený pro některé aplikace. Nová verze funkce `RFX_Date` přebírá parametr ODBC *TIMESTAMP_STRUCT* namísto objektu `CTime`. Další informace naleznete v tématu `RFX_Date` v [makrech a Globals](../../mfc/reference/mfc-macros-and-globals.md) v *Referenci knihovny MFC*.

##  <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Použití knihovny kurzorů

Když se připojíte ke zdroji dat – voláním metody [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) – můžete určit, zda se má pro zdroj dat použít knihovna kurzorů. Pokud budete v tomto zdroji dat vytvářet snímky, určete možnost `CDatabase::useCursorLib` v parametru `dwOptions` `OpenEx` nebo zadejte hodnotu TRUE pro parametr *bUseCursorLib* `Open` (výchozí hodnota je true). Pokud ovladač ODBC podporuje dynamické sady a chcete otevřít dynamické sady na zdroji dat, nepoužívejte knihovnu kurzorů (maskuje některé funkce ovladače potřebné pro dynamické sady). V takovém případě nezadávejte `CDatabase::useCursorLib` v `OpenEx` nebo v `Open`zadejte hodnotu FALSE pro parametr *bUseCursorLib* .

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)
