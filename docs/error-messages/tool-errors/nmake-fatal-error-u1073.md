---
title: Závažná chyba nástroje NMAKE U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 2aa02fd86906bd545373a313fa5e6e409ffb3cf9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582270"
---
# <a name="nmake-fatal-error-u1073"></a>Závažná chyba nástroje NMAKE U1073

Nevím, jak provést "targetname.

Zadaná cílová neexistuje a není žádný příkaz k provedení nebo odvozené pravidlo použít.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zkontrolujte, zda cílový název.

1. Pokud *targetname* je pseudotarget, zadejte jako cíl v jiném bloku popis.

1. Pokud *targetname* je volání makra, je nutné Nerozbaluje řetězec s hodnotou null.