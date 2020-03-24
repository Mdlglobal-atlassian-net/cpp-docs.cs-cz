---
title: Upozornění nástroje NMAKE U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193144"
---
# <a name="nmake-warning-u4011"></a>Upozornění nástroje NMAKE U4011

' Target ': nejsou k dispozici všechny závislé položky; cíl není sestaven.

Závislá hodnota daného cíle buď neexistuje, nebo byla zastaralá a příkaz pro aktualizaci závislého kódu vrátil nenulový ukončovací kód. Parametr/K přizpůsobuje nástroji NMAKE, aby pokračoval v zpracovávání nesouvisejících částí sestavení a vystavování ukončovacího kódu 1 při dokončení relace NMAKE.

Toto upozornění předchází upozornění [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) pro všechny závislé položky, které se nepodařilo vytvořit nebo aktualizovat.
