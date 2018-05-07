---
title: Kompilátoru (úroveň 1) upozornění C4678 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73871d69198752e12a629d441982c2da47146517
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4678"></a>C4678 kompilátoru upozornění (úroveň 1)
Základní třída 'base_type' je méně přístupný než 'derived_type.  
  
Veřejného typu odvozuje od privátního typu. Pokud veřejného typu je vytvořena v odkazovaném sestavení, členové privátní základní typ nebudou přístupné.  
  
C4678 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**. Jedná se o chybu při použití **/CLR**, tak, aby měl základní třídu, která je méně přístupný, jeho odvozené třídy.  
