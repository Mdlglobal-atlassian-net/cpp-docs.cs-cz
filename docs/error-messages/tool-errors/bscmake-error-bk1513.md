---
title: Chyba nástroje BSCMAKE BK1513 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68f49ce11c95672abd40ecbaf1873a564a3912e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118801"
---
# <a name="bscmake-error-bk1513"></a>Chyba nástroje BSCMAKE BK1513

nepřírůstková aktualizace vyžaduje všechny. Soubory SBR

BscMake – nemůže vytvořit nového procházení (.bsc) souboru, protože nejméně jeden soubor .sbr se zkrátí. Názvy souborů zkrácený .sbr najdete v článku [nástroje BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) upozornění, které nejsou poskytnuty k této chybě.

BSCMAKE souboru .BSC nástrojem aktualizujte soubor .sbr zkrácený ale nemůže vytvořit nové. BscMake – může sestavení souboru .bsc nového z následujících důvodů:

- Chybí soubor .bsc.

- Chybný název souboru zadaný pro soubor .bsc.

- Soubor BSC poškozená.

Chcete-li tento problém vyřešit, odstraňte soubory .sbr zkrácený a opětovné sestavení, nebo Vyčistit řešení a znovu sestavit. (V integrovaném vývojovém prostředí, zvolte **sestavení**, **Vyčistit řešení**a klikněte na tlačítko **sestavení**, **znovu sestavit řešení**.)