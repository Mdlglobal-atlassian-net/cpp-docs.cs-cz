---
title: 'ODBC: Knihovna kurzorů rozhraní ODBC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 064683c3905e7ad8ba1e405bd3963832c65cff57
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340401"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Knihovna kurzorů rozhraní ODBC
Toto téma popisuje knihovna kurzorů rozhraní ODBC a vysvětluje, jak ji používat. Další informace naleznete v tématu:  
  
-   [Knihovna kurzorů a 1. úrovně ovladače rozhraní ODBC](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Umístěné aktualizace a sloupce časového razítka](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Použití knihovny kurzorů](#_core_using_the_cursor_library)  
  
 Knihovna kurzorů rozhraní ODBC je dynamická knihovna (DLL), který se nachází mezi správcem ovladačů rozhraní ODBC a ovladači. V ODBC podmínky udržuje ovladač kurzoru udržovat přehled o jeho pozice v sadě záznamů. Kurzor označuje pozici v sadě záznamů, do které jste už přešli – aktuální záznam.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Knihovna kurzorů a 1. úrovně ovladače rozhraní ODBC  
 Knihovna kurzorů rozhraní ODBC poskytuje ovladače úrovně 1 následující nové funkce:  
  
-   Posun vpřed a zpět. Ovladače úrovně 2 nemusí knihovna kurzorů rozhraní, protože jsou již posuvný.  
  
-   Podpora pro snímky. Knihovna kurzorů rozhraní spravuje vyrovnávací paměť obsahující záznamy snímku. Tuto vyrovnávací paměť odráží váš program odstranění a úpravy záznamů, ale není přidání, odstranění nebo úpravy jiných uživatelů. Snímek je proto pouze jako aktuální jako knihovna kurzorů vyrovnávací paměti. Vyrovnávací paměť také nereflektuje vlastní doplňky až do okamžiku volání `Requery`. Dynamické sady nepoužívejte knihovna kurzorů rozhraní.  
  
 Knihovna kurzorů rozhraní poskytuje snímky (statický kurzor) i v případě, že jsou obvykle nepodporuje ovladače. Pokud ovladač již podporuje statický kurzor, není potřeba načíst knihovna kurzorů, jak získat podporu snímku. Pokud použití knihovny kurzorů, můžete použít pouze snímky a pouze vpřed. Jestliže ovladač podporuje dynamické sady (kurzory KEYSET_DRIVEN) a chcete je použít, nesmí používat knihovna kurzorů rozhraní. Pokud chcete použít snímky a dynamické sady, musíte je vytvořit na dva různé `CDatabase` objekty (dvě různá připojení), pokud ovladač podporuje obě.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Umístěné aktualizace a sloupce časového razítka  
  
> [!NOTE]
>  Zdroje dat rozhraní ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo třídy knihovny MFC objekt DAO (Data Access).  
  
> [!NOTE]
>  Pokud ovladač rozhraní ODBC podporuje `SQLSetPos`, které knihovna MFC používá, pokud je k dispozici, toto téma se nevztahuje na vás.  
  
 Většina ovladače úrovně 1 nepodporují umístěné aktualizace. Spolehněte se na knihovna kurzorů rozhraní pro emulaci možnosti ovladače úrovně 2 v tomto ohledu tyto ovladače. Knihovna kurzorů rozhraní emuluje podporu umístěné aktualizace tímto způsobem hledaný aktualizace neměnné polí.  
  
 V některých případech může obsahovat sadu záznamů sloupec časového razítka jako jeden z těchto polí neměnné. Při použití knihovny MFC sady záznamů tabulky obsahující sloupce časového razítka mohou vzniknout dva problémy.  
  
 První problém se týká aktualizovatelné v tabulkách se sloupci timestamp. Pokud v tabulce, ke kterému je vázán snímek obsahuje sloupec časového razítka, měli byste zavolat `Requery` po zavolání `Edit` a `Update`. V opačném případě nebude možné upravit stejný záznam znovu. Při volání `Edit` a pak `Update`, záznam se zapisují do zdroje dat a aktualizovat sloupec časového razítka. Pokud není volána `Requery`, hodnota časového razítka pro záznam ve vašem snímku už odpovídá odpovídající časové razítko ve zdroji dat. Při pokusu o záznam znovu aktualizovat zdroj dat může zakázat aktualizace z důvodu nesouladu.  
  
 Druhý problém se týká omezení třídy [CTime](../../atl-mfc-shared/reference/ctime-class.md) při použití s `RFX_Date` funkce k přenosu informací data a času na nebo z tabulky. Zpracování `CTime` režijní náklady v podobě dalších zprostředkujících zpracování při přenosu dat ukládá objekt. Obdobím `CTime` objekty mohou také být příliš omezující u některých aplikací. Nová verze `RFX_Date` funkce přijímá ODBC *TIMESTAMP_STRUCT z* parametr namísto `CTime` objektu. Další informace najdete v tématu `RFX_Date` v [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *odkaz knihovny MFC*.  

  
##  <a name="_core_using_the_cursor_library"></a> Použití knihovny kurzorů  
 Když se připojíte ke zdroji dat – voláním [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) – můžete určit, jestli se má použít pro zdroj dat knihovna kurzorů rozhraní. Pokud budete vytvářet snímky na tomto zdroji dat, zadejte `CDatabase::useCursorLib` možnost `dwOptions` parametr `OpenEx` nebo zadejte hodnotu PRAVDA pro *bUseCursorLib* parametr `Open` (výchozí hodnota je HODNOTA TRUE.) Pokud ovladač rozhraní ODBC podporuje dynamické a chcete otevřít dynamické ve zdroji dat, není použití knihovny kurzorů (zakrývá některé funkce, které potřebují pro dynamické sady). V tomto případě nezadávejte `CDatabase::useCursorLib` v `OpenEx` nebo zadat hodnotu FALSE pro *bUseCursorLib* parametr `Open`.  
  
## <a name="see-also"></a>Viz také  
 [ODBC – základy](../../data/odbc/odbc-basics.md)