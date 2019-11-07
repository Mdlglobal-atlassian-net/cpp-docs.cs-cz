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
ms.openlocfilehash: 4577bd5d76949dfb777a359c80d91814f1c45fe2
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703945"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32-bit MASM)

Zaregistruje funkci jako strukturované obslužné rutiny výjimek. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> . Identifikátor SAFESEH

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

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>