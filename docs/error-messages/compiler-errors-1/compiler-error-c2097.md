---
title: Chyba kompilátoru C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676587"
---
# <a name="compiler-error-c2097"></a>Chyba kompilátoru C2097

Neplatná inicializace

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Inicializace proměnné pomocí nekonstantním hodnoty.

1. Inicializace krátké adresy s Dlouhá adresa.

1. Inicializace místní struktury, sjednocení nebo pole s nekonstantním výrazem při kompilaci s **/Za**.

1. Inicializace pomocí výrazu obsahujícím operátor čárky.

1. Inicializace s výrazem, který není konstantní ani symbolické.