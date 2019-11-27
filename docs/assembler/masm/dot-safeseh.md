---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: df9798800da293e5e0b4f545a8442380b7ff9408
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397988"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32-bit MASM)

Zaregistruje funkci jako strukturované obslužné rutiny výjimek. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **.**  *Identifikátor* SAFESEH

## <a name="remarks"></a>Poznámky

*identifikátorem* musí být ID místně definované [procedury](../../assembler/masm/proc.md) nebo procedury [EXTRN](../../assembler/masm/extrn.md) . [Popisek](../../assembler/masm/label-masm.md) není povolený. Okně. Direktiva SAFESEH vyžaduje možnost příkazového řádku [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml. exe.

Další informace o strukturovaných obslužných rutinách výjimek naleznete v tématu [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Chcete-li například zaregistrovat bezpečnou obslužnou rutinu výjimky, vytvořte nový soubor MASM (takto), sestavte ho pomocí/SAFESEH a přidejte ho do propojených objektů.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
