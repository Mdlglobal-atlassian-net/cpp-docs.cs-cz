---
title: Zpracování výjimek v prostředí MFC
ms.date: 11/04/2016
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
ms.openlocfilehash: e8c0f1feba566ef9b961edcfacb9124830f9851d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508625"
---
# <a name="exception-handling-in-mfc"></a>Zpracování výjimek v prostředí MFC

Tento článek vysvětluje mechanismy zpracování výjimek, které jsou k dispozici v knihovně MFC. K dispozici jsou dva mechanismy:

- C++výjimky, které jsou k dispozici v knihovně MFC verze 3,0 a novější

- Makra výjimek knihovny MFC, která jsou k dispozici v MFC verzích 1,0 a novější

Pokud vytváříte novou aplikaci pomocí knihovny MFC, měli byste použít C++ mechanismus. Mechanismus založený na makrech můžete použít, pokud již vaše existující aplikace tento mechanismus často používá.

Existující kód můžete snadno převést na použití C++ výjimek namísto maker výjimek knihovny MFC. Výhody převodu kódu a pokynů pro jejich účely jsou popsány v článku [výjimky: Převod z maker](../mfc/exceptions-converting-from-mfc-exception-macros.md)výjimek knihovny MFC.

Pokud jste již vytvořili aplikaci pomocí maker výjimek knihovny MFC, můžete nadále používat tato makra v existujícím kódu při použití C++ výjimek v novém kódu. Výjimky článků [: Změny maker výjimek ve verzi 3,0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) obsahují pokyny k tomu, jak to provést.

> [!NOTE]
>  Chcete- C++ li ve svém kódu povolit zpracování výjimek, C++ vyberte možnost povolit výjimky na stránce generování kódu ve složceC++ C nebo v dialogovém okně [stránky vlastností](../build/reference/property-pages-visual-cpp.md) projektu, nebo použijte možnost kompilátoru [/EHsc](../build/reference/eh-exception-handling-model.md) .

Tento článek se zabývá následujícími tématy:

- [Kdy použít výjimky](#_core_when_to_use_exceptions)

- [Podpora výjimek MFC](#_core_mfc_exception_support)

- [Další informace o výjimkách](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a>Kdy použít výjimky

Při volání funkce během provádění programu mohou nastat tři kategorie výsledků: normální spuštění, chybné provedení nebo abnormální spuštění. Každá kategorie je popsána níže.

- Normální spuštění

   Funkce se může provádět normálně a vracet. Některé funkce vrátí kód výsledku volajícímu, který označuje výsledek funkce. Možné kódy výsledků jsou striktně definovány pro funkci a představují rozsah možných výsledků funkce. Výsledný kód může indikovat úspěch nebo neúspěch nebo může dokonce indikovat konkrétní typ selhání, který je v normálním rozsahu očekávání. Například funkce stavu souboru může vracet kód, který indikuje, že soubor neexistuje. Všimněte si, že termín "kód chyby" se nepoužívá, protože výsledný kód představuje jeden z mnoha očekávaných výsledků.

- Chybné spuštění

   Volající způsobuje chybu v předání argumentů funkci nebo volání funkce v nevhodném kontextu. Tato situace způsobí chybu a měla by být zjištěna kontrolním výrazem během vývoje programu. (Další informace o kontrolních výrazech naleznete v tématu [CC++ /kontrolní výrazy](/visualstudio/debugger/c-cpp-assertions).)

- Abnormální spuštění

   Neobvyklé provádění zahrnuje situace, kdy podmínky mimo řízení programu, například chyby nedostatku paměti nebo vstupně-výstupních chyb, ovlivňují výsledek funkce. Neobvyklé situace by měly být zpracovány zachycením a vygenerováním výjimek.

Použití výjimek je zvláště vhodné při abnormálním spuštění.

##  <a name="_core_mfc_exception_support"></a>Podpora výjimek MFC

Bez ohledu na to C++ , zda používáte výjimky přímo nebo použijte makra výjimek knihovny MFC, budete používat [CException – třídy](../mfc/reference/cexception-class.md) nebo `CException`odvozené objekty, které mohou být vyvolány rozhraním nebo aplikací.

V následující tabulce jsou uvedeny předdefinované výjimky poskytované knihovnou MFC.

|Exception – třída|Význam|
|---------------------|-------------|
|[CMemoryException – třída](../mfc/reference/cmemoryexception-class.md)|Nedostatek paměti|
|[CFileException – třída](../mfc/reference/cfileexception-class.md)|Výjimka souboru|
|[CArchiveException – třída](../mfc/reference/carchiveexception-class.md)|Výjimka archivu/serializace|
|[CNotSupportedException – třída](../mfc/reference/cnotsupportedexception-class.md)|Odpověď na požadavek na nepodporovanou službu|
|[CResourceException – třída](../mfc/reference/cresourceexception-class.md)|Výjimka přidělení prostředků Windows|
|[CDaoException – třída](../mfc/reference/cdaoexception-class.md)|Výjimky databáze (třídy DAO)|
|[CDBException – třída](../mfc/reference/cdbexception-class.md)|Výjimky databáze (třídy rozhraní ODBC)|
|[COleException – třída](../mfc/reference/coleexception-class.md)|OLE – výjimky|
|[COleDispatchException – třída](../mfc/reference/coledispatchexception-class.md)|Výjimky odeslání (automatizace)|
|[CUserException – třída](../mfc/reference/cuserexception-class.md)|Výjimka, která upozorní uživatele na okno se zprávou, potom vyvolá obecnou [třídu CException –](../mfc/reference/cexception-class.md)|

> [!NOTE]
>  Knihovna MFC podporuje C++ obě výjimky i makra MFC výjimky. Knihovna MFC přímo nepodporuje strukturované obslužné rutiny výjimek (SEH) systému Windows NT, jak je popsáno v tématu [strukturované zpracování výjimek](/windows/win32/debug/structured-exception-handling).

##  <a name="_core_further_reading_about_exceptions"></a>Další informace o výjimkách

Následující články vysvětlují použití knihovny MFC k výjimce:

- [Výjimky: Zachytávání a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Výjimky: Zkoumání obsahu výjimek](../mfc/exceptions-examining-exception-contents.md)

- [Výjimky: Uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Výjimky: Generování výjimek ve vašich vlastních funkcích](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Výjimky: Výjimky databáze](../mfc/exceptions-database-exceptions.md)

- [Výjimky: OLE – výjimky](../mfc/exceptions-ole-exceptions.md)

Následující články porovnávají makra výjimek knihovny MFC s klíčovými slovy C++ výjimky a vysvětlují, jak lze přizpůsobit kód:

- [Výjimky: Změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Výjimky: Převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Výjimky: Použití výjimek v makrech MFC a jazyce C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Viz také:

[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)<br/>
[Jak můžu: Vytvořit vlastní třídy výjimek](https://go.microsoft.com/fwlink/p/?linkid=128045)
