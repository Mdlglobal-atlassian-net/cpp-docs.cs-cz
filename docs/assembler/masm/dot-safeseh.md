---
title: . SAFESEH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAFESEH
dev_langs: C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bcbcafef4ad548ab784740a4130fc1679bf43f0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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