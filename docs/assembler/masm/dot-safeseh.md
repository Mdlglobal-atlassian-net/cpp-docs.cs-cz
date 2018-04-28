---
title: . SAFESEH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8ea34448b4dae0525e7feb2fd7cca310a95a6e3c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="safeseh"></a>.SAFESEH
Zaregistruje funkci jako obslužná rutina strukturovaných výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.SAFESEH identifier  
```  
  
## <a name="remarks"></a>Poznámky  
 *identifikátor* musí být ID pro místně definované [PROC](../../assembler/masm/proc.md) nebo [extrn –](../../assembler/masm/extrn.md) PROC. A [popisek](../../assembler/masm/label-masm.md) není povolen. Na. SAFESEH – direktiva vyžaduje [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe možnost příkazového řádku.  
  
 Další informace o obslužné rutiny výjimek strukturovaných najdete v tématu [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).  
  
 Například zaregistrovat obslužná rutina bezpečné výjimky, vytvořte nový soubor MASM (takto), sestavte s/SAFESEH a přidat jej do propojené objekty.  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)