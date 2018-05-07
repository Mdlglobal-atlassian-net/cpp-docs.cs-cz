---
title: 'ODBC: Knihovna kurzorů rozhraní ODBC | Microsoft Docs'
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
ms.openlocfilehash: e57251263738d534b7e7e22ff287607fbc5159a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: Knihovna kurzorů rozhraní ODBC
Toto téma popisuje knihovny kurzorů ODBC a vysvětluje, jak ho použít. Další informace naleznete v tématu:  
  
-   [Ovladače ODBC – knihovna kurzorů a úrovně 1](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Umístěné aktualizace a sloupce časového razítka](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Použití knihovny kurzorů](#_core_using_the_cursor_library)  
  
 Knihovna kurzorů rozhraní ODBC je dynamická knihovna (DLL), který se nachází mezi správce ovladačů ODBC a ovladači. Z hlediska rozhraní ODBC ovladač udržuje kurzoru ke sledování jeho umístění v sadě záznamů. Kurzor označí pozici v sadě záznamů, do které jste již přešli – záznam na aktuální záznam.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Ovladače ODBC – knihovna kurzorů a úrovně 1  
 Knihovna kurzorů rozhraní ODBC poskytuje ovladače úrovně 1 následující nové funkce:  
  
-   Posun vpřed a zpět. Úroveň 2 ovladače nepotřebují knihovna kurzorů, protože jsou již posuvné.  
  
-   Podpora pro snímky. Knihovna kurzorů spravuje vyrovnávací paměť, který obsahuje záznamy snímku. Této vyrovnávací paměti se vztahuje k odstranění vašeho programu a úpravy záznamů, ale není přidání, odstranění nebo úpravy jiných uživatelů. Snímek je proto pouze jako aktuální jako knihovna kurzorů vyrovnávací paměti. Vyrovnávací paměť také neodráží vaše vlastní přídavky dokud zavoláte **Requery –**. Dynamické sady nepoužívejte knihovna kurzorů.  
  
 Knihovna kurzorů vám snímků (statické kurzory) i v případě, že vaše ovladačem nepodporují normálně. Pokud ovladač již podporuje statické kurzory, není potřeba načíst knihovna kurzorů získat podporu snímku. Pokud použití knihovny kurzorů, můžete použít pouze snímky a dopředné sady záznamů. Pokud ovladač podporuje dynamické sady (kurzory KEYSET_DRIVEN) a chcete je použít, nesmí použití knihovny kurzorů. Pokud chcete použít snímky a dynamické sady, musíte je založit na dva různé `CDatabase` objekty (dvě různá připojení), pokud ovladač podporuje obě.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Umístěné aktualizace a sloupce časového razítka  
  
> [!NOTE]
>  Zdroje dat ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu nebo třídy MFC objekt DAO (Data Access).  
  
> [!NOTE]
>  Pokud ovladač ODBC podporuje **SQLSetPos**, které MFC používá, pokud je k dispozici, toto téma se nevztahuje na vás.  
  
 Většina ovladače úrovně 1 nepodporuje umístěné aktualizace. Tyto ovladače jsou závislé na knihovně kurzor v tomto ohledu emulovat možnosti ovladače Level 2. Knihovna kurzorů emuluje podporu umístěných aktualizací pomocí tohoto postupu prohledávané aktualizace na pole neměnné.  
  
 V některých případech může sada záznamů obsahovat sloupec časového razítka jako jeden z těchto neměnných polí. Při použití sady záznamů MFC tabulek, které obsahují sloupce časového razítka se vyskytnout potíže se dvěma.  
  
 První problém se týká aktualizovatelných snímků v tabulkách se sloupci časové razítko. Pokud v tabulce, ke kterému je vázán snímek obsahuje sloupec časového razítka, by měly volat **Requery –** po zavolání metody **upravit** a **aktualizace**. Pokud ne, nebudete moci upravit stejné záznam znovu. Při volání **upravit** a potom **aktualizace**, zápisu záznamu do zdroje dat a sloupec časového razítka se aktualizuje. Pokud není volána **Requery –**, hodnota časové razítko pro záznam v snímku již neodpovídá odpovídající časové razítko na datovém zdroji. Když se pokusíte znovu aktualizovat záznam, zdroj dat může zakázat aktualizace z důvodu neshody.  
  
 Druhý problém se týká omezení třídy [CTime](../../atl-mfc-shared/reference/ctime-class.md) při použití s `RFX_Date` funkce k přenosu informací data a času na nebo z tabulky. Zpracování `CTime` objekt ukládá nějakou režii ve formuláři extra pokročilého zpracování při přenosu dat. Rozsah kalendářních dat `CTime` objekty mohou být také příliš omezený pro některé aplikace. Novou verzi `RFX_Date` funkce přebírá ODBC **TIMESTAMP_STRUCT z** parametr místo `CTime` objektu. Další informace najdete v tématu `RFX_Date` v [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *odkaz knihovny MFC*.  

  
##  <a name="_core_using_the_cursor_library"></a> Použití knihovny kurzorů  
 Při připojení ke zdroji dat – voláním [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) – můžete určit, zda použití knihovny kurzorů pro zdroj dat. Pokud bude vytvářet snímky na tomto zdroji dat, zadejte **CDatabase::useCursorLib** možnost `dwOptions` parametru `OpenEx` nebo zadejte **TRUE** pro  **bUseCursorLib** parametru **otevřete** (výchozí hodnota je **TRUE**). Pokud ovladač ODBC podporuje dynamické sady a chcete otevřít dynamické sady ve zdroji dat, nepoužívejte knihovna kurzorů (skryje některé funkce, které potřebují pro dynamické sady). V takovém případě nezadávejte **CDatabase::useCursorLib** v `OpenEx` nebo zadejte **FALSE** pro **bUseCursorLib** parametr v **otevřete**.  
  
## <a name="see-also"></a>Viz také  
 [ODBC – základy](../../data/odbc/odbc-basics.md)