---
title: Upozornění linkerů Lnk4247 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 517605993199942f863faa78e14a022529214a64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4247"></a>Upozornění linkerů LNK4247
vstupní bod 'decorated_function_name' již má atribut vlákna; atribut ignorovat  
  
 Vstupní bod, zadaným [/Entry (Symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md), měl atribut vláken, ale [/CLRTHREADATTRIBUTE (nastavit CLR vláken atribut)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) také zadaná, se jiný model vláken.  
  
 Linkeru ignorovat hodnotu zadanou pomocí /CLRTHREADATTRIBUTE.  
  
 Chcete-li vyřešit toto upozornění:  
  
-   Odeberte /CLRTHREADATTRIBUTE z buildu.  
  
-   Odeberte atribut z vašeho souboru se zdrojovým kódem.  
  
-   Odeberte i atribut ze zdroje a /CLRTHREADATTRIBUTE z buildu a přijměte výchozí model vláken CLR.  
  
-   Změňte hodnotu předaný /CLRTHREADATTRIBUTE, tak, aby ho souhlasí s atributem ve zdroji.  
  
-   Změňte atribut ve zdroji, tak, aby ho souhlasí s hodnotou předaný /CLRTHREADATTRIBUTE.  
  
 Následující ukázka generuje LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```