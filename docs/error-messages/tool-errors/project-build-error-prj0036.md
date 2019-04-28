---
title: Chyba sestavení projektu PRJ0036
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 9b9232583c464548167e22d0104e0c6098093eab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348390"
---
# <a name="project-build-error-prj0036"></a>Chyba sestavení projektu PRJ0036

Vlastnost "Additional Files" pro nástroj pro nasazení webu obsahovala neplatný záznam.

Vlastnost další soubory na stránce vlastností nasazení webu obsahuje chybu, pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamenat, že cesta je chybně vytvořený kód, obsahující znaky nebo kombinace znaků, které jsou neplatné v cestě k souboru.

Chcete-li tuto chybu vyřešit, opravte makro nebo odstraňte specifikaci cesty. Vyhodnocená cesta je absolutní cesta z adresáře projektu.

Tato chyba může znamenat také, že jeden z odkazované soubory neexistuje.