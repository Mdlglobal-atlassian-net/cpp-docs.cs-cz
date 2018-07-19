---
title: Omezení obslužných rutin výjimek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13971ede3aef6d223b1c631c4a28f8bf190e7174
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37938780"
---
# <a name="restrictions-on-exception-handlers"></a>Omezení obslužných rutin výjimek
Hlavním omezením použití obslužných rutin výjimek v kódu je nemožnost použít **goto** příkazu Přejít do **__try** blok příkazů. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. Můžete přejít z celkového počtu **__try** příkaz blokovat a zanořovat obslužné rutiny výjimek dle libosti.  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)