---
title: Používání příkazu abort | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7231339ba4884445d7ad6b0161c6cff793c6db8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="using-abort"></a>Používání příkazu abort
Volání [abort](../c-runtime-library/reference/abort.md) funkce způsobí, že okamžitým ukončením. Funkce obchází běžný proces ničení inicializovaných globálních statických objektů. Také obchází všechna speciální zpracování zadaná pomocí funkce `atexit`.  
  
## <a name="see-also"></a>Viz také  
 [Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)