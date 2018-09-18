---
title: Závažná chyba C1126 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f014aafc60a36bfbb4edad50e7e3ceede6e3c8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062472"
---
# <a name="fatal-error-c1126"></a>Závažná chyba C1126

'identifier': automatické přidělování překračuje velikost

Místo přidělené pro místní proměnné funkce (včetně omezené množství využité kompilátorem, jako je například dalších 20 bajtů pro vyměnitelné funkce), překračuje limit.

Chcete-li opravit tuto chybu, použijte `malloc` nebo `new` přidělit velkých objemů dat.