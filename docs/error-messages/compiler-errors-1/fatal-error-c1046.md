---
title: Závažná chyba C1046 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1046
dev_langs:
- C++
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 449b181167ef493c149e9e34cb2f1a681148411d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035462"
---
# <a name="fatal-error-c1046"></a>Závažná chyba C1046

limit kompilátoru: struktury jsou vnořené moc hluboko

Struktury, sjednocení nebo třídy překročen limit vnoření, což je 15 úrovně. Přepsání definice ke snížení úrovně vnoření. Rozdělení na dvě nebo více částí struktury, sjednocení nebo třídy pomocí `typedef` definovat nejméně jeden z vnořené struktury.