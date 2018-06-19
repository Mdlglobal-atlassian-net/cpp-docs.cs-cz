---
title: 2.7.2.2 firstprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8e44ca52ba1f76d5b3791a1d08301bf06e7eab
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687397"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate
**Firstprivate** klauzule poskytuje větší funkce poskytované službou **privátní** klauzule. Syntaxe **firstprivate** klauzule vypadá takto:  
  
```  
firstprivate(variable-list)  
```  
  
 Proměnné zadané v *seznamu proměnné* mít **privátní** klauzule sémantikou, jak je popsáno v [části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25. Inicializace nebo vytváření se stane, jako kdyby byly na vlákno, před provádění vlákna konstruktu provádí jednou. Pro **firstprivate** klauzule na paralelní konstrukce počáteční hodnota nového privátní objektu je hodnota původní objekt, který existuje bezprostředně před paralelní konstrukce pro vlákno, které se zaznamená. Pro **firstprivate** klauzule ve sdílení práce konstrukt počáteční hodnota nový soukromý objekt pro každý podproces, který spouští konstrukce sdílení práce je hodnota původní objekt, který existuje před bod v čase, stejného podprocesu zaznamená konstrukce sdílení práce. Kromě toho pro objekty C++ nový soukromý objekt pro každé vlákno je kopírování zkonstruován z původní objekt.  
  
 Omezení, které mají **firstprivate** klauzule jsou následující:  
  
-   Zadaný v proměnné **firstprivate** klauzule nesmí mít typ neúplné nebo typu odkazu.  
  
-   Proměnná s typu třídy, který je zadaný jako **firstprivate** musí mít k přístupný, jednoznačným kopírovacího konstruktoru.  
  
-   Proměnné, která jsou soukromá v rámci paralelní oblasti nebo která se zobrazují **snížení** klauzuli **paralelní** – direktiva nelze zadat v **firstprivate** klauzule na Direktiva sdílení práce, která se sváže s paralelní konstrukce.