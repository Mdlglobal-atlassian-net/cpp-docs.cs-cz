---
title: "Vstupní datové proudy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7844ebbdc3614783a92283f573422834b1c2fce
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="input-streams"></a>Vstupní datové proudy
Objekt vstupního datového proudu je zdroj bajtů. Jsou tři nejdůležitější tříd vstupního datového proudu [IStream on Request](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md), a [istringstream –](../standard-library/basic-istringstream-class.md).  
  
 `istream` Třída je nejvhodnější pro vstup sekvenční textovém režimu. Můžete nakonfigurovat objekty třídy `istream` pro operace bez vyrovnávací paměti nebo ve vyrovnávací paměti. Všechny funkce základní třídy, `ios`, je součástí `istream`. Občas vytvoří objekty z třídy `istream`. Místo toho bude obvykle použijete předdefinovanou `cin` objekt, který je ve skutečnosti objekt třídy [ostream –](../standard-library/basic-ostream-class.md). V některých případech můžete přiřadit `cin` k ostatním objektům datového proudu po spuštění programu.  
  
 `ifstream` Třída podporuje vstupní soubor disku. Pokud budete potřebovat omezeno pouze na soubor na disku, vytvořit objekt třídy `ifstream`. Zadaný režim textové nebo binární data. Pokud zadáte filename v konstruktoru, soubor se automaticky otevře při vytvoření objektu sady. Jinak můžete použít `open` funkce po vyvolání výchozí konstruktor. Mnoho formátování možnosti a členské funkce se týkají `ifstream` objekty. Všechny funkce základní třídy `ios` a `istream` je součástí `ifstream`.  
  
 Funkce knihovny, například `sscanf_s`, `istringstream` třída podporuje vstup z řetězců v paměti. Chcete-li extrahovat data z pole znaků, který má hodnotu null. ukončovací znak, přidělit a inicializuje řetězec a pak vytvořit objekt třídy `istringstream`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření objektů vstupního streamu](../standard-library/constructing-input-stream-objects.md)  
  
 [Používání operátorů extrakce](../standard-library/using-extraction-operators.md)  
  
 [Testování pro nalezení chyb extrakce](../standard-library/testing-for-extraction-errors.md)  
  
 [Manipulátory vstupního streamu](../standard-library/input-stream-manipulators.md)  
  
 [Členské funkce vstupního streamu](../standard-library/input-stream-member-functions.md)  
  
 [Přetěžování operátoru >> pro vaše vlastní třídy](../standard-library/overloading-the-input-operator-for-your-own-classes.md)  
  
## <a name="see-also"></a>Viz také  
 [iostream – programování](../standard-library/iostream-programming.md)
