---
title: Chyba nástroje BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: c02e9b47b3d32e4d21914188b96913d6dff03127
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279289"
---
# <a name="bscmake-error-bk1513"></a>Chyba nástroje BSCMAKE BK1513

nepřírůstková aktualizace vyžaduje všechny. Soubory SBR

BscMake – nemůže vytvořit nového procházení (.bsc) souboru, protože nejméně jeden soubor .sbr se zkrátí. Názvy souborů zkrácený .sbr najdete v článku [nástroje BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) upozornění, které nejsou poskytnuty k této chybě.

BSCMAKE souboru .BSC nástrojem aktualizujte soubor .sbr zkrácený ale nemůže vytvořit nové. BscMake – může sestavení souboru .bsc nového z následujících důvodů:

- Chybí soubor .bsc.

- Chybný název souboru zadaný pro soubor .bsc.

- Soubor BSC poškozená.

Chcete-li tento problém vyřešit, odstraňte soubory .sbr zkrácený a opětovné sestavení, nebo Vyčistit řešení a znovu sestavit. (V integrovaném vývojovém prostředí, zvolte **sestavení**, **Vyčistit řešení**a klikněte na tlačítko **sestavení**, **znovu sestavit řešení**.)