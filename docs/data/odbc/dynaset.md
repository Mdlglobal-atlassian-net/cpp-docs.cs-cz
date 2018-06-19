---
title: Dynamická sada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec71b5b00b26564f9c8dc3c2d98f53f8182b0ca3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092315"
---
# <a name="dynaset"></a>Dynamická sada
Toto téma popisuje dynamické sady a jejich [dostupnosti](#_core_availability_of_dynasets).  
  
> [!NOTE]
>  Toto téma se vztahuje na třídách knihovny MFC rozhraní ODBC, včetně [CRecordset](../../mfc/reference/crecordset-class.md). Informace o dynamických sadách v třídy DAO najdete v tématu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Pomocí rozhraní DAO můžete otevřít dynamické sady záznamů.  
  
 Dynamická sada je sada záznamů s dynamických vlastností. Během celé jeho životnosti objekt sady záznamů v režimu dynamické sady (obvykle nazvaný dynamická sada) zůstává synchronizované se zdrojem dat následujícím způsobem. V prostředí s více uživateli může ostatním uživatelům upravit nebo odstranit záznamy, které jsou ve vaší dynamické sadě nebo přidejte záznamy do tabulky, kterou představuje vaše dynamická sada. Zaznamenává přidá do vaší aplikace nebo odstraní ze sady záznamů se projeví ve vaší dynamické sadě. Záznamy, které jiní uživatelé přidat do tabulky se neprojeví v vaší dynamické sadě, dokud nebude znovu sestavit dynamická sada voláním jeho **Requery –** – členská funkce. Když ostatní uživatelé odstranit záznamy, přeskočí MFC kód odstraňování ve vaší sadě záznamů. Ostatní uživatelé úpravy stávajících záznamů se projeví ve vaší dynamické sadě co nejrychleji přejděte na daný záznam.  
  
 Podobně úpravy, které provedete na záznamy v dynamická sada se projeví v dynamických sadách jinými uživateli. Záznamy, které přidáte se neprojeví v dynamických sadách jiných uživatelů, dokud znovu nespustí jejich dynamické sady. Záznamů, které odstraníte jsou označené jako "odstraněné" v sadách záznamů jiných uživatelů. Pokud máte více připojení do stejné databáze (více `CDatabase` objektů), sady záznamů, které jsou přidružené k těmto připojením mají stejný stav jako sady záznamů jiných uživatelů.  
  
 Dynamické sady jsou nejužitečnější, pokud data musí být dynamické jako (například) v systému rezervace letecká společnost.  
  
> [!NOTE]
>  Pokud chcete používat dynamické sady, musíte mít ovladače ODBC pro zdroj dat, který podporuje dynamické sady a nesmí být načtena knihovny kurzorů ODBC. Další informace najdete v tématu [Dostupnost dynamických sad](#_core_availability_of_dynasets).  
  
 Chcete-li určit, že sady záznamů je dynamická sada, předat **CRecordset::dynaset** jako první parametr **otevřete** – členská funkce objektu sady záznamů.  
  
> [!NOTE]
>  Ovladač ODBC pro aktualizovatelné dynamické sady, musí podporovat příkazy umístěných aktualizací nebo **:: SQLSetPos** funkce rozhraní API ODBC. Pokud jsou podporované, používá MFC **:: SQLSetPos** pro efektivitu.  
  
##  <a name="_core_availability_of_dynasets"></a> Dostupnost dynamických sad  
 Databázové třídy MFC podporují dynamické sady, pokud jsou splněny následující požadavky:  
  
-   Knihovna kurzorů rozhraní ODBC knihovny DLL nesmí být používán pro tento zdroj dat.  
  
     Pokud se používá knihovna kurzorů, skryje některé funkce základní ovladač ODBC, které jsou nezbytné pro podporu dynamické sady. Pokud chcete používat dynamické sady (a ovladač ODBC obsahuje funkce, které jsou požadované pro dynamické sady, jak je popsáno ve zbývající části této části), může způsobit MFC nenačte knihovna kurzorů při vytváření `CDatabase` objektu. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [otevřete](../../mfc/reference/cdatabase-class.md#open) funkce člena třídy `CDatabase`.  
  
     V terminologii rozhraní ODBC dynamické sady a snímky jsou označovány jako kurzory. Kurzor je mechanismus používaný pro udržování přehledu o pozici v sadě záznamů.  
  
-   Ovladač ODBC pro zdroj dat musí podporovat kurzory řízené.  
  
     Kurzory řízené spravovat data z tabulky pomocí načítání a ukládání sady klíčů. Klíče se používají k získání aktuálních dat z tabulky, co uživatel posune na určitý záznam. Chcete-li zjistit, zda váš ovladač poskytuje tuto podporu, zavolejte **:: SQLGetInfo** funkce rozhraní API ODBC se **SQL_SCROLL_OPTIONS** parametr.  
  
     Jestliže se pokusíte otevřít dynamickou sadu bez podpory sady klíčů, můžete získat `CDBException` s hodnotu návratového kódu **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**.  
  
-   Ovladač ODBC pro zdroj dat musí podporovat rozšířené načítání.  
  
     Rozšířené načítání je schopnost posunování zpět a také předávání přes výsledné záznamy jazyka SQL. Chcete-li zjistit, jestli ovladač podporuje tuto možnost, zavolejte **:: SQLGetFunctions** funkce rozhraní API ODBC se **SQL_API_SQLEXTENDEDFETCH** parametr.  
  
 Pokud chcete aktualizovatelné dynamické sady (nebo snímky, k tomuto účelu), ovladač ODBC musí také podporovat buď **:: SQLSetPos** rozhraní API ODBC nebo umístěné aktualizace. **:: SQLSetPos** povoluje funkce MFC se aktualizovat zdroj dat bez odesílání příkazů SQL. Pokud tato podpora je k dispozici, použije ho MFC přednostně k provedení aktualizací pomocí SQL. Chcete-li zjistit, zda ovladač podporuje **:: SQLSetPos**, volání **:: SQLGetInfo** s **SQL_POS_OPERATIONS** parametr.  
  
 Umístěné aktualizace používají syntaxi jazyka SQL (ve formátu **WHERE CURRENT OF** \<cursorname >) k identifikaci konkrétního řádku v tabulce na datovém zdroji. Chcete-li zjistit, jestli ovladač podporuje umístěné aktualizace, volejte **:: SQLGetInfo** s **SQL_POSITIONED_STATEMENTS** parametr.  
  
 Obecně platí dynamické sady MFC (ale ne dopředné sady záznamů) vyžadují ovladače ODBC s přizpůsobením API úroveň 2. Pokud ovladač pro zdroj dat odpovídá sada rozhraní API úrovně 1, stále můžete snímky v aktualizovatelné i jen pro čtení a dopředné sady záznamů, ale ne dynamické sady. Ovladač úrovně 1, může však podporovat dynamické sady, pokud podporuje rozšířené načítání a kurzory řízené. Další informace o úrovních přizpůsobení rozhraní ODBC najdete v tématu [ODBC](../../data/odbc/odbc-basics.md).  
  
> [!NOTE]
>  Pokud chcete použít snímky a dynamické sady, musíte je založit na dva různé `CDatabase` objekty (dvě různá připojení).  
  
 Na rozdíl od snímků, které používají zprostředkující úložiště udržuje pomocí knihovny kurzorů ODBC, dynamické sady načíst záznam přímo ze zdroje dat při posunutí. Díky tomu původně vybrali dynamickou sadou, synchronizované se zdrojem dat záznamy.  
  
 Seznam ovladačů ODBC zahrnuté v této verzi systému Visual C++ a informace o získání dalších ovladačů najdete v části [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)