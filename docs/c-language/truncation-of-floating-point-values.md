---
title: Zkrácení hodnot s plovoucí desetinnou čárkou | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, truncation
ms.assetid: 051a6e22-c636-4af8-9ac4-40160f4affca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b30700b52e7cbbbc295d6050b03283b4b45a0b08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103812"
---
# <a name="truncation-of-floating-point-values"></a>Zkrácení hodnot s plovoucí desetinnou čárkou

**ANSI 3.2.1.4** směr zkrácení nebo zaokrouhlování při převodu čísla s plovoucí desetinnou čárkou na užší číslo s plovoucí desetinnou čárkou

Kdykoli dojde k podtečení, hodnota proměnné s plovoucí desetinnou čárkou je zaokrouhlena na nulu. Přetečení může způsobit chybu modulu runtime nebo vytvořit nepředvídatelnou hodnotu v závislosti na určených optimalizacích.

## <a name="see-also"></a>Viz také

[Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)