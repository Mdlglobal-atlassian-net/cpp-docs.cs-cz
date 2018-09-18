---
title: Chyba kompilátoru C2097 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da955f5382a1ebacdb507a69ed02627b11462e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021860"
---
# <a name="compiler-error-c2097"></a>Chyba kompilátoru C2097

Neplatná inicializace

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Inicializace proměnné pomocí nekonstantním hodnoty.

1. Inicializace krátké adresy s Dlouhá adresa.

1. Inicializace místní struktury, sjednocení nebo pole s nekonstantním výrazem při kompilaci s **/Za**.

1. Inicializace pomocí výrazu obsahujícím operátor čárky.

1. Inicializace s výrazem, který není konstantní ani symbolické.