---
title: "Upozornění kompilátoru prostředků RW4004 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0249f7d01ee344f0fa17bdc39e58e9fce26c9b25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rw4004"></a>Upozornění kompilátoru prostředků RW4004
Není ekvivalentní virtuální klíče kódu znaků ASCII  
  
 Řetězcový literál byl použit pro virtuální kód v akcelerátor VIRTKEY typu.  
  
 Toto upozornění můžete pokračovat, ale mějte na paměti, že klávesy akcelerátoru generované nemusí odpovídat řetězec, který jste uvedli. (VIRTKEYs použít různé klíče kódy než ASCII akcelerátorů.)  
  
 Textové literály jsou syntakticky, můžete jenom zajistit, že dostanete akcelerátoru chcete pomocí **jich\* #define** hodnoty v odkazující na Windows.