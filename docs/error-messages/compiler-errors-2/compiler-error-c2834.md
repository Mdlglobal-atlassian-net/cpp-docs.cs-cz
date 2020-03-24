---
title: Chyba kompilátoru C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201911"
---
# <a name="compiler-error-c2834"></a>Chyba kompilátoru C2834

operátor operátoru musí být globálně kvalifikovaný.

Operátory `new` a `delete` jsou svázány se třídou, kde se nacházejí. Rozlišení oboru nelze použít k výběru verze `new` nebo `delete` z jiné třídy. Chcete-li implementovat více forem operátoru `new` nebo `delete`, vytvořte verzi operátoru s dalšími formálními parametry.
