---
title: Rozsah a viditelnost | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b10902d44d8bc2e24a94123cc198a3b7606dac43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136046"
---
# <a name="scope-and-visibility"></a>Rozsah a viditelnost

„Viditelnost“ identifikátoru určuje části programu, ve kterých lze na identifikátor odkazovat – jeho „rozsah“. Identifikátor je zobrazen (tj. lze jej použít) pouze v částech programu zahrnutých jeho „rozsahem“, což může představovat omezení (ve smyslu rostoucího omezení) souboru, funkce, bloku nebo prototypu funkce, ve kterých se vyskytuje. Rozsah identifikátoru je součástí programu, ve kterém lze použít název. Občas se nazývá „lexikální rozsah“. Existují čtyři druhy rozsahů: funkce, soubor, blok a prototyp funkce.

Všechny identifikátory s výjimkou popisků mají svůj rozsah určený úrovní, ve které dochází k deklaraci. Pro každý druh rozsahu viditelnosti identifikátorů programu platí následující pravidla:

Rozsah souboru deklarátor nebo specifikátor typu identifikátoru s rozsahem souboru se zobrazí vně bloku nebo seznamu parametrů a je přístupný z jakéhokoli místa v jednotce překladu po její deklaraci. Názvy identifikátorů jsou spolu s rozsahem souboru často nazývány „globální“ nebo „externí“. Rozsah globálního identifikátoru začíná v místě jeho definice nebo deklarace a končí na konci jednotky překladu.

Funkce oboru A popisek je jediný druh identifikátoru, který má rozsah funkce. Popisek je deklarován implicitně použitím v příkazu. Názvy popisků musejí být v rámci funkce jedinečné. (Další informace o popiscích a názvech popisků naleznete v tématu [příkaz goto a příkazy s popiskem](../c-language/goto-and-labeled-statements-c.md).)

Obor bloku deklarátor nebo specifikátor typu identifikátoru s rozsahem bloku se zobrazí uvnitř bloku nebo v seznamu deklarací formálních parametrů v definici funkce. Je viditelný pouze z místa jeho deklarace nebo definice až po konec bloku obsahujícího jeho deklaraci nebo definici. Jeho rozsah je omezen na tento blok a na jakékoli vnořené bloky v tomto bloku a končí složenou závorkou, která přidružený blok ukončí. Tyto identifikátory jsou někdy označovány jako „lokální proměnné“.

Rozsah prototypu funkce deklarátor nebo specifikátor typu identifikátoru s rozsahem prototypu funkce se zobrazí v seznamu deklarací parametrů v prototypu funkce (není součástí deklarace funkce). Jeho rozsah končí na konci deklarátoru funkce.

Příslušné deklarace pro zviditelnění proměnných v jiných zdrojových souborech jsou popsány v [třídy úložiště](../c-language/c-storage-classes.md). Nicméně, proměnné a funkce jsou deklarovány na vnější úrovni s **statické** – specifikátor třídy úložiště jsou viditelné pouze v rámci zdrojového souboru, ve kterém jsou definovány. Všechny ostatní funkce jsou viditelné globálně.

## <a name="see-also"></a>Viz také

[Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)