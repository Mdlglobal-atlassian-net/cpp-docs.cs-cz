---
title: 2.6.1 master – konstrukce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a60a8df380fdcc0052d8fe2d070c8d926bcb28f8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689552"
---
# <a name="261-master-construct"></a>2.6.1 master – konstrukce
**Hlavní** – direktiva identifikuje konstruktor, který určuje strukturovaných blok, který se spustí hlavní vlákno týmu. Syntaxe **hlavní** – Direktiva vypadá takto:  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 Jiná vlákna v týmu se neprovedou přidružené strukturovaných bloku. Neexistuje žádné předpokládané bariéry buď na položku na nebo ukončení z hlavní konstrukce.