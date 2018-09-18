---
title: Testování znaků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c558c5d32f75561d5722a656450d5f18f5166a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084936"
---
# <a name="character-testing"></a>Testování znaků

**ANSI 4.3.1** znakové sady testovaných funkcí `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint`, a `isupper` funkce

Následující seznam popisuje implementaci těchto funkcí v kompilátoru jazyka Microsoft C.

|Funkce|Testuje|
|--------------|---------------|
|`isalnum`|Znaky 0 - 9, A-Z, a – z ASCII 48 – 57, 65 – 90, 97 – 122|
|`isalpha`|Znaky A-Z, a – z ASCII 65 – 90, 97 – 122|
|`iscntrl`|ASCII 0-31, 127|
|`islower`|Znaky a – z ASCII 97 – 122|
|`isprint`|Znaky A-Z, a – z, 0 - 9, interpunkce, mezera ASCII 32 – 126|
|`isupper`|Znaky A – Z ASCII 65 – 90|

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)