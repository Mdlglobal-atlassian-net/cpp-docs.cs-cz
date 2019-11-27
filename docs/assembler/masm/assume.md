---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 73ef8bcc33087a56747b80f94482fcd6c50e3bf6
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399263"
---
# <a name="assume-32-bit-masm"></a>Předpokládejme (32-bit MASM)

Povoluje kontrolu chyb hodnot registru. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **Předpokládejme**  *segregister* __:__ *název* ⟦ __,__ *segregister* __:__ *název*... ⟧\
> **Předpokládejme**  *dataregister* __:__ *Zadejte* ⟦ __,__ *dataregistry* __:__ *Type*... ⟧\
> **Předpokládat**  *registraci* __: Chyba__ ⟦ __,__ *Register* __: Error__... ⟧\
> **Předpokládat** ⟦*registr* __:__ ⟧**Nothing** ⟦ __;__ *Register* __: Nothing__... ⟧

## <a name="remarks"></a>Poznámky

Po navýšení **předpokládáme** , že Assembler sleduje změny v hodnotách daných registrů. **Při** použití registru dojde k chybě. **Nic** neodebere kontrolu chyb registru. V jednom příkazu můžete kombinovat různé druhy předpokladů.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)
