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
ms.openlocfilehash: 8775f752a541d2a250e9c1c5a0c325b684335988
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464597"
---
# <a name="restrictions-on-exception-handlers"></a>Omezení obslužných rutin výjimek
Hlavním omezením použití obslužných rutin výjimek v kódu je nemožnost použít **goto** příkazu Přejít do **__try** blok příkazů. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. Můžete přejít z celkového počtu **__try** příkaz blokovat a zanořovat obslužné rutiny výjimek dle libosti.  
  
## <a name="see-also"></a>Viz také:  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)