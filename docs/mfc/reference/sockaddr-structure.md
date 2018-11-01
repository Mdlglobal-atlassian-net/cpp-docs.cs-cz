---
title: SOCKADDR – struktura
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
ms.openlocfilehash: 68d5261c6520b5baee8495b72a0b9d234a35a185
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543842"
---
# <a name="sockaddr-structure"></a>SOCKADDR – struktura

Struktura `SOCKADDR` se používá k uchování adresy protokolu IP pro počítače podílející se na komunikaci prostřednictvím rozhraní Windows Sockets.

## <a name="syntax"></a>Syntaxe

```
struct sockaddr {
    unsigned short sa_family;
    char sa_data[14];
};
```

#### <a name="parameters"></a>Parametry

*sa_family*<br/>
Skupina adres soketu.

*sa_data*<br/>
Maximální velikost všech různých struktur adres soketu.

## <a name="remarks"></a>Poznámky

Sada Microsoft TCP/IP Sockets Developer's Kit podporuje pouze domény internetových adres. Pro skutečné vyplnění hodnot všech částí adresy se používá datová struktura `SOCKADDR_IN`, která je upravena výslovně pro tento formát adresy. Datové struktury `SOCKADDR` a `SOCKADDR_IN` mají stejnou velikost. Přecházet mezi těmito dvěma typy struktur lze pouhým přetypováním.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winsock2.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[SOCKADDR_IN – struktura](../../mfc/reference/sockaddr-in-structure.md)<br/>
[CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)<br/>
[CSocket::Create](../../mfc/reference/csocket-class.md#create)

