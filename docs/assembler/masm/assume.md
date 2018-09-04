---
title: PŘEDPOKLÁDEJME | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0e43548292d2ffecbebdaead6aa12d6dacc352
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693805"
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