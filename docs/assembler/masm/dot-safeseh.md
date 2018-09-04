---
title: . SAFESEH | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10f3c751fe05c118203bb5eeff6c5cba6ec1c8b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693165"
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
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>