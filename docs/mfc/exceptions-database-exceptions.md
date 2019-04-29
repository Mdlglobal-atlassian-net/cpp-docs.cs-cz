---
title: 'Výjimky: Výjimky databáze'
ms.date: 11/04/2016
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
ms.openlocfilehash: 2f7f3bff9f28968361ecfa7374a235a727443004
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405895"
---
# <a name="exceptions-database-exceptions"></a>Výjimky: Výjimky databáze

Tento článek vysvětluje, jak zpracovat výjimky databáze. Většina materiálů v tomto článku platí, ať už pracujete s třídy knihovny MFC pro připojení ODBC (Open Database) nebo třídy knihovny MFC pro objekty DAO (Data Access). Materiály, které jsou specifické pro jeden nebo jiný model je explicitně označena. Mezi témata patří:

- [Přístupy k zpracování výjimek](#_core_approaches_to_exception_handling)

- [Příklad zpracování výjimek databáze](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a> Přístupy k zpracování výjimek

Tento přístup je stejný, ať už pracujete s objektem DAO nebo ODBC.

Měli byste psát vždy obslužné rutiny výjimek pro zpracování výjimečných podmínek.

Většina pragmatický postoj k zachycování výjimek databáze je k testování aplikace s výjimka scénáře. Určení pravděpodobně výjimky, které může dojít k operace ve vašem kódu a vynucení výjimka, která má dojít k. Pak zkontrolujte výstup trasování, které chcete zobrazit, co se výjimka nebo zkontrolujte chyby vrácené informace v ladicím programu. To vám umožňuje vědět, který návratové kódy, které uvidíte pro scénáře výjimky, které používáte.

### <a name="error-codes-used-for-odbc-exceptions"></a>Chybové kódy používané pro výjimky rozhraní ODBC

Kromě návratových kódů definována v rámci rozhraní, které mají názvy ve formátu **AFX_SQL_ERROR_XXX**, některé [CDBExceptions](../mfc/reference/cdbexception-class.md) jsou založeny na [ODBC](../data/odbc/odbc-basics.md) návratové kódy. Návratové kódy pro takové výjimky mají názvy ve formátu **SQL_ERROR_XXX**.

Návratové kódy – definované v rámci rozhraní i definované ODBC – databázové třídy může vrátit jsou popsány v části [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) datový člen třídy `CDBException`. Další informace o návratových kódech určené ODBC je k dispozici v sadě SDK ODBC *referenční informace pro programátory* v knihovně MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Chybové kódy používané pro rozhraní DAO výjimky

Další informace pro rozhraní DAO výjimky, jsou obvykle k dispozici. Informace o chybě můžete přistupovat prostřednictvím tři datové členy zachycené [cdaoexception –](../mfc/reference/cdaoexception-class.md) objektu:

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) obsahuje ukazatel [cdaoerrorinfo –](../mfc/reference/cdaoerrorinfo-structure.md) objekt, který zapouzdřuje informace o chybě v rozhraní DAO. kolekce objektů chyb souvisejících s databází.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) obsahuje rozšířený kód chyby z tříd DAO knihovny MFC. Tyto kódy chyb, které mají názvy ve formátu **AFX_DAO_ERROR_XXX**, jsou popsány v části datový člen v `CDaoException`.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) obsahuje OLE **SCODE** z rozhraní DAO, pokud je k dispozici. Musíte jen zřídka ale fungovat s tímto kódem chyby. Další informace jsou obvykle dostupné v dalších dvou datových členů. Zobrazit datový člen Další informace o **SCODE** hodnoty.

Další informace o chybách rozhraní DAO, typ objektu Chyba rozhraní DAO a kolekce rozhraní DAO chyb je k dispozici v rámci třídy [cdaoexception –](../mfc/reference/cdaoexception-class.md).

##  <a name="_core_a_database_exception.2d.handling_example"></a> Příklad zpracování výjimek databáze

Následující příklad se pokusí vytvořit [CRecordset](../mfc/reference/crecordset-class.md)-odvozenému objektu na haldě s **nové** operátor a potom otevřete sadu záznamů (pro zdroje dat rozhraní ODBC). Podobný příklad pro třídy DAO naleznete v tématu "DAO výjimka" níže uvedený příklad.

### <a name="odbc-exception-example"></a>Příklad výjimky rozhraní ODBC

[Otevřít](../mfc/reference/crecordset-class.md#open) členská funkce může vyvolat výjimku (typu [CDBException](../mfc/reference/cdbexception-class.md) pro ODBC – třídy), takže tento kód závorky `Open` volání s **zkuste** bloku. Následné **catch** blok zachytí `CDBException`. Může zkoumat výjimky samotného objektu, volá `e`, ale v takovém případě stačí vědět, že selhal pokus o vytvoření sady záznamů. **Catch** bloku zobrazí okno se zprávou a vyčistí odstraněním objektu sady záznamů.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Příklad DAO – výjimka

DAO příklad je podobné jako v příkladu pro rozhraní ODBC, ale obvykle můžete získat další druhy informací. Následující kód také pokusí otevřít sadu záznamů. Pokud tento pokus vyvolá výjimku, můžete prozkoumat datový člen objektu výjimky pro informace o chybě. Stejně jako u předchozí příklad ODBC, to je pravděpodobně dostatek vědět, že se nezdařil pokus o vytvoření sady záznamů.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Tento kód získá řetězec chybové zprávy z [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) členem objektu výjimky. MFC vyplní tento člen při vyvolá výjimku.

Informace o vrácené informace o chybě `CDaoException` objektu, naleznete v tématu třídy [cdaoexception –](../mfc/reference/cdaoexception-class.md) a [cdaoerrorinfo –](../mfc/reference/cdaoerrorinfo-structure.md).

Při práci s databázemi Microsoft Jet (MDB) a ve většině případů při práci s rozhraním ODBC, bude obsahovat pouze jeden objekt chyby. Ve výjimečných případech, když používáte zdroji dat rozhraní ODBC a existuje více chyb, můžete můžete projít na základě počtu chyby vrácené systémem kolekce chyb pro rozhraní DAO [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Pokaždé, když pomocí smyčky, volání [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) pro doplňování `m_pErrorInfo` datový člen.

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
