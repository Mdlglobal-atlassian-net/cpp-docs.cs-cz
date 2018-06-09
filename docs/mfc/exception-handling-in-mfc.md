---
title: Zpracování výjimek v MFC | Microsoft Docs
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
ms.openlocfilehash: b246e9ed09cce2fdecf8a8d6327a912061247cad
ms.sourcegitcommit: 59afc95d0e494af658cf464503f7f89bd1a8d2ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239434"
---
# <a name="exception-handling-in-mfc"></a>Zpracování výjimek v prostředí MFC
Tento článek vysvětluje dostupné v prostředí MFC mechanismus zpracování výjimek. K dispozici jsou dva mechanismů:  
  
-   Výjimky jazyka C++, k dispozici v MFC verze 3.0 nebo novější  
  
-   Makra výjimek MFC, k dispozici v MFC – verze 1.0 nebo novější  
  
 Pokud píšete novou aplikaci pomocí MFC, měli byste použít mechanismus C++. Mechanismus založený na makro můžete použít, pokud již existující aplikace hojně používá tento mechanismus.  
  
 Snadno můžete převést existující kód místo maker výjimek prostředí MFC použít výjimky jazyka C++. Výhody převodu kódu a pokyny, jak to udělat jsou popsané v článku [výjimky: převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
 Pokud jste již vytvořili aplikaci pomocí maker výjimek prostředí MFC, můžete pokračovat v použití těchto maker v váš stávající kód, při použití výjimky jazyka C++ v váš nový kód. Článek [výjimky: změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) poskytuje pokyny, jak to udělat.  
  
> [!NOTE]
>  Chcete-li C++ zpracování výjimek v kódu, vyberte na stránce vytváření kódu ve složce projektu C/C++ povolit výjimky jazyka C++ [stránky vlastností](../ide/property-pages-visual-cpp.md) dialogové okno, nebo použijte [/EHsc](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru.  
  
 Tento článek obsahuje následující témata:  
  
-   [Kdy použít výjimky](#_core_when_to_use_exceptions)  
  
-   [Podpora výjimek MFC](#_core_mfc_exception_support)  
  
-   [Další informace o výjimkách](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> Kdy použít výjimky  
 Tři kategorie výstupy může dojít, když funkce je volána v průběhu provádění programu: Normální spuštění, spuštění chybné nebo abnormální provádění. Každá kategorie je popsáno níže.  
  
-   Normální spuštění  
  
     Funkce mohou spustit normálně a vrátit. Některé funkce vrátí kód výsledku volajícího, který určuje výsledek funkce. Kódy výsledků možná jsou definovány výhradně pro funkci a představují rozsahu možných výsledků funkce. Kód výsledku můžete indikující úspěch nebo selhání nebo mohou signalizovat i konkrétní typ selhání, který je v rámci normální očekávání. Funkce stav souboru můžete například vrátit kód, který označuje, že soubor neexistuje. Všimněte si, že není termín "kód chyby" použít, protože kód výsledku představuje jeden z mnoha očekávaných výsledků.  
  
-   Chybné provádění  
  
     Volající vytváří některé chybu v předání argumentů funkce nebo volá funkci v nevhodném kontextu. Tuto situaci způsobí chybu a by měl být zjištěný kontrolní výrazy během vývoje programu. (Další informace o kontrolní výrazy najdete v tématu [kontrolní výrazy jazyka C/C++](/visualstudio/debugger/c-cpp-assertions).)  
  
-   Abnormální provádění  
  
     Abnormální provádění zahrnuje situacích, kde jsou podmínky mimo řízení programu, jako je nedostatek paměti nebo chyby při vstupně-výstupních operací, které ovlivňují výsledek funkce. Nestandardní situace měla by ji zpracovat zachytávání a vyvolávání výjimek.  
  
 Použití výjimek je obzvláště vhodný pro abnormální provádění.  
  
##  <a name="_core_mfc_exception_support"></a> Podpora výjimek MFC  
 Jestli budete používat výjimky jazyka C++ přímo nebo použijete maker výjimek prostředí MFC, budete používat [CException – třída](../mfc/reference/cexception-class.md) nebo `CException`-odvozené objekty, které mohou být vyvolány rozhraní nebo aplikací.  
  
 V následující tabulce jsou předdefinované výjimky poskytované MFC.  
  
|Exception – třída|Význam|  
|---------------------|-------------|  
|[CMemoryException – třída](../mfc/reference/cmemoryexception-class.md)|Z důvodu nedostatku paměti|  
|[CFileException – třída](../mfc/reference/cfileexception-class.md)|Soubor výjimky|  
|[CArchiveException – třída](../mfc/reference/carchiveexception-class.md)|Výjimka archivu nebo serializace|  
|[CNotSupportedException – třída](../mfc/reference/cnotsupportedexception-class.md)|Odpověď na žádost o nepodporované služby|  
|[CResourceException – třída](../mfc/reference/cresourceexception-class.md)|Výjimka přidělování zdrojů systému Windows|  
|[CDaoException – třída](../mfc/reference/cdaoexception-class.md)|Výjimky databáze (třídy DAO)|  
|[CDBException – třída](../mfc/reference/cdbexception-class.md)|Výjimky databáze (třídy rozhraní ODBC)|  
|[COleException – třída](../mfc/reference/coleexception-class.md)|OLE – výjimky|  
|[COleDispatchException – třída](../mfc/reference/coledispatchexception-class.md)|Výjimky odesílání (Automatizace)|  
|[CUserException – třída](../mfc/reference/cuserexception-class.md)|Výjimka, která upozorní uživatele s okno se zprávou, potom vyvolá obecný [CException – třída](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC podporuje výjimky jazyka C++ a maker výjimek prostředí MFC. MFC přímo nepodporuje systému Windows NT strukturovaná obslužné rutiny výjimek (SEH), jak je popsáno v [strukturované zpracování výjimek](http://msdn.microsoft.com/library/windows/desktop/ms680657).  
  
##  <a name="_core_further_reading_about_exceptions"></a> Další výklad o výjimkách  
 Na následující články vysvětlují použití knihovny MFC pro blokováním výjimka:  
  
-   [Výjimky: Zachytávání a mazání](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [Výjimky: Zkoumání obsahu výjimek](../mfc/exceptions-examining-exception-contents.md)  
  
-   [Výjimky: Uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [Výjimky: Generování výjimek ve vašich vlastních funkcích](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [Výjimky: Výjimky databáze](../mfc/exceptions-database-exceptions.md)  
  
-   [Výjimky: Výjimky OLE](../mfc/exceptions-ole-exceptions.md)  
  
 V následujících článcích porovnat maker výjimek prostředí MFC s klíčovými slovy výjimka C++ a popisují, jak můžete přizpůsobit kódu:  
  
-   [Výjimky: Změny maker pro výjimky ve verzi 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [Výjimky: Převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [Výjimky: Použití výjimek v makrech MFC a jazyce C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## <a name="see-also"></a>Viz také  
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)   
 [Jak I: vytvořit vlastní třídy výjimek vlastní](http://go.microsoft.com/fwlink/p/?linkid=128045)

