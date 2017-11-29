---
title: "iostreams – konvence | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7d9004c82d740b6abca87e3cce9d0e73e0b6fc62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iostreams-conventions"></a>iostreams – konvence
Iostreams hlavičky podporují převody mezi text a kódovaného formulářů a vstup a výstup do externích souborů:  
  
|||  
|-|-|  
|[\<fstream >](../standard-library/fstream.md)|[\<iomanip – >](../standard-library/iomanip.md)|  
|[\<IOS >](../standard-library/ios.md)|[\<iosfwd – >](../standard-library/iosfwd.md)|  
|[\<iostream >](../standard-library/iostream.md)|[\<IStream on Request >](../standard-library/istream.md)|  
|[\<ostream – >](../standard-library/ostream.md)|[\<sstream – >](../standard-library/sstream.md)|  
|[\<streambuf – >](../standard-library/streambuf.md)|[\<strstream – >](../standard-library/strstream.md)|  
  
 Nejjednodušší použití iostreams vyžaduje pouze zahrnout záhlaví [ \<iostream >](../standard-library/iostream.md). Potom můžete rozbalit hodnoty z [cin](../standard-library/iostream.md#cin) nebo [wcin](../standard-library/iostream.md#wcin) číst standardní vstup. Pravidla pro tuto činnost, jsou uvedeny v popisu třídy [basic_istream – třída](../standard-library/basic-istream-class.md). Můžete také vložit hodnoty [cout](../standard-library/iostream.md#cout) nebo [wcout](../standard-library/iostream.md#wcout) k zápisu ve standardním výstupu. Pravidla pro tuto činnost, jsou uvedeny v popisu třídy [basic_ostream – třída](../standard-library/basic-ostream-class.md). Formát společné pro extraktory i insertors správy v třídě [basic_ios – třída](../standard-library/basic-ios-class.md). Manipulace s nimi tyto informace formát guise extrahování a vkládání objektů je provincii několik manipulátory.  
  
 Může provádět stejné operace iostreams na soubory, které se otevřou podle názvu, pomocí třídy deklarované v [ \<fstream >](../standard-library/fstream.md). Pro převod mezi iostreams a objekty třídy [basic_string – třída](../standard-library/basic-string-class.md), použít třídy deklarované v [ \<sstream – >](../standard-library/sstream.md). Totožný s C řetězce proveďte pomocí třídy deklarované v [ \<strstream – >](../standard-library/strstream.md).  
  
 Zbývající hlavičky poskytovat služby podpory, obvykle přímé zájmů pouze nejpokročilejší uživatele iostreams třídy.  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
