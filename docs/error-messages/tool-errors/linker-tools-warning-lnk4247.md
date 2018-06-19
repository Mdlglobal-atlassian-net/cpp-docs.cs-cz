---
title: Upozornění linkerů Lnk4247 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6096bbfba9c60d8ed28aa660d078cd155f0316a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301200"
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