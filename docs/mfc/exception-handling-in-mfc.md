---
title: Zpracování výjimek v prostředí MFC
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365535"
---
# <a name="exception-handling-in-mfc"></a>Zpracování výjimek v prostředí MFC

Tento článek vysvětluje mechanismy zpracování výjimek, které jsou k dispozici v knihovně MFC. K dispozici jsou dva mechanismy:

- Výjimky jazyka C++ dostupné ve verzi MFC 3.0 a novějších

- Makra výjimek knihovny MFC dostupná ve verzích 1.0 a novějších

Pokud píšete novou aplikaci pomocí knihovny MFC, měli byste použít mechanismus Jazyka C++. Mechanismus založený na makru můžete použít, pokud vaše existující aplikace již používá tento mechanismus značně.

Můžete snadno převést existující kód použít výjimky jazyka C++ namísto makra výjimky knihovny MFC. Výhody převodu kódu a pokyny k tomu jsou popsány v článku [Výjimky: Převod z makra výjimek knihovny MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

Pokud jste již vyvinuli aplikaci pomocí makra výjimky knihovny MFC, můžete pokračovat v používání těchto maker v existujícím kódu při použití výjimek jazyka C++ v novém kódu. Článek [Výjimky: Změny makra výjimek ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) poskytuje pokyny k tomu.

> [!NOTE]
> Chcete-li povolit zpracování výjimek jazyka C++ v kódu, vyberte možnost Povolit výjimky jazyka C++ na stránce Generování kódu ve složce C/C++ v dialogovém okně [Stránky vlastností](../build/reference/property-pages-visual-cpp.md) projektu nebo použijte možnost kompilátoru [/EHsc.](../build/reference/eh-exception-handling-model.md)

Tento článek popisuje následující témata:

- [Kdy použít výjimky](#_core_when_to_use_exceptions)

- [Podpora výjimek knihovny MFC](#_core_mfc_exception_support)

- [Další čtení o výjimkách](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Kdy použít výjimky

Tři kategorie výsledků může dojít při volání funkce během provádění programu: normální spuštění, chybné spuštění nebo abnormální spuštění. Každá kategorie je popsána níže.

- Normální provádění

   Funkce může spustit normálně a vrátit. Některé funkce vrátí volajícímu kód výsledku, což označuje výsledek funkce. Možné kódy výsledků jsou pro funkci přesně definovány a představují rozsah možných výsledků funkce. Kód výsledku může indikovat úspěch nebo neúspěch nebo dokonce může indikovat určitý typ selhání, který je v normálním rozsahu očekávání. Funkce stavu souboru může například vrátit kód, který označuje, že soubor neexistuje. Všimněte si, že termín "kód chyby" se nepoužívá, protože kód výsledku představuje jeden z mnoha očekávaných výsledků.

- Chybné provedení

   Volající provede určitou chybu při předávání argumentů funkci nebo volá funkci v nevhodném kontextu. Tato situace způsobí chybu a měla by být zjištěna kontrolním výrazem během vývoje programu. (Další informace o kontrolních výrazech naleznete v tématu [C/C++ Assertions](/visualstudio/debugger/c-cpp-assertions).)

- Abnormální provedení

   Abnormální provádění zahrnuje situace, kdy podmínky mimo ovládací prvek programu, jako je nedostatek paměti nebo chyby vstupně-videa, ovlivňují výsledek funkce. Neobvyklé situace by měly být zpracovány zachycení a vyvolání výjimky.

Použití výjimek je zvláště vhodné pro abnormální spuštění.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>Podpora výjimek knihovny MFC

Ať už použijete výjimky jazyka C++ přímo nebo makra výjimek `CException`knihovny MFC, použijete [třídu CException](../mfc/reference/cexception-class.md) nebo odvozené objekty, které mohou být vyvolány rozhraním nebo vaší aplikací.

V následující tabulce jsou uvedeny předdefinované výjimky poskytované knihovnou MFC.

|Exception – třída|Význam|
|---------------------|-------------|
|[CMemoryException – třída](../mfc/reference/cmemoryexception-class.md)|Nedostatek paměti|
|[Třída CFileException](../mfc/reference/cfileexception-class.md)|Výjimka souboru|
|[Třída CArchiveException](../mfc/reference/carchiveexception-class.md)|Výjimka archivace/serializace|
|[CNotSupportedException – třída](../mfc/reference/cnotsupportedexception-class.md)|Odpověď na požadavek na nepodporovanou službu|
|[CResourceException – třída](../mfc/reference/cresourceexception-class.md)|Výjimka přidělení prostředků systému Windows|
|[CDaoException – třída](../mfc/reference/cdaoexception-class.md)|Výjimky databáze (třídy DAO)|
|[Třída CDBException](../mfc/reference/cdbexception-class.md)|Výjimky databáze (třídy ODBC)|
|[COleException – třída](../mfc/reference/coleexception-class.md)|OLE – výjimky|
|[Třída COleDispatchException](../mfc/reference/coledispatchexception-class.md)|Výjimky pro odeslání (automatizace)|
|[Třída CUserException](../mfc/reference/cuserexception-class.md)|Výjimka, která upozorní uživatele s okno se zprávou, pak vyvolá obecné [CException Class](../mfc/reference/cexception-class.md)|

Od verze 3.0 používá MFC výjimky jazyka C++, ale stále podporuje jeho starší makra pro zpracování výjimek, jejichž forma se podobá výjimkám jazyka C++. Přestože nejsou tato makra vhodná pro nové programování, jsou z důvodu zpětné kompatibility stále podporována. V aplikacích používajících makra lze volně používat i výjimky jazyka C++. Během předběžného zpracování jsou makra vyhodnocena podle klíčových slov zpracování výjimek definovaných v implementaci jazyka C+C ms od jazyka Visual C++ verze 2.0. Stávající makra zpracování výjimek lze při použití výjimek jazyka C++ ponechat. Informace o míchání maker a zpracování výjimek jazyka C++ a o převodu starého kódu pro použití nového mechanismu naleznete v článcích [Výjimky: Použití maker knihovny MFC a výjimek](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) a výjimek jazyka C++: [Převod z maker výjimek knihovny MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starší výjimky maker knihovny MFC, pokud je stále používáte, se vyhodnotí jako klíčová slova výjimek jazyka C++. Viz [Výjimky: Změny maker výjimek ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md). Knihovna MFC přímo nepodporuje obslužné rutiny strukturovaných výjimek systému Windows NT (SEH), jak je popsáno ve [strukturovaném zpracování výjimek](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Další čtení o výjimkách

Následující články vysvětlují použití knihovny knihovny Knihovny MFC pro předávání výjimek:

- [Výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Výjimky: Zkoumání obsahu výjimek](../mfc/exceptions-examining-exception-contents.md)

- [Výjimky: Uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Výjimky: Generování výjimek ve vašich vlastních funkcích](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Výjimky: Výjimky databáze](../mfc/exceptions-database-exceptions.md)

- [Výjimky: Výjimky OLE](../mfc/exceptions-ole-exceptions.md)

Následující články porovnávají makra výjimek knihovny MFC s klíčovými slovy výjimky jazyka C++ a vysvětlují, jak můžete přizpůsobit kód:

- [Výjimky: Změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Výjimky: Převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Výjimky: Použití výjimek v makrech MFC a jazyce C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Viz také

[Moderní osvědčené postupy jazyka C++ pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Jak mohu: Vytvořit vlastní vlastní třídy výjimek](https://go.microsoft.com/fwlink/p/?linkid=128045)
