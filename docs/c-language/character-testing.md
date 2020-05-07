---
title: Testování znaků
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740100"
---
# <a name="character-testing"></a>Testování znaků

**ANSI 4.3.1** Sady testovaných znaků `isalnum`pro funkce, `isalpha`, `iscntrl`, `islower`, a `isupper` `isprint`

Následující seznam popisuje implementaci těchto funkcí v kompilátoru jazyka Microsoft C.

|Funkce|Testuje|
|--------------|---------------|
|`isalnum`|Znaky 0-9, A-Z, A-z ASCII 48-57, 65-90, 97-122|
|`isalpha`|Znaky A – Z, a – z ASCII 65-90, 97-122|
|`iscntrl`|ASCII 0 -31, 127|
|`islower`|Znaky a – z ASCII 97-122|
|`isprint`|Znaky A – Z, a-z, 0-9, interpunkční znaménka, mezera ASCII 32-126|
|`isupper`|Znaky A – Z ASCII 65-90|

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)
