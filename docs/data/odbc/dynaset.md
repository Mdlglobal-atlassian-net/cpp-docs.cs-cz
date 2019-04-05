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
ms.openlocfilehash: 21c47546d14d9a121bdd0698fe96eb133dbc44a0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040407"
---
# <a name="dynaset"></a>Dynamická sada

Toto téma popisuje dynamické sady a jejich [dostupnosti](#_core_availability_of_dynasets).

> [!NOTE]
>  Toto téma platí pro třídy knihovny MFC rozhraní ODBC, včetně [CRecordset](../../mfc/reference/crecordset-class.md). Informace o dynamické sady tříd DAO najdete v tématu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Pomocí rozhraní DAO můžete otevřít dynamické sady záznamů.

Dynamická sada je sada záznamů s dynamických vlastností. Během celé jeho životnosti objektu sady záznamů v režimu dynamická sada (obvykle označované jako dynamická sada) zůstane synchronizovaná se zdrojem dat následujícím způsobem. V prostředí může jiným uživatelům upravit nebo odstranit záznamy, které jsou ve vaší dynamická sada nebo přidávat záznamy do tabulky, který představuje vaše dynamická sada. Záznamy aplikace přidá nebo odstraní ze sady záznamů se projeví ve vašich dynamických sad. Záznamy, které uživateli umožňuje přidat do tabulky se neprojeví v vašich dynamických sad, dokud je znovu sestavit dynamická sada voláním jeho `Requery` členskou funkci. Když ostatní uživatelé odstraní záznamy, kód knihovny MFC přeskočí odstranění v sady záznamů. Úpravy změny dalších uživatelů na existující záznamy se projeví v vašich dynamických sad, jakmile posunete na daný záznam.

Podobně úpravy, které provedete v dynamická sada záznamů se projeví v dynamických sadách používán jinými uživateli. Záznamy, které přidáte se neprojeví v dynamických sadách jiných uživatelů, dokud jejich requery jejich dynamické sady. Záznamy, které se při odstranění jsou označeny jako "odstranit" v sadách záznamů jiných uživatelů. Pokud máte několik připojení ke stejné databázi (více `CDatabase` objekty), přidružené k těmto připojením sady záznamů se stejným stavem jako sady záznamů jiných uživatelů.

Dynamické sady jsou nejvíc hodí v situaci, když data musí být dynamická a jako (například) systém pro rezervaci letenek.

> [!NOTE]
> Pokud chcete používat dynamické sady, musí mít ovladač rozhraní ODBC pro zdroj dat, která podporuje dynamické sady a nesmí být načtena knihovna kurzorů rozhraní ODBC. Další informace najdete v tématu [Dostupnost dynamických sad](#_core_availability_of_dynasets).

Chcete-li určit, že sady záznamů je dynamická sada, předejte `CRecordset::dynaset` jako první parametr `Open` členské funkce objektu sady záznamů.

> [!NOTE]
> Pro dynamické sady aktualizovat, ovladač rozhraní ODBC musí podporovat příkazy umístěných aktualizací nebo `::SQLSetPos` funkce ODBC API. Pokud jsou podporované, knihovna MFC používá `::SQLSetPos` efektivitu.

##  <a name="_core_availability_of_dynasets"></a> Dostupnost dynamických sad

MFC – databázové třídy podporovat dynamické sady, pokud jsou splněny následující požadavky:

- Knihovna kurzorů rozhraní ODBC knihovny DLL nesmí být pro tento zdroj dat používá.

   Pokud je použita knihovna kurzorů, masky některé funkce základní ovladač ODBC, které jsou nezbytné pro podporu dynamické sady. Pokud chcete použít dynamické sady (a ovladač ODBC má funkci vyžadovanou pro dynamické sady, jak je popsáno ve zbytku této části), můžete použít knihovnu MFC knihovna kurzorů rozhraní nenačte, když vytvoříte `CDatabase` objektu. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [otevřít](../../mfc/reference/cdatabase-class.md#open) členské funkce třídy `CDatabase`.

   V terminologii rozhraní ODBC snímky a dynamické sady jsou označovány jako ukazatele. Kurzor je mechanismus používaný pro uchování záznamu o jeho pozice v sadě záznamů.

- Ovladač ODBC pro zdroj dat musí podporovat kurzory řízené.

   Kurzory řízené získávání a ukládání sady klíčů spravovat data z tabulky. Klíče se používají k získání aktuálních dat z tabulky, když uživatel přesune na konkrétní záznam. Chcete-li zjistit, zda váš ovladač poskytuje této podpory, zavolejte `::SQLGetInfo` funkce ODBC API se *SQL_SCROLL_OPTIONS* parametru.

   Pokud se pokusíte otevřít dynamická sada bez podpory sady klíčů, můžete získat `CDBException` hodnotou AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED návratový kód.

- Ovladač ODBC pro zdroj dat musí podporovat rozšířené načítání.

   Rozšířené načítání je schopnost posuňte se zpět, stejně jako předat prostřednictvím záznamy výsledku dotazu SQL. Chcete-li zjistit, jestli ovladač podporuje tuto možnost, zavolejte `::SQLGetFunctions` funkce ODBC API se *SQL_API_SQLEXTENDEDFETCH* parametru.

Pokud chcete aktualizovat dynamické sady (nebo snímky k tomuto účelu), ovladač rozhraní ODBC musí také podporovat buď `::SQLSetPos` rozhraní API ODBC nebo umístěné aktualizace. `::SQLSetPos` Funkce umožňuje knihovny MFC pro aktualizaci zdroje dat bez odesílání příkazů jazyka SQL. Pokud tato podpora je k dispozici, MFC používá preferenci pro provádění aktualizací pomocí jazyka SQL. Chcete-li zjistit, jestli ovladač podporuje `::SQLSetPos`, volání `::SQLGetInfo` s *SQL_POS_OPERATIONS* parametru.

Umístěné aktualizace syntaxí SQL (ve formátu **WHERE CURRENT OF** \<cursorname >) k identifikaci konkrétního řádku v tabulce na zdroj dat. Chcete-li zjistit, jestli váš ovladač podporuje umístěné aktualizace, zavolejte `::SQLGetInfo` s *SQL_POSITIONED_STATEMENTS* parametru.

Obecně platí dynamické knihovny MFC (ale ne pouze vpřed) vyžadují ovladač rozhraní ODBC se shoda rozhraní API úrovně 2. Pokud ovladač pro zdroj dat odpovídá sada rozhraní API úrovně 1, můžete stále použít snímky aktualizovatelné i jen pro čtení a pouze vpřed, ale ne dynamické sady. Ovladač úrovně 1 může však podporovat dynamické sady, pokud ji podporuje rozšířené načítání a kurzory řízené. Další informace o úrovních ODBC přizpůsobení, najdete v části [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Pokud chcete použít snímky a dynamické sady, musíte je vytvořit na dva různé `CDatabase` objekty (dvě různá připojení).

Na rozdíl od snímků, které používají udržuje sloužící jako přechodné úložiště podle knihovna kurzorů rozhraní ODBC, dynamické sady načíst záznam přímo ze zdroje dat poté, co přejděte do něj. Záznamy původně zvolila dynamická sada synchronizované se zdrojem dat se takto zachová.

Seznam ovladačů ODBC zahrnuté v této verzi systému Visual C++ a informace o získání dalších ovladačů najdete v tématu [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Viz také:

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)