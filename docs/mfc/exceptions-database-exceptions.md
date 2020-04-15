---
title: 'Výjimky: Výjimky databáze'
ms.date: 09/17/2019
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
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366630"
---
# <a name="exceptions-database-exceptions"></a>Výjimky: Výjimky databáze

Tento článek vysvětluje, jak zpracovat výjimky databáze. Většina materiálu v tomto článku platí, zda pracujete s třídami Knihovny MFC pro připojení k otevřené databázi (ODBC) nebo třídy Knihovny MFC pro objekty přístupu k datům (DAO). Materiál specifický pro jeden nebo druhý model je explicitně označen. Témata:

- [Přístupy ke zpracování výjimek](#_core_approaches_to_exception_handling)

- [Příklad zpracování výjimek databáze](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>Přístupy ke zpracování výjimek

Přístup je stejný, zda pracujete s DAO (zastaralé) nebo ODBC.

Vždy byste měli psát obslužné rutiny výjimek pro zpracování výjimečných podmínek.

Nejpragmatičtější přístup k zachycení výjimky databáze je otestovat aplikaci s výjimkou scénáře. Určete pravděpodobné výjimky, které mohou nastat pro operaci v kódu a vynutit výjimku dojít. Potom zkontrolujte výstup trasování zobrazíte, jaká výjimka je vyvolána, nebo zkontrolujte vrácené informace o chybě v ladicím programu. To vám umožní zjistit, které návratové kódy se zobrazí pro scénáře výjimek, které používáte.

### <a name="error-codes-used-for-odbc-exceptions"></a>Kódy chyb používané pro výjimky ODBC

Kromě návratových kódů definovaných rozhraním, které mají názvy formuláře **AFX_SQL_ERROR_XXX**, jsou některé [výjimky CDBexception založeny](../mfc/reference/cdbexception-class.md) na návratových kódech [ROZHRANÍ ODBC.](../data/odbc/odbc-basics.md) Návratové kódy pro tyto výjimky mají názvy formuláře **SQL_ERROR_XXX**.

Návratové kódy – definované rámcem i definované rozhraním ODBC – které mohou třídy databáze vrátit, jsou dokumentovány pod [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) datovým členem třídy `CDBException`. Další informace o návratových kódech definovaných rozhraním ODBC jsou k dispozici v *referenční příručce programátora* sady ODBC SDK v knihovně MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Kódy chyb používané pro výjimky DAO

Pro výjimky DAO jsou obvykle k dispozici další informace. K informacím o chybě můžete přistupovat prostřednictvím tří datových členů zachyceného objektu [CDaoException:](../mfc/reference/cdaoexception-class.md)

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) obsahuje ukazatel na objekt [CDaoErrorInfo,](../mfc/reference/cdaoerrorinfo-structure.md) který zapouzdřuje informace o chybě v kolekci chybových objektů dao přidružených k databázi.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) obsahuje rozšířený kód chyby z tříd Knihovny MFC DAO. Tyto kódy chyb, které mají názvy formuláře **AFX_DAO_ERROR_XXX**, `CDaoException`jsou dokumentovány pod datovým členem v .

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) obsahuje OLE **SCODE** z DAO, pokud je k dispozici. S tímto kódem chyby však budete muset pracovat jen zřídka. Obvykle více informací je k dispozici v dalších dvou datových členů. Další informace o hodnotách SCODE naleznete v datovém **členu.**

Další informace o chybách DAO, typu objektu Chyba DAO a kolekci chyb DAO jsou k dispozici v rámci třídy [CDaoException](../mfc/reference/cdaoexception-class.md).

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>Příklad zpracování výjimek databáze

Následující příklad se pokusí vytvořit [objekt odvozený cRecordset](../mfc/reference/crecordset-class.md)na haldě s **novým** operátorem a potom otevřete sadu záznamů (pro zdroj dat ODBC). Pro podobný příklad pro třídy DAO, viz "DAO Exception Example" níže.

### <a name="odbc-exception-example"></a>Příklad výjimky ODBC

Členská funkce [Open](../mfc/reference/crecordset-class.md#open) může vyvolat výjimku (typu [CDBException](../mfc/reference/cdbexception-class.md) pro třídy `Open` ODBC), takže tento kód závorky volání s **try** bloku. Následující **catch** blok chytí `CDBException`. Můžete prozkoumat samotný objekt `e`výjimky, nazvaný , ale v tomto případě stačí vědět, že pokus o vytvoření sady záznamů se nezdařil. Blok **catch** zobrazí okno se zprávou a vyčistí odstraněním objektu sady záznamů.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Příklad výjimky DAO

Příklad DAO je podobný příkladu pro ROZHRANÍ ODBC, ale obvykle můžete načíst další druhy informací. Následující kód se také pokouší otevřít sadu záznamů. Pokud tento pokus vyvolá výjimku, můžete zkontrolovat datový člen objektu výjimky pro informace o chybě. Stejně jako v předchozím příkladu rozhraní ODBC pravděpodobně stačí vědět, že pokus o vytvoření sady záznamů se nezdařil.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Tento kód získá řetězec chybové zprávy od [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) člen objektu výjimky. Knihovna MFC vyplní tento člen při vyvolání výjimky.

Diskuse o chybové informace vrácené objektem `CDaoException` naleznete v tématu třídy [CDaoException](../mfc/reference/cdaoexception-class.md) a [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Při práci s databázemi Microsoft Jet (.mdb) a ve většině případů při práci s ROZHRANÍ ODBC, bude existovat pouze jeden objekt chyby. Ve výjimečných případech, kdy používáte zdroj dat ODBC a existuje více chyb, můžete procházet dao chyby kolekce na základě počtu chyb vrácených [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Pokaždé, když prostřednictvím smyčky, volání [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) k doplnění datového `m_pErrorInfo` člena.

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
