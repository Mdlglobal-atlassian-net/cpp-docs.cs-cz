---
title: Makra názvů souborů
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 38fe4408ebfbc2503fcb6be5b53c18d430067aa6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419678"
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

[Speciální makra NMAKE](../build/special-nmake-macros.md)
