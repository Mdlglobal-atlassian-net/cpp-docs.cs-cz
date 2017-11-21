---
title: Rozsah a viditelnost | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9e9dca1b95af3971045a1ce86807ef28be096546
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="scope-and-visibility"></a>Rozsah a viditelnost
„Viditelnost“ identifikátoru určuje části programu, ve kterých lze na identifikátor odkazovat – jeho „rozsah“. Identifikátor je zobrazen (tj. lze jej použít) pouze v částech programu zahrnutých jeho „rozsahem“, což může představovat omezení (ve smyslu rostoucího omezení) souboru, funkce, bloku nebo prototypu funkce, ve kterých se vyskytuje. Rozsah identifikátoru je součástí programu, ve kterém lze použít název. Občas se nazývá „lexikální rozsah“. Existují čtyři druhy rozsahů: funkce, soubor, blok a prototyp funkce.  
  
 Všechny identifikátory s výjimkou popisků mají svůj rozsah určený úrovní, ve které dochází k deklaraci. Pro každý druh rozsahu viditelnosti identifikátorů programu platí následující pravidla:  
  
 Rozsah souboru  
 Deklarátor nebo specifikátor typu identifikátoru s rozsahem souboru se zobrazí vně bloku nebo seznamu parametrů a je přístupný z jakéhokoli místa v jednotce překladu po její deklaraci. Názvy identifikátorů jsou spolu s rozsahem souboru často nazývány „globální“ nebo „externí“. Rozsah globálního identifikátoru začíná v místě jeho definice nebo deklarace a končí na konci jednotky překladu.  
  
 Rozsah funkce  
 Popisek je jediný druh identifikátoru, který má rozsah funkce. Popisek je deklarován implicitně použitím v příkazu. Názvy popisků musejí být v rámci funkce jedinečné. (Další informace o popisky a názvy štítků najdete v tématu [goto a příkazy s popiskem](../c-language/goto-and-labeled-statements-c.md).)  
  
 Rozsah bloku  
 Uvnitř bloku nebo v seznamu deklarací formálních parametrů se v definici funkce objeví deklarátor nebo specifikátor typu pro identifikátor s rozsahem bloku. Je viditelný pouze z místa jeho deklarace nebo definice až po konec bloku obsahujícího jeho deklaraci nebo definici. Jeho rozsah je omezen na tento blok a na jakékoli vnořené bloky v tomto bloku a končí složenou závorkou, která přidružený blok ukončí. Tyto identifikátory jsou někdy označovány jako „lokální proměnné“.  
  
 Rozsah prototypu funkce  
 Deklarátor nebo specifikátor typu identifikátoru s rozsahem prototypu funkce se zobrazí v seznamu deklarací parametrů v prototypu funkce (není součástí deklarace funkce). Jeho rozsah končí na konci deklarátoru funkce.  
  
 Odpovídající deklarace pro viditelnosti proměnné v jiné zdrojové soubory jsou popsané v [třídy úložiště](../c-language/c-storage-classes.md). Nicméně, proměnné a funkce deklarovat na externí úrovni s **statické** – specifikátor třídy úložiště jsou viditelné pouze v rámci zdrojový soubor, ve kterém jsou definovány. Všechny ostatní funkce jsou viditelné globálně.  
  
## <a name="see-also"></a>Viz také  
 [Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)