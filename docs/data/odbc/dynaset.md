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
ms.openlocfilehash: ed7098600126005978c8b017e7db378fca4c1a68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213236"
---
# <a name="dynaset"></a>Dynamická sada

Toto téma popisuje dynamické sady a popisuje jejich [dostupnost](#_core_availability_of_dynasets).

> [!NOTE]
>  Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC, včetně [CRecordset](../../mfc/reference/crecordset-class.md). Informace o dynamických sadách v třídách rozhraní DAO naleznete v tématu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Pomocí rozhraní DAO můžete otevřít sady záznamů typu dynamická sada.

Dynamická sada je sada záznamů s dynamickými vlastnostmi. Během své životnosti objekt sady záznamů v režimu dynamické sady (obvykle označované jako dynamická sada) zůstává synchronizován se zdrojem dat následujícím způsobem. Ve víceuživatelském prostředí mohou jiní uživatelé upravovat nebo odstraňovat záznamy, které jsou v dynamické sadě, nebo přidávat záznamy do tabulky, kterou vaše dynamická sada představuje. Záznamy, které vaše aplikace přidá nebo odstraní ze sady záznamů, se projeví ve vaší dynamické sadě. Záznamy, které jiní uživatelé přidají do tabulky, se neprojeví ve vaší dynamické sadě, dokud znovu sestavíte dynamickou sadu voláním její členské funkce `Requery`. Pokud jiní uživatelé odstraňují záznamy, kód knihovny MFC přeskočí odstranění v sadě záznamů. Změny stávajících záznamů v ostatních uživatelích se projeví ve vaší dynamické sadě, jakmile se posuňte na ovlivněný záznam.

Podobně, úpravy, které provedete v záznamech v dynamické sadě, se projeví v dynamických sadách používaných ostatními uživateli. Záznamy, které přidáte, se neprojeví v dynamických sadách uživatelů, dokud se znovu nespustí jejich dynamické sady. Záznamy, které odstraníte, jsou v sadách záznamů jiných uživatelů označené jako odstraněné. Pokud máte více připojení ke stejné databázi (více `CDatabase` objektů), sady záznamů přidružené k těmto připojením mají stejný stav jako sady záznamů jiných uživatelů.

Dynamické sady jsou nejužitečnější, když data musí být dynamická, jako (například) v systému rezervace leteckých společností.

> [!NOTE]
> Chcete-li použít dynamické sady, je nutné mít ovladač ODBC pro zdroj dat, který podporuje dynamické sady a knihovnu kurzorů rozhraní ODBC nesmí být načtena. Další informace naleznete v tématu [dostupnost dynamických sad](#_core_availability_of_dynasets).

Chcete-li určit, že sada záznamů je dynamická sada, předejte `CRecordset::dynaset` jako první parametr do `Open` členské funkce objektu Recordset.

> [!NOTE]
> Pro aktualizovatelné dynamické sady musí váš ovladač ODBC podporovat buď příkazy umístěné v aktualizaci, nebo funkci `::SQLSetPos` rozhraní API ODBC. Pokud jsou podporovány obě, knihovna MFC používá `::SQLSetPos` pro efektivitu.

##  <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Dostupnost dynamických sad

Třídy databáze knihovny MFC podporují dynamické sady, pokud jsou splněny následující požadavky:

- Knihovna kurzorů rozhraní ODBC se nesmí pro tento zdroj dat používat.

   Pokud se používá knihovna kurzorů, maskuje některé funkce základního ovladače ODBC, který je nezbytný pro podporu dynamické sady. Chcete-li použít dynamické sady (a váš ovladač rozhraní ODBC má funkcionalitu požadovanou pro dynamické sady, jak je popsáno ve zbývající části této části), můžete způsobit, že knihovna MFC nenačte knihovnu kurzorů při vytváření objektu `CDatabase`. Další informace naleznete v tématu [rozhraní ODBC](../../data/odbc/odbc-basics.md) a [OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [otevřená](../../mfc/reference/cdatabase-class.md#open) členská funkce třídy `CDatabase`.

   V terminologii rozhraní ODBC jsou dynamické sady a snímky označovány jako kurzory. Kurzor je mechanismus, který slouží k udržení přehledu o pozici v sadě záznamů.

- Ovladač ODBC pro zdroj dat musí podporovat kurzory řízené sadou klíčů.

   Kurzory řízené sadou klíčů spravují data z tabulky tím, že získávají a ukládají sadu klíčů. Klíče se používají k získání aktuálních dat z tabulky, když se uživatel posune na konkrétní záznam. Chcete-li zjistit, zda ovladač poskytuje tuto podporu, zavolejte funkci `::SQLGetInfo` rozhraní ODBC API s parametrem *SQL_SCROLL_OPTIONS* .

   Pokud se pokusíte otevřít dynamickou sadu bez podpory sady klíčů, získáte `CDBException` s hodnotou návratového kódu AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- Ovladač ODBC pro zdroj dat musí podporovat rozšířené načítání.

   Rozšířené načítání je schopnost procházet zpět a přenášet na výsledných záznamech dotazu SQL. Chcete-li zjistit, zda ovladač podporuje tuto schopnost, zavolejte funkci `::SQLGetFunctions` rozhraní ODBC API s parametrem *SQL_API_SQLEXTENDEDFETCH* .

Pokud chcete aktualizovatelné dynamické sady (nebo snímky), musí váš ovladač ODBC podporovat také funkci `::SQLSetPos` rozhraní ODBC API nebo umístěné aktualizace. Funkce `::SQLSetPos` umožňuje knihovně MFC aktualizovat zdroj dat bez odeslání příkazů SQL. Pokud je tato podpora k dispozici, knihovna MFC ji používá v předvolbách k provádění aktualizací pomocí SQL. Chcete-li zjistit, zda ovladač podporuje `::SQLSetPos`, zavolejte `::SQLGetInfo` s parametrem *SQL_POS_OPERATIONS* .

Umístěné aktualizace používají syntaxi SQL (z formuláře, **kde Current z** \<Cursor >) k identifikaci konkrétního řádku v tabulce ve zdroji dat. Chcete-li zjistit, zda ovladač podporuje umístěné aktualizace, zavolejte `::SQLGetInfo` s parametrem *SQL_POSITIONED_STATEMENTS* .

Dynamické sady MFC (ale ne pouze dopředné sady záznamů) vyžadují ovladač ODBC s odpovídající úrovní rozhraní API úrovně 2. Pokud ovladač zdroje dat odpovídá sadě rozhraní API úrovně 1, můžete i nadále používat jen aktualizovatelné snímky i snímky jen pro čtení a pouze dopředné sady záznamů, ale ne dynamické sady. Ovladač úrovně 1 však může podporovat dynamické sady, pokud podporuje rozšířené načítání a kurzory řízené sadou klíčů. Další informace o úrovních dodržování rozhraní ODBC najdete v tématu [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Pokud chcete použít snímky i dynamické sady, je nutné je založit na dvou různých `CDatabase` objektů (dvě různá připojení).

Na rozdíl od snímků, které používají mezilehlé úložiště udržované knihovnou kurzorů rozhraní ODBC, dynamická sada načítá záznam přímo ze zdroje dat hned po jeho přesunutí. Tím se zachová záznamy původně vybrané pomocí dynamické sady synchronizované se zdrojem dat.

Seznam ovladačů rozhraní ODBC, které jsou součástí této verze sady Visual C++ , a informace o získání dalších ovladačů naleznete v tématu [seznam ovladačů rozhraní ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
