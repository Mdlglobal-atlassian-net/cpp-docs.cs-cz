---
title: Vnitřní objekty a vložené sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2b99eedcdd81a96dc3091046a4f62ffe002509
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464519"
---
# <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení
Jeden omezení x64 kompilátoru je vložený assembler nepodporují. To znamená, že funkce, které nelze zapsat do jazyka C nebo C++ se buď musí být napsány podprogramy nebo jako vnitřní funkce podporovány kompilátorem. Některé funkce jsou citlivé na výkon, některé nikoli. Citlivé na výkon funkce by měla být implementována jako vnitřní funkce.  
  
 Vnitřní objekty podporovány kompilátorem jsou popsány v [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)