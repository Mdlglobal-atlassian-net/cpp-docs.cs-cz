---
title: "Povinné a nepovinné hlavičkové soubory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.headers
dev_langs:
- C++
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9dde09f2125b595ffb3d79a69b4755353a0116bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="required-and-optional-header-files"></a>Povinné a nepovinné hlavičkové soubory
Popis každé spuštění rutiny zahrnuje seznam požadované a volitelné zahrnout, nebo hlavičce (. H), soubory pro tuto rutinu. Požadovaná hlavička soubory musí být součástí získat deklarace funkce pro rutiny nebo definice používá jiné rutiny volá se interně. Nepovinné hlavičkové soubory jsou obvykle součástí využít předdefinované konstanty, definice typu nebo vložené makra. Následující tabulka uvádí některé příklady nepovinné hlavičkové obsah souboru:  
  
|Definice|Příklad|  
|----------------|-------------|  
|Definice makra|Pokud rutiny knihovny je implementovaný jako makra, může být definici makra v záhlaví souboru než v záhlaví souboru původní rutiny. Například `_toupper` makro je definována v záhlaví souboru CTYPE. H při funkce `toupper` je deklarován v STDLIB. H.|  
|Předdefinované konstanta|Mnoho rutiny knihovny naleznete konstanty, které jsou definovány v hlavičkových souborů. Například `_open` rutiny, jako používá konstanty `_O_CREAT`, který je definován v záhlaví souboru FCNTL. H.|  
|Definice typu|Některé rutiny knihovny vrátí do struktury nebo trvat struktura jako argument. Vstupní a výstupní rutiny datového proudu použít například struktura typu `FILE`, která je definována v STDIO. H.|  
  
 Soubory hlaviček běhové knihovny poskytují funkce deklarace ve stylu jazyka C ANSI/ISO standardní doporučené. Kompilátor provede kontrolu na všechny rutiny odkaz, ke kterému dochází po jeho přidružené funkce deklaraci typu. Deklarace funkcí jsou obzvláště důležité pro rutiny, které vrátí hodnotu typu jiné než `int`, který je výchozí. Rutiny, které neurčují jejich odpovídající vrátit hodnotu v jejich deklaraci bude považovat za kompilátorem vrátit `int`, což může vést k neočekávaným výsledkům. V tématu [kontrola typu](../c-runtime-library/type-checking-crt.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)