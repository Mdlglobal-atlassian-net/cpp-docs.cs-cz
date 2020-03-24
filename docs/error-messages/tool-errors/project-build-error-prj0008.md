---
title: Chyba sestavení projektu PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192950"
---
# <a name="project-build-error-prj0008"></a>Chyba sestavení projektu PRJ0008

Soubor ' file ' nelze odstranit.

**Ujistěte se, že soubor není otevřen jiným procesem a není chráněn proti zápisu.**

Při opětovném sestavení nebo vyčištění vizuál C++ odstraní všechny známé mezilehlé a výstupní soubory pro sestavení a také všechny soubory, které splňují specifikace zástupných znaků v části **rozšíření k odstranění vlastnosti vyčistit na** [stránce vlastností Obecné nastavení konfigurace](../../build/reference/general-property-page-project.md).

Tato chyba se zobrazí, pokud vizuál C++ nemůže odstranit soubor. Chcete-li chybu vyřešit, zajistěte, aby byl soubor a jeho adresář zapisovatelné pro uživatele, který provádí sestavení.
