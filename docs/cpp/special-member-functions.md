---
title: "Speciální členské funkce | Microsoft Docs"
ms.custom: 
ms.date: 12/06/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff4fc72d2a40cc52ec614cbd5b470738ad1aa391
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="special-member-functions"></a>Speciální členské funkce  
  
*Speciální členské funkce* členské funkce, že v některých případech, kompilátor automaticky generuje pro vás jsou – třída (nebo struktura). Tyto funkce jsou [výchozí konstruktor](constructors-cpp.md#default_constructors), [– destruktor](destructors-cpp.md), [kopírovacího konstruktoru a operátor přiřazení kopie](copy-constructors-and-copy-assignment-operators-cpp.md)a [přesunout konstruktor a operátor Move assignment](move-constructors-and-move-assignment-operators-cpp.md). Pokud třídě nedefinuje nejméně jeden speciální členské funkce, pak kompilátor může implicitně deklarace a definice funkce, které se používají. Implementace generované kompilátorem se nazývají *výchozí* speciální členské funkce. Kompilátor negeneruje funkce, pokud nejsou potřeba.  
  
Speciální členské funkce výchozí je možné deklarovat explicitně pomocí `= default` – klíčové slovo. To způsobí, že kompilátoru definice funkce pouze v případě potřeby stejným způsobem, jako kdyby funkce nebyl deklarován vůbec. 

V některých případech může generovat kompilátor *odstranit* speciální členské funkce, které nejsou určené a proto není možné volat. K tomu dochází v případech, kde volání konkrétní speciální členské funkce na třídě nemá smysl, ostatní vlastnosti třídy zadaný. Pokud chcete explicitně zabránit automatické generování speciální členské funkce, je možné deklarovat ji odstranil pomocí `= delete` – klíčové slovo.  
  
Kompilátor generuje *výchozí konstruktor*, konstruktor, který se nezadávaly žádné argumenty, pouze v případě, že nebyly deklarovaný jiných konstruktor. Pokud máte deklarovat jenom konstruktor, který používá parametry, kód, který se pokouší volat výchozí konstruktor způsobí, že kompilátor zobrazí chybová zpráva. Generované kompilátorem výchozí konstruktor provede jednoduché member-wise [výchozí inicializace](initializers.md#default_initialization) objektu. Výchozí inicializace ponechá všechny proměnné členů v neurčitém stavu.  
  
Výchozí destruktor provede member-wise odstranění objektu. Virtuální je pouze v případě, že je virtuální základní třída destruktor.  
  
Výchozí kopírování a přesunutí konstrukce a přiřazení operací provést member-wise bitový kopíruje nebo přesouvá nestatické datových členů. Přesun operace jsou generovány pouze, pokud jsou deklarovány žádné destruktor nebo operace přesunutí nebo kopírování. Výchozí konstruktor kopírování se vygeneruje pouze tehdy, když je deklarovaná bez kopírovacího konstruktoru. Odstraní se implicitně, pokud je deklarovaná operaci přesunutí. Operátor přiřazení kopie výchozí se vygeneruje pouze v případě, že žádný operátor přiřazení kopie je explicitně deklarován. Odstraní se implicitně, pokud je deklarovaná operaci přesunutí.  
  
## <a name="see-also"></a>Viz také  
[Referenční dokumentace jazyka C++](cpp-language-reference.md)  



 
