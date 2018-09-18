---
title: Závažná chyba nástroje NMAKE U1045 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2b9be4f7440d9e79d603e917c1886aebe7c44af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056882"
---
# <a name="nmake-fatal-error-u1045"></a>Závažná chyba nástroje NMAKE U1045

Vytvoření podřízeného procesu selhalo: zpráva

Program nebo volané NMAKE se nezdařila z důvodu daný příkaz. Když NMAKE volá jiný program – například kompilátoru nebo linkeru – volání může selhat nebo chybu mohou být vráceny názvem programu. Tato zpráva se používá k ohlaste chybu.

Chcete-li vyřešit tento problém, nejprve určete příčinu chyby. Můžete použít příkazy hlášené NMAKE [/N](../../build/nmake-options.md) možnost, pokud chcete ověřit nastavení prostředí a opakovat akce prováděné NMAKE na příkazovém řádku.