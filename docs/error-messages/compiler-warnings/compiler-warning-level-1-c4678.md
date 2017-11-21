---
title: "Kompilátoru (úroveň 1) upozornění C4678 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4678
dev_langs: C++
helpviewer_keywords: C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 52ebd41531cd5fdfd7aeb6ba6f52cf8981fa6120
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4678"></a>C4678 kompilátoru upozornění (úroveň 1)
Základní třída 'base_type' je méně přístupný než 'derived_type.  
  
Veřejného typu odvozuje od privátního typu. Pokud veřejného typu je vytvořena v odkazovaném sestavení, členové privátní základní typ nebudou přístupné.  
  
C4678 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**. Jedná se o chybu při použití **/CLR**, tak, aby měl základní třídu, která je méně přístupný, jeho odvozené třídy.  
