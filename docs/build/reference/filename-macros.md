---
title: Makra názvů souborů
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 54527c6f06bee396fdc7419647c607f8979c6a38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271239"
---
# <a name="filename-macros"></a>Makra názvů souborů

Makra názvů souborů jsou předdefinovány jako názvy souborů podle závislostí (specifikace není úplný název souboru na disku). Tato makra nemusí být uzavřen v závorkách při vyvolání; Zadejte pouze $ uvedené.

|– Makro|Význam|
|-----------|-------------|
|**$\@**|Aktuální cíl úplný název (cesta, základní název rozšíření), jak je aktuálně zadaný.|
|**$$\@**|Aktuální cíl úplný název (cesta, základní název rozšíření), jak je aktuálně zadaný. Platné pouze jako závislé v závislosti.|
|**$&#42;**|Aktuální cíl cestu a základní název bez přípony souboru.|
|**$&#42;&#42;**|Všechny položky závislé na aktuální cíle.|
|**$?**|Všechny položky závislé na s časovým razítkem novější než aktuální cíl.|
|**$<**|Závislý soubor s časovým razítkem novější než aktuální cíl. Platné pouze v příkazech odvozených pravidel.|

K určení součástí název souboru předdefinované makro, přidat modifikátor – makro a uvést upravené – makro v závorkách.

|Modifikátor|Výsledná část názvu souboru|
|--------------|-----------------------------|
|**D**|Jednotky a adresáře|
|**B**|Základní název|
|**F**|Základním názvem a rozšíření|
|**R**|Jednotky plus adresáře a základní název|

## <a name="see-also"></a>Viz také:

[Speciální makra NMAKE](special-nmake-macros.md)
