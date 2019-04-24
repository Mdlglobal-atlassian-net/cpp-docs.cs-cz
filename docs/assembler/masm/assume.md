---
title: ASSUME
ms.date: 08/30/2018
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 97a57cc8a1acccf70572ff963e496aa79fa3ab43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166461"
---
# <a name="assume"></a>ASSUME

Povolí kontrolu chyb pro hodnot registru.

## <a name="syntax"></a>Syntaxe

> PŘEDPOKLÁDAT *segregister*:*název* [[, *segregister*:*název*]]...<br/>
> PŘEDPOKLÁDAT *dataregister*:*typ* [[, *dataregister*:*typ*]]...<br/>
> PŘEDPOKLÁDAT *zaregistrovat*: Chyba [[, *zaregistrovat*: Chyba]]...<br/>
> PŘEDPOKLÁDAT [[*zaregistrovat*:]] nic [[, *zaregistrovat*: nic]]...

## <a name="remarks"></a>Poznámky

Po `ASSUME` začíná platit, sleduje změny hodnot registrů dané assembler. **Chyba** vygeneruje chybu, pokud se používá do registru. **NIC** odebere registraci kontroly chyb. Můžete kombinovat různé druhy předpoklady v jednom příkazu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>