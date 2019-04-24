---
title: Upozornění linkerů LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298578"
---
# <a name="linker-tools-warning-lnk4020"></a>Upozornění linkerů LNK4020

> záznam typu v "*filename*' je poškozen; některé symboly a typy nemusejí být dostupné z ladicího programu

Soubor PDB *filename* má poškozený typ záznamu.

Tento problém je často sekundární další problémy se sestavením; Pokud je první problém ohlášené sestavení, řešit tyto chyby a upozornění na první. Pokud je toto první nahlášeného problému, budete muset čištění adresáře sestavení a znovu sestavte projekt. Pokud používáte procesy paralelního buildu, přečtěte si Pokud chyba přetrvává při serializaci sestavení.