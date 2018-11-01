---
title: LINGER – struktura
ms.date: 11/04/2016
f1_keywords:
- LINGER
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
ms.openlocfilehash: 78f1a5ce993373ea9e477262f0779515c52dbd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495314"
---
# <a name="linger-structure"></a>LINGER – struktura

`LINGER` Struktura se používá pro manipulaci s možností SO_LINGER a SO_DONTLINGER `CAsyncSocket::GetSockOpt`.

## <a name="syntax"></a>Syntaxe

```
struct linger {
    u_short l_onoff;            // option on/off
    u_short l_linger;           // linger time
};
```

## <a name="remarks"></a>Poznámky

Nastavení možnosti SO_DONTLINGER brání blokování u členské funkce `Close` při čekání na unsent dat k odeslání. Nastavení této možnosti je ekvivalentní nastavení SO_LINGER s `l_onoff` nastavena na hodnotu 0.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winsock2.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)<br/>
[CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

