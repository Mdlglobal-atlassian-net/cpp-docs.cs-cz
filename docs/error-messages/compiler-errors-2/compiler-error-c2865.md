---
title: C2865 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b2c6c831fde18f9054e139a120d834a75b6950
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246213"
---
# <a name="compiler-error-c2865"></a>C2865 chyby kompilátoru
'function': Neplatný porovnání pro handle_or_pointer  
  
 Můžete porovnat odkazy na [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md) nebo spravovaná odkazové typy pouze rovnosti chcete zobrazit, pokud se vztahují ke stejnému objektu (==) nebo k různým objektům (! =).  
  
 Nelze porovnáním k řazení, protože modul runtime rozhraní .NET může přesunout spravované objekty v každém okamžiku změna výsledek testu.