---
title: Dynamická sada
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371831"
---
# <a name="dynaset"></a>Dynamická sada

Toto téma popisuje dynasady a popisuje jejich [dostupnost](#_core_availability_of_dynasets).

> [!NOTE]
> Toto téma se týká tříd rozhraní MFC ODBC, včetně [sady CRecordset](../../mfc/reference/crecordset-class.md). Informace o dynasetech ve třídách DAO naleznete v [tématu CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Pomocí dao můžete otevřít sady záznamů typu dynaset.

Sada dynasetu je sada záznamů s dynamickými vlastnostmi. Během své životnosti zůstane objekt sady záznamů v režimu dynasetu (obvykle nazývaný dynasada) synchronizován se zdrojem dat následujícím způsobem. Ve víceuživatelském prostředí mohou ostatní uživatelé upravovat nebo odstraňovat záznamy, které jsou ve vaší dynasetě, nebo přidávat záznamy do tabulky, kterou vaše sada dynasad představuje. Záznamy, které aplikace přidá nebo odstraní ze sady záznamů, se projeví ve vaší dynasetě. Záznamy, které ostatní uživatelé přidají do tabulky, se v dynasetě neprojeví, dokud neobnovíte dynasetu voláním její `Requery` členské funkce. Když ostatní uživatelé odstraní záznamy, kód knihovny MFC přeskočí odstranění v sadě záznamů. Změny úprav existujících záznamů ostatních uživatelů se projeví ve vaší dynasetě, jakmile přejdete na ovlivněný záznam.

Podobně úpravy, které provedete u záznamů v dynasetě, se projeví v dynasetech, které používají jiní uživatelé. Záznamy, které přidáte, se neprojeví v dynasetech jiných uživatelů, dokud znovu nezadají dotaz na své dynasady. Záznamy, které odstraníte, jsou v sadách záznamů jiných uživatelů označeny jako "odstraněné". Pokud máte více připojení ke stejné `CDatabase` databázi (více objektů), mají sady záznamů přidružené k těmto připojením stejný stav jako sady záznamů jiných uživatelů.

Dynamické sady jsou nejcennější, když data musí být dynamická, jako například v rezervačním systému leteckých společností.

> [!NOTE]
> Chcete-li používat sady dynasetu, musíte mít ovladač ODBC pro zdroj dat, který podporuje sady dynase, a knihovna kurzorů ODBC nesmí být načtena. Další informace naleznete v [tématu Dostupnost dynasetu](#_core_availability_of_dynasets).

Chcete-li určit, že sada záznamů je `CRecordset::dynaset` sada dynasetu, předejte jako první parametr `Open` členské funkci objektu sady záznamů.

> [!NOTE]
> U aktualizovatelných dynasese musí ovladač ROZHRANÍ ODBC podporovat `::SQLSetPos` buď umístěné příkazy aktualizace, nebo funkci rozhraní API ROZHRANÍ ODBC. Pokud jsou podporovány obě, knihovna MFC používá `::SQLSetPos` pro efektivitu.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Dostupnost dynasetu

Třídy databáze knihovny MFC podporují sady dynasadů, pokud jsou splněny následující požadavky:

- Knihovna DLL knihovny kurzorů ROZHRANÍ ODBC nesmí být pro tento zdroj dat používána.

   Pokud je použita knihovna kurzorů, maskuje některé funkce základního ovladače ODBC, který je nezbytný pro podporu dynasetu. Pokud chcete použít sady dynasets (a ovladač ROZHRANÍ ODBC má funkce požadované pro dynasady, jak je popsáno ve zbývající části této `CDatabase` části), můžete způsobit, že knihovna MFC nenačte knihovnu kurzorů při vytváření objektu. Další informace naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [Open](../../mfc/reference/cdatabase-class.md#open) člen funkce třídy `CDatabase`.

   V terminologii ODBC jsou dynasady a snímky označovány jako kurzory. Kurzor je mechanismus používaný pro sledování jeho pozice v sadě záznamů.

- Ovladač ROZHRANÍ ODBC pro váš zdroj dat musí podporovat kurzory řízené sadou klíčů.

   Kurzory řízené sadou klíčů spravují data z tabulky získáním a uložením sady klíčů. Klíče se používají k získání aktuálních dat z tabulky, když uživatel posouvá na konkrétní záznam. Chcete-li zjistit, zda ovladač `::SQLGetInfo` poskytuje tuto podporu, zavolejte funkci ROZHRANÍ API ROZHRANÍ ODBC s parametrem *SQL_SCROLL_OPTIONS.*

   Pokud se pokusíte otevřít sadu dynaset bez `CDBException` podpory sady klíčů, získáte s hodnotou návratového kódu AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- Ovladač ROZHRANÍ ODBC pro váš zdroj dat musí podporovat rozšířené načítání.

   Rozšířené načítání je možnost posunout zpět i vpřed přes výsledné záznamy dotazu SQL. Chcete-li zjistit, zda ovladač `::SQLGetFunctions` tuto schopnost podporuje, zavolejte funkci ROZHRANÍ API ROZHRANÍ ODBC s parametrem *SQL_API_SQLEXTENDEDFETCH.*

Pokud chcete aktualizovatelné dynamické sady (nebo snímky, když na to přijde), ovladač `::SQLSetPos` ODBC musí také podporovat funkci rozhraní API ROZHRANÍ ODBC nebo umístěné aktualizace. Funkce `::SQLSetPos` umožňuje knihovně MFC aktualizovat zdroj dat bez odesílání příkazů SQL. Pokud je tato podpora k dispozici, knihovna MFC ji používá přednostně k provádění aktualizací pomocí sql. Chcete-li zjistit, `::SQLSetPos`zda `::SQLGetInfo` ovladač podporuje , volejte s *parametrem SQL_POS_OPERATIONS.*

Umístěné aktualizace používají syntaxi SQL (formuláře, **kde current of** \<cursorname>) k identifikaci konkrétního řádku v tabulce ve zdroji dat. Chcete-li zjistit, zda ovladač `::SQLGetInfo` podporuje umístěné aktualizace, zavolejte s *parametrem SQL_POSITIONED_STATEMENTS.*

Dynasady knihovny MFC (ale ne pouze dopředu) obvykle vyžadují ovladač ROZHRANÍ ODBC s shodou rozhraní API úrovně 2. Pokud ovladač pro váš zdroj dat odpovídá sadě rozhraní API úrovně 1, můžete stále používat aktualizovatelné snímky i snímky jen pro čtení a sady záznamů pouze pro předávání, ale ne dynamické sady. Ovladač úrovně 1 však může podporovat dynasady, pokud podporuje rozšířené načítání a kurzory řízené sadou klíčů. Další informace o úrovních shody rozhraní ODBC naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Pokud chcete použít snímky i dynasady, musíte je založit na dvou různých `CDatabase` objektech (dvě různá připojení).

Na rozdíl od snímků, které používají zprostředkující úložiště spravované knihovnou kurzorů ROZHRANÍ ODBC, načíst dynasady záznam přímo ze zdroje dat, jakmile se k němu přejdete. Tím se záznamy původně vybrané sadou dynasetu synchronizují se zdrojem dat.

Seznam ovladačů ODBC zahrnutých v této verzi jazyka Visual C++ a informace o získání dalších ovladačů naleznete v [tématu Seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
