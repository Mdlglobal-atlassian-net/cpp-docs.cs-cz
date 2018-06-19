---
title: Upozornění kompilátoru prostředků RW4004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94bd1c043ac5660c5cb8fc8b2bfa1dd2f6968b55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337103"
---
# <a name="resource-compiler-warning-rw4004"></a>Upozornění kompilátoru prostředků RW4004
Není ekvivalentní virtuální klíče kódu znaků ASCII  
  
 Řetězcový literál byl použit pro virtuální kód v akcelerátor VIRTKEY typu.  
  
 Toto upozornění můžete pokračovat, ale mějte na paměti, že klávesy akcelerátoru generované nemusí odpovídat řetězec, který jste uvedli. (VIRTKEYs použít různé klíče kódy než ASCII akcelerátorů.)  
  
 Textové literály jsou syntakticky, můžete jenom zajistit, že dostanete akcelerátoru chcete pomocí **jich\* #define** hodnoty v odkazující na Windows.