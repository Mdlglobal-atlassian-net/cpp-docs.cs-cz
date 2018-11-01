---
title: .SAFESEH
ms.date: 08/30/2018
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: adfb9106095de3d15bafb67172b001d0f4597418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649849"
---
# <a name="safeseh"></a>.SAFESEH

Zaregistruje funkci jako strukturovanou obslužnou rutinou.

## <a name="syntax"></a>Syntaxe

> . Identifikátor SAFESEH

## <a name="remarks"></a>Poznámky

*identifikátor* musí být ID pro místně definovaný [PROC](../../assembler/masm/proc.md) nebo [EXTRN](../../assembler/masm/extrn.md) PROC. A [popisek](../../assembler/masm/label-masm.md) není povolený. Na. SAFESEH – direktiva vyžaduje [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe možnost příkazového řádku.

Další informace o obslužné rutiny strukturovaných výjimek naleznete v tématu [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Například zaregistrovat obslužnou rutinu výjimky bezpečné, vytvořte nový soubor MASM (následujícím způsobem), sestavit pomocí/SAFESEH a přidejte ho do propojené objekty.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>