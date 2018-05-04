---
title: Uchovávání a zarovnání struktur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4a70ab5fbeb4a1672279e7e9b617e3b4de1c1b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="storage-and-alignment-of-structures"></a>Uchovávání a zarovnání struktur
**Konkrétní Microsoft**  
  
 Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.  
  
 Má každý datový objekt *zarovnání požadavek*. U struktur je požadavek ten největší ze svých členů. Každý objekt je přidělen *posun* tak, aby  
  
 *Posun* `%` *zarovnání požadavek* `==` 0  
  
 Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.  
  
 Z důvodu úspory místa nebo vyhovění existujícím datovým strukturám, lze struktury uložit více či méně kompaktně. [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] – možnost kompilátoru a [#pragma pack](../preprocessor/pack.md) řízení jak struktura dat je "balí" do paměti. Při použití /Zp [*n*] možnost, kde *n* je 1, 2, 4, 8 nebo 16, každý člen struktura po uložení první bajt hranice, které jsou buď požadavek zarovnání pole nebo okolních velikost () *n*), než je menší. Vyjádřené jako vzorec, jsou hranice bajtu  
  
```  
min( n, sizeof( item ) )  
```  
  
 kde *n* je velikost okolních vyjádřit s /Zp [*n*] možnost a *položky* je struktura člena. Výchozí velikost komprimace je /Zp8.  
  
 Chcete-li pomocí direktivy pragma `pack` pro danou strukturu určit jinou komprimaci než specifikovanou příkazovým řádkem, použijte před touto strukturou direktivu pragma `pack`, kde je velikost komprimace 1, 2, 4, 8 nebo 16. Chcete-li obnovit komprimaci zadanou na příkazovém řádku, zadejte direktivu pragma `pack` bez argumentů.  
  
 Bit pole výchozí velikost **dlouho** pro kompilátor C společnosti Microsoft. Členové struktury odpovídají na velikost, typ nebo /Zp [*n*] velikost, než je menší. Výchozí velikost je 4.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarace struktury](../c-language/structure-declarations.md)