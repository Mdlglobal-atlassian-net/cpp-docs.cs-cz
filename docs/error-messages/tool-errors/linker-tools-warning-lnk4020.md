---
title: Upozornění linkerů LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194223"
---
# <a name="linker-tools-warning-lnk4020"></a>Upozornění linkerů LNK4020

> záznam typu v*souboru filename*je poškozen. Některé symboly a typy nemůžou být dostupné z ladicího programu.

*Název* souboru PDB má poškozený záznam typu.

Tento problém je často sekundární pro jiné problémy při sestavování. Pokud se nejedná o první nahlášený problém s sestavením, zapište nejprve další chyby a upozornění. Pokud se jedná o první nahlášený problém, může být nutné vyčistit adresáře sestavení a znovu sestavit projekt. Pokud používáte paralelní procesy sestavení, přečtěte si, zda chyba přetrvává při serializaci sestavení.
