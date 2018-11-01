---
title: Závažná chyba nástroje NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645022"
---
# <a name="nmake-fatal-error-u1059"></a>Závažná chyba nástroje NMAKE U1059

> Chyba syntaxe: "}" u závislé položky chybí

Cesty pro hledání adresu závislého byl nesprávně zadán. Buď místo existoval v cestě nebo pravou složenou závorku (**}**) byl vynechán.

Syntaxe specifikace adresáře pro závislé je

> **{** *adresáře* **} závislé**

kde *adresáře* Určuje jednu nebo více cest, každé oddělené středníkem (**;**). Nejsou povoleny mezery.

Pokud makro nahrazuje část nebo všechny cesty pro hledání, ujistěte se, že neexistují žádné mezery v rozšíření makra.