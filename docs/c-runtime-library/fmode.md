---
title: _fmode
ms.date: 11/04/2016
f1_keywords:
- fmode
- _fmode
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
ms.openlocfilehash: a41d665eab50203fc3bb176f8bb1bbc30737e844
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343885"
---
# <a name="fmode"></a>_fmode

`_fmode` Proměnné se nastaví výchozí režim překladu souboru textový nebo binární překlad. Tato globální proměnná se už nepoužívá pro bezpečnější funkční verze [_get_fmode –](../c-runtime-library/reference/get-fmode.md) a [_set_fmode –](../c-runtime-library/reference/set-fmode.md), který by měl být zastoupen globální proměnnou. Je deklarována v souboru Stdlib.h následujícím způsobem.

## <a name="syntax"></a>Syntaxe

```
extern int _fmode;
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení `_fmode` je `_O_TEXT` pro překlad textu režimu. `_O_BINARY` je toto nastavení pro binárním režimu.

Můžete změnit hodnotu `_fmode` třemi způsoby:

- Propojení s knihovnou Binmode.obj. Tím se změní nastavení počáteční `_fmode` k `_O_BINARY`, způsobí všechny soubory kromě `stdin`, `stdout`, a `stderr` otevřít v binárním režimu.

- Volání `_get_fmode` nebo `_set_fmode` pro získání nebo nastavení `_fmode` globální proměnné, v uvedeném pořadí.

- Změňte hodnotu vlastnosti `_fmode` přímo nastavením ve svém programu.

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
