---
title: "Důležité informace k ukončování další | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: acbe2332-9d8a-4a58-a471-dd652a837384
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 134f08c8745105daa64b5401c7dbccd726e02d16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="additional-termination-considerations"></a>Další důležité informace k ukončování
Můžete ukončení programu C++ pomocí **ukončete**, `return`, nebo **abort**. Pomocí funkce `atexit` lze přidat funkci, která bude zpracována před ukončením programu. Tyto funkce jsou popsány v následujících částech.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění a ukončení](../cpp/startup-and-termination-cpp.md)