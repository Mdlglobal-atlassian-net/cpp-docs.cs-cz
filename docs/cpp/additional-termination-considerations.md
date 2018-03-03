---
title: "Důležité informace k ukončování další | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: acbe2332-9d8a-4a58-a471-dd652a837384
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3f2cd02a80ce1dc1002c9fa1bea1cc1dd22ed68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="additional-termination-considerations"></a>Další důležité informace k ukončování
Můžete ukončení programu C++ pomocí **ukončete**, `return`, nebo **abort**. Pomocí funkce `atexit` lze přidat funkci, která bude zpracována před ukončením programu. Tyto funkce jsou popsány v následujících částech.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění a ukončení](../cpp/startup-and-termination-cpp.md)