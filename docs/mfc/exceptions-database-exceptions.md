---
title: 'Výjimky: Databáze výjimky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2168bc530accfdde6fad4d41cd68e94d3088f153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-database-exceptions"></a>Výjimky: Výjimky databáze
Tento článek vysvětluje způsob zpracování výjimek databáze. Většina materiálu v tomto článku platí jak pro práci s třídy MFC pro připojení ODBC (Open Database) nebo třídy MFC pro objekty DAO (Data Access). Materiály, které jsou specifické pro jednu nebo jiný model je explicitně označen. Témata zahrnují:  
  
-   [Přístupy k zpracování výjimek](#_core_approaches_to_exception_handling)  
  
-   [V příkladu zpracování výjimek databáze](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> Přístupy k zpracování výjimek  
 Přístup je stejný, zda pracujete s DAO nebo ODBC.  
  
 Vždy byste měli zapsat obslužné rutiny výjimek pro zpracování výjimečných podmínek.  
  
 Většina protokol přístup k zachycování výjimek databáze je k testování aplikace s výjimce scénářů. Určení pravděpodobně výjimky, které může dojít k operace ve vašem kódu a vynutit výjimka, která má dojít. Poté vyhledejte ve výstupu trasování, pokud chcete zobrazit, jaké se výjimka nebo zkontrolujte chyby vrácené informace v ladicím programu. Tímto způsobem zjistíte, které návratové kódy, které se zobrazí pro scénáře výjimky, které používáte.  
  
### <a name="error-codes-used-for-odbc-exceptions"></a>Chybové kódy používané pro výjimky rozhraní ODBC  
 Kromě definované rozhraní návratové kódy, které mají názvy ve formátu **AFX_SQL_ERROR_XXX**, některé [CDBExceptions](../mfc/reference/cdbexception-class.md) jsou založené na [ODBC](../data/odbc/odbc-basics.md) návratové kódy. Návratové kódy pro takové výjimky mít názvy ve formátu **SQL_ERROR_XXX**.  
  
 Návratové kódy – definované framework i definované ODBC – databázové třídy může vrátit jsou popsané v části [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) – datový člen třídy `CDBException`. Další informace o návratové kódy, které jsou definované rozhraní ODBC jsou k dispozici v sadě SDK ODBC *referenční informace pro programátory* v knihovně MSDN.  
  
### <a name="error-codes-used-for-dao-exceptions"></a>Chybové kódy používané pro výjimky rozhraní DAO  
 Výjimky rozhraní DAO je obvykle dostupná na další informace. Informace o chybě můžete přistupovat prostřednictvím tři datové členy zachycení [CDaoException](../mfc/reference/cdaoexception-class.md) objektu:  
  
-   [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) obsahuje odkazy [cdaoerrorinfo –](../mfc/reference/cdaoerrorinfo-structure.md) objekt, který zapouzdřuje informace o chybě v rozhraní DAO na kolekci objektů chyba přidružený k databázi.  
  
-   [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) obsahuje rozšířené chybový kód z tříd MFC rozhraní DAO. Tyto kódy chyb, které mají názvy ve formátu **AFX_DAO_ERROR_XXX**, jsou popsané v části datového člena v `CDaoException`.  
  
-   [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) obsahuje OLE `SCODE` z rozhraní DAO, pokud je k dispozici. Málokdy budete potřebovat pro práci s tímto kódem chyby, ale. Další informace jsou obvykle dostupné v dalších dvou datových členů. Viz datový člen Další informace o `SCODE` hodnoty.  
  
 Další informace o rozhraní DAO chyby, typ objektu chyby rozhraní DAO a kolekce DAO chyb jsou k dispozici v rámci třídy [CDaoException](../mfc/reference/cdaoexception-class.md).  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> V příkladu zpracování výjimek databáze  
 V následujícím příkladu se pokusí vytvořit [CRecordset](../mfc/reference/crecordset-class.md)-odvozené objektu v haldě s **nové** operátor a potom otevřete sadu záznamů (pro zdroje dat ODBC). Podobně jako příklad pro třídy DAO najdete v tématu "DAO výjimky" následující příklad.  
  
### <a name="odbc-exception-example"></a>Příklad výjimky rozhraní ODBC  
 [Otevřete](../mfc/reference/crecordset-class.md#open) – členská funkce může vyvolat výjimku (typu [CDBException](../mfc/reference/cdbexception-class.md) pro třídy rozhraní ODBC), takže tento kód závorky **otevřete** volání s **akci**  bloku. Následujících **catch** blok zachytí `CDBException`. Může zkontrolujte objekt výjimky, samostatně, názvem `e`, ale v takovém případě stačí vědět, že pro vytvoření sady záznamů se nezdařilo. **Catch** bloku zobrazí okno se zprávou a vyčistí odstraněním objekt sady záznamů.  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]  
  
### <a name="dao-exception-example"></a>Příklad Výjimka rozhraní DAO  
 Příklad DAO je podobný příklad pro rozhraní ODBC, ale obvykle můžete získat další druh informací. Následující kód také pokusí otevřít sadu záznamů. Pokud tento pokus vyvolá výjimku, můžete prozkoumat datový člen objektu výjimky pro informace o chybě. Protože předchozí příklad ODBC, je pravděpodobně dostatek vědět, že pokus o vytvoření sady záznamů se nezdařilo.  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]  
  
 Tento kód získá řetězec chybové zprávy z [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) členem objekt výjimky. MFC doplní tento člen, pokud ji vyvolá výjimku.  
  
 Informace o vrácené informace o chybě `CDaoException` objektu, najdete v tématu třídy [CDaoException](../mfc/reference/cdaoexception-class.md) a [cdaoerrorinfo –](../mfc/reference/cdaoerrorinfo-structure.md).  
  
 Při práci s databázemi Microsoft Jet (.mdb) a ve většině případů při práci s rozhraním ODBC, budou existovat jenom jeden objekt chyby. V případě, že výjimečných když používáte zdroje dat ODBC a existuje několik chyb, můžete ve smyčce projít DAO na kolekce chyb na základě počtu chyb vrácených nástrojem [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Pokaždé, když pomocí smyčky, volání [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) k doplnění `m_pErrorInfo` – datový člen.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

