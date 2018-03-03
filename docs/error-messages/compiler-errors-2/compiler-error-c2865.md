---
title: "C2865 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 149ca019ef30d66dba63bc927d79064a269d8c70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2865"></a>C2865 chyby kompilátoru
'function': Neplatný porovnání pro handle_or_pointer  
  
 Můžete porovnat odkazy na [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md) nebo spravovaná odkazové typy pouze rovnosti chcete zobrazit, pokud se vztahují ke stejnému objektu (==) nebo k různým objektům (! =).  
  
 Nelze porovnáním k řazení, protože modul runtime rozhraní .NET může přesunout spravované objekty v každém okamžiku změna výsledek testu.