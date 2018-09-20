---
title: Sockaddr – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac6e433c0bbc70e6e1caa79599d5388aef49b4c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435282"
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

