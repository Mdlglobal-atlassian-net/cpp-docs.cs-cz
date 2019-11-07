---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 4bf8f0c41e9ce3e296cf201efd4fd9be2033cbdb
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2019
ms.locfileid: "73702463"
---
# <a name="assume-32-bit-masm"></a>Předpokládejme (32-bit MASM)

Povoluje kontrolu chyb hodnot registru. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> PŘEPOKLÁDEJME *segregister*:*Name* [[; *segregister*:*Name*]]...<br/>
> PŘEPOKLÁDEJME *dataregister*:*typ* [[, *dataregister*:*Type*]]...<br/>
> PŘEDPOKLÁDAT *registraci*: Chyba [[, *Register*: Error]]...<br/>
> PŘEPOKLÁDEJME [[*Register*:]] Nothing [[; *Register*: Nothing]]...

## <a name="remarks"></a>Poznámky

Jakmile je `ASSUME` vstoupí v platnost, assembler sleduje změny hodnot daných registrů. **Při** použití registru dojde k chybě. **Nic** neodebere kontrolu chyb registru. V jednom příkazu můžete kombinovat různé druhy předpokladů.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>