---
title: Vnitřní propojení
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 857badd1284378a066c6c19c7159c1535e313593
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452363"
---
# <a name="internal-linkage"></a>Vnitřní propojení

Pokud deklarace identifikátoru rozsahu souboru pro objekt nebo funkci obsahuje *storage-class-specifier* **statické**, má identifikátor vnitřní propojení. Jinak má identifikátor vnější propojení. Zobrazit [třídy úložiště](../c-language/c-storage-classes.md) diskuzi o *storage-class-specifier* neterminálu.

V rámci jedné jednotky překladu označuje každá instance identifikátoru s vnitřním propojením stejný identifikátor nebo funkci. Vnitřně propojené identifikátory jsou pro jednotku překladu jedinečné.

## <a name="see-also"></a>Viz také

[Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)