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
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317562"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (32-bit MASM)

Zaregistruje funkci jako strukturované obslužné rutiny výjimek. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **.**  *Identifikátor* SAFESEH

## <a name="remarks"></a>Poznámky

*identifikátorem* musí být ID místně definované [procedury](proc.md) nebo procedury [EXTRN](extrn.md) . [Popisek](label-masm.md) není povolený. Okně. Direktiva SAFESEH vyžaduje možnost příkazového řádku [/SAFESEH](ml-and-ml64-command-line-reference.md) ml. exe.

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

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
