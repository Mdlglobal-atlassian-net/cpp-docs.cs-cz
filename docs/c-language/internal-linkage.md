---
title: Vnitřní propojení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b5a02b7892bff0233e37bbd63020a4d2904ec3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094205"
---
# <a name="internal-linkage"></a>Vnitřní propojení

Pokud deklarace identifikátoru rozsahu souboru pro objekt nebo funkci obsahuje *storage-class-specifier* **statické**, má identifikátor vnitřní propojení. Jinak má identifikátor vnější propojení. Zobrazit [třídy úložiště](../c-language/c-storage-classes.md) diskuzi o *storage-class-specifier* neterminálu.

V rámci jedné jednotky překladu označuje každá instance identifikátoru s vnitřním propojením stejný identifikátor nebo funkci. Vnitřně propojené identifikátory jsou pro jednotku překladu jedinečné.

## <a name="see-also"></a>Viz také

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)