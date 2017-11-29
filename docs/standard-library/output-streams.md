---
title: "Výstupní datové proudy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2a16e9125c0c121aea3905b6e20eba59ef1dc68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="output-streams"></a>Výstupní datové proudy
Objekt výstupní datový proud je cíl pro bajtů. Jsou tři nejdůležitější tříd výstupní datový proud `ostream`, `ofstream`, a `ostringstream`.  
  
 `ostream` Třídu, v rámci odvozené třídy `basic_ostream`, podporuje objektů předdefinované datového proudu:  
  
-   `cout`standardní výstup  
  
-   `cerr`Standardní chyba s omezenou ukládání do vyrovnávací paměti  
  
-   `clog`Podobně jako `cerr` , ale s úplnou ukládání do vyrovnávací paměti  
  
 Objekty zřídka se vytvářejí na základě `ostream`; předdefinované objekty se obecně používají. V některých případech můžete opětovně přiřazovat předdefinované objekty po spuštění programu. `ostream` Třídy, která můžete nakonfigurovat pro operace bez vyrovnávací paměti nebo ve vyrovnávací paměti, je nejvhodnější pro výstup sekvenční textovém režimu. Všechny funkce základní třídy, `ios`, je součástí `ostream`. Pokud vytvoříte objekt třídy `ostream`, je nutné zadat `streambuf` objekt konstruktoru.  
  
 `ofstream` Třída podporuje výstup souboru disku. Pokud potřebujete diskem jen výstup, sestavte objekt třídy `ofstream`. Můžete zadat zda `ofstream` objekty přijímat textové nebo binární data při sestavování `ofstream` objektu nebo při volání metody `open` – členská funkce objektu. Mnoho formátování možnosti a členské funkce se týkají `ofstream` objekty a všechny funkce základní třídy `ios` a `ostream` je součástí.  
  
 Pokud zadáte filename v konstruktoru, tento soubor se automaticky otevře při vytvoření objektu sady. Jinak můžete použít `open` – členská funkce po vyvolání výchozí konstruktor.  
  
 Běhové funkce, jako `sprintf_s`, `ostringstream` třída podporuje výstup do řetězců v paměti. Pokud chcete vytvořit řetězec v paměti pomocí formátování vstupně-výstupní datový proud, vytvořit objekt třídy `ostringstream`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření objektů výstupního datového proudu](../standard-library/constructing-output-stream-objects.md)  
  
 [Používání operátorů Insertion a řízení formátu](../standard-library/using-insertion-operators-and-controlling-format.md)  
  
 [Členské funkce datového proudu souboru výstup](../standard-library/output-file-stream-member-functions.md)  
  
 [Účinky ukládání do vyrovnávací paměti](../standard-library/effects-of-buffering.md)  
  
 [Binární výstupní soubory](../standard-library/binary-output-files.md)  
  
 [Přetížení << operátor pro vaše vlastní třídy](../standard-library/overloading-the-output-operator-for-your-own-classes.md)  
  
 [Psaní vlastních manipulátorů bez argumentů](../standard-library/writing-your-own-manipulators-without-arguments.md)  
  
## <a name="see-also"></a>Viz také 
 [ofstream](../standard-library/basic-ofstream-class.md)   
 [ostringstream –](../standard-library/basic-ostringstream-class.md)   
 [iostream – programování](../standard-library/iostream-programming.md)
