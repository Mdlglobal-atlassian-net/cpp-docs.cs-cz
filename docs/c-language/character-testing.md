---
title: Testování znaků
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147188"
---
# <a name="character-testing"></a>Testování znaků

**ANSI 4.3.1** znakové sady testovaných funkcí `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint`, a `isupper` funkce

Následující seznam popisuje implementaci těchto funkcí v kompilátoru jazyka Microsoft C.

|Funkce|Testuje|
|--------------|---------------|
|`isalnum`|Znaky 0 - 9, A-Z, a – z ASCII 48 – 57, 65 – 90, 97 – 122|
|`isalpha`|Znaky A-Z, a – z ASCII 65 – 90, 97 – 122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|Znaky a – z ASCII 97 – 122|
|`isprint`|Znaky A-Z, a – z, 0 - 9, interpunkce, mezera ASCII 32 – 126|
|`isupper`|Znaky A – Z ASCII 65 – 90|

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)
