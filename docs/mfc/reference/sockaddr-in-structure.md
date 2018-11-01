---
title: SOCKADDR_IN – struktura
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR_IN
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
ms.openlocfilehash: 22d02b2e3c6fd7151e59cad0f3233539c04a16e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431223"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN – struktura

V rodině adres sítě Internet `SOCKADDR_IN` struktura používá rozhraní Windows Sockets k určení adresy místního nebo vzdáleného koncového bodu pro připojení soketu.

## <a name="syntax"></a>Syntaxe

```
struct sockaddr_in{
    short sin_family;
    unsigned short sin_port;
struct in_addr sin_addr;
    char sin_zero[8];
};
```

#### <a name="parameters"></a>Parametry

*sin_family*<br/>
Rodina adres (musí být AF_INET).

*sin_port*<br/>
Port VIP.

*sin_addr*<br/>
IP adresa.

*Sin_Zero*<br/>
Odsazení, aby struktura stejnou velikost jako `SOCKADDR`.

## <a name="remarks"></a>Poznámky

To je forma `SOCKADDR` struktury specifické pro rodinu adres sítě Internet a může být převeden na `SOCKADDR`.

Součást adresy IP této struktury je typu `IN_ADDR`. `IN_ADDR` Struktura je definována v souboru hlaviček rozhraní Windows Sockets rozhraní WINSOCK. H následujícím způsobem:

```
struct in_addr {
    union {
        struct {
            unsigned char s_b1, s_b2, s_b3, s_b4;
        } S_un_b;
        struct {
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;
};
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** winsock2.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[SOCKADDR – struktura](../../mfc/reference/sockaddr-structure.md)
