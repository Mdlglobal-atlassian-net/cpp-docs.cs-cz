---
title: Chyba kompilátoru C2722 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2722
dev_langs:
- C++
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9138172bb108095c4e72407f1e17e8f4fa2370c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082661"
---
# <a name="compiler-error-c2722"></a>Chyba kompilátoru C2722

':: operator': neplatné po příkazu operátoru; operátor ' operátor '

`operator` Příkaz předefinování `::new` nebo `::delete`. `new` a `delete` operátory jsou globální, takže operátoru rozlišení oboru (`::`) nemá význam. Odeberte `::` operátor.