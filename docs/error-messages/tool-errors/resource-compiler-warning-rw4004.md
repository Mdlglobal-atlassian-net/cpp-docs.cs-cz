---
title: Upozornění kompilátoru prostředků RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182341"
---
# <a name="resource-compiler-warning-rw4004"></a>Upozornění kompilátoru prostředků RW4004

Znak ASCII není ekvivalentní kódu virtuálního klíče.

Řetězcový literál byl použit pro kód virtuálního klíče v akcelerátoru typu VIRTKEY.

Toto upozornění vám umožní pokračovat, ale mějte na paměti, že vygenerované klávesy akcelerátoru nemusí odpovídat řetězci, který jste uvedli. (VIRTKEYs použít jiné kódy klíčů než akcelerátory ASCII.)

I když jsou řetězcové literály syntakticky platné, můžete zajistit, abyste získali akcelerátor, který požadujete, pomocí **VK_\* #define** hodnoty v systému Windows. h.
