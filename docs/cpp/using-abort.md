---
title: Používání příkazu abort | Dokumentace Microsoftu
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
ms.openlocfilehash: e63c3134dee6c316519dfcc34cff30b591b56460
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465393"
---
# <a name="using-abort"></a>Používání příkazu abort
Volání [přerušit](../c-runtime-library/reference/abort.md) funkce dojde k okamžitému ukončení. Funkce obchází běžný proces ničení inicializovaných globálních statických objektů. Také obchází všechna speciální zpracování zadaná pomocí funkce `atexit`.  
  
## <a name="see-also"></a>Viz také:  
 [Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)