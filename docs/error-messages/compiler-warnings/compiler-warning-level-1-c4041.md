---
title: Upozornění kompilátoru (úroveň 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 14ea6d9cae3b490107b656153bb68815026971e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164232"
---
# <a name="compiler-warning-level-1-c4041"></a>Upozornění kompilátoru (úroveň 1) C4041

limit kompilátoru: ukončuje se výstup prohlížeče.

Informace o prohlížeči překročily limit kompilátoru.

Toto upozornění může být způsobeno kompilací s [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) (informace o prohlížeči včetně místních proměnných).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Zkompiluje s/fr (informace o prohlížeči bez místních proměnných).

1. Zakáže výstup prohlížeče (zkompiluje bez/FR nebo/fr).
