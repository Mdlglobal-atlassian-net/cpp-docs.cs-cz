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
ms.openlocfilehash: c279c5b788cc7bd8a68fe36128c116d8df91c2eb
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095818"
---
# <a name="exceptions-database-exceptions"></a>Výjimky: Výjimky databáze

Tento článek vysvětluje, jak zpracovat výjimky databáze. Většina materiálu v tomto článku se vztahuje na to, jestli pracujete s třídami MFC pro rozhraní ODBC (Open Database Connectivity) nebo třídy MFC pro objekty přístup k datům (DAO). Materiály specifické pro jeden nebo jiný model jsou explicitně označeny. Témata zahrnují:

- [Přístupy ke zpracování výjimek](#_core_approaches_to_exception_handling)

- [Příklad zpracování výjimek databáze](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a>Přístupy ke zpracování výjimek

Přístup je stejný, ať už pracujete s rozhraním DAO (zastaralé) nebo rozhraním ODBC.

Vždy byste měli napsat obslužné rutiny výjimek pro zpracování mimořádných podmínek.

Nejpohodlnější přístup k zachycení výjimek databáze je testování aplikace s využitím scénářů výjimek. Určete pravděpodobné výjimky, které mohou nastat pro operaci ve vašem kódu a vynutit, aby k výjimce došlo. Pak zkontrolujte výstup trasování, abyste viděli, jaká výjimka je vyvolána, nebo zkontrolujte informace o vrácených chybách v ladicím programu. To vám umožní zjistit, které návratové kódy se zobrazí pro scénáře výjimek, které používáte.

### <a name="error-codes-used-for-odbc-exceptions"></a>Kódy chyb používané pro výjimky rozhraní ODBC

Kromě návratových kódů definovaných rozhraním, které mají názvy **AFX_SQL_ERROR_XXX**formuláře, jsou některé [CDBExceptions](../mfc/reference/cdbexception-class.md) založeny na návratových kódech [ODBC](../data/odbc/odbc-basics.md) . Návratové kódy těchto výjimek mají názvy **SQL_ERROR_XXX**formuláře.

Návratové kódy – definovaná rozhraním i rozhraním ODBC, které třídy databáze mohou vracet, jsou zdokumentovány v rámci [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) datových členů třídy `CDBException`. Další informace o návratových kódech definovaných rozhraním ODBC jsou k dispozici v *Referenční příručce programátora* sady ODBC SDK v knihovně MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Kódy chyb používané pro výjimky rozhraní DAO

Pro výjimky DAO jsou obvykle k dispozici další informace. K informacím o chybě můžete přistupovat prostřednictvím tří datových členů zachyceného objektu [CDaoException](../mfc/reference/cdaoexception-class.md) :

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) obsahuje ukazatel na objekt [CDaoErrorInfo –](../mfc/reference/cdaoerrorinfo-structure.md) , který zapouzdřuje informace o chybách v kolekci chybových objektů rozhraní DAO přidružených k databázi.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) obsahuje rozšířený kód chyby z tříd MFC rozhraní DAO. Tyto chybové kódy, které mají názvy formuláře **AFX_DAO_ERROR_XXX**, jsou zdokumentovány v rámci datového člena v `CDaoException`.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) obsahuje **Code** OLE z DAO, pokud je to možné. Tento kód chyby ale budete muset používat zřídka. Obvykle jsou další informace k dispozici v dalších dvou datových členech. Další informace o **Code** hodnotách najdete v datovém členu.

Další informace o chybách rozhraní DAO, typu objektu chyby DAO a kolekci chyb rozhraní DAO jsou k dispozici v rámci třídy [CDaoException](../mfc/reference/cdaoexception-class.md).

##  <a name="_core_a_database_exception.2d.handling_example"></a>Příklad zpracování výjimek databáze

Následující příklad se pokusí vytvořit objekt odvozený [CRecordset](../mfc/reference/crecordset-class.md)na haldě s operátorem **New** a následně otevřít sadu záznamů (pro zdroj dat rozhraní ODBC). Podobný příklad pro třídy DAO naleznete níže v části "příklad výjimky pro rozhraní DAO".

### <a name="odbc-exception-example"></a>Příklad výjimky ODBC

[Otevřená](../mfc/reference/crecordset-class.md#open) členská funkce může vyvolat výjimku (typu [CDBException](../mfc/reference/cdbexception-class.md) pro třídy rozhraní ODBC), takže tento `Open` kód zazávorí volání pomocí bloku **Try** . Následný blok **catch** bude zachytit `CDBException`. Mohli byste prošetřit samotný objekt výjimky, `e`ale v tomto případě je dostatečně známo, že pokus o vytvoření sady záznamů se nezdařil. Blok **catch** zobrazí okno se zprávou a vyčistí odstraněním objektu sady záznamů.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Příklad výjimky DAO

Příklad rozhraní DAO je podobný příkladu pro rozhraní ODBC, ale můžete obvykle načíst více druhů informací. Následující kód se také pokusí otevřít sadu záznamů. Pokud tento pokus vyvolá výjimku, můžete ověřit datový člen objektu výjimky, pokud chcete získat informace o chybě. Stejně jako v předchozím příkladu rozhraní ODBC je pravděpodobné, že se pokus o vytvoření sady záznamů nezdařil.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Tento kód Získá řetězec chybové zprávy od člena [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) objektu Exception. Knihovna MFC vyplní tento člen, když vyvolá výjimku.

Diskuzi o chybách vrácených `CDaoException` objektem naleznete v tématu třídy [CDaoException](../mfc/reference/cdaoexception-class.md) a [CDaoErrorInfo –](../mfc/reference/cdaoerrorinfo-structure.md).

Při práci s databázemi Microsoft Jet (. mdb) a ve většině případů při práci s rozhraním ODBC bude k dispozici pouze jeden objekt Error. V případě nečastého případu, kdy používáte zdroj dat rozhraní ODBC a existuje více chyb, můžete projít kolekci chyb rozhraní DAO na základě počtu chyb vrácených funkcí [CDaoException:: GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Pokaždé, když projdete smyčku, zavolejte [CDaoException:: GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) pro `m_pErrorInfo` doplnění datového členu.

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
