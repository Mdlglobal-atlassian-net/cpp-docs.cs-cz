---
title: Závažná chyba C1852 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0adfa7eed25f1902300fa2378b8ffc19eb8dfafd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023797"
---
# <a name="fatal-error-c1852"></a>Závažná chyba C1852

'filename' není platný předkompilovaného hlavičkového souboru

Soubor není předkompilovanou hlavičku.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Neplatný soubor určený parametrem **/Yu** nebo **#pragma hdrstop**.

1. Kompilátor předpokládá příponu souboru .pch, pokud neurčíte jinak.