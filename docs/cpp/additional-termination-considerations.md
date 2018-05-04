---
title: Důležité informace k ukončování další | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: acbe2332-9d8a-4a58-a471-dd652a837384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b634c7c792d4462f96f022f223d0b1eec2a750ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="additional-termination-considerations"></a>Další důležité informace k ukončování
Můžete ukončení programu C++ pomocí **ukončete**, `return`, nebo **abort**. Pomocí funkce `atexit` lze přidat funkci, která bude zpracována před ukončením programu. Tyto funkce jsou popsány v následujících částech.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění a ukončení](../cpp/startup-and-termination-cpp.md)