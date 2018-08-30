---
title: Zpracování výjimek v MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14887f5d85fc6c1a3fcd83474240c68c90ca2991
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200764"
---
# <a name="exception-handling-in-mfc"></a>Zpracování výjimek v prostředí MFC
Tento článek vysvětluje mechanismus zpracování výjimek, který je k dispozici v knihovně MFC. K dispozici jsou dva mechanismy:  
  
-   Výjimky jazyka C++, které jsou k dispozici ve verzi knihovny MFC 3.0 a novější  
  
-   Makra výjimek MFC, k dispozici v MFC – verze 1.0 nebo novější  
  
 Pokud píšete nové aplikace pomocí knihovny MFC, měli byste použít mechanismus C++. Pokud už vaše stávající aplikace často používá tento mechanismus, můžete použít mechanismus založený na – makro.  
  
 Můžete snadno převést existující kód nahrazujícím maker výjimek prostředí MFC výjimky jazyka C++. K výhodám tohoto převodu vašeho kódu a pokyny pro to jsou popsané v článku [výjimky: převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
 Pokud již jste vytvořili aplikaci pomocí maker výjimek prostředí MFC, můžete pokračovat v používání těchto maker v existujícím kódu při použití výjimek jazyka C++ v váš nový kód. Tento článek [výjimky: změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) poskytuje pokyny pro to udělat.  
  
> [!NOTE]
>  Pokud chcete povolit ve vašem kódu zpracování výjimek jazyka C++, vyberte na stránce vytváření kódu ve složce projektu na C/C++ povolit výjimky jazyka C++ [stránky vlastností](../ide/property-pages-visual-cpp.md) dialogového okna, nebo použijte [/EHsc](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru.  
  
 Tento článek obsahuje následující témata:  
  
-   [Kdy použít výjimky](#_core_when_to_use_exceptions)  
  
-   [Podpora výjimek MFC](#_core_mfc_exception_support)  
  
-   [Další informace o výjimkách](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> Kdy použít výjimky  
 Tři kategorie výsledků může dojít, pokud funkce je volána v průběhu provádění programu: Normální spuštění, provádění chybných nebo abnormální provádění. Níže je popsána jednotlivých kategorií.  
  
-   Normální spuštění  
  
     Funkce může normálně spustit a vrátit. Některé funkce vrátí kód výsledku volajícímu, který určuje výsledek funkce. Kódy výsledků možná jsou přísně definována pro funkci a představují rozsah možné výsledky funkce. Kód výsledku může indikuje úspěch nebo neúspěch nebo dokonce můžete určit konkrétní typ selhání, který je v rámci normálního rozsahu očekávání. Stav souboru funkce může například vrátit kód, který označuje, že soubor neexistuje. Všimněte si, že termín "kód chyby" není vzhledem k tomu, že kód výsledku představuje jeden z mnoha očekávaných výsledků.  
  
-   Chybné spuštění  
  
     Volající provede nějakou chybu v předávání argumentů do funkce nebo volá funkci v kontextu nevhodný. Tato situace způsobí chybu a by měl být detekoval kontrolní výraz během vývoje aplikace. (Další informace o kontrolních výrazů naleznete v tématu [kontrolní výrazy jazyka C/C++](/visualstudio/debugger/c-cpp-assertions).)  
  
-   Abnormální provádění  
  
     Abnormální provádění zahrnuje situacích, kdy jsou podmínky mimo řízení programu, jako je nedostatek paměti nebo vstupně-výstupní chyby, vliv na výsledek funkce. Neobvyklých situací by měly být zpracovány zachytávání a vyvolávání výjimek.  
  
 Použití výjimek je obzvláště vhodný pro abnormální provádění.  
  
##  <a name="_core_mfc_exception_support"></a> Podpora výjimek MFC  
 Ať už používají výjimky jazyka C++ přímo nebo pomocí maker výjimek prostředí MFC, budete používat [cexception – třída](../mfc/reference/cexception-class.md) nebo `CException`-odvozené objekty, které může být vyvolána v rámci rozhraní nebo aplikací.  
  
 V následující tabulce jsou uvedeny předdefinované výjimky, které jsou k dispozici v prostředí MFC.  
  
|Exception – třída|Význam|  
|---------------------|-------------|  
|[CMemoryException – třída](../mfc/reference/cmemoryexception-class.md)|Out – z důvodu nedostatku paměti|  
|[CFileException – třída](../mfc/reference/cfileexception-class.md)|Soubor výjimky|  
|[CArchiveException – třída](../mfc/reference/carchiveexception-class.md)|Výjimka archivu/serializace|  
|[CNotSupportedException – třída](../mfc/reference/cnotsupportedexception-class.md)|Odpovědi na požadavek pro nepodporované služby|  
|[CResourceException – třída](../mfc/reference/cresourceexception-class.md)|Výjimka přidělování zdrojů Windows|  
|[CDaoException – třída](../mfc/reference/cdaoexception-class.md)|Výjimky databáze (DAO – třídy)|  
|[CDBException – třída](../mfc/reference/cdbexception-class.md)|Výjimky databáze (třídy rozhraní ODBC)|  
|[COleException – třída](../mfc/reference/coleexception-class.md)|OLE – výjimky|  
|[COleDispatchException – třída](../mfc/reference/coledispatchexception-class.md)|Výjimky odeslání (Automatizace)|  
|[CUserException – třída](../mfc/reference/cuserexception-class.md)|Výjimka, která upozorní uživatele s okno se zprávou, potom vyvolá obecný [cexception – třída](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC podporuje výjimky jazyka C++ a maker výjimek prostředí MFC. MFC přímo nepodporuje Windows NT strukturované obslužných rutin výjimek (SEH), jak je popsáno v [strukturovaného zpracování výjimek](https://msdn.microsoft.com/library/windows/desktop/ms680657).  
  
##  <a name="_core_further_reading_about_exceptions"></a> Další informace o výjimkách  
 Tyto články vysvětlují použití knihovny MFC pro zpracování výjimek:  
  
-   [Výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [Výjimky: Zkoumání obsahu výjimek](../mfc/exceptions-examining-exception-contents.md)  
  
-   [Výjimky: Uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [Výjimky: Generování výjimek ve vašich vlastních funkcích](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [Výjimky: Výjimky databáze](../mfc/exceptions-database-exceptions.md)  
  
-   [Výjimky: Výjimky OLE](../mfc/exceptions-ole-exceptions.md)  
  
 V následujících článcích porovnat maker výjimek prostředí MFC s klíčová slova výjimek jazyka C++ a popisují, jak je možné převést kódu:  
  
-   [Výjimky: Změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [Výjimky: Převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [Výjimky: Použití výjimek v makrech MFC a jazyce C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md)   
 [Jak mohu: vytvořit vlastní třídy vlastní výjimky](http://go.microsoft.com/fwlink/p/?linkid=128045)

