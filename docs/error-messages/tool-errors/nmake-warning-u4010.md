---
title: Upozornění nástroje NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: f68da1893eec6325ccccfd0e2e2dd0e612f28eb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193131"
---
# <a name="nmake-warning-u4010"></a>Upozornění nástroje NMAKE U4010

' Target ': sestavení se nezdařilo; /K zadáte, pokračuje se...

Příkaz v bloku Commands pro daný cíl vrátil nenulový ukončovací kód. Parametr/K přizpůsobuje nástroji NMAKE, aby pokračoval v zpracovávání nesouvisejících částí sestavení a vystavování ukončovacího kódu 1 při dokončení relace NMAKE.

Pokud je zadaný cíl, sám o sobě závislý pro jiný cíl, aplikace NMAKE po tomto upozornění vydá upozornění [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) .
