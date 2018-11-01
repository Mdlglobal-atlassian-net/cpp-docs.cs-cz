---
title: Testování znaků
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: 31a90f28d710ffc1b58f9c6b3fcfd01fd8d2d00c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523198"
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